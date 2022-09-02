
Beam Search 는 최고우선탐색(Best-First Search) 기법의 개선된 형태 이다.

먼저 알아두어야 할 것은 RNN에서의 Beam Search를 다루기 때문에 트리 탐색의 관점으로 살펴볼 것이다.


## Best-First Search

휴리스틱에 따라 목표까지 가장 좋은 경로 상에 있따고 판단되는 노드를 우선 방문하도록 진행

예시로는 Dijkstra 알고리즘, A* 알고리즘이 있다.

!= Breadth-first Search


Heuristic : 어떤 경로의 끝이 solution에 얼마나 근접한 것인지 예측, solution에 더 가깝다고 판정되는 경로들을 먼저 확장한다. 선택은 일반적으로 우선순위 큐를 사용하여 구현함


## Beam Search

여기에서는 미리 가장 좋은 노드 후보를 몇 개 뽑는다. 이걸 Beam이라고 하고 개수를 Beam size라고 함

Top-Down 방식과 Bottom-Up 방식으로 나뉘는데 보통 NLP에서는 Bottom-Up 방식이 자주 쓰인다고 한다.
