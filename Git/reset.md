# 첫 커밋을 지우기(push하기전)

원래 커밋을 취소하는 거는
```sh
git reset HEAD^1
```

로 하면 되는데 첫 커밋의 경우 이 방법으로는 지울 수 없다.

이때는 최초의 commit을 지운다기 보다는 그 브랜치를 지우는 것이라고 한다.
대신 git branch -D를 사용하면 안되는데, safety check이 걸리기 때문!

```sh
git update-ref -d HEAD
git rm --cached -r .
```

1. HEAD를 가리키고 있는 해시값 지우기
   
   `update-ref` : `commit`을 가리키는 해시 값(`ref`)을 업데이트
   
2. --cached를 통해 원격에서만 지우고 로컬에는 파일 남기기

**그런데 이렇게 하면 첫커밋 이후의 커밋 모두 사라지고 최종 파일만 남는다..!**

## 최초 (initial) 커밋으로부터 rebase 하기

```sh
git rebase -i --root
```

목록이 쭉 나오면 거기서 `pick 첫 커밋`만 지우면 됨

# 방금 시도한 병합 취소

```sh
git reset --merge ORIG_HEAD
```
