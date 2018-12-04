# CSS Float를 Clear하는 방법 (Clearfix)

Float 속성을 Clearfix 하기 위해서 가상 선택자 :after를 사용하면 된다. Float 속성을 적용한 요소들의 부모 컨테이너에 다음과 같은 :after 스타일을 추가한다.

```css
#container:after {
    content: ""; 
    display: block; 
    clear:  both;
}
```

(참고) 만약 IE 5.5~7 브라우저를 지원해야 한다면 다음의 Hack을 추가한다.

```css
#container {
    *zoom: 1; /* IE5.5~7 Hack */
} 
```
