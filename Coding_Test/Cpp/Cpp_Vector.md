## 2차원 벡터 초기화 하기

~~~
vector<vector<int>> v (10, vector<int> (10, 1));
~~~

## copy

vector를 copy할 때는 두 개의 크기를 먼저 맞춰주고 진행해야 한다. 

## C++ 벡터 중복 제거

~~~
sort(v.begin(), v.end());
v.erase(unique(v.begin(), v.end()), v.end());
~~~

정렬을 하고 나서 진행해주어야 한다. 