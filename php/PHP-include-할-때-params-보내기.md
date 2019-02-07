# PHP, include 할 때 params 보내기

include() 함수 자체에는 params을 보낼 수는 없지만, 상단에 변수를 선언하면 include한 파일 내에도 통용된다.

```php
<?php
$parameter = "Hello World";
include("header.php");
?>
```
