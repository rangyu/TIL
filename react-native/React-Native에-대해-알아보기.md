# React Native에 대해 알아보기

## React Native 앱을 만드는 두 가지 방법

- Expo(react-native-create-app)를 사용해서 세팅하는 방법
- react-native-cli를 이용해서 세팅하는 방법

---

## import 상대경로 지옥 탈출법

- `babel-plugin-root-import`를 사용하면 편리

```
// before
import SomeExample from `../../../../some/example.js';  

// after
import SomeExample from `~/some/example.js'; 
```

---

## Flex를 이용한 화면 구성

레이아웃 배치는 Flex를 사용한다. Flex 문법 익힐 것.

- Flex 코딩 쉬운 공부 사이트(귀여움 주의!) : http://flexboxfroggy.com/#ko


----

## Flow로 PropTypes 지정하기

잘못된 PropTypes을 파라미터로 보내는 실수를 사전에  잡기 위해서는
개발 초기부터 Flow를 도입하면 좋음.
- [Flow로 React Type 정의하기](https://medium.com/@pitzcarraldo/flow로-react-type정의하기-7d1dbfa9e61b)


---

## Optional Chaining로 간결해진 코드

(Optional Chaining는 0.56 버전부터 가능)


```
// before
if(data && data.items && data.items.length > 2) {
  drawList(data);
}

// after
if(data?.items?.length > 2) {
  drawList(data);
}
```

---
## 플랫폼 별 스타일 정의하는 법

하나의 스타일시트에 플랫폼 (web/ ios / android) 별 스타일을 따로 지정할 수 있다.

```
import StyleSheet from './PlatformStyleSheet';
const styles = StyleSheet.create({
  title: {
    fontSize: 16,
    ios: { fontSize: 18}
    android: { fontSize: 17, color: 'red'} 
  }
})
```