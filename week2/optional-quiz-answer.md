## (선택) 연습문제 10개를 풀이/해설을 제출하세요. (번역이 어색한 점 양해바랍니다!)
1. Auto Scaling을 이용해 서버를 실행할 때 서버 타입에 대한 세부사항은 어디에서 정의할 수 있나요?
```
A. Auto Scaling Group
B. Launch Template or Launch Configuration
C. Elastic Load Balancer
D. Application Load Balancer
```
```
정답 B
런칭할 서버의 세부 타입은 LT(혹은 LC)에서 정의한다.
```

2. Healthcheck에서 Elasitc Load Balacing이 실패하면 어떤일이 발생하나요? (Choose the best appropriate answer)
```
A. Elasitc Load Balancing이 실패하면 다른 Load Balancer를 실행시킴
B. Elasitc Load Balancing이 인스턴스가 응답할 때까지 계속 회신을 요청함
C. Elasitc Load Balancing이 해당 인스턴스에 대한 트래픽을 차단하고 새 인스턴스를 실행시킴
D. 로드 밸런서는 용량이 더 큰 인스턴스를 실행시킴
```
```
정답 C
ELB는 일정 시간 내에 인스턴스의 응답이 없는 경우 새 인스턴스를 시작한다.
```

3. 서버를 위한 Auto Scaling 메커니즘을 생성할 때 두 가지 필수적 구성 요소는 무엇인가요? (정답 2개)
```
A. Elastic Load Balancing
B. Auto Scaling Group
C. DNS 연결
D. Launch Template or Launch Configuration
```
```
정답 BD
Auto Scaling을 구성하려면 ASG와 LT(혹은 LC)에 대한 정의는 필수다.
```

4. EC2의 CPU 사용률이 증가하면 Auto Scaling을 통해 새 서버를 시작하는 규칙을 작성할 때 CPU 사용률을 모니터링하는 데 사용되는 도구는 무엇인가?
```
A. CloutWatch 성능 지표 
B. 리눅스 top 명령어 결과값
C. ELB healthcheck 지표
D. 운영체제에 따라 다름. Auto Scaling은 CPU 사용률 측정을 위해 OS native 도구를 사용함.
```
```
정답 A
ASG는 스케일링 정책을 위한 지표를 얻기 위해서 CloudWatch의 지표를 사용한다. 
```

5. 유입 트래픽을 확인하기 위해 로드 밸런서가 필요로 하는 두 가지 정보는 무엇인가?
```
A. 운영체제 종류
B. Port Number
C. Network Protocol
D. IP Address
```
```
정답 BC
로드밸런서 리스너는 유입 트래픽의 네트워크 프로토콜과 포트번호를 알아야 한다.
https://docs.aws.amazon.com/ko_kr/elasticloadbalancing/latest/application/load-balancer-listeners.html#listener-configuration
```

6. 다음 중 healthcheck를 할 수 없는 로드밸런서는?
```
A. ALB
B. NLB
C. CLB
D. 위에 보기 중에 없음
```
```
정답 D
모든 LB는 헬스체크 기능을 가진다.
```

1. 컨텐츠 캐싱 장점을 최대한 살리기 위해 동일 인스턴스에 대해 반복적으로 요청을 전달하는 기술은?
```
A. sticky session
B. multi availablity zone 활용
C. cross-zone load balancing
D. 인스턴스 별로 하나의 ELB 활용
```
```
정답 A
```

8. 내부 전용 어플리케이션의 아키텍쳐를 구상할 때 ELB를 통한 인터넷 접속을 막을 수 있는 방법은?
```
A. ELB에서 Internet Gateway 분리
B. Private Subnet에 인스턴스를 생성하고 ELB와 연결
C. VPC에는 어떠한 Internet Gateway도 attach 해서는 안됨
D. 콘솔에서 ELB를 생성할 때 내부용(internal) 또는 외부용(internet-facing)을 선택 가능
```
```
정답 D
ELB에는 인터넷 게이트웨이를 attach/detach할 수 없다.
더불어 Private Subnet에 인스턴스를 생성하고 ELB와 연결하는 것도 불가능하다.
VPC에서 인터넷 게이트웨이를 붙이지 않더라도 외부영(Internet-Facing) ELB를 추가하면 인터넷 연결이 가능해진다.
```

9. 다음주 맞는 것을 2개 고르세요.
```
A. ELB는 다수의 Region 간에 트래픽 분산 가능
B. ELB는 다수의 AZ 간에 트래픽 분산 가능하지만 다수의 Region 간에는 트래픽 분산 불가
C. ELB는 다수의 AZ 간에 트래픽 분산 가능
D. ELB는 다수의 Region 간에는 트래픽 분산 가능하지만 다수의 AZ 간에 트래픽 분산 불가
```
```
정답 BC
ELB는 단일 리전 내에서 다중 AZ 구조로 확장할 수 있으나 다중 리전 구존로 확장하는 것은 불가능하다.
```

10. Auto Scaling Group에서 생성할 수 있는 EC2 인스턴스의 최대 개수는?
```
A. 10
B. 20
C. 100
D. 제한 없음
```
```
정답 D
ASG에 넣을 수 있는 EC2 인스턴스 수에는 제한이 없으나 사용자의 계정상 EC2 인스턴스 생성에 개수 제한이 있을 수 있다. 이는 서포트 티켓을 통해 그 제한을 풀 수 있다.
```