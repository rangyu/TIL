# [React] Create-React-App로 리액트 시작하기 


npx로 create-react-app 실행하기 (`my-app` 부분은 프로젝트명으로 바꾸기)

```
npx create-react-app my-app
```

## 로컬호스트에서 테스트하기

`my-app` 안으로 이동 후 `npm start`하면 이제 `http://localhost:3000`에서 결과 화면을 볼 수 있다.

```
cd my-app 
npm start
```

## [이슈1]  babel-loader 버전 에러가 났음


`npm start`를 했지만 아래와 같은  babel-loader 버전관련 에러 메시지가 뜨며 테스트 서버가 뜨지 않았다.


### 원인

create-react-app으로 자동설치된 babel 버전과 예전에 npm으로 로컬에 수동 설치했던 babel 버전이 서로 달라서 에러가 난듯.

### 해결

기존 로컬에 설치되어 있던 `node_modules`를 삭제했더니 문제가 해결되었음.
```
sudo rm -rf /Users/사용자명/node_modules
```

## 빌드하기

npm으로 배포용 파일을 빌드할 수 있다. (build 폴더가 생김)
```
npm run build
```

## [이슈2] React 빌드 후 리소스 경로 에러가 낫음


### 원인 
빌드 후 root 경로 기준으로 리소스 URL이 자동 생성되는데, 만약 실제 위치가 이와 다르면 리소스 경로 에러가 난다.

### 해결

방법1) 빌드 파일을 root 경로로 이동시켜준다.

방법2) `package.json`에 다음과 같이 `homepage` 경로를 직접 지정해준다. 
```
 "homepage": ".",
```
그 다음 다시 빌드하면 경로 에러가 없어진다.
```
npm run build
```
