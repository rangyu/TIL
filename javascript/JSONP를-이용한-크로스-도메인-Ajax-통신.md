# JSONP를 이용한 크로스 도메인 Ajax 통신

JSONP는 크로스 도메인 이슈를 해결하기 위한 방법 중 하나이다. 이 글에서는 JQuery를 사용해서 JSONP 방법으로 Ajax 통신하는 방법에 대해 알아보고자 한다.

## 크로스 도메인 이슈

크로스 도메인(Cross Domain) 이슈란 보안 상의 이유로 생긴 동일 출처 정책(Same Origin Policy)으로 인해 외부 서버 경로의 자바스크립트 호출이 막히는 문제를 뜻한다. 

JSONP는 이러한 크로스 도메인 이슈를 해결하기 위해서 외부 서버 경로로 접속할 수 있는 `<script/>` 태그를 사용함으로써 동일 출처 정책을 우회한다.

## 클라이언트 측에서의 처리

ajax를 사용한 호출 방법은 다음과 같다. 

(참고로 JSONP는 `<script/>` 태그를 이용한 방법이기 때문 데이터 전송 타입은 POST은 불가능하며 GET으로만 가능하다.)

```javascript
$.ajax({ 
    url: url, 
    dataType: 'jsonp', 
    jsonpCallback: "myCallback", 
    success: callback 
}); 
```

getJSON를 사용한 호출 방법은 다음과 같다. URL에 `callback=?` 포함되면 자동으로 JSONP 방식으로 호출한다.

```javascript
$.getJSON(url + "?callback=?", data, callback);
```


## 서버 측에서의 처리

JSONP 방법을 사용하려면 서버 측에서도 해당 처리가 필요하다. 

```
Uncaught SyntaxError: Unexpected token :
```

만약 기존과 같은 JSON 타입으로 출력하면 위와 같은 Syntax 에러가 난다. JSONP 방법을 사용하려면 서버 측에서는 JSON 데이터를 Callback 함수 형태로 출력해야 한다.

예를 들면 다음과 같다. (이때 `myCallback` 부분은 클라이언트에서 호출한 Callback과 동일하게 바꿔주면 된다.)

```javascript
myCallback({name:'홍길동', age:32})
```


php의 경우 배열 타입의 데이터를 JSON를 바꾼 뒤 콜백 함수로 출력하면 된다. 

```php
$data = array(
    "counter" => $counter,
    "gallery" => $gallery
);
echo "myCallback(".json_encode($data).")";
``` 
 
