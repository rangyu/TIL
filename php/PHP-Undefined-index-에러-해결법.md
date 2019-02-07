# PHP, Undefined index 에러 해결법

해당 변수가 값이 없을 수도 있는 경우 Undefined index 에러가 날 수 있다.
다음과 같이 `??`를 사용하면 해당하는 값이 없을 경우의 대체값을 지정할 수 있다.

```php
<?php
$mode = $_REQUEST['mode'] ?? '';
?>
```
