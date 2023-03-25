# 하나의 로컬에서 여러 계정 사용하기

```shell
cd ~/.ssh
```

```shell
ssh-keygen -t rsa -C "view7186@naver.com" -f "id_rsa_leepae"
```

![](https://i.imgur.com/ckrxBlv.png)

```shell
ssh-keygen -t rsa -C "view7186@dalcomsoft.com" -f "id_rsa_yeonji_dalcom"
```

## SSH key 생성 확인
```shell
ls -al ~/.ssh
```

![](https://i.imgur.com/VR40eOQ.png)

.pub : 공개키 파일
붙지 않은 파일이 개인키 파일

## ssh-agent에 새로 생성한 SSH key 추가 

백그라운드에 ssh-agent 실행

```shell
eval "$(ssh-agent -s)"
```
이렇게 입력하면 pid 값이 나옴

개인키를 추가
```shell
ssh-add ~/.ssh/id_rsa_leepae
ssh-add ~/.ssh/id_rsa_yeonji_dalcom
```

ssh-agent에 정상적으로 SSH 개인키가 추가되었는지 확인
```shell
ssh-add -l
```

## GitHub에 새 SSH 공개키 추가
vscode로 공개키 열기
```shell
code ~/.ssh/id_rsa_leepae.pub
```

![](https://i.imgur.com/algZgjx.png)

다른 계정도 동일한 과정 진행

## SSH config 파일 설정하고 SSH 연결 테스트
```shell
cd ~/.ssh
code config
```

-   2, 8 라인 SSH 연결에 사용될 대표이름  
    `Host`에 대한 값이 중요
    나중에 ssh로 연결할 때 Host 지시자에 지정된 값이 사용되니 구분하기 쉽고 기억하기 편리한 이름으로 작성
-   3, 9 라인 : github의 도메인
-   4,10 라인 : github 사용자 아이디
-   5, 11 : 앞서 생성한 개인키 경로

SSH 연결 테스트
```shell
ssh -T git@github.com-leepae
ssh -T git@github.com-yeonji-dalcom
```

**git은 반드시 git으로 작성**
자신의 계정으로 변경X 
**github.com-userA 는 SSH config 파일에서 Host 지시자 뒤에 설정한 값**으로 대신하면 됨

다음과 같이 출력됨
```
Hi Yeonji-Lim! You've successfully authenticated, but GitHub does not provide shell access.
```

깃헙 로컬 디렉토리로 들어간 뒤 다음과 같이 입력
```shell
git remote set-url origin git@github.com:Yeonji-Lim/ps-log.git
```

클론 받을 때 이런식으로 내가 설정한 이름을 붙여주어야 한다.
```shell
git clone git@github.com-yeonji-dalcom:dalcomsoft/ss_-gm.dalcomsoft.net.git
```

## 비밀번호 없이 push/pull 하기
위와 같이 진행해주고 나면 push, pull 할 때 계속해서 비밀번호를 입력해주어야 하는 귀찮음이 있다.

해당 레포지토리의 로컬 위치로 이동

```shell
git remote add origin git@github.com-leapae:dongguk-umc-3rd/Spring_A_Study.git
```

이미 있다고 하면 기존 origin 삭제 후 다시 진행

```shell
git remote remove origin
git remote add origin git@github.com-leapae:dongguk-umc-3rd/Spring_A_Study.git
git remote show
```

## git config 연동 안됨 이슈
SSH키만 설정하고 푸시하면 의도하지 않은 계정으로 기록이 남을 수 있다. 
이를 방지하기 위해 다음의 링크를 참고해야 한다.
https://www.lainyzine.com/ko/article/useful-git-settings-when-using-github-multi-account/

## 참고
https://usingu.co.kr/frontend/git/%ED%95%9C-%EC%BB%B4%ED%93%A8%ED%84%B0%EC%97%90%EC%84%9C-github-%EA%B3%84%EC%A0%95-%EC%97%AC%EB%9F%AC%EA%B0%9C-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0/

https://goddaehee.tistory.com/254
