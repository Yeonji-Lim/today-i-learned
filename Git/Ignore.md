# .gitignore 적용하기

```shell
git rm -r --cached .
git add .
git commit -m "Apply gitignore"
```

# .DS_Store 파일

Desktop Services Store의 약자로, 맥에서 시스템이 finder로 폴더에 접근할 때 자동으로 생기는 파일.

해당 폴더에 대한 메타데이터(디렉토리의 크기, 아이콘 위치, 폴더의 배경 등)를 저장한다. 


윈도우는 비슷하게 thumb.db 파일이 있다. 

프로젝트를 깃 레포로 진행할 때, 자꾸 이게 포함되어 있는데, 이건 프로젝트랑 상관이 없는 파일이니까 초반에 ignore 해주는 것이 좋다


이미 있고 몇번 올렸다면 삭제하기

터미널에서 해당 레포 위치로 이동 후 다음을 입력

~~~
find . -name .DS_Store -print0 | xargs -0 git rm --ignore-unmatch -f
~~~