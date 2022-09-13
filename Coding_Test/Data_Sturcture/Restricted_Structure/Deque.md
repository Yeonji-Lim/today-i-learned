# Deque
## 구현
### STL
double ended queue의 느낌보다는 
**vector와 비슷한데, front에서도 O(1)의 추가&제거가 가능하다!**
vector와 다르게 데이터가 연속으로 배치되어 있지 않다.

앞과 뒤에 추가 제거가 빈번한 경우에 사용하자

### Array
스택, 큐와 다르게 양쪽 모두에서 삽입삭제가 이루어질 수 있으므로, 
초기 head, tail을 가운데 인덱스에 둔다.
-> 배열의 크기는 `2*MX+1`이고 head와 tail의 초기값은 `MX`로 설정

[큐](Queue)와 마찬가지로 원형으로 구현할 수 있지만, 배열의 크기를 크게 만들면 됨
