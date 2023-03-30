# 생성된 커밋의 유저 변경

## 1. git config에 바꾸고자 하는 user가 설정되어 있어야 한다.

## 2. 변경하고자 하는 commit 선택

### rebase
rebase, 3번째 커밋을 바꾸고 싶은 경우
```sh
git rebase -i HEAD~3
```

전체 커밋을 보고 싶은 경우
```sh
git rebase -i --root
```

### 선택
나오는 커밋 목록에서 변경하고자 하는 커밋의 `pick`을 `e`로 수정

## 3. 변경할 author 입력

```sh
git commit --amend --author="아이디 <이메일>"
```

```sh
git commit --amend --author="Yeonji-Lim <view7186@naver.com>"
```

## 4. github repository에 반영

```sh
git rebase --continue 
git push -f origin master
```