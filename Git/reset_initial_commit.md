# 첫 커밋을 지우기(push하기전)

원래 커밋을 취소하는 거는
```
git reset HEAD^1
```

로 하면 되는데 첫 커밋의 경우 이 방법으로는 지울 수 없다.

이때는 최초의 commit을 지운다기 보다는 그 브랜치를 지우는 것이라고 한다.
대신 git branch -D를 사용하면 안되는데, safety check이 걸리기 때문!

```
git update-ref -d HEAD
git rm --cached -r .
```

1. HEAD를 가리키고 있는 branch 지우기
2. --cached를 통해 원격에서만 지우고 로컬에는 파일 남기기