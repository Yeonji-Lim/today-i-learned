# Cpp로 순열 구현하기

```cpp
void swap(char & a, char & b) {
	char temp = a;
	a = b;
	b = temp;
}

void permutation(char data[], int depth, int n, int r) { //최초 depth == 0
	
	if (depth == r) {
		// do sth
		return;
	}
	
	for(int i = depth; i < n; i++) {
		swap(data[depth], data[i]);
		permutation(data, depth+1, n, r);
		swap(data[depth], data[i]);
	}
}
```