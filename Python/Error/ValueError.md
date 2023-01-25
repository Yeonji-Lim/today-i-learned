# ValueError: too many values to unpack

unpack 시 변수의 개수가 맞지 않아 발생함

- list의 값들을 unpack 하려고 할 때, 원소의 개수가 일치하지 않는 경우

	```
	appliances = ['Fridge', 'Microwave', 'Toaster']
	appliance_1, appliance_2 = appliances
	```

- 메서드 반환값의 개수와 해당 메서드를 호출하여 그 값을 저장하려는 변수의 수가 일치하지 않는 경우

	```
	def compute(x, y):
		sum = x + y
		product = x * y
		quotient = x / y
		return sum, product, quotient
	
	result_1, result_2 = compute(12, 5)
	```

- 변수 개수 불일치

참고 : https://www.learndatasci.com/solutions/python-valueerror-too-many-values-unpack/