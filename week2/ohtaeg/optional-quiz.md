1. Auto Scaling을 이용해 서버를 실행할 때 서버 타입에 대한 세부사항은 어디에서 정의할 수 있나요?
```
A. Auto Scaling Group
B. Launch Template or Launch Configuration
C. Elastic Load Balancer
D. Application Load Balancer
```
- 선택 : (B)
```
어떤 속성인지 명시가되면 더 확실하겠지만 Auto Scailing은 보통 시작 템플릿에서 EC2 인스턴스에 대한 정보를 지정한다.
AMI, 인스턴스 타입, 키 페어, 보안 그룹 등 EC2 인스턴스의 속성을 사용하여 시작 구성을 만들 수 있기에 B 선택
```

<br>
<br>

2. Healthcheck에서 Elasitc Load Balacing이 실패하면 어떤일이 발생하나요? (Choose the best appropriate answer)
```
A. Elasitc Load Balancing이 실패하면 다른 Load Balancer를 실행시킴
B. Elasitc Load Balancing이 인스턴스가 응답할 때까지 계속 회신을 요청함
C. Elasitc Load Balancing이 해당 인스턴스에 대한 트래픽을 차단하고 새 인스턴스를 실행시킴
D. 로드 밸런서는 용량이 더 큰 인스턴스를 실행시킴
```
- 선택 : (C)
```
비정상 임계 값에 설정한 만큼 헬스 체크시 비 정상이라고 판단할 수 있는 횟수만큼 회신을 요청하고 비정상적이라면 트래픽을 보내지 않기에 C 선택
```

<br>
<br>

3. 서버를 위한 Auto Scaling 메커니즘을 생성할 때 두 가지 필수적 구성 요소는 무엇인가요? (정답 2개)
```
A. Elastic Load Balancing
B. Auto Scaling Group
C. DNS 연결
D. Launch Template or Launch Configuration
```
- 선택 : (B, D)
```
Auto Scaling 생성시 오토 스케일링 그룹과 시작 템플릿 설정하는 단계가 있는 것으로 보아 B, D 선택
A 같은 경우는 기존에 존재하고 있는 LB를 선택할 수도 있고, 새로 생성할 수도 있어서 선택 사항이라 생각함
```
<br>
<br>

4. EC2의 CPU 사용률이 증가하면 Auto Scaling을 통해 새 서버를 시작하는 규칙을 작성할 때 CPU 사용률을 모니터링하는 데 사용되는 도구는 무엇인가?
```
A. CloutWatch 성능 지표 
B. 리눅스 top 명령어 결과값
C. ELB healthcheck 지표
D. 운영체제에 따라 다름. Auto Scaling은 CPU 사용률 측정을 위해 OS native 도구를 사용함.
```
- 선택 : (A)

<br>
<br>

5. 유입되는 트래픽을 확인하기 위해 로드 밸런서가 필요로 하는 두 가지 정보는 무엇인가?
```
A. 운영체제 종류
B. Port Number
C. Network Protocol
D. IP Address
```
- 선택 (B, C)
```
A - LB는 OS와 상관없음
D - LB는 클라이언트가 어떤 destination에 대한 정보를 더 중요하게 보기에 소스 IP의 중요성은 낮아보인다.
```

<br>
<br>

6. 다음 중 healthcheck를 할 수 없는 로드밸런서는?
```
A. ALB
B. NLB
C. CLB
D. 위에 보기 중에 없음
```
- 선택 : (D)
```
셋다 헬스체크는 기본적으로 하는 것으로 알고있다.
NLB는 헬스체크는 하되 Unhealthy 상태여도 통신을 하는데, 
NLB의 Health check와는 무관하게 대상 그룹에 트래픽을 전달하기 때문에 살짝 헷갈렸음
NLB 헬스 체크는 할 수 없지는 않으니까 D 선택
```

<br>
<br>

7. 컨텐츠 캐싱 장점을 최대한 살리기 위해 동일 인스턴스에 대해 반복적으로 요청을 전달하는 기술은?
```
A. sticky session
B. multi availablity zone 활용
C. cross-zone load balancing
D. 인스턴스 별로 하나의 ELB 활용
```
- 선택 : (A)
```
동일한 클라이언트에 대해 동일한 인스턴스로 요청을 하기 위한 설정은 A
```

<br>
<br>

8. 내부 전용 어플리케이션의 아키텍쳐를 구상할 때 ELB를 통한 인터넷 접속을 막을 수 있는 방법은?
```
A. ELB에서 Internet Gateway 분리
B. Private Subnet에 인스턴스를 생성하고 ELB와 연결
C. VPC에는 어떠한 Internet Gateway도 attach 해서는 안됨
D. 콘솔에서 ELB를 생성할 때 내부용 또는 외부용을 선택 가능
```
- 선택 : (D)
```
CLB, ALB, NLB 실습 생성시, 네트워크 영역에 대해서 Internal, External에 대한 구분 선택값이 있던걸로 기억
```

<br>
<br>

9. 다음주 맞는 것을 2개 고르세요.
```
A. ELB는 다수의 Region 간에 트래픽 분산 가능
B. ELB는 다수의 AZ 간에 트래픽 분산 가능하지만 다수의 Region 간에는 트래픽 분산 불가
C. ELB는 다수의 AZ 간에 트래픽 분산 가능
D. ELB는 다수의 Region 간에는 트래픽 분산 가능하지만 다수의 AZ 간에 트래픽 분산 불가
```
- 선택 : (B, C)
```
ELB 생성시 어떤 VPC로 할지 선택하고, 두 개 이상의 가용 영역 서브넷을 선택하는 부분은 있었지만
어떤 지역에 대해서 선택하는 부분은 없었기에 하나 이상의 가용 영역에서 등록된 대상에 대해서만 라우팅 한다고 판단하여 B, C 선택
```

<br>
<br>


10. Auto Scaling Group에서 생성할 수 있는 EC2 인스턴스의 최대 개수는?
```
A. 10
B. 20
C. 100
D. 제한 없음
```
- 선택 : (D)
```
실습시, 갯수에 대한 제한이 없었던 것 같아 D 선택
```