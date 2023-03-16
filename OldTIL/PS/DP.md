## Dynamic Programming


어떤 유형의 문제를 푸는가?

1. 큰 문제를 작은 문제로 나눌 수 있음

2. 작은 문제의 답을 큰 문제에서도 동일 -> 작은 문제를 다시 계산해도 같은 값 -> 동일한 함수가 반복 호출됨


분할정복과의 차이 : DP에서는 문제들이 서로 영향을 미치고 있음


탑다운 방식 - 메모이제이션Memoization(캐싱Cashing) 기법, 재귀함수 사용, 큰 문제 -> 작은 문제

보텀업 방식 - 반복문, 작은 문제 -> 큰 문제

보통 보텀업 방식으로 푸는 것이 좋다.


수열 처럼 연속적이지 않고 모든 작은 문제가 아니라 작은 문제의 일부만 접근한다고 했을 때 사전 자료형을 이용하기도 한다.