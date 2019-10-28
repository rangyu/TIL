# CSS Select 스타일 커스텀하기

다음과 같이 Select 스타일을 커스텀할 수 있다.
(단, option은 커스텀 불가능)

```css
/* select */
select {
  width: 200px; 
  padding: 6px 10px; 
  font-size: 0.9rem;
  font-family: inherit; 
  background: url('./img/icon-arrow-down.svg') no-repeat 95% 50%; 
  background-size: 15px 15px;
  border: 1px solid #333;
  background-color: #fff;
  border-radius: 0; 
  -webkit-appearance: none; /* 네이티브 외형 감추기 */
  -moz-appearance: none;
  appearance: none;
  outline: none;
}

select:focus {
  border-color: #0094e1;
}
```