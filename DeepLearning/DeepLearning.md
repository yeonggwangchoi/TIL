# 학습이란?

## 학습(Learning)
* Input(데이터)가 들어오게 되면 모델을 통해 예측을 하고 예측된 값을 정답과 비교하며 오차를 피드백하며 학습을 진행.
 * cheating(모델이 학습하던 데이터셋을 테스트하면 예측이 잘되는 현상)이 생기게 됨을 방지하기 위해서 데이터셋을 분할함.
* 모델을 통해 학습한 내용을 반복적으로 피드백하면 모델의 예측이 높아지게 됨.

## 지도학습(Supervised Learning), 비지도학습(Unsupervied Learning), 반지도학습(Semi-supervised Learning)
* 지도학습
    Dataset = Data + Label
* 비지도학습
    Dateset = Data
* 반지도학습
    지도학습 + 비지도학습

# 선형회귀(Linear regression)

## 선형회귀란?
* 데이터를 일반화하는 선을 찾는다.
* 그 선을 이용해 새로운 데이터를 예측한다.
* 직석의 방정식 y = Wx + b에서 W는 가중치를 의미하고, b는 편향을 의미한다.

## 회귀 직선
* H(x) = Wx + b
* error = H(x) - y (H(x)는 예측, y는 정답)

## 비용 함수(Cost function)
* error제곱(음수를 방지하기 위해)의 합
* 선형 회귀는 cost를 가장 작게하는 직선

