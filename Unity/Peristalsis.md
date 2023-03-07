# Unity에 Github, VSCode 연동하기

옛날에 윈도우 환경에서 유니티를 잠깐 써보고 (진짜 완전 입문정도)

지금은 mac 환경에서 리듬게임 프로토타입을 만들어야하는 목표가 주어졌다. 

깃헙과 vscode를 연동할 계획이다.

​

먼저 Unity hub를 깔아주고 유니티 계정을 만들고 퍼스널 라이센스를 받아준다.

​

깃헙 연동은 간단히 깃헙 레포를 먼저 만들고(gitignore에 unity)

클론 받아서 hub을 통해서 그 위치에 프로젝트를 생성하면 된다. 

​

유니티는 게임 구성 편집 및 빌드를 담당하는 툴인 Unity Editor와 스크립터 편집기가 분리되어 있다.

보통 유니티를 처음 시작하면 유니티를 설치할 때 같이 설치할 수 있는 MonoDevelop이나 Visual Studio를 사용한다.

그런데 나는 mac이기도하고 vscode가 편하기 때문에 vscode로 진행하겠다.

​

.NET Core SDK를 설치한다. 

https://dotnet.microsoft.com/en-us/download

(윈도우는 설치후 재시작해야 함)

터미널에서 dotnet 명령어를 실행해서 잘 설치되었는지 확인이 가능하다


그런데 난 안됐다
~~~
zsh: command not found: dotnet
~~~

그래서 그냥 brew로 설치

~~~
$ brew install --cask dotnet-sdk
~~~
dotnet이라고 치면 다음과 같이 나온다.

~~~
Usage: dotnet [options]
Usage: dotnet [path-to-application]

Options:
  -h|--help         Display help.
  --info            Display .NET information.
  --list-sdks       Display the installed SDKs.
  --list-runtimes   Display the installed runtimes.

path-to-application:
  The path to an application .dll file to execute.
~~~

이제 vscode로 가서 c# 확장을 설치해주자

mac에서는 이게 .NET Core SDK가 호환되지 않는 경우가 있다고 한다. 

이럴 경우 호환되는 버전으로 다운그레이드하고 자동 업데이트를 해제하면 된다고함

나는 그냥 처음부터 호환되는 버전인 1.22.1을 깔고 자동 업데이트 해제해줌


그리고 유니티 에디터로 넘어간다. 

Preferences의 External Tools에서 External Script Editor를 Visual Studio Code로 설정해준다.
​
그러면 일단 연동은 완료.