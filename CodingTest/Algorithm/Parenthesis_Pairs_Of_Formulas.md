# 수식의 괄호쌍
주어진 괄호 문자열이 올바른지 판단하는 문제

## 한 종류의 괄호만으로 구성
- 안쪽부터 짝맞추기를 해서 지워나가는 방법, 다 짝이 맞으면 올바른 괄호 쌍
- ) 의 갯수가 ( 의 갯수를 넘지 않으면 된다

## 여러 종류의 괄호로 구성
- 개수를 세서 비교하는 것은 안된다. ( { ) } -> 올바르지 x
- 붙어있는 ( ) 혹은 { } 를 지우는 방법은 여전히 잘 동작
   배열로 구현할 경우 최대 N번 중간에 있는 원소의 삭제가 발생하기 때문에 O(N2)
   연결 리스트로 구현할 경우 O(N)
   스택으로 간단하게 구현 가능

### 스택으로 구현
문자열을 앞에서부터 읽어나갈 때, '닫는 괄호'는 남아있는 괄호 중에서 가장 최근에 들어온 여는 괄호와 짝을 지어 없애버리는 명령이라고 생각
문자열을 모두 읽고 스택이 비어있으면 올바른 수식
