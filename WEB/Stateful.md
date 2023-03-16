# Stateful

**[세션](Session)이 종료될 때까지 클라이언트의 세션 정보를 저장하는 네트워크 [프로토콜](Protocol)**

ex : [TCP](TCP) 프로토콜, 온라인 뱅킹

-   장점 : 통신이 중단되더라도 중단된 곳에서 다시 시작 가능
    
-   단점 : 확장성이 좋지 않음
    
    → 세션 정보가 새로 scale out 된 서버에 저장 되어 있지 않음
    
    → scale out 시 클라이언트의 세션 정보를 새로운 서버로 옮겨주는 등의 부수적인 관리가 요구됨