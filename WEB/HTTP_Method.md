# [HTTP](ComputerScience/ComputerNetwork/HTTP.md) Method

REST를 지키면서 행위를 전달하는 방법

Idempotence, 멱등성 : 여러번 수행해도 결과가 같음, 호출로 인하여 데이터가 변형되지 않음

-   GET : 서버로 부터 데이터 취득 데이터를 읽거나 검색할 때 사용
    
    -   성공 : 200 (OK) / 실패 : 404(Not Found), 400 (Bad Request)
    -   HTTP 명세에서는 GET은 오로지 데이터를 읽을 때만 사용하고 수정 시는 사용하지 않음 → 데이터를 변경하는 연산에 사용하면 안된다.
    -   캐싱을 하기 때문에 여러번 요청시 POST보다 조금 더 빠를 수 있다.
    -   idempotent 하다 : 같은 요청을 여러번해도 항상 같은 응답
    
    ```
    GET /user/1
    ```
    
-   POST : 서버에 데이터를 추가, 작성 주로 새로운 리소스 생성에 사용, 하위 리소스들을 생성하는데에 사용
    
    -   성공 : 201 (Created)
    -   idempotent 하지 않다. : 항상 같은 결과물이 나오는 것을 보장하지 않는다. 두 개의 같은 POST 요청 → 같은 정보를 담은 두개의 다른 resource를 반환할 가능성이 높다.
    -   요청시마다 데이터를 생성한다는 것이 PUT과 다르다.
    
    ```
    POST /user
    body : {date : "example"}
    Content-Type : "application/json"
    ```
    
    url을 통해 데이터를 받지 않고, body 값을 통해서 받는다.
    
    데이터 조회에 성공하면 body 값에 저장한 데이터 값을 저장하여 성공응답을 보냄
    
-   PATCH : 리소스의 일부분 수정
    
    -   indempotent하지 않다. : PUT과 다르게 정보를 일부만 수정하기 때문
-   PUT : 서버의 데이터 갱신, 작성 리소스를 생성/업데이트 하기 위해 서버로 데이터를 보내는 데 사용
    
    -   indempotent 하다. : 동알한 요청을 여러번해도 항상 같은 응답
    -   같은 요청을 계속 하더라도 데이터가 새로 생성되지는 않는다. (POST와 비교)
    
    ```
    PUT /user/1
    body : {date : "update example"}
    Content-Type : "application/json"
    ```
    
    데이터를 수정하는 것이기 때문에 요청시에 Body값과 Content-Type 값을 작성해야 함
    
    URL을 통해 어떤 데이터를 수정할지 파라미터를 받음
    
    수정할 데이터를 body 값을 통해서 받음
    
    데이터 조회에 성공하면 Body값에 저장한 데이터 값을 저장하여 성공 응답을 보냄
    
-   DELETE : 서버의 데이터 삭제 지정된 리소스 삭제
    
    ```
    DELETE /user/1
    ```
    
    데이터 삭제 요청이기 때문에, body, Content-Type 비워짐
    
    URL을 통해 어떤 데이터 삭제인지 파라미터를 받음
    
    데이터 삭제에 성공하면 Body 값 없이 성공 응답만 보냄