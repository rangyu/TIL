# 서브도메인을 특정 폴더와 연동하기 (mod_rewrite)

## DNS 설정  

DNS 설정으로 가서 CNAME 레코드를 추가한다. 만들고자 하는 `subdomain.example.com`이 원래의 도메인 주소를 `example.com`을 가리키도록 설정한다.


## RewriteRule 작성

아파치 환경설정 파일에 다음과 같은 RewriteRule을 추가한다. 

```
RewriteEngine On
RewriteCond $1 !^(subdomain)/
RewriteCond %{HTTP_HOST} ^subdomain\.example\.com [NC]
RewriteRule ^(.*)$ /mydir/$1 [L]
```

이때 `subdomain`, `example.com`, `mydir`은 해당하는 값으로 변경하고 사용하면 된다.

## 아파치 재시작

변경 후 아파치를 재시작한다. 

### 우분투
```
sudo service apache2 restart
```

### 비트나미
```
sudo /opt/bitnami/ctlscript.sh restart apache
```

### Mac
```
sudo apachectl graceful
```

이제 서브 도메인이 연결한 폴더 내 파일과 제대로 연결되는 것을 볼 수 있다.
