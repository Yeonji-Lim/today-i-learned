# OAuth

소셜 로그인

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