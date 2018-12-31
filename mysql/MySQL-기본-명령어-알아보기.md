# MySQL 기본 명령어 알아보기 

MySQL 기본 명령어를 알아보자.

## MySQL 버전 확인하기

```
mysql --version
mysql  Ver 14.14 Distrib 5.7.19, for osx10.12 (x86_64) using  EditLine wrapper
```
=> 버전 5.7.19

## MySQL 로그인

다음 같이 MySQL에 접속할 수 있다. 호스트명(-h)을 생략하면 자동으로 localhost로 접속한다. 

```
$ mysql -u 사용자명 -p
$ mysql -h 호스트명 -u 사용자명 -p
$ mysql -u 사용자명 -p 데이터베이스명
```