# Blockly 크롬 Uncaught (in promise) DOMException 에러 해결법

Blockly 설치 시 다음과 같은 크롬 에러가 발생함.

![크롬에러메시지](https://user-images.githubusercontent.com/36276682/56076261-e919a780-5e09-11e9-9a2e-47340838602a.png)

 
원인은 사운드 play()관련 함수 탓. 해결법은 다음을 추가하여 preloadAudio_ 함수를 덮어씌우면 된다.

~~~javascript
Blockly.WorkspaceSvg.prototype.preloadAudio_ = function() {};
~~~

---
출처 : https://github.com/google/blockly/issues/299
