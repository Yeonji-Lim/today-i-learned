## this exceeds GitHub's file size limit of 100.00 MB 해결

-> git lfs 설치해야 함

먼저 git 버전 1.8.2 이상을 요구함
~~~
git --version
~~~

mac의 경우, brew로 git-lfs 설치

~~~
brew update
brew install git-lfs
~~~
해당하는 레포로 위치를 옮긴 다음, git lfs 설치

~~~
git lfs install
~~~

그러면 다음과 같은 문구가 나옴

~~~
Updated git hooks.
Git LFS initialized.
~~~
그리고 안올라갔던 용량이 큰 파일들을 git lfs의 관리대상으로 추가해줌

exe 파일을 모두 추가하고 싶은 경우 다음과 같은 명령

~~~
git lfs track “*.exe”
~~~

## _pickle.UnpicklingError: invalid load key, 'v' 해결

위 처럼 git lfs 를 쓰면 용량이 큰 파일이 텍스트 파일로 변경되어서 올라가는 방식으로 용량문제를 해결한다고 한다.

그런데 이걸 다시 다운 받을때 그대로 텍스트 파일이기 때문에 위와 같은 에러가 발생한다. 

이때는 다음의 명령을 해주면 된다.

~~~
git lfs fetch
~~~