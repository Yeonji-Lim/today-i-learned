# git filter

깃허브 레포에 잘못해서 공개해서는 안되는 파일이 올라가서 삭제해야하는 경우, 삭제 기록이 남아서 그 내용까지 모두 볼 수 있게 된다.

보안 상으로 문제가 되는데, 처음부터 프라이빗으로만 레포를 운영한다던가 처음부터 gitignore로 관리해주면 괜찮지만,

공개 레포의 경우에는 git init으로 다시 레포를 정리하던가 해야하지만 다른 방법으로 git filter 가 있다.


git filter는 해당 파일을 git 전체 히스토리에서 필터링해서 재작성해준다.

~~~
$ git filter-branch -f --index-filter 'git rm --cached --ignore-unmatch [해당파일경로&이름]' --prune-empty -- --all
~~~

git rm --cached : 리모트 브랜치에 있는 해당 파일을 정리, 이름이 맞지 않는 파일은 무시하고 해당 파일만 원격 브랜치에서 삭제해줌


만약에 resource라는 폴더 하위에 있는 것들 모두 진행하고 싶다면

~~~
$ git filter-branch -f --index-filter 'git rm --cached --ignore-unmatch resource/' --prune-empty -- --all
~~~

그랬더니 recursive한거는 삭제 못했다면서 뭐라고 떴다. 

~~~
$ git filter-branch -f --index-filter 'git rm --cached -r --ignore-unmatch [해당파일경로&이름]' --prune-empty -- --all
~~~

위와 같이 cached 다음에 -r 옵션을 추가해준다.

브랜치가 재작성되면 원격 저장소와 로컬 저장소의 브랜치가 서로 나뉘어 있는 데,

~~~
$ git push origin [브랜치이름] --force
~~~

위 명령어를 통해 강제로 push 해서 로컬 브랜치를 원격 브랜치로 넣어주면 됨. 모든 브랜치를 재작성 했기 때문에 브랜치 별로 다 해주어야 함

# Unable to merge unrelated histories in this repository. 에러

그런데 팀원들에게 다시 받으라고 했을 때, 이런 에러가 뜨면서 풀이 받아지지 않았다.

해당 폴더를 지우고 시도해도 마찬가지 였다.

이를 해결하기 위해서 다음과 같은 명령으로 히스토리를 병합해야 한다고 한다.

~~~
git pull origin main --allow-unrelated-histories
~~~

이미 존재하는 두 프로젝트의 기록을 저장할 때 사용된다.

다른 사람의 경우 잠깐 올리고 엇 하고 바로 지운 경우여서 이런 케이스가 안생기는 데,

우리 같은 경우에는 내내 프라이빗으로 그냥 보안이고 뭐고 다 올리다가 퍼블릭으로 바꾸면서 기록을 삭제해서 이런 오류가 생겼다.

# git dry run

git 명령을 할 때 약간 쫄린다 싶으면 사용하자

어떤 명령 뒤에 --dry-run을 붙이면 실제로 실행되지는 않고 실행되었을 시 결과물만 볼 수 있다.

