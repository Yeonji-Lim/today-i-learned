# 하나의 로컬에서 여러 계정 사용하기

```shell
cd ~/.ssh
```

```shell
ssh-keygen -t rsa -C "view7186@naver.com" -f "id_rsa_leepae"
```

![[Multi_User_user1.png]]

```shell
ssh-keygen -t rsa -C "view7186@dalcomsoft.com" -f "id_rsa_yeonji_dalcom"
```

## SSH key 생성 확인
```shell
ls -al ~/.ssh
```

![[ssh_key_check.png]]

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

![[github_key_setting.png]]

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
```

**git은 반드시 git으로 작성**
자신의 계정으로 변경X 
**github.com-userA 는 SSH config 파일에서 Host 지시자 뒤에 설정한 값**으로 대신하면 됨

다음과 같이 출력됨
```
Hi Yeonji-Lim! You've successfully authenticated, but GitHub does not provide shell access.
```

## 참고
https://usingu.co.kr/frontend/git/%ED%95%9C-%EC%BB%B4%ED%93%A8%ED%84%B0%EC%97%90%EC%84%9C-github-%EA%B3%84%EC%A0%95-%EC%97%AC%EB%9F%AC%EA%B0%9C-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0/