# phpMyAdmin 암호화 문자열(blowfish_secret) 경고문 해결법.md

![2018-12-11 9 25 37](https://user-images.githubusercontent.com/36276682/49802991-ecd0eb00-fd91-11e8-995a-5082ff56b85c.png)

phpMyAdmin에 접속했을 때 위와 같이 `이제 설정 파일을 암호화 문자열(blowfish_secret)을 필요로 합니다.`라는 경고문이 나오는 경우가 있다. 

## 해결법
이를 해결하기 위해서는 `config.inc.php` 파일 내 `$cfg['blowfish_secret']` 값을 넣어주면 된다. 

```
$cfg['blowfish_secret'] = '' // 여기에 임의의 문자열을 넣는다.
```

이때 blowfish_secret 값으로는 특수문자와 숫자, 대문자, 소문자 등을 섞어서 임의의 값으로 넣어준다. 

(참고) https://www.question-defense.com/tools/phpmyadmin-blowfish-secret-generator 사이트에서 blowfish_secret 문자열 값을 임의로 생성해준다. 
