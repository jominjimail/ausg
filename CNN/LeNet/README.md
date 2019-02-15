# LeNet5



연구진들은 local receptive field, shared weight, sub-sampling의 개념을 결합한 CNN의 개념을 개발했다. 

- 최초로 개발한 LeNet-1 (1990)

  <img src="./image/2.png" width="90%">

  - input 영상 크기 28x28 

  - 16x16  로 샘플 이미지를 줄인 후 그것은 28x28 크기의 중앙에 위치함

  - 1단계 convolution을 통해 얻은 feature map의 개수 4개

  - 2 단계 pooling을 통해 얻은 feature map의 크기 12x12

  - 여러 단계의 convolution을 거치면서 작은 feature에서 좀 더 global한 feature을 얻어가는 과정

  - 의미있는 global feature을 얻어 이것은 Fully-connected neural network에 연결해 classify 함 


- LeNet-5

  <img src="./image/1.png" width="90%">

  - LeNet-1 개발 당시 컴퓨팅 능력이 낮았기에 파라미터의 수가 작은 망을 개발함

  - 입력 이미지의 크기 및 convolution kernel의 개수를 늘리고 최종단의 FC layer 의 크기도 키움

  - MNIST 28x28 이미지를 32x32 크기의 중앙에 위치함 

  - C는 convolution, S는 sub-sampling, F는 Fully-connected layer을 의미

  - 대문자 알파벳 다음에 오는 숫자는 layer의 번호를 의미

- LeNet-5 구조

  - 3개의 convolution layer, 2rodml sub-sampling layer 및 1개의 fully-connectec layer을 가진다.

  - C1은 convolution layer이며 32x32 영상을 입력으로 받아, 6@28x28 크기의 feature map 영상을 만들어 낸다. 5x5 kernal(filter)을 사용하고, zero-padding을 지원하지 않기 때문에 boundary 정보가 사라지면서 28x28 크기의 feature map 영상이 나오는 것이다. 

    ex: 0 ~31 -> 0-4 , 1-5, 2-6, 3-7, 4-8 .... 27-31 이므로, 28개가 나옴

    *convolution kernal의 계수는 사전에 결정되는 것이 아니라, 학습을 통해 결정된다.*

    C1의 kernel은 5x5 +1 총 26개의 자유 파라미터가 있고, 그런 커널이 6@개 있기에 총 156개의 free parameter가 있다. 

  - S2는 sub-sampling을 수행하며 2x2 크기의 receptive filed로 부터 average pooling을 수행한다. 

    6@28x28 크기의 feature map 영상을 입력으로 받아, 6@14x14 크기의 출력영상을 만들어 낸다.

    ex: 0~27 -> 0-1 , 2-3, 3-4, 4-5 ... 16-17 이므로, 14개가 나옴

    average pooling을 수행하기 때문데 weight 1개, bias 1개로 2개의 파라미터를 갖고, 6@개의 커널이 있으므로 총 12개의 free parameter가 있다.

  - C3는 C1과 동일한 크기의 5x5 kernal 크기를 가지고 수행하며, 6@14x14 입력 영상을 받아 16@10x10 크기의 출력 영상을 만들어 낸다. 

    이때 6개의 모든 입력 영상이 16개의 모든 출력에 연결이 되는것이 아니라, 아래의 테이블과 같이 선택적으로 입력 영상을 골라, 출력 영상에 반영될 수 있도록 한다. 

    이렇게 하는 이유는 처음 convolution 으로부터 얻은 6개의 low-level feature가 서로 다른 조합으로 섞이면서 global feature로 나타나기를 기대하기 때문이다.

    <img src="./image/3.png" width="90%">

    free parameter개수는 25(5x5 filter) * 60(S2와 C3의 연결 'X') + 16(bias) = 1516개이다.

  - S4는 S2와 마찬가지로 sub-samplint 단계이며, 16@10x10 feature 영상을 받아 16@5x5 출력영상을 만든다. free parameter개수는 32(2x16)개이다.

  - C5는 16@5x5 영상을 받아 5x5 kernel conv 수행하기에 출력은 1x1 크기의 feature-map이다. fully connected 의 형태로 연결하여 총 120개의 feature map을 생성한다. 

    free parameter 개수는 25(5x5 filter) * 1920(S4와 C5의 연결 ) + 120(bias) = 48120개이다.

  - F6은 fully-connected 이며 C5의 결과를 84개의 unit에 연결 시킨다. 

    free parameter 개수는 (120+1) x 84 = 10164 가 된다. 

    <img src="./image/4.png" width="80%">

  - 단계별 영상을 보면, topology 변화나 잡음에 대한 내성이 상당히 강함을 알 수가 있다. 

- 결론

  - 여러 기존 알고리즘와 비교해보면, fully-connecte NN에 비해 LeNet-1의 성능이 훨씬 뛰어나고, LeNet-5의 결과는 그것보다 더 좋다는 것을 알 수 있다.

    <img src="./image/5.png" width="100%">