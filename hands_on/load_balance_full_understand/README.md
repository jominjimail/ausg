
## AWS 란?

:Amazon Web Service 는 아마존에서 제공하는 *클라우드* 서비스

<img src="./image/26.png" width="40%"> 

## 클라우드 컴퓨팅이란?

:기존의 물리적인 형태의 실물 컴퓨팅 리소스를 네트워크 기반 서비스 형태로 제공하는 것

여러분은 물리적인 컴퓨터가 없어도 100개의 컴퓨터를 사용하실 수 있습니다.

<img src="./image/27.png" width="60%">

## 왜필요할까?

- 나의 노트북은 서버가 될 수... 있지만.. 한계가 있을것이다. 수많은 request를 처리할 파워가 없다.

- 나의 노트북에 VMware를 설치해 linux를 돌리면... 용량 부족이라고 새빨갛게 된다. (학기가 끝나면 지워버린다.) AWS에서 instance를 50개를 만들어도 내 노트북에는 영향이 없다. 저 멀리 Tokyo region에 있는 컴퓨터에 *connect* 해서 사용하는것이기때문이다. 

- 계산량이 많은 코드를 작성했을때 나의 노트북으로 돌리면 4시간이 걸린다. 생상성이 확 떨어진다. 이때 AWS의 좋은 Instance를 구입해서 30분만에 돌릴수 있다면 어떻게 할것인가? 나쁘지 않다.

- 실제 서버를 만들땐 이것저것 손봐줘야 할게 굉장히 많다. 어떤 port를 이용해서 통신을 할지 방화벽 설정, 메모리설정등 딥하게 공부해야할 것들 천지이다. AWS는 GUI를 제공하며 몇번의 클릭으로 서버를 쉽게 만들 수 있다. 이는 굉장히 대단한것이다. 
- 모바일게임을 만들었따. 10만명의 게임 사용자를 예상하고 하드웨어를 구매했는데, 막상 게임을 출시했더니 사용자가 100만명이 몰릴 수도 있따. AWS는 사용자 수에 맞춰 단 몇 분 안에 서버를 자동으로 증설해줄 수 있다. 
- 한국 기업이 미국 사용자를 대상으로 게임을 내놓을 떄 region 설정만 비꾸면 보다 빠른 속도로 서비스를 제공할 수 있다.

*그외 많은 이유가 있겠지만 AWS 초보자인 저의 생각이었습니다.*





## AWS의 주요 서비스

1. Amazon Elastic Compute Cloud(**EC2**)
   - 가상 서버 자원을 제공하는 서비스, 이때 하나의 가상 서버 자원은 인스턴스(instance)로 분류되며, AMI(Amazon Machine Image)라고 부릅니다.

   - 장점: Auto Scailing 서비스를 통한 자동 확장 및 축소 가능

     <img src="./image/28.jpg" width="30%"> 

2. AWS Elastic Load Balancing(**ELB**)
   - 트래픽 로드 밸런싱 서비스, EC2의 앞에 위치 시키고 여러개의 EC2 인스턴스에 대해 트래픽을 분산해 줍니다.
<img src="./image/29.png" width="30%"> 

3. Auto Scaling(**ASG**)
   - CPU 또는 메모리 등의 사용량에 따라 EC2 인스턴스의 개수를 자동으로 증설/축소 하는 서비스입니다. 
   <img src="./image/30.png" width="30%"> 

4. Amazon Simple Storage Service(**S3**)
   - 온라인 스토리지 서비스입니다.   S3에 있는 데이터에 대한 강력한 분석을 바로 실행할 수 있습니다

     <img src="./image/31.png" width="30%"> 



## AWS 무료 서비스 - Free Tier

- AWS는 처음 가입 후 12개월 동안 주요 서비스에 대한 무료 서비스를 제공합니다.

- 주요 서비스에 대해 기본적인 테스트와 블로그 같은 작은 서비스 운영이 가능합니다.

  - EC2 서버: 원 750시간 t2.micro 운영 가능 
  - S3 스토리지: 5GB (다운로드 2만회, 업로드 2천회)

- 여러분이 사용 중 프리 티어를 초과하지 않으면 이용 요금이 부과되지 않습니다.

- 해당 세미나는 프리 티어를 초과하지 않습니다.



*핸즈온 진행 중 궁금하신점이 있다면 언제든 질문해주세요.*



STEP 1. [AWS 기초 개념](https://github.com/jominjimail/ausg/blob/master/hands_on/load_balance_full_understand/step1.md)


STEP 2. [EC2](https://github.com/jominjimail/ausg/blob/master/hands_on/load_balance_full_understand/step2.md)


STEP 3. [ELB](https://github.com/jominjimail/ausg/blob/master/hands_on/load_balance_full_understand/step3.md)


STEP 4. [CLImode_S3](https://github.com/jominjimail/ausg/blob/master/hands_on/load_balance_full_understand/step4.md)

