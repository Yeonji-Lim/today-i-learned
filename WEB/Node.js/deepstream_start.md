
## 패키지 관리자

RedHat 계열의 Cent OS에서는 YUM(Yellow dog, Updater, Modified)이 있고,

Debian 계열의 Ubuntu에서는 APT(Advanced Packaging Tool)가 있다.

macOS 용으로는 Homebrew가 있음


## NPM(Node Package Manager)

자바스크립트 프로그래밍 언어를 위한 패키지 관리자

node.js에서 사용하는 모듈들을 패키지로 만들어서 npm을 통해서 관리하고 배포함

-> 비슷한 개념으로 python의 pip, Java의 Jpm, C#의 NuGet, PHP의 Composer, ruby의 Gem


맥북의 경우, node가 brew로 설치가 안되는 경우가 있는데, 그냥 node.js로 가서 pkg 파일을 다운로드 해서 진행하는 편이 빠를 수 있음

~~~
npm install (with no args, in package dir)
npm install [<@scope>/]<name>
npm install [<@scope>/]<name>@<tag>
npm install [<@scope>/]<name>@<version>
npm install [<@scope>/]<name>@<version range>
npm install <alias>@npm:<name>
npm install <git-host>:<git-user>/<repo-name>
npm install <git repo url>
npm install <tarball file>
npm install <tarball url>
npm install <folder>
aliases: npm i, npm add
common options: [-P|--save-prod|-D|--save-dev|-O|--save-optional|--save-peer] [-E|--save-exact] [-B|--save-bundle] [--no-save] [--dry-run]
~~~

~~~
npm test [-- <args>]
aliases: t, tst
~~~

## git 계정 인증 관련
이제 새로운 컴퓨터에서 github을 접근하려고 할 때 비밀번호가 아니라 토큰으로 로그인해야 함

깃허브에서 settings에서 토큰 받을 수 있음

비밀번호 대신 토큰 값을 넣으면 됨


실시간 서버로 deepstream server 사용하기

deepstream io를 git clone 하고 사용

가이드와 다름!

다음의 링크를 따라함

https://github.com/deepstreamIO/deepstream.io
