# Cordova 작업환경 구축하기 (Mac 기준)

## 설치하기

### Cordova 설치하기 

시작하기 전에 npm과 node.js가 미리 설치되어 있어야 한다. npm으로 Cordova를 설치한다.

```bash
sudo npm install -g cordova
```

설치된 Cordova 버전을 확인하려면 다음과 같이 입력하면 된다

```bash
cordova -v
8.1.2 (cordova-lib@8.1.1)
```

### Android SDK 설치하기

다음의 명령어로 현재 Java가 설치되어 있는지 확인한다.

```bash
javac -version
```

만약 Java가 설치되어 있지 않다면 Apple 사이트에서 다운로드 받아서 설치한다.
- Java 다운로드 : https://support.apple.com/downloads/java

### Ant 설치하기

Apache Ant는 Java를 빌드하기 위해 필요하다. 먼저 Ant가 설치되어 있는지 확인한다.

```bash
ant -version
```

만약 Ant가 설치되어 있지 않다면 Homebrew를 사용해서 설치할 수 있다. Homebrew가 설치되어 있는지 확인한다. 

```bash
brew --version
```

만약 Homebrew 설치되어 있다면 최신 버전으로 업데이트한 후 Ant를 설치한다.

```bash
brew update
brew install ant
```

만약 Homebrew가 설치되어 있지 않다면, 다음과 같이 Homebrew를 설치한 뒤 Ant를 설치한다.

```bash
ruby -e "$(curl -fsSL https://raw.github.com/Homebrew/homebrew/go/install)"
brew install ant
```


## 새 프로젝트 만들기

다음과 같이 새 Cordova 프로젝트를 만든다.

```bash
cordova create hello com.example.hello HelloCordova
```

## 플랫폼 추가하기

생성된 프로젝트 경로로 들어간다.

```bash
cd hello
```

필요한 플랫폼을 추가한다.

```bash
cordova platform add ios
cordova platform add amazon-fireos
cordova platform add android
cordova platform add blackberry10
cordova platform add firefoxos
```

(참고) 만약 설치된 플랫폼을 확인하고 싶다면 다음과 같이 입력하면 된다.

```bash
cordova platforms ls
```

설치된 플랫폼을 삭제하는 명령어는 다음과 같다.

```bash
cordova platform remove firefoxos
cordova platform rm ios
```

## VSCode에서 Cordova 작업하기 

VSCode > Extensions > Cordova Tools 검색. 설치 후 reload한다.
