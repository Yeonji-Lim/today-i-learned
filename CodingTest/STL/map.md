```cpp
#include <map>
```

자동으로 `key` 에 대해 오름차순 정렬

내부적으로 `tree` 형태를 가지고 있다. -> find : `O(log(n))`
`unordered_map`은 `hash table` 형태 -> find : `O(1)`

중복 `key` 를 사용하기 위해서는 `multimap`을 사용해야 한다.