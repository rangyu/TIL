# mysqli 사용이 안될 때 php.ini 설정법 

mysqli 함수가 동작하지 않는다면 php.ini 설정 문제일 수가 있다. php.ini 파일을 수정하면 해결된다.

## php.ini 경로

보통 `/etc/php.ini` 경로에 php.ini 파일이 있다. 하지만 설정에 따라 다른 위치에 있을 수도 있다. 

다음과 같이 php.ini 파일의 위치를 찾을 수 있다. 

```bash
php -i | grep php.ini
```

만약 해당 경로에 php.ini 파일이 없고, php.ini.default 파일만 있는 경우도 있다. 그렇다면 php.ini.default을 복사해서 php.ini 파일을 만들자.

```
sudo cp /etc/php.ini.default /etc/php.ini
```

## mysqli 사용하기

php.ini 파일을 열고 `;extension=php_mysqli.dll` 부분을 찾는다.

```
sudo vi /etc/php.ini
```

이때 문장 앞에 붙은 `;` 세미콜론은 주석을 뜻한다. 주석을 제거한 뒤 저장한다.

```
extension=php_mysqli.dll
```

## 아파치 재시작

아파치를 재시작하면 이제 mysqli 함수가 제대로 동작하는 것을 볼 수 있다.

```
sudo apachectl restart
```
