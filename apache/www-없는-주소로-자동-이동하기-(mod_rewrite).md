# www 없는 주소로 자동 이동하기 (mod_rewrite)

이 글에서는 mod_rewrite를 사용하여 www 없는 주소로 자동 이동하는 방법을 알아본다.

## 왜 필요한가?
검색엔진은 서브도메인은 본래 도메인과 별개의 것으로 인식한다. 만약 www 붙인 URL와 붙이지 않은 URL을 혼용해서 사용할 경우, 검색엔진에서 하나의 글을 중복 문서로 여길 가능성이 있으므로 둘 중 하나의 도메인만 사용하는 편이 SEO에 유리하다. 

따라서 이를 위해 www로 접속했을 경우 www가 없는 도메인으로 리다이렉트 하도록 만드는 편이 좋다.

## www 없애기

아파치 환경설정 파일(` httpd.conf`), 비트나미 워드프레스라면 `httpd-prefix.conf` 파일을 수정하면 URL 재작성 규칙(Rewrite Rule)을 적용할 수 있다.

`RewriteEngine On` 밑에 다음과 같이 작성한다. 
www.mysite.com -> mysite.com 

```
# www.mysite.com -> mysite.com
RewriteCond %{HTTPS} !=on
RewriteCond %{HTTP_HOST} ^www\.(.+)$ [NC]
RewriteRule ^ http://%1%{REQUEST_URI} [R=301,L]
```

## www 붙이기

먄약 이와 반대로 하고 싶다면(www를 붙인 도메인을 사용하고 싶다면) 다음과 같이 작성한다. 
mysite.com -> www.mysite.com 

```
# mysite.com -> www.mysite.com
#RewriteCond %{HTTPS} !=on
#RewriteCond %{HTTP_HOST} !^www\..+$ [NC]
#RewriteRule ^ http://www.%{HTTP_HOST}%{REQUEST_URI} [R=301,L]
```

## 아파치 재시작

아파치를 재시작하면 변경 사항이 반영된다.

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
