
## Torch 설치하기 

아래 사이트에서 원하는 지금 환경에 맞는 pytorch를 설치할 수 있다. 

https://pytorch.org/

## torch.tensor -> 단일 종류의 변수로 이루어진 다차원 행렬

## torch.unsqeeze -> 지정된 위치에 1차원 크기가 삽입된 새 텐서

## torch.long -> long으로 자료형 변경

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

## torch.Tensor.repeat(*sizes) -> Tensor

해당 텐서의 특정 차원을 반복한다. 

expand와 다르게 텐서의 데이터를 복사한다.

✻ 또한 numpy.repeat보다는 numpy.tile과 비슷하다

sizes : torch.Size나 int 형태, 각 차원 마다 반복할 횟수를 정한다.

       >>> x = torch.tensor([1, 2, 3])
       >>> x.repeat(4, 2)
       tensor([[ 1,  2,  3,  1,  2,  3],
              [ 1,  2,  3,  1,  2,  3],
              [ 1,  2,  3,  1,  2,  3],
              [ 1,  2,  3,  1,  2,  3]])
       >>> x.repeat(4, 2, 1).size()
       torch.Size([4, 2, 3])
​

## Tesor Views

기존 텐서(base tensor)의 view 텐서로 바꿀 수 있다. 

기존 텐서와 동일한 기본 데이터를 공유함 -> 뷰 텐서에서 값을 수정하면 기존 텐서의 값에 반영됨!

명시적인 데이터 복사를 방지함 -> 메모리의 효율적인 재구성,Slicing, Element-wise operation

같은 데이터를 다른 차원으로 변형해서 볼 수 있다. 

​
## torch.full

torch.full(size, fill_value, *, out=None, dtype=None, layout=torch.strided, device=None, requires_grad=False) -> Tensor

크기가 size만하고 값을 fill_value로 채운 텐서를 만들어냄

out : 결과 텐서 

dtype : 데이터 타입

## torch.Tensor.expand_as

Tensor.expand_as(other)

expand(other.size())와 동일한 의미, 해당하는 텐서를 other와 동일한 크기로 확장시켜줌


## torch.Tensor.topk

Tensor.topk(k, dim=None, largest=True, sorted=True)

해당 텐서 특정 차원의 값중 가장 큰 k개의 값을 반환한다. 

dim 기본 값은 해당 텐서의 가장 큰 차원

largest가 false이면 가장 작은 k개의 값
