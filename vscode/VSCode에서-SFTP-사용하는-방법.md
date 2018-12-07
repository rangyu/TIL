# VSCode에서 SFTP 사용하는 방법

## SFTP 확장기능 설치하기

1. VSCode 확장기능(Extensions) 탭에서 `sftp`를 검색한다. 
2. 검색된 liximomo의 sftp를 설치한다. (sftp/ftp sync 기능)
3. 해당 기능을 reload한다.

## SFTP 설정하기

프로젝트 폴더를 연 상태에서 F1키를 누른다. (Mac일 경우 Fn + F1) 

```
> SFTP: Config
```

명령 프롬프트 창에 위와 같이 입력한다. 그럼 해당 폴더 내 `.vscode/sftp.json` 파일이 생성된다. 아래와 같은 json 설정 파일을 내 접속 경로로 바꾼다. 

```
{
    "protocol": "sftp",
    "host": "localhost",
    "port": 22,
    "username": "username",
    "remotePath": "/"
}
```

만약 private key로 접속하려면 다음을 추가한다.
```
{
    "privateKeyPath": "your_privateKeyPath"
}
```

먄약 비밀번호로 접속하려면 다음을 추가한다. 
```
{
    "password": "your_password"
}
```

## SFTP Sync하기 

설정을 저장하고 난 뒤 SFTP 연동을 하려면 해당 폴더 영역에서 마우스 오른쪽 버튼을 클릭한다.  

![vscode-sftp-popup](https://user-images.githubusercontent.com/36276682/49629101-16ed7a80-fa2b-11e8-901e-8b26e6724018.png)

다음과 같은 메뉴가 추가된 것을 볼 수 있다.

- Sync Local -> Remote (로컬에서 원격으로 동기화한다)
- Sync Remote -> Local (원격에서 로컬로 동기화한다)
- Sync Both Directions (양방향으로 동기화한다)

이제 자유롭게 로컬과 원격 데이터를 동기화할 수 있다. 