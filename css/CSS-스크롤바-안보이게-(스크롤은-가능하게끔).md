# CSS 스크롤바 안보이게 (스크롤은 가능하게끔)


```css
/* IE */
div {
  -ms-overflow-style: none; 
}

/* chrome etc */
div::-webkit-scrollbar { 
    display: none !important; 
}
```