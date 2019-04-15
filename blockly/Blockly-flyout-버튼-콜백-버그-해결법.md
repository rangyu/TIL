
# Blockly flyout 버튼 콜백 안되는 버그 해결법 (scratch-blocks 경우)

## 문제 

flyout에 커스텀 버튼과 콜백 함수를 가이드 문서대로 추가했지만 callbacks를 찾을 수 없다는 warning만 나옴.

```html
  <!-- toolbox xml --> 
  <button text="button with callback" callbackKey="CALLBACKBUTTON"></button>
```
```javascript
  /* callback function */
  myWorkspace.registerButtonCallback('CALLBACKBUTTON', function(button) {
    console.log("Button Callback!");
  });
```

---

## 해결 
해당 문제는 blocly의 구버전 버그였음(flyout_button.js) 현재  원본 blockly 내 버그는 현재 고쳐진 상태. 

https://github.com/google/blockly/pull/2196 

하지만 스크래치 블록(scratch-blocks) 버전에서는 해당 버그가 여전히 남아 있었음. 그래서 위 링크 내 코드대로 수동으로 버그를 고쳐주니 해결되었다.

