bool 반환하는 함수로 sort 커스텀 가능

```cpp
bool compare(int a, int b) {
	return a > b; //내림차순
}
```

점점 작아지는 느낌 `>` 내림차순

정렬하려는 것이 2차원 배열이어도 그 안에 것까지 고려해서 오름차순으로 정렬함! 원소 내부는 정렬 x 

`[[a, a], [a, b], [b, a]]`
