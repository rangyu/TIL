# Blockly 크롬 Uncaught (in promise) DOMException 에러 해결법

Blockly 설치 시 다음과 같은 크롬 에러가 발생함.

![크롬에러메시지](https://user-images.githubusercontent.com/36276682/56076261-e919a780-5e09-11e9-9a2e-47340838602a.png)

 
원인은 사운드 play()관련 함수 탓. 크롬 정책상 제대로 로딩하지 않은 사운드를 play할 경우 에러를 띄운다고 한다.

아래가 문제가 되는 원본 코드.

```javascript
// 문제가 된 부분 : play() 함수를 호출하는 부분 (workspace_audio.js 파일)
Blockly.WorkspaceAudio.prototype.preload = function() {
  for (var name in this.SOUNDS_) {
    var sound = this.SOUNDS_[name];
    sound.volume = 0.01;
    sound.play();
    sound.pause();
    // iOS can only process one sound at a time.  Trying to load more than one
    // corrupts the earlier ones.  Just load one and leave the others uncached.
    if (goog.userAgent.IPAD || goog.userAgent.IPHONE) {
      break;
    }
  }
};
```

해결법은 play() 함수를 호출하기 전 load() 함수를 이용해서 이미 사운드를 로딩하는 것. 다음과 같이 Blockly.WorkspaceAudio.prototype.preload 함수를 오버라이드하면 된다.

```javascript
Blockly.WorkspaceAudio.prototype.preload = function() {
  for (var a in this.SOUNDS_) {
      var b = this.SOUNDS_[a];
      b.load();
      if (goog.userAgent.IPAD || goog.userAgent.IPHONE)
          break
  }
}
```

---
Thank You, jonmersan!

출처 : https://github.com/google/blockly/issues/299

