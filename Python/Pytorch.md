

torch.tensor -> 단일 종류의 변수로 이루어진 다차원 행렬

torch.unsqeeze -> 지정된 위치에 1차원 크기가 삽입된 새 텐서

torch.long -> long으로 자료형 변경

## tensor.mean()

평균을 구한다. 차원을 나누지 않고 그냥 사용하는 경우 모든 원소의 평균이 나온다

차원을 지정하는 경우, 입력에서 해당 차원을 제거한다.


~~~
t = torch.FloatTensor([[1, 2], [3, 4]])

print(t.maen(dim=0)) # 입력에서 첫번째 차원을 제거한다.
~~~

~~~
tensor([2., 3.])
~~~
1, 3의 평균 2, 2, 4의 평균 3이 저장된다.

~~~
t = torch.FloatTensor([[1, 2], [3, 4]])

print(t.maen(dim=1)) # 입력에서 두번째 차원을 제거한다.
~~~
~~~
tensor([1.5000., 3.5000])
~~~

## torch.cat

concatenate하고자 하는 차원을 증가시킨다.

차원의 수는 그대로, 차원을 지정하면 그 차원으로 두 tensor의 차원을 더한 값으로 차원이 변경됨

~~~
import torch

batch_size, N, K = 3, 10, 256

x = torch.rand(batch_size, N, K) # [M, N, K]
y = torch.rand(batch_size, N, K) # [M, N, K]

output1 = torch.cat([x,y], dim=1) #[M, N+N, K]
output2 = torch.cat([x,y], dim=2) #[M, N, K+K]
~~~

## torch.no_grad()

모델을 학습한 뒤 평가할 때 사용하는 함수. model.eval()과 비슷하다.

model.eval과는 다르게 dropout을 비활성화 시키진 않음

## torch.arange()

어떤 범위 내의 일정 차이를 가지는 원소들을 가지는 1차원 텐서를 반환한다.

~~~
>>> torch.arange(5)
tensor([ 0,  1,  2,  3,  4])
>>> torch.arange(1, 4)
tensor([ 1,  2,  3])
>>> torch.arange(1, 2.5, 0.5)
tensor([ 1.0000,  1.5000,  2.0000])
~~~

## torch.permute()

tensor의 모양을 바꾼다.

~~~
import torch

a = [[1,2,3,4],
     [1,2,3,4],
     [1,2,3,4]]

a = torch.Tensor(a) # [3, 4]

b = a.view(4, 3) # [4, 3]
print(b)
c = a.permute(1, 0) # [4, 3]
print(c)
~~~
~~~
tensor([[1., 2., 3.],
       [4., 1., 2.],
       [3., 4., 1.],
       [2., 3., 4.]])
tensor([[1., 1., 1.],
       [2., 2., 2.],
       [3., 3., 3.],
       [4., 4., 4.]])
~~~


## torch.Tensor.normal_

~~~
Tensor.normal_(mean=0, std=1, *, generator=None)
~~~

주어진 mean과 std로 매개변수화된 정규 분포의 원소 표본을 사용해서 텐서를 채움
