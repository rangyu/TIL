# Blockly workspace에 새로운 block 생성하기

```javascript
var block = workspace.newBlock('operator_random'); // 블록 프로토타입 이름
block.initSvg();
block.moveBy(230, 45); // 위치 바꾸기 (기본 0,0)
block.render(false); 
```