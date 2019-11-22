# SSH 접속 오류 (ECDSA host key 에러) 해결법

## 문제 

SSH 접속 시 다음과 같이 ECDSA host key 에러가 발생했다.

Host key를 새롭게 변경했는데 이전 정보가 그대로 남아있어서 뜬 에러인 듯함.

```
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@       WARNING: POSSIBLE DNS SPOOFING DETECTED!          @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
The ECDSA host key for ***.com has changed,
and the key for the corresponding IP address ***.***.***.***
is unknown. This could either mean that
DNS SPOOFING is happening or the IP address for the host
and its host key have changed at the same time.
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the ECDSA key sent by the remote host is
SHA256:bS3YVX************************************
Please contact your system administrator.
Add correct host key in /Users/******/.ssh/known_hosts to get rid of this message.
Offending ED25519 key in /Users/******/.ssh/known_hosts:37
ECDSA host key for seoirim.com has changed and you have requested strict checking.
Host key verification failed.
```


## 해결

ssh-keygen을 사용해서 이전에 캐시된 정보를 삭제해준 후 다시 시도하니 제대로 접속되었다.


```
ssh-keygen -R 111.222.333.444
```
or
```
ssh-keygen -R yourdomain.com
```


## 참고문서
- https://superuser.com/questions/421004/how-to-fix-warning-about-ecdsa-host-key