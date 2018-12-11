# Mac OS 업데이트 후의 Git 에러 해결법

Mac OS를 업데이트 후 git 명령어를 쓰면 다음과 같은 에러가 뜬다. 

```bash
git --version
xcrun: error: invalid active developer path (/Library/Developer/CommandLineTools), missing xcrun at: /Library/Developer/CommandLineTools/usr/bin/xcrun
```

이 문제를 해결하려면 xcode를 업데이트하거나, 터미널에서 `xcode-select` 명령어를 사용하면 된다. 만약 원래 xcode를 사용하지 않는다면, 후자의 방법으로 간단히 해결하자. 

터미널에서 다음과 같이 명령어를 입력한다.
```bash
xcode-select --install
```

그러면 아래 이미지와 같이 명령어 라인 개발자 도구를 설치하라는 창이 뜬다. 설치 버튼을 누른다. 

![2018-12-11 9 35 06](https://user-images.githubusercontent.com/36276682/49801702-3b7c8600-fd8e-11e8-8bcd-b6610d2abedc.png)

약관에 동의를 하면 설치가 진행된다. 

![2018-12-11 9 35 21](https://user-images.githubusercontent.com/36276682/49801715-433c2a80-fd8e-11e8-8a60-0b3f4d8cc952.png)

설치가 마치면 이제 git 명령어가 제대로 실행되는 것을 볼 수 있다. (VSCode를 재시작하면 Git 에러가 해결된다.)