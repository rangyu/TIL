# PHP 짧은 태그(short_open_tag) 허용하도록 설정하기

php를 사용할 때는 다음과 같이 `<?php`로 시작해서 `?>`로 끝나야 한다. 하지만 짧은 태그(short_open_tag)를 허용하면 `<?`로 시작하고 `?>`로 끝낼 수 있다. 


## 현재 설정 확인하기

현재 php.ini 내 설정에서 짧은 태그(short_open_tag) 허용하고 있는지 확인하려면 다음과 같이 입력하면 된다. 

```
cat /etc/php.ini | grep ^short_open_tag
short_open_tag = Off
```

`short_open_tag`값이 Off로 되어 있다면 짧은 태그를 사용할 수 없다. 이를 허용하려면 php.ini를 수정해서 `short_open_tag = On`으로 바꿔주면 된다.

## php.ini 수정하기

```
sudo vi cat /etc/php.ini
```

`short_open_tag = Off`를 찾아서 다음과 같이 바꾼다.

```
short_open_tag = On
```

vi 저장하고 닫기
```
wq!
```


## 아파치 재시작

변경된 php 설정을 적용하기 위해 아파치를 재시작한다.

(Mac일 경우)
```
sudo apachectl graceful
```