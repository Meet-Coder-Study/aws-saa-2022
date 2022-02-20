# 2주차 과제
- [Udemy AWS SAA 강의](https://www.udemy.com/course/best-aws-certified-solutions-architect-associate) 내 `고기용성 및 스케일링성: ELB 및 ASG`

## 제출방법
- 본인의 이름으로 폴더 생성하여 아래와 같이 제출
- week2/HonGilDong/clb.png
- week2/HonGilDong/alb.png
- week2/HonGilDong/nlb.png
- week2/HonGilDong/asg-1.png
- week2/HonGilDong/asg-2.png
- week2/HonGilDong/quiz.md
- week2/HonGilDong/optional-quiz.md

## 실습 과제
- CLB 실습하고 인증
- ALB 실습하고 인증
- NLB 실습하고 인증
- ASG 실습
 - ASG를 구성하고 Desired Capacity, Minumum Capacity, Maximum Capacity를 값을 조정하여 scale-in 혹은 scale-out을 구현해보세요.
 - Activity History를 캡처해서 보여주세요. 
- ASG 스케일링 정책 실습
  - EC2에 스트레스를 주고 스케일링 아웃되도록 재현하세요.
  - Activity History를 캡처해서 보여주세요.

## 문제 과제
- 고가용성 및 스케일링성 퀴즈 23개 풀이/해설하세요.

## (선택) 문제 과제
1. Auto Scaling을 이용해 서버를 실행할 때 서버 타입에 대한 세부사항은 어디에서 정의할 수 있나요?
```
A. Auto Scaling Group
B. Launch Template or Launch Configuration
C. Elastic Load Balancer
D. Application Load Balancer
```

2. Healthcheck에서 Elasitc Load Balacing이 실패하면 어떤일이 발생하나요? (Choose the best appropriate answer)
```
A. Elasitc Load Balancing이 실패하면 다른 로드밸런서를 실행시킴
B. Elasitc Load Balancing이 인스턴스가 웅덥헐 때까지 계속 회신을 요청함
C. Elasitc Load Balancing이 해당 인스턴스에 대한 트래픽을 차단하고 새 인스턴스를 실행시킴
D. 로드 밸런서는 용량이 더 큰 인스턴스를 실행시킴
```

3. 서버를 위한 Auto Scaling 메커니즘을 생성할 때 두 가지 필수적 구성 요소는 무엇인가요? (정답 2개)
```
A. Elastic Load Balancing
B. Auto Scaling Group
C. DNS 연결
D. Launch Template or Launch Configuration
```

4. EC2의 CPU 사용률이 증가하면 Auto Scaling을 통해 새 서버를 시작하는 규칙을 작성할 때 CPU 사용률을 모니터링하는 데 사용되는 도구는 무엇인가?
```
A. CloutWatch 성능 지표 
B. 리눅스 top 명령어 결과값
C. ELB healthcheck 지표
D. 운영체제에 따라 다름. Auto Scaling은 CPU 사용률 측정을 위해 OS native 도구를 사용함.\
```

5. 유입되는 트래픽을 확인하기 위해 로드 밸런서가 필요로 하는 두 가지 정보는 무엇인가?
```
A. 운영체제 종류
B. 포트 번호
C. 네트워크 프로토콜
D. IP 주소
```

6. 다음 중 healthcheck를 할 수 없는 로드밸런서는?
```
A. ALB
B. NLB
C. CLB
D. 위에 보기 중에 없음
```

7. 컨텐츠 캐싱 장점을 최대한 살리기 위해 동일 인스턴스에 대해 반복적으로 요청을 전달하는 기술은?
```
A. Sticky Session
B. Multi Availablity Zone 활용
C. cross-zone load balancing
D. 인스턴스 별로 하나의 ELB 활용
```

8. 내부 전용 어플리케이션의 아키텍쳐를 구상 중일 때 ELB를 통한 인터넷 접속을 막을 수 있는 방법은?
```
A. ELB에서 Internet Gateway 분리
B. Private Subnet에 인스턴스를 생성하고 ELB와 연결
C. VPC에는 어떠한 Internet Gateway도 attach 해서는 안됨
D. 콘솔에서 ELB를 생성할 때 내부용 또는 외부용을 선택 가능
```

9. 다음주 맞는 것을 2개 고르세요.
```
A. ELB는 다수의 Region 간에 트래픽 분산 가능
B. ELB는 다수의 AZ 간에 트래픽 분산 가능하지만 다수의 Region 간에는 트래픽 분산 불가
C. ELB는 다수의 AZ 간에 트래픽 분산 가능
D. ELB는 다수의 Region 간에는 트래픽 분산 가능하지만 다수의 AZ 간에 트래픽 분산 불가
```

10. Auto Scaling Group에서 생성할 수 있는 EC2 인스턴스의 최대개수는?
```
A. 10
B. 20
C. 100
D. 제한 없음
```