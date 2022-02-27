# 고가용성 및 스케일링성 퀴즈
## 1. EC2 인스턴스를r4.large에서 r4.4xlarge로 스케일링하는 것을 `수직 스케일링성(Vertitcal Scalinig)`이라 합니다.
## 2. EC2 인스턴스 수를 스케일링 및 축소하는 ASG에서 어플리케이션을 실행하는 것을 `수평 스케일링성(Horizontal Scalinig)`
## 3. AWS ELB는 `static DNS NAME`를 제공합니다.
```
A. static IPv4
B. static DNS Name
C. static IPv6
```
```
정답 B. ELB는 인프라가 변경되더라도 statis endpoint로서 DNS를 제공합니다.
```
### 4. EC2 10개로 인프라를 운영중입니다. 사용자들은 페이지를 이동할 때마다 재인증을 해야하는 것에 대해서 컴플레인이 들어오고 있습니다. EC2 1개 때와 개발환경에서는 문제가 없었습니다. 이 현상의 이유는 무엇일까요?
```
ELB에 Sticky Session이 활성화되어 있지 않습니다.
https://docs.aws.amazon.com/ko_kr/elasticloadbalancing/latest/application/sticky-sessions.html
```
## 5. ALB - EC2 구조로 웹사이트의 트래픽을 분산하고 있고 웹사이트는 ALB의 Private IPv4 주소만 인식하고 있습니다. 실제 클라이언트 IP 주소를 얻으려면 어떻게 해야 하나요?
```
XFF(X-Forwarded-For) 헤더에서 클라이언트 IP 주소를 가져오도록 백엔드를 수정합니다.
```

## 6. ELB - EC2 구조에서 유저들은 어플리케이션이 간헐적으로 작동을 멈춘다고 이야기합니다. 조사 결과 일부 EC2 인스턴스들이 충돌(crash)하는 것을 발견했습니다. 충돌하는 인스턴스에 연결되지 못하도록 하는 방법은?
```
ELB Health CHecks를 활성화하여 비정상(충돌)인 EC2 인스턴스로 트래픽을 보내지 않도록 합니다.
```

## 7. 고성능 저지연 어플리케이션을 위한 아키텍쳐를 설계하려 합니다. 어떤 ELB를 선택해야 할까요?
```
A. ALB
B. CLB
C. NLB
```
```
정답 C. NLB는 ELB 중에서 최고의 성능과 가장 낮은 지연시간을 제공합니다.
```

## 8. ALB가 지원하는 프로토콜이 아닌 것은?
```
A. HTTP
B. HTTPS
C. TCP
D. WebSocket
```
```
정답 C. ALB는 Layer7에 해당하며 HTTP/HTTPS/Websocket을 제공합니다. TCP는 Layer4를 지원하는 CLB, NLB에 해당합니다.
```

## 9. ALB의 라우팅 기준이 아닌 것은?
```
A. client 위치(지역)
B. 호스트명
C. request URL path
D. source IP address
```
```
정답 A. ALB는 URL 경로, 호스트 이름, HTTP 헤더 및 쿼리 문자열을 기반으로 트래픽을 다른 대상 그룹으로 라우팅할 수 있습니다.
```

## 10. 다음 중 ALB의 Target Group이 될 수 없는 것은?
```
A. EC2
B. NLB
C. Private IP
D. Lamda Function
```
```
정답 B. NLB의 TG에 ALB에 등록이 가능하지만 ALB의 TG에는 다른 LB를 등록할 수 없다.
```

## 11. 규정 준수를 위해 최종 사용자에게 고정 주소를 노출하여 승인받은 안정적인 방화벽 규칙을 작성하려고 합니다. 어떤 ELB를 선택하시겠습니까?
```
A. Elastic IP가 연결된 ALB
B. NLB
C. CLB
```
```
정답 B. NLB에는 AZ당 고정 IP 주소가 있으며 Elatic IP를 연결할 수 있습니다. ALB, CLB는 static DNS 이름으로 사용합니다.
```

## 12. 다음 중 애플리케이션 로드 밸런서 (ALB)에서 사용자 지정 애플리케이션 기반 쿠키를 생성 시 쿠키 이름으로 사용할 수 있는 것은 무엇일까요?
```
A. AWSALBAPP
B. APPUSERC
C. AWSALBTG
D. AWSALB
```
```
정답 B. AWSALBAPP, AWSALBTG, AWSALB 모두 ELB에서 사용하는 쿠키 이름이다.
```

## 13. 여러분은 us-east-1의 EC2 인스턴스 세트에 트래픽을 분산하는 네트워크 로드 밸런서 (NLB)가 있습니다. us-east-1b AZ에 2개의 EC2 인스턴스와 us-east-1e AZ에 5개의 EC2 인스턴스가 있습니다. us-east-1b AZ의 EC2 인스턴스에서 CPU 사용률이 더 높다는 것을 확인했습니다. 추가 조사 후 트래픽이 두 AZ에 균등하게 분산되어 있음을 알 수 있습니다. 이 문제를 어떻게 해결하시겠습니까?
```
a. Cross-Zone Load Balancing 활성화
b. sticky session 활성화
c. ELB health check 활성화
d. SSL termination 활성화
```
```
정담 a. Cross-Zone Load Balancing 기능은 모든 AZ의 등록된 모든 EC2
 인스턴스에 트래픽을 고르게 분산합니다.
```

## 14. 애플리케이션 로드 밸런서 (ALB)와 네트워크 로드 밸런서 (NLB)의 어떤 기능을 통해 하나의 리스너에서 여러 SSL 인증서를 로드할 수 있을까요?
```
- TLS Termination
- SNI
- SSL Security Policies
- Host Headers
```
```
정답 SNI.
https://aws.amazon.com/ko/blogs/korea/application-load-balancers-now-support-multiple-tls-certificates-with-smart-selection-using-sni/
https://aws.amazon.com/ko/about-aws/whats-new/2019/09/elastic-load-balancing-network-load-balancers-now-supports-multiple-tls-certificates-using-server-name-indication/
```

## 15. 
여러분은 다음 호스트 이름을 기반으로 트래픽을 3개의 대상 그룹으로 리디렉션하도록 구성된 애플리케이션 로드 밸런서 (ALB)가 있습니다: users.example.com, api.external.example.com 및 checkout.example.com. 이러한 각 호스트 이름에 대해 HTTPS를 구성하려고 합니다. 이 작업을 수행하려면 ALB를 어떻게 구성해야 할까요?
```
- HTTP -> HTTPS 리다이렉션 규칙 사용
- 보안그룹 SSL 인증서 사용
- SNI 사용
```
```
정답 SNI 사용. SNI를 사용하면 여러 HTTPS 어플리케이션을 노출할 수 있습니다.
https://aws.amazon.com/ko/blogs/korea/application-load-balancers-now-support-multiple-tls-certificates-with-smart-selection-using-sni/
```

## 16. 여러분은 원하는 용량과 최대 용량을 모두 3으로 구성한 오토 스케일링 그룹 (ASG)에서 관리하는 EC2 인스턴스 세트에서 호스팅되는 애플리케이션이 있습니다. 또한 CPU 사용률이 60%에 도달하면 ASG를 스케일링하도록 구성된 CloudWatch 경보를 생성했습니다. 여러분의 애플리케이션은 갑자기 엄청난 트래픽을 수신했고 현재 80% CPU 사용률로 실행되고 있습니다. 이제 무슨 일이 일어날까요?
```
- 아무일도 일어나지 않음
- desired capacity 4, maximum capacity 3
- desired capacity 4, maximum capacity 4
```
```
정답 desired capacity 4, maximum capacity 3.
ASG는 설정한 maximum capacity를 초과할 수 없습니다.
```

## 17. 여러분은 애플리케이션 로드 밸런서 (ALB)가 전면에 있는 오토 스케일링 그룹이 있습니다. ALB 상태 확인을 사용하도록 ASG를 구성했는데 하나의 EC2 인스턴스가 비정상으로 보고되었습니다. 이 EC2 인스턴스는 어떻게 될까요?
```
- ASG는 인스턴스를 계속 실행하고 어플리케이션을 재시작
- ASG는 EC2 인스턴스를 분리하고 계속 실행
- ASG는 EC2 인스턴스를 종료
```
```
정답 ASG는 EC2 인스턴스를 종료.
ALB의 EC2 인스턴스에 대한 healthcheck가 실패하면 비정상으로 표시하고 ASG는 기존 인스턴스를 종료하고 새 인스턴스를 실행합니다.
```

## 18. 여러분의 상사는 애플리케이션이 데이터베이스에 대해 수행하는 분당 요청 수를 기반으로 오토 스케일링 그룹을 스케일링하도록 요청했습니다. 어떻게 해야 할까요?
```
a. CloudWatch 사용자 지정 지표를 생성한 다음 이 지표에 대한 CloudWatch 경보를 생성하여 ASG를 스케일링
b. 정중하게 불가능하다고 답변
c. 세부 모니터링을 활성화한 다음 CloudWatch 경보를 생성하여 ASG를 스케일링
```
```
정답 a.
app<->database에 대한 분당 요청 수에 CloudWatch 지표는 없기 때문에 사용자 지정 지표를 생성해야 합니다.
```

## 19. 오토 스케일링 그룹 (ASG)에서 관리하는 EC2 인스턴스 플릿이 호스팅하는 웹 애플리케이션이 있습니다. 여러분은 애플리케이션 로드 밸런서 (ALB)를 통해 이 애플리케이션을 노출하고 있습니다. EC2 인스턴스와 ALB는 모두 다음 CIDR 192.168.0.0/18을 사용하여 VPC에 배포됩니다. ALB만 포트 80에서 액세스할 수 있도록 EC2 인스턴스의 보안 그룹을 구성하려면 어떻게 해야 할까요
```
a. 포트 80, 0.0.0.0/0 소스 인바운드 규칙 추가
b. 포트 80, 192.168.0.0./18 소스 인바운드 규칙 추가
c. 포트 80, ALB SG 소스 인바운드 규칙 추가
d. ALB에서 SSL 인증서 로드
```
```
정답 c.
```

## 20. eu-west-2 리전에서 실행 중인 오토 스케일링 Configured가 있으며 eu-west-2a 및 eu-west-2b 가용 영역 두 개를 생성하도록 구성되어 있습니다. 현재 eu-west-2a에서 EC2 인스턴스 3개와 eu-west-2b에서 EC2 인스턴스 4개가 실행 중입니다. ASG가 곧 축소됩니다. 어떤 EC2 인스턴스가 종료될까요?
```
a. 임의의 eu-wast-2a 인스턴스
b. 가장 오래된 LT 버전의 eu-wast-2a 인스턴스
c. 임의의 eu-wast-2b 인스턴스
d. 가장 오래된 LT 버전의 eu-wast-2b 인스턴스
```
```
정답 b.
ASG는 많은 인스턴스가 있는 AZ 내에서 가장 오래된 LT 버전의 인스턴스를 먼저 종료한다.
```

## 21. 애플리케이션은 애플리케이션 로드 밸런서 (ALB) 및 오토 스케일링 그룹과 함께 배포됩니다. 현재 ASG를 수동으로 스케일링하고 EC2 인스턴스에 대한 평균 연결 수가 약 1000개인지 확인하는 스케일링 정책을 정의하려고 합니다. 어떤 스케일링 정책을 사용해야 할까요?
```
a. 단순 스케일링 정책
b. 단계 스케일링 정책
c. 대상 추적 정책
d. 예약 스케일링 정책
```
```
정답 c. 
EC2 인스턴스에 대한 평균적인 지표를 기준으로 사용하는 정책은 대상 추적정책이다.
https://docs.aws.amazon.com/ko_kr/autoscaling/ec2/userguide/as-scaling-target-tracking.html
```

## 22. 오토 스케일링 그룹 (ASG)가 관리하는 EC2 인스턴스에서 호스팅되는 애플리케이션이 갑자기 트래픽 급증을 수신하여 ASG가 스케일링되고 새 EC2 인스턴스가 시작되었습니다. 트래픽은 지속적으로 증가하지만 ASG는 새 EC2 인스턴스를 즉시 시작하지 않고 5분 후에 시작합니다. 이 동작이 가능한 원인은 무엇일까요?
```
a. 쿨다운 기간
b. 수명주기 후크
c. 대상추적 정책
d. Launch Template
```
```
정답 a.
ASG는 스케일링 직후 쿨다운 기간이 있으며 이 기간 동안에는 EC2 인스턴스를 시작하거나 종료하지 않으며 메트릭이 안정화될 시간을 제공
```

## 23. 여러분의 회사에는 지난 달에 임의의 EC2 인스턴스가 갑자기 충돌한 오토 스케일링 그룹 (ASG)이 있습니다. ASG가 비정상 EC2 인스턴스를 종료하고 새 EC2 인스턴스로 교체할 때, EC2 인스턴스가 충돌하는 이유를 알아낼 수 없었습니다. 문제를 해결하고 비정상 인스턴스가 ASG에 의해 종료되는 것을 방지하기 위해 어떻게 해야할까요?
```
a. 종료하기 전에 Lambda를 사용하여 EC2 인스턴스 일시 중지
b. ASG 라이프사이클 훅을 사용하여 종료 중 상태의 EC2 인스턴스를 일시 중지
c. CloudWatch Logs를 사용하여 문제 해결
```
```
b. 
https://docs.aws.amazon.com/ko_kr/autoscaling/ec2/userguide/lifecycle-hooks.html
https://brunch.co.kr/@alden/65
```