
이 두 알고리즘은 그래프 탐색 알고리즘으로, 구현에 스택, 큐, 재귀함수가 쓰이므로 그래프와 이들에 대한 사전지식이 필요하다.


# DFS

Depth-First Search 깊이 우선 탐색

그래프를 탐색할 때, 계속해서 깊게 들어가서 탐색한 후, 다른 경로로 탐색하는 알고리즘이다.

계속해서 자식노드를 방문하며, BFS는 가까운 노드를 우선으로 탐색한다면, DFS는 멀리 있는 노드를 우선하여 탐색하는 방식.


스택 자료구조를 이용하여 구현하며, 방문했는지 안했는지를 저장해야 한다.


다음과 같이 동작한다.

1. 시작노드를 스택에 push, 방문처리

2. 스택 top 노드의 인접 노드 중에서

- 방문하지 않은 노드가 있다면 스택에 push, 방문처리

- 방문하지 않은 노드가 없다면 스택 pop

3. 스택이 빌 때까지 반복


시간 복잡도 : O(N)

재귀 함수를 이용하면 매우 간결하게 구현할 수 있다.


# BFS

Breadth First Search 너비 우선 탐색

가까운 노드부터 탐색한다. 형제 노드를 먼저 탐색하고 나서 자식노드를 탐색한다.


큐 자료구조를 사용하는 것이 정석이고 DFS와 같이 방문 처리를 필요로 한다.


다음과 같이 동작한다.

1. 시작노드를 큐에 push, 방문처리

2. 큐의 맨 앞 노드의 인접 노드 중에서 방문하지 않은 노드를 모두 큐에 push, 방문처리

3. 큐가 빌 때까지 반복


시간 복잡도 : O(N)

재귀함수로 DFS를 구현하면 컴퓨터 시스템의 동작 특성상 실제 프로그램의 수행 시간은 느려질 수 있다.

따라서, 보통 DFS보다는 BFS가 좀 더 빠르게 동작한다.


꼭 그래프의 문제가 아니라 1차원이나 2차원 배열이 주어졌을 때

이를 그래프의 형태로 생각하여 문제를 수월하게 풀 수도 있다.