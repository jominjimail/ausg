## week 6 Gradient Descent Algorithm

### 우선 기초
- the hypothesis funcion이란: input(feature)과 output(target)의 관계를 나타내는 함수이다. output값이 나오게 하는 진짜 변수들과 그 변수와 output 사이의 관계식을 정확히 정의하는것은 불가능하다. 우리는 어마어마한 변수들을 모두 고려하고 그 변수들 간의 복잡한 방정식을 찾는 대신 주로 이러이러한 변수들이 output에 영향을 미칠거야 하고 추정하는 일종의 가설을 세우기 때문에 hypothesis라고 부르기 시작한 것으로 여겨진다. 

- linear regression에서의 hypothesis function:


## Cost functions
- linear regression에서의 const function:
  - 주어진 데이터에 가장 잘 맞는 직선을 선택하려면 일정한 기준이 있어야 한다. 우리의 hypothesis funcgion의 정확도를 측정하기 위해 cost function을 이용할 것이다. 
  
  - training example 들이 parameter 추정에 이용된다 h(x)가 y와 비슷해지는 세타를 고르는 것이다. 
  - error 값을 최소화하는 값을 찾는것이다. 하지만 error값은 양수값이 될수도 있고 음수값일 수도 있기때문에 제곱값의 합을 구하여 그 합이 최소가 되는 parameter를 찾는 방법이 일반적이다. 이를 LSE(least squared error) criterion이라고 한다.
  - 이 cost function은 mean-squared-error (MSE) 이다. 즉 (error)^2의 평균이 cost값이 된다. 
  - 여기서 error란, 추정한 y값과 y.hat 값의 차이를 말한다. 
  - 다만 평균이라면 data 갯수인 m으로 나누어야 하는데 2m으로 나누었다. 2는 계산상의 편의를 위한 것으로 나중에 약분되는 것을 확인하게 될것이다. 
  

## Gradient Descent Algorithm
- Gradient Descent 는 cost funcgion을 최소화하기 위해 이용할 수 있는 방법 중 하나이며, cost function말고도 각종 optimization에 이용되는 일반적인 방법이다. 

> Gradient Descent Outline : start 
> start with some Theta0, Theta1 ( Theta0 = 0 , Theta1 = 1)
> keep changing Theta0, Theta1 to reduce J(Theta0, Theta1) until we hopefully end up at minimum.

## Learning rate

## Batch and Mini batch
