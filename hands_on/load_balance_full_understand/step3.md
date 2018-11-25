## ELB

:Elastic Load Balancing은 들어오는 애플리케이션 트래픽을 Amazon EC2 인스턴스, 컨테이너, IP 주소와 같은 여러 대상에 자동으로 분산시킵니다.

ELB는 3 가지 유형의 로드 밸런서를 지원합니다.

- Application Load Balancer
- Network Load Balancer
- Classic Load Balancer

저희는 마지막, Classic Load Balancer를 다룰것 입니다.

### Load Balancer란?

우선, 왜 Load Balancer가 필요할까?

clinet가 한 두명인 경우 시스템은 아래와 같이 동작한다.

<img src="./image/35.png" width="50%"> 

하지만, clinet가 수천만명이라면? server는 모든 사람들의 응답을 해주려고 노력하지만 결국엔 파업을 한다. 멈춰버린다.



그럼, 서버의 파업을 막기위해 어떻게 해야할까?

- Scale-up: Server가 더 빠르게 동작하기 위해 HW성능을 올리는 방법
- Scale-out: 하나의 server 보다는 여러 대의 server가 나눠서 일을 하는 방법

scale-up은 금전적, 기술적 한계가 있다.



*하지만, AWS에서는 클릭 몇번으로 scale-up이 가능하다. 이 과정을 실습하다 과금이 나온바람에 실습에서는 제외했다...[궁금하신 분들을 위한 SCALE-UP링크](https://docs.aws.amazon.com/ko_kr/AWSEC2/latest/UserGuide/ec2-instance-resize.html)*



우리는 scale-out 해결법을 사용할 것이다. 이의 장점은 무엇일까?

- 하드웨어 향상하는 비용보다 서버 한대 추가 비용이 더 적다. (현실적)
- 여러 대의 server 덕분에 무중단 서비스를 제공할 수 있습니다. (여러대의 server가 있으니 안전)

즉, 하나의 인터넷 서비스가 발생하는 트래픽이 많을 때 여러 대의 서버가 분산처리하여 서버의 로드율 증가, 부하량, 속도저하 등을 고려하여 적절히 분산처리하여 해결해주는 서비스 입니다.







