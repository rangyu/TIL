# 비트나미 워드프레스의 Let's Encrypt 인증서 자동 갱신하기

> 이전글 [비트나미 워드프레스에 Let’s Encrypt 인증서 설치하기](./비트나미-워드프레스에-Letsencrypt-인증서-설치하기.md)에서 이어짐

Let's Encrypt 인증서는 유효 기간이 90일까지로, 해당 인증서를 지속적으로 이용하기 위해서는 그전에 인증서를 갱신해야 한다. 매번 수동으로 인증하는 것으로 번거롭기 때문에, 이 글에서는 crontab을 사용하여 비트나미 워드프레스에서 Let's Encrypt 인증서를 자동 갱신하는 방법에 대해 알아보겠다. 

## Let's Encrypt 인증서 갱신하기

Lego 클라이언트를 사용하여 Let's Encrypt 인증서를 갱신하는 방법은 다음과 같다. 

```bash
sudo /opt/bitnami/ctlscript.sh stop
sudo lego --email="EMAIL-ADDRESS" --domains="DOMAIN" --path="/etc/lego" --http renew
sudo /opt/bitnami/ctlscript.sh start
```

## 쉘 스크립트 만들기 

`/etc/lego` 폴더 내로 이동한다. 

```bash
sudo su
cd /etc/lego
```
인증서 갱신을 위한 쉘 스크립트 ``renew-certificate.sh``를 만든다.

```bash
vi renew-certificate.sh
```

다음과 같은 내용을 입력한다. ``EMAIL-ADDRESS``과 ``DOMAIN`` 부분은 해당하는 값으로 바꿔서 넣는다.

```bash
#!/bin/bash

sudo /opt/bitnami/ctlscript.sh stop
sudo lego --email="EMAIL-ADDRESS" --domains="DOMAIN" --path="/etc/lego" renew
sudo /opt/bitnami/ctlscript.sh start
```
생성된 스크립트의 퍼미션을 변경한다.

```bash
chmod +x /etc/lego/renew-certificate.sh
```

## 크론탭에 등록하기

반복 작업을 위해 생성한 쉘 스크립트를 크론탭에 등록한다.

```
sudo crontab -e
```

(참고) 이때 만약 에디터를 직접 선택하고 싶다면 다음과 같이 입력하면 된다.

```
EDITOR=vi crontab -e
```

크론탭 파일 내 다음과 같은 내용을 추가한다.

```
0 0 1 * * /etc/lego/renew-certificate.sh 2> /dev/null
```

이후 제대로 변경되었는지 확인하려면 `crontab -l` 명령어를 사용하면 된다.

## 크론탭 의미

### 반복 시각

```
0 0 1 * * 
```

해당 내용은 매달 1일 0시 0분에 실행하라는 의미가 된다.

| 위치    | 뜻 (범위)     | 해석          |
|--------|-------------|---------------|
| 1번째   | 분 (0 - 59)  | 0 => 0분      |
| 2번째   | 시 (0 - 23)  | 0 => 0시      |
| 3번째   | 일 (1 - 31)  | 1 => 1일      |
| 4번째   | 월 (1 - 12)  | * => 매월     |
| 5번째   | 요일 (0 - 6)  | * => 요일 무관 |


### 출력

```
2> /dev/null
```
``2``는 표준에러, STRERR(standard error)를 뜻하고 ``>``는 리다이렉션을 뜻한다. ``/dev/null``로 리다이렉션 할 경우 화면에 아무것도 출력되지 않는다.

따라서 ``2> /dev/null``는 표준에러의 경우 출력하지 않는다는 뜻이 된다.

## 마치며

이제 매달 1일 0시 0분마다 ``/etc/lego/renew-certificate.sh`` 스크립트가 자동 실행되고, Let's Encrypt 인증서를 갱신 요청하게 된다. 
