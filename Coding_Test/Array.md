배열은 데이터를 자주 바꾸지 않고 그냥 쌓아두고 싶을 때 활용
데이터 쌓는 용 말고 빠르게 접근하는 목적의 배열 사용 : BOJ 10808

배열 성질
1. k 번째 원소를 찾을 때 O(1)
2. 추가적으로 소모되는 메모리의 양이 거의 없다.
3. 메모리 상에 데이터들이 붙어있으니까 [Cache hit rate](Cache_hit_rate)가 높음
4. 메모리 상에 연속한 구간을 잡아야해서 할당에 제약이 걸림

추가와 삭제에서 데이터를 밀어줘야 해서 O(N)이 걸린다.
vector에서도 마찬가지임

```c++
vector<int> v = {1,2,3,4,5,6};

// 이렇게 하면 안된다.
for(int i = 0; i <= v.size()-1; i++) {
	cout << v[i] << ' ';
}
```
v.size()는 unsigned int 혹은 unsigned long long을 반환
 unsigned int를 int와 연산하면 자동 형변환 발생 0-1은 -1이 아니라 4294967295 -> unsigned int overflow
런타임 에러가 발생할 수 있기 때문에 이렇게 쓰지 않기


