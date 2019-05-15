# MySQL root 비밀번호 분실했을 때 재설정하기

MySQL root 비밀번호를 까먹었다! 

그럼 아래처럼 해결해보자.



## 현재 동작 중인 MySQL 프로세스 죽이기

만약 현재 MySQL 프로세스가 실행 중이면 mysqld_safe을 실행할 때 에러가 난다. 

MySQL 프로세스가 동작 중이라면 이를 먼저 죽이자.

(homebrew로 설치했을 경우)
```bash
brew services stop mysql
```

(launchctl을 등록했다면 내리기)
```bash
sudo launchctl unload -w ~/Library/LaunchAgents/homebrew.mxcl.mysql.plist
```

## mysqld_safe 경로 확인하기

```bash
which mysqld_safe
/usr/local/bin/mysqld_safe
```

## mysqld_safe 실행하기

백그라운드에서 실행시키기 위해 `&`를 덧붙인다. 

```bash
/usr/local/bin/mysqld_safe --skip-grant-tables &
```

(`&`를 붙이지 않고 명령어를 실행했다면 터미널 새창을 띄어서 이어서 진행한다)


## Root 비밀번호 없이 MySQL 접속하기

이제 비밀번호를 입력하지 않아도 Root로 접속할 수 있게 된다.

MySQL에 접속하자.

```bash
mysql -u root
```

mysql 데이터베이스 사용을 선언한다.

```bash
mysql> use mysql;
```


## Root 비번 바꾸기

버전에 따라 다르다! 

(아래는 MySQL 8.0.13 버전 기준)

### MySQL 구 버전과 달라진 점 (MySQL 5.7버전 이상)

```sql
mysql> update user set password=PASSWORD("newpassword") where User='root';
```
예전에는 위와 같이 root 비번을 번경할 수 있었지만, MySQL 5.7 이상 버전에서는 에러가 발생할 것이다. 그 이유는 다음과 같다.

#### 1. User 필드에 `password`필드가 사라졌다. 

예전 MySQL 버전에서 user의 비밀번호를 저장하는 `password` 필드가 사라졌다. 대신 `authentication_string` 필드에 비밀번호를 저장한다. 

#### 2. `PASSWORD()` 함수를 더이상 권장하지 않는다. 

SQL 쿼리 내 `PASSWORD()` 함수를 사용하면 syntax 에러가 발생한다. 비밀번호를 암호화하기 위해 `PASSWORD()` 함수를 사용하는 대신 플러그인(`mysql_native_password` 혹은 `caching_sha2_password`)을 지정할 수 있다. 


### 현재 상태를 확인해보자

다음과 같이 입력하면 현재 user별 비밀번호(`authentication_string`)와 암호화 플러그인(`plugin`)을 확인할 수 있다. 
```sql
mysql> select host, user, plugin, authentication_string, password_last_changed from user;
```
대략 이런 식으로 결과값이 나온다.
```
+-----------+------------------+-----------------------+------------------------------------------------------------------------+-----------------------+
| host      | user             | plugin                | authentication_string                                                  | password_last_changed |
+-----------+------------------+-----------------------+------------------------------------------------------------------------+-----------------------+
| localhost | tester           | mysql_native_password | *F2E31D76033713872F3AB9DE9N039B7E9ED15234                              | 2019-03-04 15:33:07   |
| localhost | mysql.infoschema | caching_sha2_password | $A$006$THISISACOMBINATIONOFINVALIDSALTANDPASSWORDTHATMUSTNEVERBRBEUSED | 2019-02-08 20:58:03   |
| localhost | mysql.session    | caching_sha2_password | $A$006$THISISACOMBINATIONOFINVALIDSALTANDPASSWORDTHATMUSTNEVERBRBEUSED | 2019-02-08 20:58:03   |
| localhost | mysql.sys        | caching_sha2_password | $A$006$THISISACOMBINATIONOFINVALIDSALTANDPASSWORDTHATMUSTNEVERBRBEUSED | 2019-02-08 20:58:03   |
| localhost | root             | mysql_native_password | *F1234D76073813872F3AB9DE9LL39B799ED15151                              | 2019-02-08 21:01:09    |
+-----------+------------------+-----------------------+------------------------------------------------------------------------+-----------------------+
```


### Root 비밀번호 바꾸기 

다음과 같은 쿼리를 날려서 플러그인과 함께 새로운 비밀번호를 설정해주자. 

```sql
mysql> alter user 'root'@'localhost' identified with mysql_native_password by 'yourpassword';
```


```bash
mysql> flush privileges;
```

```bash
mysql> exit;
```
