## Introduction to Convolutional Neural Network

1. ### CNN 이란

   - 말 그대로 **convolution** 이라는 작업이 들어가는 NN을 의미한다.

     <img src="./image/0.png" width="80%">

2. ### CNN의 역사 

   - 초창기에 CNN을 개발한 분들이 고양이가 보는 것마다 *자극 받는 **뇌의 위치*** 가 다른 것을 보고 아이디어를 얻어 CNN을 만들었다고 한다. 

     - NN의 활성화 부분이 다르다.

     - 세모 그림을 봤을때와 네모 그림을 봤을때 각각 활성화되는 뉴런이 다른다.

       <img src="./image/3.png" width="60%">

   - *특징 표현 학습(feature representation learning)* : image 전체를 보는 것이 아니라 부분을 보는 것이 핵심 아이디어이다.

     - 부분 에 해당하는 것을 **filter** 라고 한다. 대게 image보다 작다.

   - 1989년 LeCun이 발표한 논문 [*Backpropagation applied to handwritten zip code recognition*](http://yann.lecun.com/exdb/publis/pdf/lecun-89e.pdf) 에서 처음 소개가 되었고, 우체국 주소의 필기체 zip code 를 인식하기 위해 개발 되었다.

     LeCun이 처음 소개한 CNN은 필기체 인식에 있어서는 매우 의미있는 결과가 나왔다. *Mnist*

   - 이후, 2003년 Behnke의 논문 [*Hierarchical Neural Networks for Image Interpretation*](https://www.ais.uni-bonn.de/behnke/papers/diss_short.pdf) 을 통해 일반화가 되었다.

   - Simard의 논문 [*Best Practices for Convolutional Neural Networks Applied to Visual Document Analysis*](http://cognitivemedium.com/assets/rmnist/Simard.pdf) 을 통해 단순화 되면서 개념 확대의 단초가 마련되었다. 

3. ### 기존 Multi-layered Neural Network의 문제점

   - 필기체 A를 인식하기 위해 MLN로 네트워크를 구성해보자

     <img src="./image/13.png" width="70%">

   - 236개의 입력단과 100개의 hidden-layer 및 26개의 출력단으로 구성되면 이 망에 필요한 weight와 bias는 총 28,326개가 된다.

     - 입력단에 1x1 의 데이터가 들어가게 되는데 이때, 위치 정보가 사라진다.

     - 만약 전체 글자에서 only 2 픽셀값이 달라져도 새로운 학습 데이터로 처리해줘야 한다.

     - 글자의 크기가 달라지거나, 글자가 회전되거나 변형이(distortion)이 조금만 생기더라도 새로운 학습 데이터를 넣어주지 않으면 좋은 결과를 기대하기 어렵다.

       <img src="./image/14.png" width="50%">

     - 결과적으로 기존 multi-layered neural network는 글자의 topology는 고려하지 않고, 말 그대로 raw data에 대해 직접적으로 처리하기 때문에 많은 학습 데이터가 필요하고, 이에 따른 학습 시간이 필요하다는 문제점이 있다.

4. ### 그럼, ***convolution*** 이란?

   - 영상 처리 분야에서 convolution은 주로 filter 연산에 사용이 되며, 영상으로부터 특정 feature들을 추출하기 위한 필터를 구현할 때 convolution을 사용한다.

     <img src="./image/10.gif" width="50%">

   - 컴퓨터는 그림을 여러개의 픽셀로 이루어진 행렬로 본다.

     convolution matrix는 이 커다란 픽셀 배열에 작은 행렬을 통해 그 픽셀의 값을 수정하는 방법이다.

     <img src="./image/8.png" width="50%">

5. ### CNN의 특징

   - ##### Locality

     - CNN은 receptiva field와 유사하게 local 정보를 활용한다. 공간적으로 인접한 신호들에 대한 correlation 관계를 비선형 필터를 적용하여 추출해 낸다. 이런 필터를 여러 개를 적용하면 다양한 local 특징을 추출해 낼 수 있게 된다. 
     - subsampling 과정을 거치면서 영상의 크기를 줄이고 local feature들에 대한 filter 연ㅅ나을 반복적으로 적용하면 점차 global featrure을 얻을 수 있게 된다.

   - ##### Shared Weights

     - 동일한 계수를 갖는 filter을 전체 영상에 반복적으로 적용함으로 변수의 수를 획기적으로 줄일 수 있으며, topoloty 변화에 무관한 항상성(invariance)를 얻을 수 있게 된다.

   - CNN은 filter의 계수를 학습한다는게 핵심이다.

   - 추출할때는 다양한 여러장을  추출하여  강인한 특징(왜곡,변형같은 환경변화에 잘 적응하는)을 유도하는데  이것을 feature maps이라 한다. 

     <img src="./image/9.png" width="80%">

6. ### subsampling이란?

   - 화면의 크기를 줄이는 과정이다.

   - 아래의 방법인 max pooling을 사용한다. (해당 영역의 최대치를 선택하는 기법)

   - 위 그림처럼 4개중 가장 큰 수를 선택한다. 이것은 뉴런이 가장 큰 신호에 반응하는것과 유사한다.

     <img src="./image/11.png" width="60%">

   - 이렇게 하면 노이즈가 감소하고 속도도 빨라지고 영상의 분별력이 좋아진다고 한다.

7. ### CNN으로

- 우리의 커널이 정확하게 고정된 값을 갖게하는 대신 convolution net을 학습 시켜 점점 더 주어진 이미지 필터링을 잘 하게 된다. 

- 이 프로세스는 자동적으로 이루어지므로 피처 학습이라고도 불린다.

  피처 학습은 자동으로 각각의 목적에 따라 생성된다. 

  > 예전엔 사람의 예측에 의해 뽑히던 이 특징들을 지금은 이마저도 기계학습을 이용해 뽑는다는 것입니다. 다시 말해, 예전엔 ‘선들을 추출해서 학습시키면 사물인식이 잘 될 거야.’와 같이 사람이 먼저 이 선들을 추출하는 알고리즘을 만들어 주었는데, 이제는 특징 추출과 학습 모두가 딥 러닝 알고리즘 안에 포함되었다는 것이죠.
  >
  > 다단계로 특징을 추출해 학습하는 컨볼루셔널 뉴럴 네트워크(Convolutional Neural Network)는 현재 딥 러닝의 대세로서 특히 이미지 인식에서 큰 발전을 이룩하고 있습니다.

  > 딥러닝계의 라이징 스타 중 한명인 OpenAI의 AndrejKarpathy의 간단한 조사에 따르면 공개 논문 저장소 arXiv을 통해 매월 공개되는 머신러닝 논문의 수가 5년 사이 100배 이상 늘었다고 한다. 다시말하면 10년 동안 나올 머신러닝 논문들이 지금은 한 달 안에 쏟아지고 있는 셈이다.
  >
  > <img src="./image/12.png" width="100%">