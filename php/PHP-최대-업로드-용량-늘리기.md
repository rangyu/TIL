# PHP 최대 업로드 용량 늘리기

### php.ini 수정하기

php.ini를 수정해서 php 최대 업로드 가능 용량을 늘려보자.

```
sudo vi /etc/php.ini
```

#### 최대 업로드 가능 용량

```
upload_max_filesize = 2M
```

#### 최대 POST 전송 용량

```
post_max_size = 8M
```
(upload_max_filesize 보다 커야 한다)


#### 최대 실행 시간

```
max_execution_time = 30
```

#### 최대 입력 시간

```
max_input_time = 60
```
(max_execution_time 보다 커야 한다)

#### 메모리 제한 크기

```
memory_limit = 128M
```

* 참고
: post_max_size 값 > upload_max_filesize 값 >= memory_limit 값 

### 아파치 재시작

(Mac일 경우)
```
sudo apachectl graceful
```