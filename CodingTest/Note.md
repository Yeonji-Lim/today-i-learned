# 코테 노트

- 미리 시간제한과 n,k 등을 보고 O(n^2) 이 되면 안되겠네 등을 파악하고 들어가자

- 다 풀고 나면 예외 처리 한 것 위주로 다시 보자 
	- 7569: 다익은 경우를 dist-1이 0인 경우로 했는데 이 경우 익은 토마토가 하나 있고 빈공간으로 그 토마토가 둘러쌓인 경우에는 모두가 익은 것이 아니다.

- 공간이 2차원이 아니라 3차원으로 갈 경우에 STL pair 대신 vector를 사용하면 그대로 {}형식으로 push 할 수 있음

## 실수 방지

- 반복문에서 초기화는 `continue` 전에도 해줘야 한다.
  
- 소수관련 문제는 꼭 `1 ~ 전체 범위`의 소수를 모두 만들지 않아도 될 수도!
  -> 그냥 그 수 `n`을 2 부터 `sprt(n)`까지 나눠봐서 소수인지 판단하는 걸 수도 있다.

- `int` 연산 값이 `long long`이 될 경우 각 변수를 `long long`으로 미리 변환하고 연산해야 한다.
  
  ```cpp
  long long lnum = (long long)(inum1) * (long long)(inum2);
  ```

## 상한 값

![](https://i.imgur.com/KfKDBR5.png)
https://gall.dcinside.com/mgallery/board/view/?id=ps&no=16797