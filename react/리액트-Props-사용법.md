# 리액트 Props 사용법

## Props 사용법 

### 함수형 컴포넌트일 때

props를 파라미터로 받아서 사용한다.
```javascript
const MyComponent = (props) => {
  return(
    <ul>
      <li>이름 : {props.name}</li>
      <li>나이 : {props.age}</li>
    </ul>
  )
}
```

혹은 다음과 같이 destructuring props를 사용해도 된다.

```javascript
const MyComponent = ({name, age}) => {
  return(
     <ul>
      <li>이름 : {name}</li>
      <li>나이 : {age}</li>
    </ul>
  )
}
```


### 클래스일 때 
Component 클래스를 상속 받으면 `this.props`로 Props에 접근할 수 있다.
```javascript
class MyComponent extends React.Component {
  render() {
    return (
      <ul>
        <li>이름 : {this.props.name}</li>
        <li>나이 : {this.props.age}</li>
      </ul>
    );
  }
}
```

## 참고

### Q. 언제 클래스를 쓰고 언제 함수형 컴포넌트를 쓰는가?

A. 만약 State나 LifeCycle API를 써야한다면 클래스로 컴포넌트를 만들면, 필요 없다면 그냥 간단하게 함수형 컴포넌트를 쓰면 된다.


### Q. 언제 State를 쓰고 언제 Props를 쓰는가?

A. Props는 외부로부터 받은 것이기 때문에 바꿔서는 안된다(=바꿀 수 없다). State는 내부의 상태이기 때문에 언제든 바꿀 수 있다. Props값을 받은 후 바꾸고 싶다면 State에 넣어서 바꾼다.

