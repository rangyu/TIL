# 비트나미 워드프레스에 서브도메인을 vhost로 설정하기

## DNS 설정 변경

DNS 설정에서 `mysub.domain.com`의 A 레코드 값을 해당 서버의 IP로 바꾼다.


## 디렉토리 생성

도메인에 연결할 루트 디렉토리(myapp)를 생성한다.

```
mkdir /opt/bitnami/apps/wordpress/myapp
```
### 소유자:소유그룹 변경
소유자는 bitnami, 소유그룹은 daemon으로 변경한다. 

```
sudo chown -R bitnami:daemon /opt/bitnami/apps/wordpress/myapp
```

## bitnami.conf 수정 

### `bitnami.conf` 열기

```
sudo vi /opt/bitnami/apache2/conf/bitnami/bitnami.conf
```

### 디폴트 설정을 제거한다

다음의 부분을 찾아서 삭제 혹은 주석처리한다.

```
#<VirtualHost _default_:80>
#  DocumentRoot "/opt/bitnami/apache2/htdocs"
#  <Directory "/opt/bitnami/apache2/htdocs">
#    Options Indexes FollowSymLinks
#    AllowOverride All
#    <IfVersion < 2.3 >
#      Order allow,deny                       
#      Allow from all
#    </IfVersion>
#    <IfVersion >= 2.3 >
#      Require all granted 
#    </IfVersion>
#  </Directory>
#   
#  # Error Documents
#  ErrorDocument 503 /503.html
#
#  # Bitnami applications installed with a prefix URL (default)
#  Include "/opt/bitnami/apache2/conf/bitnami/bitnami-apps-prefix.conf"
#</VirtualHost>
```

### 새로운 vhost 설정을 추가한다
```
# 원래 도메인 설정
<VirtualHost *:80>
  ServerName domain.com
  ServerAlias www.domain.com
  DocumentRoot /opt/bitnami/apps/wordpress/htdocs/
  <Directory /opt/bitnami/apps/wordpress/htdocs/>
    Options Indexes FollowSymLinks MultiViews
    AllowOverride All
    Order allow,deny
    allow from all
    Require all granted
  </Directory>
  # Bitnami applications installed with a prefix URL (default)
  Include "/opt/bitnami/apache2/conf/bitnami/bitnami-apps-prefix.conf"
</VirtualHost>

# 새로 추가할 서브 도메인 설정
<VirtualHost *:80>
  ServerName mysub.domain.com
  DocumentRoot /opt/bitnami/apps/wordpress/myapp/
  <Directory /opt/bitnami/apps/wordpress/myapp/>
    Options Indexes FollowSymLinks MultiViews
    AllowOverride All
    Order allow,deny
    allow from all
    Require all granted
  </Directory>
  # Bitnami applications installed with a prefix URL (default)
  Include "/opt/bitnami/apache2/conf/bitnami/bitnami-apps-prefix.conf"
</VirtualHost>
```

## httpd-prefix.conf 수정

### `httpd-prefix.conf` 열기 

```
sudo vi /opt/bitnami/apps/wordpress/conf/httpd-prefix.conf
```

### 다음의 부분을 찾아 주석 처리한다

```
#Include "/opt/bitnami/apps/wordpress/conf/httpd-app.conf"
```

## 아파치 재시작

아파치를 재시작하고 설정한 대로 연결되는지 확인한다.

```
sudo /opt/bitnami/ctlscript.sh restart apache
```

