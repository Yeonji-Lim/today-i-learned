## pytorch - squeeze

설정한 차원에 해당하는 것을 제거한다. 설정하지 않으면 1인 차원을 모두 제거

## pytorch - unsqueeze

지정한 차원에 1인 차원을 생성한다. 어느 차원에 생성할 지 꼭 지정

0으로 지정하면 그 텐서의 바깥에 하나 더 껍질 붙는 느낌


## 모델 불러오기 저장하기

torch.save(model.state_dict(), PATH) : 모델 저장하기

torch.load(PATH) : 모델 불러오기
