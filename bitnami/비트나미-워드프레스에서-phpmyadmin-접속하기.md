# 비트나미 워드프레스에서 phpMyAdmin 접속하기

비트나미 워드프레스를 설치하면 자동으로 phpMyAdmin도 같이 설치된다. 하지만 보안상 해당 phpMyAdmin은 로컬에서만 접속할 수 있도록 설정되어 있다. 

따라서 비트나미 워드프레스에서 phpMyAdmin 접속하려면 SSH tunnel을 사용하면 된다.

- 참고문서 : https://docs.bitnami.com/virtual-machine/components/phpmyadmin


## SSH tunnel

(맥과 윈도우의 방법이 다름. 아래는 맥 기준)

로그아웃된 상태에서 터미널에 다음과 같이 입력한다.

```
ssh -N -L 8888:127.0.0.1:80 -i ~/.ssh/your-key.pem bitnami@yourdomain.com
```

이후 `http://localhost:8888/phpmyadmin/`로 접속하면 된다.
