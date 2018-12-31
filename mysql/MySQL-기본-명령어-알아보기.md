# MySQL 기본 명령어 알아보기 

MySQL 기본 명령어를 알아보자.

## MySQL 버전 확인하기

```
mysql --version
mysql  Ver 14.14 Distrib 5.7.19, for osx10.12 (x86_64) using  EditLine wrapper
```
=> 버전 5.7.19

## MySQL 로그인

접속 명령어는 다음과 같다. 

```
$ mysql -u 사용자명 -p
$ mysql -h 호스트명 -u 사용자명 -p
$ mysql -u 사용자명 -p 데이터베이스명
```