# CSS 이미지 하단에 여백이 생기는 문제

``margin: 0px; padding: 0px;``을 적용했는데도 이미지 하단에 여백이 생기는 경우가 있다. 

## 해결법

이 문제는 해당 이미지 스타일이 ``vertical-align: baseline``일 경우 생긴다. 따라서 다음과 같이 img 속성의 정렬을 바꿔서 해결할 수 있다. 

```css
img {
    vertical-align: middle;
}
```

