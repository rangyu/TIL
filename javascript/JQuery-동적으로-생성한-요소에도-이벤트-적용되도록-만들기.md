# JQuery 동적으로 생성한 요소에도 이벤트 적용되도록 만들기

jquery 구버전에서는 `.live()`가 해당 역할을 했었으나, 현재 버전에서는 `.live()` 더이상 쓰지 않으며, `.on()`로 통합됨.


아래의 방법으로 하면 선언 이후 동적으로 생성한 요소에 적용되지 않음.

```javascript
/* 이후 동적 생성한 요소에는 적용되지 않는다 */
$('#content').on('click', function() {
  //...
});
```

대신 이렇게 선언하면 적용 된다.

```javascript
/* 이후 동적 생성한 요소에도 적용된다 */
$(document).on('click', '#content', function() {
  //...
});
```
