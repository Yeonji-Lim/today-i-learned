Transformer는 번역기라고 볼 수 있다.

말그대로 어떤 언어의 문장을 넣으면 다른 언어로 번역된 문장이 출력으로 생성된다.

문장과 같이 어떤 도메인의 데이터 시퀀스를 넣으면 다른 도메인의 데이터 시퀀스를 출력하는 것으로 볼 수 있다.


## Architecture

전체적으로 인코더 블록과 디코더 블록이 있다.


인코더 블록에는 인코더 레이어가 쌓여있고, 디코더 블록에는 같은 개수의 디코더 레이어가 쌓여있다.

인코더는 소스의 시퀀스 정보를 압축해서 디코더로 보내주고, 디코더는 이 정보를 받아서 타깃 시퀀스를 생성한다.


                다음 토큰

                    ^

인코더 블록 -> 디코더 블록

    ^               ^

소스 시퀀스        <s>


인코더의 입력은 소스 시퀀스 전체이고 디코더의 입력은 타깃 시퀀스의 시작을 뜻하는 스페셜 토큰 <s>이다.

디코더는 인코더에서 보내온 정보와 현재 디코더의 입력을 보고 다음 토큰을 맞춘다.


그런데 실제로 디코더의 출력물은 다음 토큰 그 자체가 아니라 타깃 언어의 어휘 수만큼의 차원으로 구성된 벡터이다.

값은 모두 해당하는 어휘가 정답일 확률로 구성되어 있고, 다음토큰으로 예상되는 어휘의 확률이 가장 높다.


그 다음 두번째에는 <s> 와 바로 전에 예상한 토큰을 포함해서 시퀀스 자체를 디코더의 입력으로 넣는다.


## Input


1. Embedding

transformer에 문장을 입력하기 전에 문장의 단어들을 먼저 vector형태로 변환한다.

Word2Vec 이라는 알고리즘을 사용하는데 이 과정을 word embedding이라고 한다.


2. Positional Encoding

transformer는 기존의 RNN을 사용하는 seq2seq 모델에서 RNN 대신 Attention만을 사용하는 모델이다.

기존에는 RNN을 통해 각 데이터의 위치정보를 자동으로 가질 수 있었던 반면, RNN을 사용하지 않으므로 위치정보를 따로 받아야한다.

그래서 임베딩된 벡터 값을 포지셔널 인코딩으로 조정하여 입력한다.

이렇게 순서 정보가 보존되어 같은 데이터로 구성되어도 위치에 따라서 다른 입력이 됨


이 포지셔널 인코딩 벡터를 구하기 위한 함수로 논문에서는 sin 함수 cos 함수의 합으로 표현하였다.

이 함수의 특성상 특정 위치에 대한 포지셔널 벡터는 다른 위치에 대한 포지셔널 벡터의 합으로 표현

-> 모델이 학습당시 보지 못한 길이의 긴 문장을 만나도 대응할 수 있게 됨


## Encoder

각 인코더 레이어는 두 개의 서브층으로 구성되어있다.

입력 -> Self-Attention -> Feed Forward Network -> 출력


1. Self-Attention (Encoder)

이 층은 각 단어의 vector들끼리 서로 간의 관계가 얼마나 중요한지 점수화한다.


과정은 다음과 같다.

먼저 세가지 Weight vector W와 벡터 곱하여 각 단어에 대한 Query(Q), Key(K), Value(V) 벡터를 만든다.

Q와 K와의 유사도를 구하고 이 유사도를 가중치로 각 K의 V에 반영해준다.


(원래 어텐션은 Q는 디코더 셀에서 가져온 단어로 계산하고, 나머지는 인코더 셀에서 가져온 단어로 계산하는데,

모두 같은 곳에서 가져오는 경우를 Self-Attention 이라고 함)


Q, K 유사도 가중치를 V에 반영하는 연산 과정은 다음과 같다.

Q는 문장의 다른 단어들의 K들과 곱한다 -> 각 단어가 서로에게 얼마나 중요한지 파악 (주의 : 자기자신의 K와도 내적함)

각 값들을 K의 크기의 제곱근으로 나누고 softmax를 적용한다 -> 계산 편의를 위함

각 값에 V를 곱한다 -> 각 K의 V에 유사도 반영

V들을 모두 더해서 리턴 -> Self-Attention Layer의 출력, Attention Value


2. Position-wise FFNN

어텐션 레이어를 지나면 Fully-connected Feed-forward Network를 지난다.

하나의 인코더 블록 내에서는 다른 문장이나 단어들 마다 동일하게 사용되지만 인코더 마다 다른 값을 가지게 된다.


## Decoder

각 디코더 레이어는 세 개의 서브 층으로 구성되어 있다.

-> Self-Attention -> Encoder-Decoder Attention -> Feed Forward Network ->


1. Self-Attention (Decoder)

인코더와 유사하지만, 전체 위치에 대해서 attention하지 않고, 현재 위치의 이전 위치까지에 대해서만 진행한다.


seq2seq 모델의 경우, RNN으로 위치정보를 전달해오기 때문에 미래 시점의 단어를 참고하지는 않는다.

그런데 Transformer의 경우, 위치정보를 참고하기 위해 전체의 포지셔널 인코딩 벡터를 도입했기 때문에 미래 시점까지 참고하는데,

이런 부분을 개선하기 위한 것이다.


결과인 스코어 행렬에 Look-Ahead Mask를 이용해서 현재 시점 이후의 위치는 음의 무한대 값으로 마스킹한다.

기존에 어텐션에는 패딩 마스크를 전달하는데 이때에도 필요하므로 룩-어헤드 마스크가 패딩 마스크를 포함하도록 구현한다.


2. Encoder-Decoder Attention

계산된 3개의 벡터중 Q만 가져오고, K, V는 인코더 블록의 출력을 가져온다.

그 외의 수행 과정은 다른 어텐션과 같다.


## Train

영어를 프랑스어로 번역하는 경우를 생각해보자

어떤 영어 단어가 있으면 그에 해당하는 프랑스어 단어가 있을 것이다.

학습을 하면서 해당하는 프랑스어 단어가 뭔지 찾아간다.


전혀 학습되지 않은 상태에서는 그 단어에 대한 프랑스어 각각의 확률값이 모두 비슷하고,

학습이 충분히 된 상태라면 해당하는 프랑스어 단어의 확률이 가장 높게된다.


문장으로 넘어가자

해당하는 포지션에 나올 확률이 가장 높은 단어를 선택하는 방식으로 진행한다면

그게 가장 올바른 예측 방법은 아니다.

특정 time step에서는 낮은 확률이 있더라도 전체 구간에 대한 확률이 더 높을 수 있다.


그래서 여기서 Bean Search라는 방법을 도입한다.

각 위치별로 <beam size>개의 확률이 높은 단어 후보들에 대해

<top beams>번째 time step까지의 경우를 모두 계산하면서 정답을 찾아간다.

이 두가지 변수는 hyperparameter로, 임의로 설정 가능
