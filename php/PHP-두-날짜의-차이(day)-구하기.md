# PHP 두 날짜의 차이(day) 구하기

php의 `date_diff(시작일, 종료일)`함수를 이용하면 두 날짜의 차이를 쉽게 구할 수 있다. (일수 기준)

```php
<?php
   $start_data = new DateTime('2018-12-01'); 
   $end_date = new DateTime('2019-1-20');
   $diff_days = date_diff($start_data, $end_date);
   
   echo $diff_days->days; // 50
?>
```