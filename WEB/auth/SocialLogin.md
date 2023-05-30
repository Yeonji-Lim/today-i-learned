# 소셜 로그인

## 주체
### Client
사용자 아님, 우리 서비스

### Resource Owner
서비스를 사용하는 유저.

Client가 받고자하는 정보의 주인

### Resource Server
소셜 로그인 기능을 제공하는 곳

정보를 가지고 있음

## 절차
1. 소셜 로그인을 누름
	1. Client는 OAuth라는 서비스로 Resource Server랑 상호작용함
2. 소셜 로그인 페이지로 이동
3. 로그인 성공
	1. Resource Server가 Client의 페이지로 Resource Owner를 redirect

## [OAuth](OAuth)
서비스 제공자와 사용자 사이에서 로그인을 중개함
- Resource Server는 Client에게 Access Token을 제공
- Client는 Access Token으로 Resource Server에게 접근 가능 -> Client는 Resource Owner에게 로그인 페이지 제공 가능

## 구현 절차

### 1. Client 를 Resource Server에 등록한다.

### 2. 소셜 로그인 진행

#### 1. Resource Owner에게 승인 받기
소셜 로그인 시도 창으로 이동
- 로그인 되어있는 경우 Resource Server에서 로그인을 시도한 링크의 Client ID 점검
- 로그인 x : 로그인 진행

#### 2. 로그인을 시도한 링크의 redirect URL 비교
- Resource Server가 해당 URL을 가지고 있지 않으면 종료
- 같지 않다면 Resource Owner에게 Client에게 정보를 주어도 되는지 물어봄 -> 허용시 응답을 Client에 전달
  `user id : [링크에 담겨있던 client id 값], scope:[그 링크에 담겨있던 scope]`

#### 3. Resource Owner에게 승인을 받았으니 승인 받은 증거로 Resource Server에게 정보 요청
- Authorization Code를 Resource Server가 Resource Owner에게 제공하는 응답의 헤더에 `location: https://[redirect URL]?code=[Authorization Code]` 이라는 값을 주어 redirect
- location으로 인해 Resource Client는 해당 주소로 redirect
- client는 params을 통해 authorization code를 알게됨

#### 4. Client는 Resource Server에 접속
![](https://i.imgur.com/8uTTZFw.png)

- Resource Server는 Authorizaion code와 clientID, client secret, redirect URL이 모두 일치하는지를 확인
- 일치하면 Access Token을 발급

## +
고유한 id와 provider를 같이 사용하자
- 소셜 로그인 마다 고유한 id를 부여하는 것을 보장
- email의 경우 유저가 임의로 변경할 수 있음