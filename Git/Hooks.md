# Git Hooks

어떤 이벤트가 생겼을 때 자동으로 특정 스크립트를 실행하도록 할 수 있다.

- 클라이언트 훅 : Commit, Merge 할 때 실행
- 서버 훅 : Push 할 때 서버에서 실행

## 설치하기

hook은 git 디렉토리 아래에 `hooks` 디렉토리에 저장 (기본 훅 디렉토리는 `.git/hooks`)

쉘, Perl, Ruby, Python 등 스크립트 구현시 언어는 큰 상관이 없다. 

실행할 수 있는 스크립트 파일을 확장자 없이 저장소의 hooks 디렉토리에 넣으면 훅 스크립트가 켜지고 이 스크립트는 앞으로 계속 호출된다.

## 클라이언트 훅

저장소를 clone 해도 클라이언트 훅은 복사되지 않는다. 반드시 적용되도록 하려면 서버 훅을 이용해야만 한다.

### 커밋 워크플로 훅
- pre-commit
- prepare-commit-msg
- commit-msg
- post-commit

### 이메일 워크플로 훅

모두 `git am` 명령으로 실행된다.

## 서버 훅

모두 Push 전후에 실행된다.

훅이 0이 아닌 값을 반환하면 해당 Push는 거절되고 클라이언트는 에러 메시지를 출력한다.

- pre-receive : 브랜치의 푸시 권한 제어
- update
- post-receive : 사용자나 서비스에 알림 메시지 보낼 수 있음
