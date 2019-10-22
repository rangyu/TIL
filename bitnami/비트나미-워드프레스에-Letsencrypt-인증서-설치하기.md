# 비트나미 워드프레스에 Let’s Encrypt 인증서 설치하기

Let’s Encrypt는 무료로 사용할 수 있는 SSL 인증서다. 이 글에서는 비트나미 워드프레스에서 Let’s Encrypt 인증서를 설치하는 방법을 알아보겠다.

- 참고한 문서 (https://docs.bitnami.com/aws/how-to/generate-install-lets-encrypt-ssl/)

## Lego 클라이언트 설치하기

깃허브 저장소에서 Lego 최신 버전 다운받는다.
```bash
cd /tmp
curl -Ls https://api.github.com/repos/xenolf/lego/releases/latest | grep browser_download_url | grep linux_amd64 | cut -d '"' -f 4 | wget -i - tar xf lego_vX.Y.Z_linux_amd64.tar.gz
```

다운받은 Lego 압축파일명을 확인한다.
```bash
ls
lego_v1.2.1_linux_amd64.tar.gz
```

다운받은 파일 압축을 푼다. 
```bash
tar xf lego_v1.2.1_linux_amd64.tar.gz
```

생성된 lego 파일을 /usr/local/bin으로 옮긴다. 
```bash
sudo mv lego /usr/local/bin/lego
```
이제 Lego 클라이언트를 사용할 준비를 마쳤다.


## Let’s Encrypt SSL 인증서 발급받기

비트나미 서비스를 잠시 꺼둔다.
```bash
sudo /opt/bitnami/ctlscript.sh stop
```

설치한 lego 클라이언트를 이용해서 Let's Encrypt 인증서를 발급받는다.
```bash
sudo lego --tls --email="EMAIL-ADDRESS" --domains="DOMAIN" --domains="www.DOMAIN" --path="/etc/lego" --http run
```
domains 옵션을 사용했기 때문에 최소 2개 이상의 도메인을 입력해야 한다. mydomain.com과 www.mydomain.com를 포함한 2개 이상의 도메인을 모두 입력한다.

```
Do you accept the TOS? Y/n
```

`Y`를 눌러 동의하면 다음으로 진행된다.


## 아파치 환경설정 수정하기

기존 설정된 인증서는 백업하고 방금 발급받은 인증서를 웹서버 인증서로 사용하기 위해 다음과 같은 명령어를 입력한다. 

```bash
sudo mv /opt/bitnami/apache2/conf/server.crt /opt/bitnami/apache2/conf/server.crt.old
sudo mv /opt/bitnami/apache2/conf/server.key /opt/bitnami/apache2/conf/server.key.old
sudo mv /opt/bitnami/apache2/conf/server.csr /opt/bitnami/apache2/conf/server.csr.old
sudo ln -s /etc/lego/certificates/DOMAIN.key /opt/bitnami/apache2/conf/server.key
sudo ln -s /etc/lego/certificates/DOMAIN.crt /opt/bitnami/apache2/conf/server.crt
```

소유자는 root, 퍼미션은 600으로 변경한다.

```
sudo chown root:root /opt/bitnami/apache2/conf/server*
sudo chmod 600 /opt/bitnami/apache2/conf/server*
```


비트나미 서비스를 재시작한다.
```bash
sudo /opt/bitnami/ctlscript.sh start
```

이제 https로 접속이 제대로 되는 것을 볼 수 있다.


## http로 접속 시 https로 리다이렉트 설정하기

``httpd-prefix.conf`` 설정파일을 연다.
```bash
vi /opt/bitnami/apps/wordpress/conf/httpd-prefix.conf
```

다음과 같은 RewriteRule을 추가한다. 
```
RewriteCond %{HTTPS} !=on
RewriteRule ^/(.*) https://%{SERVER_NAME}/$1 [R,L]
```

비트나미 서비스를 재시작한다.
```bash
sudo /opt/bitnami/ctlscript.sh restart
```

이후부터 http로 접속 시 자동으로 https로 변경된다. 

