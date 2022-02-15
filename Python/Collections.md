## Python Collections Counter

python에서 Collections 모듈의 Counter 클래스는 데이터의 개수를 셀 때 유용하다.

어떤 데이터들이 있을 때, 그 데이터들에서 각 데이터의 개수를 딕셔너리 형태로 반환 해준다.

~~~
>>> cnt = Counter()
>>> for word in ['red', 'blue', 'red', 'green', 'blue', 'blue']:
...     cnt[word] += 1
>>> cnt
Counter({'blue': 3, 'red': 2, 'green': 1})
~~~