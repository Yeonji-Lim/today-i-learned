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

np.insert

np.expand_dims
