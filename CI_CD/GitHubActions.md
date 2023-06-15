# GitHub Actions

Github 저장소를 기반으로 소프트웨어 개발 Workflow를 자동화 할 수 있는 도구

build, test, package, release, deploy 등 다양한 이벤트를 기반으로 직접 원하는 Workflow

Workflow는 **Runners**라고 불리는 Github에서 호스팅 하는 Linux, macOS, Windows 환경에서 실행된다. 
그리고 이 Runners를 사용자가 직접 호스팅하는 환경에서 직접 구동시킬 수도 있음(self-hosted runner)

## 장점

- 기존의 Circle CI / Travis CI / Jenkins CI와 같은 서비스 또는 설치형 CI처럼 Github에서도 Actions이라는 CI툴을 선보였으며 별다른 복잡한 절차 없이 Github를 통해 사용할 수 있다
- 워크 플로우 복제 용이
- GitHub와 통합
- 라이브 로그
- 다중 컨테이너 테스트
- 리눅스, 맥, 윈도우, ARM 및 컨테이너를 쉽게 빌드, 테스트
- 여러 운영체제 및 런타임 버전에서 동시 테스트 가능
- 모든 언어 어플리케이션 빌드, 테스트 및 배포