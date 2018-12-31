# MySQL 기본 명령어 알아보기 

MySQL 기본 명령어를 알아보자.

## 버전 확인하기

```bash
mysql --version
mysql  Ver 14.14 Distrib 5.7.19, for osx10.12 (x86_64) using  EditLine wrapper
```
=> 버전 5.7.19 

## 접속 명령어

다음 같이 MySQL에 접속할 수 있다. 호스트명(-h)을 생략하면 자동으로 `localhost`로 접속한다. 

```bash
$ mysql -u 사용자명 -p
```

접속할 호스트명 정하기 
```bash
$ mysql -h 호스트명 -u 사용자명 -p
```

사용할 데이터베이스 선택하기 
```bash
$ mysql -u 사용자명 -p 데이터베이스명
```

접속 종료하기 
```mysql
mysql> exit;
```

## 데이터베이스 명령어

모든 데이터베이스 목록 보기
```mysql
mysql> show databases;
```

사용할 데이터베이스 선택하기
```mysql
mysql> use 데이터베이스명;
```

선택된 데이터베이스 목록 보기
```mysql
mysql> select database();
```

새로운 데이터베이스 생성하기
```mysql
mysql> create database 데이터베이스명
```

데이터베이스 삭제하기
```
mysql> drop database 데이터베이스명
```