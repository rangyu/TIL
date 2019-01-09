# CSS 이미지 선택 시 하이라이트 없애기

이미지 선택 시 보이는 하이라이트를 없애려면 스타일시트에 다음과 같이 추가하면 된다.

```css
img {
    -ms-user-select: none;      /* IE 10+ */
    -moz-user-select: none;     /* Firefox all */
    -webkit-user-select: none;  /* Chrome all / Safari all */
    user-select: none;          /* Likely future */      
}
```