# CSS Placeholder 색 바꾸기

다음과 같이 바꾸면 된다.

```
/* placeholder */

::placeholder { /* Chrome, Firefox, Opera, Safari 10.1+ */
  color: #aaa;
  opacity: 1; /* Firefox */
}
:-ms-input-placeholder { /* Internet Explorer 10-11 */
  color: #aaa;
}
::-ms-input-placeholder { /* Microsoft Edge */
  color: #aaa;
}
```