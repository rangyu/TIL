# Expo로 리액트 네이티브 시작하기 

## Expo란?

리액트와 자바스크립트 언어로 안드로이드/아이폰/웹용 통합해서 개발 가능한 플랫폼.

(페이스북이 React Native for web를 출시한 후
Expo에서도 웹용 포팅을 지원한다.)

과거 리액트 네이티브 앱을 빠르게 시작할 수 있게끔 자동세 팅해주는 react-native-create-app가 따로 있었는데 지금은 expo 안으로 통합되었다.

---

- 공식 홈 : https://expo.io/
- 공식 문서 : https://docs.expo.io/versions/latest/

## Expo CLI 설치하기

Expo 앱를 자동으로 만들어주는 툴인 Expo CLI를 설치한다.
```
npm install -g expo-cli
```

## 새로운 Expo 앱 만들기


### expo init

설치한 Expo CLI를 이용해서 새로운 Expo 앱을 생성해준다. (`expo init` 명령어)
```
expo init my-app
```

이후 다음의 순서로 진행된다.

1. template 고르기
2. 홈화면 이름 설정하기
3. Yarn 의존성 파일들 설치


### 프로젝트 시작하기

```
cd my-app
yarn start
```

- Expo 개발자도구  : `http://localhost:19002`


## 테스트용 디바이스에 Expo 앱 설치하기

- [안드로이드 설치 링크](https://play.google.com/store/apps/details?id=host.exp.exponent)
- [아이폰 설치 링크](https://itunes.com/apps/exponent)