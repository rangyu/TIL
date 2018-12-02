# Mac에서 가상 호스트 (VirtualHost) 설정하기

이 글에서는 Mac에서 가상 호스틍(VirtualHost)를 설정하는 방법에 대해 알아본다. 



## 1. httpd.conf 수정하기

먼저 ``httpd.conf`` 파일을 연다. 

```bash
sudo vi /etc/apache2/httpd.conf
```

vhost로 검색해서 다음의 두 군데 주석을 제거한다.

```bash
LoadModule vhost_alias_module libexec/apache2/mod_vhost_alias.so
```

```bash
# Virtual hosts
Include /private/etc/apache2/extra/httpd-vhosts.conf
```



## 2. httpd-vhosts.conf 수정하기

``httpd-vhost.conf`` 파일을 수정한다.

```bash
sudo vi /etc/apache2/extra/httpd-vhosts.conf
```

다음과 같은 설정을 추가한다.

```
<VirtualHost *:80>
    ServerName local.mysite.com
    ServerAlias www.local.mysite.com
    DocumentRoot "/Users/username/mydirectory"
    <Directory "/Users/username/mydirectory">
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>
```

위의 서버명과 디렉토리 루트는 해당하는 값으로 바꿔서 넣어준다. 



## 3. DNS 주소 추가하기

DNS 주소를 추가하기 위해 ``hosts`` 파일을 연다.

```bash
sudo vi /private/etc/hosts
```

``httpd-vhosts.conf`` 에 넣었던 도메인을 추가한다.

```
127.0.0.1       local.mysite.com
```

아파치를 재시작한다.

```
sudo apachectl graceful
```

이제 해당 도메인으로 접속하면 아까 설정해둔 디렉토리로 호스팅된다.