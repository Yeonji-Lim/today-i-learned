vector를 함수인자로 그냥 넘기면 값을 복사해서 넘긴다..!

[[Cpp_Reference]] 를 사용해서 넘겨야 함

다음과 같은 코드는 vector의 크기가 N이라고 할 때, 시간 복잡도가 O(N)임

```c++
bool cmp1(vector<int> v1, vector<int> v2, int idx) {
	return v1[idx] > v2[idx];
}
```

왜?

vector를 하나하나 복사해서 넘기기 때문...!
그래서 연산을 한번하는데도 O(N)이 걸린다.

reference로 넘기면 복사본을 따로 만들지 않고 참조 대상의 주소 정보만 넘어가기 때문에 시간 복잡도는 의도대로 O(1)이 됨