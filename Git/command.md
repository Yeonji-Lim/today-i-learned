## deleted된 파일들 한번에 반영하기

~~~
git add -u
git commit -m "."
git push
~~~

-u는 update tracked files라고 함

## 삭제된 원격 브랜치 목록을 로컬에 반영하기
```sh
git remote prune origin
```