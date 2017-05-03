# Lecture 7-2
### Leaning and test data sets
* 모델이 얼마나 잘 동작하는지 확인 하는 방법에 대해 공부


전체 데이터에서 7:3정도로 짤라서 7을 training, 3을 test set으로 부른다.

test set은 절대 사용해선 안된다.

training set만 가지고 모델을 학습한다.
그리고 다 끝났을때 단 한번 test data set을 줘서(test의 답을 알고 있지) 예측값과 실제값 Y들을 비교하면 된다.

training을 교과서, test set을 실전문제 라고 비유할 수 있다

<br>
알파라는 learning rate와 또하나의 상수가 람다;어떤 regularization을 얼마나 강하게 할 것인가에 대한 값들로 튜닝할 필요가 있을때, 보통 training set에서 또 두개로 나눈다.

training과 validation으로 나눈다.
* training set: 모델 학습
* validation set: 알파, 람다값으로 어떤게 좋을까를 튜닝하게 된다. 




또 데이터셋이 굉장히 많을 경우 학습을 다 시키기 힘들때가 있다. (뭐 메모리 올리기도 힘들고)
Online learning이란 학습방법도 있다.





또 test set을 가지고 있으면 Accuracy를 측정하는 것은 간단한 일이다.
실제 Y값과 모델이 예측한 값을 비교해서 100개 중에 10개 맞으면 10%, 90개 맞으면 90%.

보통 이미지 인식하는 곳에 정확도는 95~99%정도로 잘된다.
