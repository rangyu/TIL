# Git hook 사용하기 

## 깃훅(Git hook)이란?
git에서 제공하는 프로세스(커밋, 푸시, 리베이스 등)의 전이나 후 이벤트를 후킹하여 특정 액션을 실행하는스크립트를 git hook이라고 한다.

## 여러가지 Git hooks

- applypatch-msg
- pre-applypatch
- post-applypatch
- pre-commit
- prepare-commit-msg
- commit-msg
- post-commit
- pre-rebase
- post-checkout
- post-merge
- pre-receive
- update
- post-receive
- post-update
- pre-auto-gc
- post-rewrite
- pre-push

## Git hooks 사용법 

### 내부 저장소를 이용한 방법 

깃허브 로컬 저장소 폴더 내 `./git/hook` 경로에 사용하고자 하는 깃훅 이벤트명으로 확장자가 없는 실행 가능한 스크립트를 넣으면 된다. 


### 웹훅을 이용한 방법

깃허브 사이트 내 원격 저장소 > Settings > Webhooks 메뉴에서 URL를 설정하면 된다.

