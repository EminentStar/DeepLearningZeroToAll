# Lecture 8-1
### Deep Neural Nets and XOR problem



* XOR problem
  - 매우 단순한 로직이지만 옛날에 만든 기계를 가지고는 어떻게 선을 그어도 100% 예측을 할 수가 없었음.

* Perceptrons by Marvin Minsky (1969)
  - MLP(Multilayer Perceptrons)를 여러개 합치면 XOR을 풀 수 있다.!
  - 근데 각각의 MLP에 들어가는 Weight과 bias를 학습을 시킬 수가 없다..
  - 이걸 발표하면서부터 뉴럿넷쪽 발전은 10~20년 정도 후퇴를 하게 됨.

* Backpropagation (1974, 1982 by Paul Werbos, 1986 by `Hinton`)
  - 뉴럴넷이 연결되있고 각각이 w,b가 있으면 입력을가지고 쭉 출력을 만들어 낼 수 있는데, 출력이 실제 가지고 있는 값과 틀릴 경우 w,b를 조절해야했는데 이것이 어려웠다.
  - 그래서 backpropagation이란 알고리즘이 개발됬는데, 
  - 출력을 구하는 쪽에서 error를 구해서 이걸 뒤로 전달을 해나가면서 각각을 chain 시키면 어떨까? 하는 알고리즘임.


* Convolutional Neural Networks
  - 데이터의 형태에따라 활성화되는 뉴런이 달라지는 것.
  - 부분부분을 잘라서 보낸다음에 나중에 합치는 방법으로 뉴럴넷 구성
  - 알파고도 이 뉴럴넷을 사용함.

* 근데 Backpropagation 알고리즘이 몇개정도의 layer에서는 잘 동작하지만 실제로 복잡한 문제를 풀려면 최소 10여개 이상의 Layer를 학습시킬 수 있어야하는데, backpropagation으로 앞에서 뒤로 보내야하는 구죠였는데 앞의 error를 뒤로보내야할때 가면 갈수록 약해져서 마지막에 가면 error가 거의 전달되지 않고 학습을 못하게 된다.
  - 한마디로 layer가 많을 수록 성능이 떨어진다.

* 한편, 다른 형태로의 알고리즘들이 많이 나오기 시작함.(어떻게 보면 뉴럴넷보다 간단한 알고리즘들이 잘 동작함. e.g. SVM, RandomForest etc.)

### 이러면서 뉴럴넷의 두번째 침체기가 오게 된다.
