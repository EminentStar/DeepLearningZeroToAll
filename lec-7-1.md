# Lecture 7-1
### Leaning rate, data preprocessing, overfitting


cost function을 정의하고 그 cost function을 최소화하는 값을 찾기 위해서 사용했던 Gradient Descent(경사를 타고 내려가는 알고리즘)을 쓰는데, 이때 이 알고리즘을 정할 때, learning_rate이라는 알파값을 정하었음.
<br>

그런데 learning_rate를 잘 정하는게 중요한데,, learning_rate를 굉장히 큰 값을 정한다면, 경사를 내려가는 스텝이 크다고 한다면 한발자국씩 내려가는 범위가 너무 커질 수가 있다. 이러면 학습이 이뤄지지 않을 수도 있다. cost가 줄어들지않고 큰값으로 갔다가 바깥으로 튕겨져 나갈 수도 있다. 이걸 `overshooting` 이라함

<br>
그런데 또 learning_rate를 굉장히 작게 잡는다면, 우리가 정한 step내에서 최소값을 못정할 수도 있다.  
이걸 피하기 위해서는 한번 cost함수를 출력해보면서 변하는 폭을 봐야한다.

* learning_rate 를 정하는 특별한 답은 없다.. 데이터나 환경에따라 조금씩 다르다.. 보통 처음에는 0.01 정도로 시작하는데, 이렇게 해보고 발산이 된다고 한다면 좀 더 작게 하고,,, 너무 늦게 움직이면 좀 크게 하는게 좋은 방법이 될 것이다.

<br>


우리가 가지고 있는 feature 데이터라고 하는 X 데이터를 선처리할 필요가 가끔씩 있다.

우리가 사용하는 Gradient Descent에서 Weight/loss 로 그래프가 있는데, 이게 weight이 여러개가 있을때(2개가 있다고 가정) 2차원상에 표시를 해보면 등고선처럼 되어서 최고로 낮은 지점에 도착하는게 목표일텐데,, w1, w2와 곱해지는 x1,x2 이 둘간의 값 차이가 많이 난다면, w1, w2 등고선 그래프가 심각하게 왜곡되게 그려질 것이다. 이러면 아무리 좋은 알파값을 가지고 있더라도 조금이라도 잘못 밖으로 나가버리게되면 밖으로 튀어나갈 수도 있다. 이부분을 주의해야하는데,  이걸 보통 `normalize`라고 부른다. 

보통 많이 쓰는게 zero-centered (데이터의 중심이 0으로 갈 수 있도록 바꿔주는 방법), 또 가장 많이 사용하는 것이 어떤 값이 전체의 범위가 어떤 형태안에 항상 들어가도록 하는 normalized

learning_rate도 잘 잡은거같은데 학습이 잘 되지않고 발산을 한다거나 이상한 동작을 보이면, 데이터 중에 차이가 큰게 나는게 있는지, data preprocessing을 했는지 확인을 해봐라.

normalization 하는 법은 매우간단하다.
데이터 값에 평균을 뺀 값을 분산으로 나누면 됨.

* python example
> X_std[:, 0] = (X[:, 0] - X[:, 0].mean()) / X[:, 0].std()

이런 형태의 normalization을 Standardization이라고 부른다.


`Overfitting`
가장 큰 문제다..

한마디로,, 학습을 통해 모델을 만드는데,, 학습데이터에 너무 잘 맞는 모델을 만들어 낼 수가 있는 것.. 
training data set은 잘 맞지만, test나 실제 데이터로 하면 안 맞는 것.

Overfitting을 줄이는 방법은 
- training data가 많으면 많을 수록
- feature의 개수를 중복된 게 있으면 줄인다던지 
- Regularization(일반화)을 통해

* Regularization은 우리가 가지는 Weight을 너무 큰 값을 가지지 말자. 이다.
Overfitting이라는 걸 설명할때, Decision boundary를 막 특정한 데이터에 맞게 구부리는 거라고 말하는데,, 

Regularization은 구부리지 말고 펴자! 이다. 
여기서 편다는 말은 weight이 좀 적은 값을 가진다는 표현이고
구부린 다는 건 weight이 큰값을 가질때 구부린다는 것

이걸 하기 위해서는 cost func에서 어떤 값를 더해주는 것이다.
가장 일반적인게 벡터 W; 각각의 엘리먼트에 제곱을 한 값을 합한 것을 cost func에 추가한 것의 최소값!

그 더하는 값에 상수를 줄 수 있는데 이걸 regularization strength라고 하는데 이 값이 0이 되면 regularization을 쓰지 않겠다,이고,, 1이되면 regularization을 굉장히 중요하게 생각한다.라고 볼 수 있다. 이값을 우리가 정할 수 있다.


이걸 Tensorflow같은 걸로 구현할때는 굉장히 간단하게 할 수 있는데 
l2reg 란 변수를 하나 만들어서
```
l2reg = 0.001 * tf.reduce_sum(tf.square(W))
```

이 l2reg를 cost와 더한 다음에 최소화를 시키면 된다.





