# OAuth

```
인터넷 사용자들이 비밀번호를 제공하지 않고

다른 웹사이트 상의 자신들의 정보에 대해 웹사이트나 애플리케이션의 접근 권한을 부여할 수 있는

공통적인 수단으로서 사용되는 접근 위임을 위한 개방형 표준
```

소셜로그인을 위한 프로토콜

어떤 정보를 보낼지도 다 체크를 하게 되어있다. Permission List

클라이언트가 유저가 만든 퍼미션 리스트를 받아서 서버에 넘겨주면

서버는 해당 소셜에 퍼미션 리스트를 보냄 (토큰 포함)

그러면 그 소셜은 퍼미션 리스트에 포함된 값만 응답

-   REST API를 활용한 카카오 로그인 구현하는 방법
    
    1.  프론트 엔드
        1.  카카오로 부터 인가 코드를 받는다
        2.  받은 인가코드를 백엔드에 넘겨준다.
    2.  백엔드
        1.  프론트로부터 받은 인가코드로 카카오로부터 토큰을 발급 받는다.
        2.  해당 토큰에 담긴 유저 정보를 활용해 회원가입을 진행한다. (데이터 유지를 위해, 유지가 필요없다면 패스)
        3.  해당 유저에 대한 프로젝트 전용 토큰을 새로 발급하여 프론트에 넘겨준다.
    
    [REST-API 활용한 카카오 소셜 로그인 구현(feat. React)](https://data-jj.tistory.com/53)
    
    [[Spring Boot] REST API를 이용한 카카오 로그인 구현](https://mangchhe.github.io/springboot/2021/07/18/SpringKakaoLogin/)
    
-   REST API를 활용한 구글 로그인 구현하는 방법
    
    1.  구글 OAuth API 프로젝트 환경 구성
    2.  REST API 구현
        1.  소셜 로그인 요청 처리
        2.  소셜 로그인 페이지에서 로그인 후 승인된 리디렉션 URI로 리다이렉트됨
            1.  API 서버로 부터 1회용 access code을 받음
            2.  access code로 access token, refresh token을 받음
        3.  access token으로 인가처리, 이 토큰으로 정보를 받아올 수 있다.
    
    [Spring Boot에서 구글 소셜 로그인 REST 방식으로 구현하기](https://mslilsunshine.tistory.com/171#--%25--%EA%25B-%AC%EA%25B-%25--%25--OAuth%25--API%25--%ED%25--%25--%EB%25A-%25-C%EC%25A-%25-D%ED%25-A%25B-%25--%ED%25--%25--%EA%25B-%BD%25--%EA%25B-%AC%EC%25--%25B-)

## 원리와 과정
-   OAuth 참여자
    
    -   Resource Server : Client가 제어하고자 하는 자원을 보유하고 잇는 서버 ex) Google, Naver, Kakao
    -   Resource Owner : 자원의 소유자, 유저, Client가 제공하는 서비스를 통해 로그인하는 실제 유저
    -   Client : Resource Server에 접속해서 정보를 가져오고자 하는 애플리케이션
    
-   OAuth Flow
    
    (Github의 예시)
    
    1.  Client 등록
        
        Resource Server에 클라이언트를 등록하여 사전 승인을 받는다. 등록 후 다음 정보를 받음
        
        -   Client ID : 노출 OK
        -   Client Secret : 노출 XX
        -   Authorized redirect URL : Authorization Code를 전달 받을 Redirect 주소
        
        리다이렉트된 주소에 Query String으로 Code가 전달됨
        
        Client는 해당 Code, Client ID, Client Secret을 Resource Server에게 보내서 Resource Server의 자원을 이용할 수 있는 Access Token을 발급받음
        
        등록되지 않은 리다이렉트 URL의 경우 Resource Server가 인증을 거부함
        
    2.  Resource Owner 승인
        
        1.  Resource Owner가 Client에서 소셜 로그인을 하고자 하면,
            
            Resource Server가 제공하는 URL에 필요한 파라미터 포함하여 요청을 보낸다.
            
            → Github의 경우 client_id, redirect_url, scope
            
            → scope : Client가 Resource Server로 부터 인가받을 권한의 범위
            
        2.  Resource Owner는 Resource Server에 접속하여 로그인 → Resource Server는 쿼리 스트링으로 넘어온 파라미터들로 Client 검사
            
            -   Client ID와 동일한 ID 값이 존재하는가
            -   Client ID에 해당 하는 Redirect URL이 파라미터로 전달된 Redirect URL과 같은가
            - 
        3.  Resource Server의 검증이 끝나면, Resource Owner에게 해당 scope에 해당하는 권한을 Client에 정말 부여할 것인지 승인을 요청함
            
    3.  Resource Server 승인
        
        1.  Resource Server는 명시된 Redirect URL로 Client를 리다이렉트 시킴
        2.  Client에게 Authorixation Code를 쿼리 스트링으로 부여
        3.  Authorixation Code를 Resource Server에 전달
        4.  Resource Server는 정보를 검사한 후, 유효한 요청이면 Access Token 발급
        5.  Client는 해당 토큰을 서버에 저장해두고, Resource Server의 자원을 이용하는 API 호출 시 해당 토큰을 헤더에 담아 요청
        
    4.  API 호출
        
        Access Token을 헤더에 담아 API를 호출하면, 해당 계정과 연동된 Resource Server의 풍부한 자원 및 기능들을 사용할 수 있음
        
    5.  Refresh Token
        
        Access Token은 만료 기간이 있음.
        
        Access Token을 발급받을 때 같이 발급되는 Refresh Token으로 새로운 Access Token을 발급 받게 됨
