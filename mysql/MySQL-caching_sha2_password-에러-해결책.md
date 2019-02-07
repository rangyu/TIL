# MySQL caching_sha2_password 에러 해결책

## 에러

```
error: mysqli_connect(): The server requested authentication method unknown to the client [caching_sha2_password] 
```

mysqli 확장은 caching_sha2_password 방식을 지원하지 않기 때문에 위와 같은 에러가 났다. 


## 해결책

이를 해결하기 위해서는 해당 mysql 유저의 비밀번호 방식을 mysql_native_password 방식으로 변경하면 된다.

#### 기존 사용자 수정

```sql
ALTER USER 'yourUserName'@'localhost' IDENTIFIED WITH mysql_native_password BY '비밀번호';
```

#### 신규 사용자 생성
```sql
CREATE USER 'yourUserName'@'localhost' IDENTIFIED WITH mysql_native_password BY '비밀번호';

```


출처 : https://stackoverflow.com/questions/50026939/php-mysqli-connect-authentication-method-unknown-to-the-client-caching-sha2-pa