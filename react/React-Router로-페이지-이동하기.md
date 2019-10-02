# React-Router로 페이지 이동하기

효과적인 페이지 이동을 위해 React-Router를 사용해보자.

## Q. 왜 라우터를 사용할까?

- 라우터를 이용해서 URL 주소에 따라 보여줄 화면을 직접 구현할 수 있다.
- SPA (Single Page Application) 앱을 라우터 없이 구현하면 한 페이지 안에서 전체 자바스크립트 코드를 불러와야 하기 때문에 용량이 커진다. 반면 라우터를 사용하면 페이지별로 나눌 수 있으므로 코드 스플리팅(Code Splitting) 통해 필요한 코드만 불러올 수 있다.
- 브라우저 히스토리 내역이 생기므로 페이지 뒤로가기 등을 구현할 수 있어서 사용자가 느끼는 편의성이 높아진다.


## react-router-dom 설치하기

공식문서 : https://www.npmjs.com/package/react-router-dom

### npm으로 설치하기 

웹 브라우저 상에서 react-router를 사용하기 위해 npm으로 react-router-dom을 설치하자.

```
npm install --save react-router-dom
```

### 사용 예제

```javascript
// using ES6 modules
import { BrowserRouter, Route, Link } from "react-router-dom";
 
// using CommonJS modules
const BrowserRouter = require("react-router-dom").BrowserRouter;
const Route = require("react-router-dom").Route;
const Link = require("react-router-dom").Link;
```

## React-Router 적용하기

### 폴더 구조

- **src/**
    - **pages/**
        - [x] index.js
        - [x] Home.js
        - [x] Channel.js
        - [x] More.js
    - **shared/**
        - [x] App.js
    - **client/**
        - [x] Root.js
    - [x] index.js
    - index.css
    - serviceWorker.js

### index.js

```javascript
import React from 'react';
import ReactDOM from 'react-dom';
import Root from './client/Root';
import './index.css';
import * as serviceWorker from './serviceWorker';

ReactDOM.render(<Root />, document.getElementById('root'));

// If you want your app to work offline and load faster, you can change
// unregister() to register() below. Note this comes with some pitfalls.
// Learn more about service workers: https://bit.ly/CRA-PWA
serviceWorker.unregister();
```

### client/Root.js

```javascript
import React from 'react';
import { BrowserRouter } from 'react-router-dom';
import App from '../shared/App';

const Root = () => (
    <BrowserRouter>
        <App/>
    </BrowserRouter>
);

export default Root;
```

### shared/App.js

```javascript
import React, { Component } from 'react';
import { Route } from 'react-router-dom';
import { Home, Channel, More  } from '../pages';

class App extends Component {
  render() {
    return (
      <div>
        <Route exact path="/" component={Home}/>
        <Route path="/channel" component={Channel}/>
        <Route path="/more" component={More}/>
      </div>
    );
  }
}

export default App;
```

#### Route의 exact 속성 여부

`exact`는 필요에 따라 붙이거나 생략한다.

만약 `exact`를 붙였다면, path가 URL과 정확히 일치하는 경우에만 보여준다는 의미이다.  `exact`를 붙이지 않았을 경우, URL에 해당 path가 정확히 일치하지 않더라도 전체의 일부로 포함되어 있다면, 해당 컴포넌트를 보여준다.

```html
<Route exact path="/" component={Home}/>
```
따라서, 위와 같이 경로가 `/` 경우에는 꼭 `exact`를 붙여야 한다. 안그러면 모든 path에 `Home` 컴포넌트가 보이게 된다.

### pages/Home.js

```javascript
import React from 'react';

const Home = () => {
  return (
    <div>
       Home
    </div>
  );
};
export default Home;
```

### pages/index.js

```javascript
export { default as Home } from './Home';
export { default as Channel } from './Channel';
export { default as More } from './More';
```
