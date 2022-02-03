## np.zeros

0으로 채워진 array를 생성한다.

~~~
np.zeros(shape, dtype, order)
~~~

## np.concatenate

어떤 축으로 두 배열을 조인한다.

~~~
a = np.array([[1, 2], [3, 4]])
b = np.array([[5, 6]])

np.concatenate((a, b), axis=0)

array([[1, 2],
       [3, 4],
       [5, 6]])

np.concatenate((a, b.T), axis=1)

array([[1, 2, 5],
       [3, 4, 6]])

np.concatenate((a, b), axis=None)

array([1, 2, 3, 4, 5, 6])

~~~

## np.insert

주어진 축, 주진 인덱스 앞에 값을 삽입

~~~
import numpy as np

a = np.array([1, 2, 3])
b = np.insert(a, 1, 5)

print(a)
print(b)
~~~
~~~
[1 2 3]
[1 5 2 3]
~~~

축(axis)을 지정하지 않으면 우선 1차원 배열로 변환(flatten)하고 삽입

~~~
import numpy as np

a = np.array([[1, 1], [2, 2], [3, 3]])
b = np.insert(a, 1, 5)


print(a)
print(b)
~~~
~~~
[[1 1]
 [2 2]
 [3 3]]
[1 5 1 2 2 3 3]
~~~
~~~
import numpy as np

a = np.array([[1, 1], [2, 2], [3, 3]])
b = np.insert(a, 1, 5, axis=0)
c = np.insert(a, 1, 5, axis=1)

print(a)
print(b)
print(c)
~~~
~~~
[[1 1]
 [2 2]
 [3 3]]
[[1 1]
 [5 5]
 [2 2]
 [3 3]]
[[1 5 1]
 [2 5 2]
 [3 5 3]]
~~~
~~~

## np.expand_dims

차원을 확장해줌

## numpy random choice
~~~
np.random.choice(a, size=None, replace=True, p=None)
~~~

a는 array

a에서 랜덤으로 샘플링하는 함수

a빼고 나머지는 optional

size는 output size 기본값은 1

replace는 여러번 선택될 수 있는지 여부 기본값은 True

p는 적용할 확률분포, array
