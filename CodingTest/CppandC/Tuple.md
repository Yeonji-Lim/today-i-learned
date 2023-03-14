## tuple

`#include <tuple>`

vector안에 튜플이 들어가고 특정 순서의 값으로 sorting 해야할 때

~~~
static bool CmpName(tuple<int, int, int> &x, tuple<int, int, int> &y){
    return get<2>(x) < get<2>(y); // 오름차순 정렬
}

int main() {
    ...
    sort(v.begin(), v.end(), CmpName);
    ...
}
~~~