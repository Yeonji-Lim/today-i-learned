# 기울기 소실 현상
딥러닝의 역전파 과정에서 출력층에서 멀어질 수록 gradient 값이 매우 작아지는 현상

활성화 함수의 기울기와 연관이 깊음

Sigmoid의 경우 가장 큰 기울기가 0.25인데, 점점 곱해질수록 작아짐

이에 대한 해결책으로 제안된 것이 ReLU