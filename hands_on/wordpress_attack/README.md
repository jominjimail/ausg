AWS 실습 따라해보기

상황: 
wordpress라는 무거운 instance에 user가 동시 접속했다.

필요한거:
xshell - ssh 접속을 위해 필요 

준비 과정:
새로운 instance를 lunch 한다.
aws marketpace에서 wordpress를 검색하고 select하다.

새로운 instance를 또 lunch 한다.
이번에는 ubuntu를 select한다.

각각 wp와 attack이름을 붙여 줬다.

wp와 attck을 xshell에 연결해준다. 
새로 만들기 해서 연결해준다.

사용자 인증은 aws instance할때 생성받은 public key로 지정해준다.
사용자 이름은 ubuntu라고 정해준다. 나는 ubuntu

ssh -i "awspwd.pem" ubuntu@ec2-13-230-102-248.ap-northeast-1.compute.amazonaws.com 
명령어를 쳐서 연결해준다.

wp$top // cpu 점유율 상태를 보여준다.

attack$sudo apt-get update
attack$sudo apt-get install apache2-utils
attck$ab -n 400 -c 1 http://13.230.102.248/
명령어를 친다. 이러면 해당 ip인 wp에 400개의 요청을 보내는것이다. 동시접속자수는 1명이다.






