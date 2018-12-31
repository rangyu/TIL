# PHP 숫자 천 단위 마다 쉼표 찍기

숫자를 출력할 때 천(1000)단위 마다 숫자를 찍고 싶다면 `number_format(숫자)`를 사용하면 된다.
```php
<?php
    echo number_format(1234567);
?>

1,234,567
```

