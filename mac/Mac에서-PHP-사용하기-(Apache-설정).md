# Mac에서 PHP 사용하기 (Apache 설정)

Mac OS에서 php 파일을 실행하려면 아파치 웹서버의 환경설정 파일을 변경하면 된다. `/etc/apache2/httpd.conf` 파일을 연다.

```
sudo vi /etc/apache2/httpd.conf
```

다음과 같은 php 모듈 설정라인을 찾아서 앞의 주석을 `#`을 제거한다.

```
LoadModule php7_module libexec/apache2/libphp7.so
```

이후 아파치를 재시작하면 이제 php 파일을 제대로 실행된다.

```
sudo apachectl graceful
```