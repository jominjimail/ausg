# Tensorflow 기본 용어 정리

LeNet5 코드보다 너무 암담해서 기본부터.. 차근차근정리해보기로.. 

## 용어

### 오퍼레이션(operation)

- 그래프 상의 노드는 오퍼레이션으로 불린다.
- 오퍼레이션은 하나 이상의 텐서를 받을 수 있다.
- 오퍼레이션은 계산을 수행하고, 결과를 하나 이상의 텐서로 반환할 수 있다.

### 텐서(Tensor)

- 내부적으로 모든 데이터는 텐서를 통해 표현된다.
- 텐서는 일종의 다차원 배열이다.
- 그래프 내의 오퍼레이션 간에는 텐서만이 전달된다.

### 세션(Session)

- 그래프를 실행하기 위해서는 세션 객체가 필요하다.
- 세션은 오퍼레이션의 실행 환경을 캡슐화한 것이다.

### 변수(Variables)

- 변수는 그래프 실행시, 파라미터를 저장하고 갱신하는데 사용된다.
- 메모리 상에서 텐서를 저장하는 버퍼역할을 한다.

```python
import tensorflow as tf
# 변수를 0으로 초기화
state = tf.Variable(0, name="counter")
# state에 1을 더할 오퍼레이션 생성
one = tf.constant(1)
new_value = tf.add(state, one)
update = tf.assign(state, new_value)
# 그래프는 처음에 변수를 초기화해야 합니다. 아래 함수를 통해 init 오퍼레이션을 만듭니다.   
init_op = tf.initialize_all_variables()
    
# 그래프를 띄우고 오퍼레이션들을 실행
with tf.Session() as sess:
	# 초기화 오퍼레이션 실행
	sess.run(init_op)
	# state의 초기 값을 출력
	print(sess.run(state))
	# state를 갱신하는 오퍼레이션을 실행하고, state를 출력
	for _ in range(3):
		sess.run(update)
    	print(sess.run(state))
'''
0
1
2
3
'''
```



## 문제풀이

경사 하강법으로 인자 찾아내기

- w, b를 경사하강법을 통해서 찾아내보자.

```python
import tensorflow as tf
import numpy as np
# Numpy 랜덤으로 2<-100 개의 가짜 데이터 채우기.
x_data = np.float32(np.random.rand(2, 100))
# 학습 레이블(목표값)은 아래의 식으로 산출. (W = [0.1, 0.2], b = 0.3)
# dot(), vector와 matrix의 product 구하기. 1x2 dot 2x100
y_data = np.dot([0.100, 0.200], x_data) + 0.300

# b는 0,
b = tf.Variable(tf.zeros([1]))
# W 원하는 shape[1,2] 대로 만들어줌
#( [minval,maxval) 사이의 균등확률분포 값을 생성해주는 함수)
W = tf.Variable(tf.random_uniform([1, 2], -1.0, 1.0))
y = tf.matmul(W, x_data) + b

# 손실 함수 정의 tf.square->제곱을 계산 
loss = tf.reduce_mean(tf.square(y - y_data))
# 경사하강법으로 손실 함수를 최소화 (0.5는 학습 비율)
optimizer = tf.train.GradientDescentOptimizer(0.5)
# 학습 오퍼레이션 정의
train = optimizer.minimize(loss)
# 모든 변수를 초기화.
init = tf.initialize_all_variables()
# 세션 시작
sess = tf.Session()
sess.run(init)
# 200번 학습.
for step in xrange(0, 201):
    sess.run(train)
    if step % 20 == 0:
        print step, sess.run(W), sess.run(b)
'''
0 [[0.16538364 0.5533881 ]] [0.17327008]
20 [[0.13463596 0.2870798 ]] [0.23895775]
40 [[0.11550944 0.22516522]] [0.27947173]
60 [[0.10587969 0.20771122]] [0.29311782]
80 [[0.10208811 0.20245282]] [0.2976965]
100 [[0.10071956 0.20079757]] [0.29922968]
120 [[0.10024429 0.20026258]] [0.29974252]
140 [[0.10008232 0.20008706]] [0.29991394]
160 [[0.10002764 0.20002899]] [0.29997122]
180 [[0.10000926 0.20000964]] [0.2999904]
200 [[0.10000309 0.20000322]] [0.2999968]
'''
```