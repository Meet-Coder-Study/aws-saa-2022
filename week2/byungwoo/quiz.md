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