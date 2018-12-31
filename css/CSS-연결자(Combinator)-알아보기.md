# CSS 연결자(Combinator) 알아보기

CSS 선택자(Selector)는 또 다른 선택자와 연결할 수 있는데, 이때 두 선택자를 연결해주는 기호를 연결자(Combinator)라고 말한다. 

```
[Selector] [Combinator] [Selector] 
```

CSS에서 제공하는 연결자는 다음과 같이 4가지 종류가 있다.

- 하위 선택자 : descendant selector (스페이스)
- 자식 선택자 : child selector (>)
- 인접 형제 선택자 : adjacent sibling selector (+)
- 일반 형제 선택자 general sibling selector (~)


## 하위 선택자 : descendant selector (스페이스)

하위 선택자(descendant selector)는 [첫번째 요소]보다 하위에 있는 모든 [두번째 요소]를 뜻한다.

```
div p
```

## 자식 선택자 : child selector (>)

자식 선택자(child selector)는 [첫번째 요소]의 바로 아래에 있는 [두번째 요소]를 뜻한다.

```
div > p
```

## 인접 형제 선택자 : adjacent sibling selector (+)

인접 형제 선택자(adjacent sibling selector)는 [첫번째 요소]의 형제이면서 바로 다음에 오는[두번째 요소]를 뜻한다.

```
div + p
```

## 일반 형제 선택자 : general sibling selector (+)

일반 형제 선택자(general sibling selector)는 [첫번째 요소]의 모든 형제인 [두번째 요소]를 뜻한다.

```
div ~ p
```