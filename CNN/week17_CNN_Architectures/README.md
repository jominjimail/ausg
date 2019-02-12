# CNN 아키텍처

대량 영상 인식 경연 대회인 image Net ILSVRC에서 우승을 하거나 준우승을 한 것 들을 살펴볼 것이다.

- imageNet

  세계 최대의 영상 데이터 베이스이며, 컴퓨터 비젼을 연구하는 사람들이 벤치마크로 사용할 수 있는 영상 데이터 베이스이다. 

  현재 약 22000 종류로 분류가 가능한 1500만장의 인터넷 기반의 영상이 확보되어 잇다. 

- ILSVRC

  imageNet Large Scale Visual Recognition Challenge의 약어

  대회의 분야는 object localization, object detection, object detection from video등으로 나뉜다.

  [IMAGENET ILSVRC](http://www.image-net.org/challenges/LSVRC/)

- LeNet

  - Yann LeCun 이 1990년대에 발표한 구조로, 처음으로 CNN이라는 개념을 도입
  - 우편 번호나 숫자등을 인식하기 위함

- AlexNet

  - 2012년 ILSVRC 대회에서 우승
  - Krizhevsky, Hinton 등에 의해 개발 됨
  - LeNet 과 유사하지만, 보통 conv layer 다음에 pooling layer가 오는 기본 구조와 달리, conv layer 뒤에 conv layer가 온 점이 특이함 

- ZFNet

  - 2013 년 ILSVRC  대회에서 우승
  - AlexNet 의 hyper-parameter를 수정하여 성능을 좀 더 개선함
  - 중간에 있는 conv layer의 크기를 늘림

- GoogLeNet

  - 2014 년 ILSVRC 대회에서 우승
  - Inception Module 개념을 도입 (망의 파라미터 수를 대폭 줄임)
  - AlexNet : 60M , GoogLeNet : 4M

- VGGNet

  - 2014 년 ILSVRC 대회에서 준우승
  - 대량의 이미지를 인식함에 있어, 망의 깊이가 정확도에 어떤 영향을 주는지 보여줌
  - 망의 시작부터 끝까지 동일하게 3x3 conv, 2x2 pooling 사용
  - depth가 16일 때 최적의 결과가 나오는걸 보여줌 
  - 단점은 메모리 수와 파라미터 수가 크다.

- ResNet

  - 2015 년 ILSVRC 대회에서 우승
  - MS의 Kaiming He 등에 의해서 개발 됨
  - 기존 DNN보다 layer 수가 훨씬 많은 Deeper NN에 대한 학습을 쉽게 할 수 있도록 해주는 residual framework 개념을 도입했다.