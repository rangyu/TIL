# React CSS에서 height 100%가 안 먹힐 때

React CSS에서 `width: 100%;`는 적용이 되지만, `height: 100%;`는 적용되지 않는다. 

그럴 경우 `100vh`를 사용하면 된다.

```
div {
  height: 100vh;
}
```

위와 같이 `height: 100%;` 대신에 `height: 100vh;`를 사용하면 세로 사이즈 100%로 표시된다. 