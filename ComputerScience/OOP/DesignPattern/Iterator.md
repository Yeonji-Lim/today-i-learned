# 반복자 패턴

객체 집합의 요소를 순차적으로 접근하는 데에 Iterator라는 객체를 사용

리스트 객체와 방문하는 프로세스 사이의 결합을 줄인다.

원래는 데이터 형태가 어떤 형태인지 클라이언트가 알아야 하고, 데이터의 형태가 바뀌면 클라이언트도 다르게 접근해야 한다.

그래서 데이터와 클라이언트 중간에 이터레이터를 두어서 핸들링을 클라이언트가 하지 않겠다는 것.

<img width="488" alt="image" src="https://user-images.githubusercontent.com/57888020/169953944-995d5120-1cde-42a1-bde6-80cde69bed45.png">