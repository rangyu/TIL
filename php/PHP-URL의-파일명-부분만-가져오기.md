# PHP URL의 파일명 부분만 가져오기

`basename($link)`를 쓰면 된다.

```php
$link = $_SERVER['PHP_SELF'];
echo basename($link)
```

만약 `.php` 확장자까지 제거하고 싶다면 다음과 같이 쓴다. 

```php
$link = $_SERVER['PHP_SELF'];
echo str_replace('.php', '', basename($link));
```