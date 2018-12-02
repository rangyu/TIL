# 워드프레스 주소창 URL에서 /wp 폴더명 없애기
워드프레스 설치 시 ``/wp`` 폴더 내에 설치했다면 ``mysite.com/wp``와 같이 URL 뒷부분에 폴더명이 붙는다. 

이 글에서는 이와 같은 경우에 ``/wp`` 폴더명을 없애는 방법에 대해서 알아보겠다. 

## 1. 워드프레스 설정 바꾸기
워드프레스 관리자로 로그인 후 ``설정`` > ``일반``으로 들어간다. 아래와 같이 워드프레스 주소와 사이트 주소를 각각 수정 후 저장한다. (저장하면 에러페이지로 이동하지만 정상적으로 적용된 상태이다)

- 워드프레스 주소 (URL) : ``mysite.com/wp`` (폴더명을 붙인 url)
- 사이트 주소 (URL) : ``mysite.com`` (폴더명이 없는 url)


## 2. index.phpd와 .htaccess(없으면생략) 파일 복사
``/wp`` 폴더에 있는 index.php 파일과 .htaccess(없으면생략)을 루트에 복사한다.

## 3. 루트의 index.php 수정하기
루트에 복사해둔 index.php 파일을 열고 아래와 같은 구문을 찾는다.
```php
/** Loads the WordPress Environment and Template */
require( dirname( __FILE__ ) . '/wp-blog-header.php' );
```
다음과 같이 ``require(‘./wp-blog-header.php’);`` 부분을 ``require(‘./wp/wp-blog-header.php’);`` 으로 바꾼다. 

```php
/** Loads the WordPress Environment and Template */
require( dirname( __FILE__ ) . '/wp/wp-blog-header.php' );
```

## 4. .htaccess 바꾸기
만약 고유주소 설정을 바꿨다면 변경된 .htaccess 파일을 ``root``와 ``/wp`` 폴더 내 각각 추가해준다. 이후 워드프레스 URL에 /wp 경로가 안 붙여진 것을 볼 수 있다. 
