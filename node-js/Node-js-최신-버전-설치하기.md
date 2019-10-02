
# Node.js 최신 버전 설치하기

## Node.js 현재 버전 확인

만약 최신 버전이 아니라면 업데이트할 것.
```
node -v
```


##  Node.js 최신 버전 설치하기
### 캐시 삭제하기
최신 버전 업데이트를 위해 남아 있는 캐시를 강제로 삭제하기.
```
sudo npm cache clean -f
```

### n 설치
npm으로 n을 설치. (n은 node.js의 버전을 관리하는 패키지)
```
sudo npm install -g n
```

### 최신 버전 설치하기
최신의 안정(stable) 버전을 설치한다.
```
sudo n stable
```

#### (참고)

만약 특정 버전의 node.js를 설치하고 싶다면 아래와 같이 "stable" 대신 특정 버전을 입력하면 된다. 

```
sudo n 12.10.0﻿
```

혹은 가장 최신 버전을 설치하고 싶다면,

```
sudo n latest
```

혹은 LTS 버전 (Long Term Support, 장기간 지원 버전)을 설치하고 싶다면,

```
sudo n lts
```