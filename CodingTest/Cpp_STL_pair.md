# STL pair
header : utility

make_pair로 값을 넣어줄 수 있지만,
C++11 이상에서는 그냥 중괄호로 쉽게 넣어줄 수 있다.
```cpp
pair<int, int> p1 = make_pair(10, 20);
pair<int, int> p2 = {2, 3};
```

각 값은 first, second로 접근가능
`#define`으로 더 직관적으로 보이게 바꿀 수 있다. 
```cpp
#define X first
#define Y second
```

미리 대소관계가 설정되어 있어서 알아서 앞쪽 값을 먼저 비교하고 뒤쪽 값을 비교함

