# 리액트 Fragment 사용하기

리액트 버전 15까지 모든 컴포넌트의 루트는 한개만 가능했다. 따라서 render 함수 내에서 여러개의 컴포넌트들을 감싸주기 위해 종종 무의미한 `<div></div>`를 추가해야만 했다.

리액트 버전 16부터는 여러개의 컴포넌트를 `<div></div>`를 대신에 `<Fragment>`를 사용한다. 

## Fragment 사용 예시
```
import React, { Fragment } from 'react';

...
render() {
  return (
    <Fragment>
      <ChildA />
      <ChildB />
      <ChildC />
    </Fragment>
  );
}
```

## 짧은 Fragment 표기법

`<Fragment>` 컴포넌트를 import한 대신에 다음과 짧은 표기법을 사용할 수도 있다. 

(다만 짧은 표기법은 아직 지원하는 경우가 많지 않아서, 에디터에 따라 에러가 날 수 있으니 현재는 사용을 권장하지 않는다.)

```
render() {
  return (
    <>
      <ChildA />
      <ChildB />
      <ChildC />
    </>
  );
}
```
## 왜 Fragment를 사용하는가

`<div>`와 달리 `<Fragment>`는 `style`을 가질 수 없고, 속성 값으로는 오직 `key` 값만 가질 수 있다. 

## 참고

- [Fragments - 공식문서](https://ko.reactjs.org/docs/fragments.html)
- [React-버전-16-총정리](https://www.vobour.com/%EB%A6%AC%EC%95%A1%ED%8A%B8-react-%EB%B2%84%EC%A0%84-16-%EC%B4%9D%EC%A0%95%EB%A6%AC)