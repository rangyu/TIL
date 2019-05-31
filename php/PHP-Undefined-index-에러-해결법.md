# PHP, Undefined index 에러 해결법

php 설정에 따라 초기화되지 않은 변수을 사용할 경우 Undefined index 에러가 나는 경우가 있다. 



## 해결법 1

다음과 같이 `??`를 사용하면 해당하는 값이 없을 경우의 대체값을 지정할 수 있다.

```php
<?php
$mode = $_REQUEST['mode'] ?? '';
?>
```

## 해결법 2

php.ini을 수정해서 Undefined index 에러를 띄우지 않도록 설정할 수도 있다.

```
sudo vi /etc/php.ini
```

### php.ini 수정하기

에러 리포팅 설정을 찾는다.

```
error_reporting = E_ALL
```

혹은

```
error_reporting = E_ALL & ~E_DEPRECATED
```
처럼 되어 있을 것이다. 

`E_ALL`는 모든 에러 발생 시 로그를 표시한다는 뜻

`E_DEPRECATED` 나중에 동작하지 않을 함수에 대해 로그를 표시한다는 뜻

`E_NOTICE`는 초기화되지 않은 변수 사용 시 로그를 표시한다는 뜻

`~` 앞에 물결 표시를 붙이면 역을 뜻한다.

### `~E_NOTICE` 붙이기

즉 Undefined index 에러에 대해 로그를 표시하지 않으려면 `~E_NOTICE`를 뒤에 붙이면 된다.


```
error_reporting = E_ALL & ~E_NOTICE
```

혹은 

```
error_reporting = E_ALL & ~E_DEPRECATED & ~E_NOTICE
```

이런 식으로 입력한다.

### 아파치 재시작

php.ini를 수정했다면 아파치를 재시작해서 변경사항을 적용한다.

(Mac일 경우)
```
service httpd restart
```