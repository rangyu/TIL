# Material UI makeStyles을 component에서 적용하려면?


makeStyles로 component의 style을 적용할 수 없다. 만약 리액트 component에 스타일을 적용하고 싶다면 makeStyle 대신 withStyles을 사용하면 된다.

## withStyles 적용법

### 설치
makeStyles와 마찬가지로 기존에 @material-ui/styles이 설치되어 있어야 한다. (이미 설치했다면 생략)

```
// with npm
npm install @material-ui/styles

// with yarn
yarn add @material-ui/styles
```

### import 

다음과 같이 withStyles를 import한다
```
import { withStyles } from '@material-ui/styles';
```

### style 정의하기
`const styles` 스타일 상수를 정의한다. 이때 클래스 외부에 정의해야 한다.

```
const styles = {
  root: {
    background: 'linear-gradient(45deg, #FE6B8B 30%, #FF8E53 90%)',
    border: 0,
    borderRadius: 3,
    boxShadow: '0 3px 5px 2px rgba(255, 105, 135, .3)',
    color: 'white',
    height: 48,
    padding: '0 30px',
  },
};
```

### props

component 내에서 해당 스타일을 적용하기 props에서 classes 값을 가져온다.

```
const { classes } = props;
```


### export

export 부분에 withStyles을 적용한다

```
export default withStyles(styles)(HigherOrderComponent);
```


### 전체 코드

```javascript
import React from 'react';
import PropTypes from 'prop-types';
import { withStyles } from '@material-ui/core/styles';
import Button from '@material-ui/core/Button';

const styles = {
  root: {
    background: 'linear-gradient(45deg, #FE6B8B 30%, #FF8E53 90%)',
    border: 0,
    borderRadius: 3,
    boxShadow: '0 3px 5px 2px rgba(255, 105, 135, .3)',
    color: 'white',
    height: 48,
    padding: '0 30px',
  },
};

function HigherOrderComponent(props) {
  const { classes } = props;
  return <Button className={classes.root}>Higher-order component</Button>;
}

HigherOrderComponent.propTypes = {
  classes: PropTypes.object.isRequired,
};

export default withStyles(styles)(HigherOrderComponent);
```
- 예제소스 출처 : 공식문서 (https://material-ui.com/styles/basics/)
