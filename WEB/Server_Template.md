# 서버 템플릿 구조
![](https://i.imgur.com/CrHNLUj.png)

## 각 요소 설명

### route
restful하게 설계해야 함

요청 메소드로 받아서 restful하게 설계

즉, api로 요청을 보내면 route가 캐치.

이건 Controller에 연결이 되어 있음, Controller로 request 값을 보내준다.

### Controller
request 값을 povider와 service에 넘겨준다. 

이때 route에 있는 path-variable, query-string, body 등에 있는 변수 값을 가져와야 한다. 그리고 파라미터 값으로 povider와 service에넘겨줌

Validation 처리를 해준다.

Provider나 Service에서 결과값을 받으면 json으로 response를 보내준다.

### Service 
1. DB Connection이 일어난다.

2. transaction 처리를 진행한다.

Select 외의 Insert, update, delete 할 때 사용된다.

Dao function에 해당 파라미터 값을 그대로 넘겨준다.

결과값을 controller에 넘겨준다. 

### Provider
Select 할 때 사용

중복 검사를 하기 위해서는 select를 해주어야 하므로, 중복검사가 필요 할 때 필요함

Service에서 조회할 때도 Provider를 통해서 조회해야 한다.

### Dao
실질적인 쿼리 작성 및 실행이 이루어진다.

결과가 되는 row들을 호출한 provider나 service에 넘겨준다.

## 언어별 차이

### PHP
route가 없다.
index.php에서 route를 지정해주는 형식이다.

### Node.js
다 있음

### Spring Boot
route가 없다.

controller 안에 route까지 직접 지정해준다.

## 폴더 구조
구조의 각 구성 요소  별로 모아두는 것이 아니라. 

**도메인 별로 요소들이 모아져야 한다.**


