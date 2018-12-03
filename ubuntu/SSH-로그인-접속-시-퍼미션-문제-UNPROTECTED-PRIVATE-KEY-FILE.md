# SSH 로그인 접속 시 퍼미션 문제 (UNPROTECTED PRIVATE KEY FILE)

잘못된 퍼미션으로 SSH 로그인 접속 시 위와 같은 같은 에러가 났다. 

```
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@         WARNING: UNPROTECTED PRIVATE KEY FILE!          @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
Permissions 0644 for '/Users/username/.ssh/your-key.pem' are too open.
It is required that your private key files are NOT accessible by others.
This private key will be ignored.
```

private key의 퍼미션이 너무 공개되어 있어서 생긴 문제였다. 해당 private key의 퍼미션을 644에서 600으로 바꿔서 해결하였다.

```
chmod 600 ~/.ssh/your-key.pem
```

 
## .ssh 폴더 내 퍼미션
.ssh 폴더 및 하위 파일들의 올바른 퍼미션은 다음과 같다.

```
chmod 700 ~/.ssh
chmod 600 ~/.ssh/id_rsa
chmod 644 ~/.ssh/id_rsa.pub  
chmod 644 ~/.ssh/authorized_keys
chmod 644 ~/.ssh/known_hosts
```