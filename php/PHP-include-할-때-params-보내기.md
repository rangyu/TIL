# PHP, include 할 때 params 보내기

include() 함수 자체에는 params을 보낼 수는 없지만, 상단에 변수를 선언하면 include한 파일 내에도 통용된다.

```php
<?php
$parameter = "Hello World";
include("header.php");
?>
```

include한 파일 내에서 변수를 사용할 때는 다음과 같이, 변수 값이 없을 경우 대체할 기본값과 함께 사용한다.

```php
<?php
$parameter = isset($parameter) ? $parameter : "Default Text";
?>
```
