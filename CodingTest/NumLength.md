파이썬에서 숫자 길이 체크

```python
def get_length(value):

    length = 0

    while value > 0:

        value //= 10

        length += 1

    return length
```

자주 쓰이는 거라 쉽게 짤 수 있도록 연습하자