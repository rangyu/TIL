# Mac에서 Docker 설치하기

이 글에서는 Mac에서 Docker를 설치하는 방법을 알아보고자 한다. (더 자세한 내용은 [Docker 공식 문서](https://docs.docker.com/get-started/)를 참고하자)

## 홈브류(homebrew)로 설치하기

다음과 같이 홈브류(homebrew)로 Docker를 설치한다. 

```
brew install Docker
```

## Docker 어플리케이션 설치

아래 링크에서 맥용 Docker 어플리케이션을 다운받는다. 
https://docs.docker.com/docker-for-mac/install/

다운받은 어플리케이션을 설치한다.

![docker1](https://user-images.githubusercontent.com/36276682/50847373-c912bc00-13b4-11e9-8d56-eefe56bcabf8.png)

실행하면 다음과 같이 백그라운드에서 docker가 실행된다.

![docker2](https://user-images.githubusercontent.com/36276682/50847384-cd3ed980-13b4-11e9-96da-4d8c3b9f7def.png)

## Docker 버전 확인

이제 터미널에서 `dockder version`을 입력하면 다음과 같이 dockder 클라이언트 및 서버 버전을 볼 수 있다. 
```
$ docker version
Client: Docker Engine - Community
 Version:           18.09.0
 API version:       1.39
 Go version:        go1.10.4
 Git commit:        4d60db4
 Built:             Wed Nov  7 00:47:43 2018
 OS/Arch:           darwin/amd64
 Experimental:      false

Server: Docker Engine - Community
 Engine:
  Version:          18.09.0
  API version:      1.39 (minimum version 1.12)
  Go version:       go1.10.4
  Git commit:       4d60db4
  Built:            Wed Nov  7 00:55:00 2018
  OS/Arch:          linux/amd64
  Experimental:     false
```

## Hello, Docker

다음과 같이 입력하고 제대로 실행이 되는지 확인해보자. 

```
docker run hello-world
```