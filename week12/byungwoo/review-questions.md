# [AWS 공인 솔루션스 아키텍트 – 어소시에이트 SAA-C02 연습문제](https://www.udemy.com/course/aws-saa-c02/) 어소시에이트 연습문제 2 오답 풀이/해설

## 1.
DevOps팀은 퍼블릭 서브넷과 프라이빗 서브넷이 있는 VPC에서 2계층 애플리케이션을 프로비저닝하고 있습니다. 이 팀은 퍼블릭 서브넷에서 NAT 인스턴스 또는 NAT 게이트웨이를 사용하여 프라이빗 서브넷의 인스턴스가 인터넷에 대한 IPv4 트래픽을 시작할 수 있도록 지원하려고 하지만 NAT 인스턴스와 NAT 게이트웨이에 사용할 수 있는 구성 옵션과 관련하여 몇 가지 기술적 지원이 필요합니다.
다음 중 올바른 옵션은 무엇입니까?(3개 선택)
- (선택) NAT 게이트웨이는 포트 전달을 지원합니다.
- 보안 그룹은 NAT 게이트웨이와 연관 될 수 있습니다.
- (선택/정답) NAT 인스턴스는 접속 서버로 사용할 수 있습니다.
- (정답) NAT 인스턴스는 포트 전달을 지원합니다.
- NAT 게이트웨이는 접속 서버로 사용할 수 있습니다.
- (선택/정답) 보안 그룹은 NAT 인스턴스와 연관 될 수 있습니다.
```markdown
# NAT 디바이스 (인스턴스)
- NAT 디바이스를 사용하여 프라이빗 서브넷의 인스턴스를 인터넷(예: 소프트웨어 업데이트용) 또는 기타 AWS 서비스에 연결하는 한편, 인터넷에서 해당 인스턴스와의 연결을 못하도록 할 수 있습니다.
- NAT 디바이스는 주소 변환과 포트 변환을 모두 담당합니다.
```

## 2.
회사는 신규 개발자를 위한 교육 워크샵을 진행하고 있습니다. Amazon S3에 대한 평가 연습의 일환으로, 새로운 개발자들은 S3에 저장된 객체에 대한 잘못된 스토리지 클래스 수명 주기 전환을 판별하도록 요청 받았습니다.
아래 옵션에서 잘못된 수명의 전환은 무엇입니까? (2 개 선택)
- (정답) S3 One Zone-IA -> S3 Standard-IA
- S3 Standard-IA -> S3 Intelligent-Tiering
- (선택/정답) S3 Intelligent-Tiering -> S3 Standard
- (선택) S3 Standard-IA -> S3 One Zone-IA
- S3 Standard -> S3 Intelligent-Tiering
```markdown
# 해설
- 액세스가 적고 비용이 낮아지는 순서로 옮길 수 있고 그 반대로는 불가하다고 이해하면 된다.
- S3 Standard-IA가 S3 One Zone-IA 보다 액세스 빈도가 낮고 비용이 낮아진다.

# S3 종류
## S3 Standard
- 모든 데이터 유형에 적합한 범용 스토리지로, 대개 자주 액세스하는 데이터에 사용됨
## S3 Intelligent - Tiering
- 액세스 패턴을 알 수 없거나 액세스 패턴이 변경되는 데이터에 대해 자동 비용 절감 효과 제공
## S3 Standard - Infrequent Access
- 라이브 상태가 된 지 오래되었지만 밀리초 단위 액세스 성능이 요구되는 자주 액세스하지 않는 데이터용
## S3 One Zone - Infrequent Access
- 밀리초 단위 액세스 성능이 요구되는 다시 생성 가능한 자주 액세스하지 않는 데이터용
## S3 Glacier
- 검색 옵션이 1분부터 12시간까지인 장기적인 백업 및 아카이브용
## S3 Glacier Deep Archive
- 일년에 한두 번 액세스하고 12시간 이내에 복원할 수 있는 장기적인 데이터 아카이빙용
```
![img.png](https://lh4.googleusercontent.com/gNmh9sIBClNb1OMBBEkwOfzfi5E3Ah_I1CtKPFzvTcBXA6sgvBbeD5trN7IGCQsEOJNuVEFpBjwmNac6BTK0pgnNbWomLNzEcCP3qehSu25_Rwlwvn-M6IkGn4XAwErzpy51lhtW)
![img.png](https://lh4.googleusercontent.com/FeZOW98VD4ErnRuxJFrUbs9DiCahasIXfTns_7Rlfa6DJsM_otbCBm-kSAorKbzHYDKG0uEWYGo9ayITDcYJOx226YsSHF_FGAdhOp49UVHXQB7W6OOILc6550kDgZsHltoEB-_b)


## 3.
웹 애플리케이션에는 항상 최소 6개의 EC2 인스턴스가 실행되어야 합니다. 애플리케이션을 아시아 태평양(서울) 리전의 3개의 가용 영역(ap-northeast-2a, ap-northeast-2b 및 ap-northeast-2c)에 배포해야 합니다. 시스템은 하나의 가용 영역을 손실할 때까지 내결함성을 유지해야 합니다.
다음 중 시스템의 내결함성을 유지하는 가장 비용 효율적인 솔루션은 무엇입니까?
- (정답) ap-northeast-2a의 인스턴스 3개, ap-northeast-2b의 인스턴스 3개, ap-northeast-2c의 인스턴스 3개
- ap-northeast-2a의 인스턴스 6개, ap-northeast-2b의 인스턴스 6개, ap-northeast-2c의 인스턴스 6개
- ap-northeast-2a의 인스턴스 6개, ap-northeast-2b의 인스턴스 6개, ap-northeast-2c의 인스턴스 0개
- (선택) ap-northeast-2a의 인스턴스 2개, ap-northeast-2b의 인스턴스 2개, ap-northeast-2c의 인스턴스 2개
```markdown
- 키워드:  최소 6개의 인스턴스, 가용 영역을 손실, 내결함성(fault tolerance), 비용 효율적
- '최소 6개의 인스턴스', '비용 효율적' 키워드를 파악하지 못하고 2-2-2가 아닌 3-3-3 인스턴스를 선택함
```

## 4.
회사가 기존 워크로드의 상당 부분을 AWS 클라우드로 이전했으며, 현재 모든 부서에서 일부 AWS 솔루션을 사용하고 있습니다. 이러한 변경으로 인해 회사의 유연성이 향상되었지만 DevOps 팀은 여전히 IT 보안을 강화해야 합니다. 이 팀은 안전한 호스트 솔루션을 위해 고가용성 아키텍처를 지원하고자 합니다.
다음 중 추천할 수 있는 옵션은 무엇입니까?
- 탄력적 IP를 생성하여 ASG(Auto Scaling 그룹)가 관리하는 접속 호스트인 모든 EC2 인스턴스에 할당합니다.
- (정답) ASG(Auto Scaling 그룹)에서 관리하는 접속 호스트인 EC2 인스턴스에 연결하는 퍼블릭 Network Load Balancer를 생성합니다.
- ASG(Auto Scaling 그룹)에서 관리하는 접속 호스트인 EC2 인스턴스 집합에 대한 VPC 엔드 포인트를 생성합니다.
- (선택) ASG(Auto Scaling 그룹)에서 관리하는 접속 호스트인 EC2 인스턴스에 연결하는 퍼블릭 Application Load Balancer를 생성합니다.
```markdown
- 키워드: 보안, 접속 호스트
- 접속 호스트 EC2 인스턴스에 연결 -> SSH 연결이 필요하다고 유추할 수 있는가?

# 공식 해설
VPC 환경에 접속 호스트(접속 호스트)를 포함하면 환경을 인터넷에 노출시키지 않고 Linux 인스턴스에 안전하게 연결할 수 있습니다. 접속 호스트를 설정한 후 Linux에서 Secure Shell(SSH) 연결을 통해 VPC 내 다른 인스턴스에 액세스할 수 있습니다. 또한 접속 호스트는 미세 조정된 수신 제어를 제공하는 보안 그룹으로 구성됩니다.

Network Load Balancer는 개방형 시스템 간 상호 연결(OSI) 모델의 네 번째 레이어에서 작동합니다.

ALB (Application Load Balancer)는 요청 수준 (계층 7)에서 작동하고 트래픽을 대상 (EC2 인스턴스, 컨테이너, IP 주소 및 Lambda)으로 라우팅합니다. HTTP 및 HTTPS 트래픽의 고급 로드 밸런싱에 이상적인 Application Load Balancer는 마이크로 서비스 및 컨테이너 기반 애플리케이션을 포함한 최신 애플리케이션 아키텍처를 제공하는 고급 요청 라우팅을 제공합니다. ALB는 레이어7 인 HTTP 트래픽만 지원하지만 SSH 프로토콜은 TCP를 기반으로 하며 레이어4입니다. 따라서 Application Load Balancer가 작동하지 않습니다.
```

## 5.
엔지니어링팀은 Amazon CloudWatch 경보를 사용하여 EC2 인스턴스가 손상된 경우 자동으로 복구하려고 합니다. 팀은 주제별 전문 지식을 제공하기 위해 솔루션 아키텍트로 귀하를 고용했습니다.
다음 중 자동 복구 프로세스에 대해 올바른 설명은 무엇입니까? (2 개 선택)
- (정답) 복구된 인스턴스는 인스턴스 ID, 프라이빗 IP 주소, 탄력적 IP 주소 및 모든 인스턴스 메타 데이터를 포함하여 원래 인스턴스와 동일합니다.
- (정답) 인스턴스에 퍼블릭 IPv4 주소가 있는 경우 복구 후 퍼블릭 IPv4 주소를 유지합니다.
- (선택) 종료된 EC2 인스턴스는 인스턴스 시작 시 구성된 경우 복구 할 수 있습니다.
- (선택) 인스턴스에 퍼블릭 IPv4 주소가 있는 경우 복구 후 퍼블릭 IPv4 주소를 유지하지 않습니다.
- 인스턴스 복구 중에는 인스턴스를 재부팅 하는 동안 인스턴스가 마이그레이션 되고 메모리에 있는 모든 데이터가 유지됩니다.
```markdown
# 공식 해설
사용자는 Amazon EC2 인스턴스를 모니터링하고 기본 하드웨어 장애나 복구에 AWS 개입이 필요한 문제로 인해 인스턴스가 손상된 경우 인스턴스를 자동으로 복구하는 Amazon CloudWatch 경보를 만들 수 있습니다. 종료한 인스턴스는 복구할 수 없습니다. 복구된 인스턴스는 인스턴스 ID, 프라이빗 IP 주소, 탄력적 IP 주소 및 모든 인스턴스 메타데이터를 포함하여 원본 인스턴스와 동일합니다. 손상된 인스턴스가 배치 그룹에 있다면, 복구된 인스턴스는 배치 그룹에서 실행됩니다.

# 인스턴스 복구
- 인스턴스의 기본 구성을 사용하거나 Amazon CloudWatch 경보를 생성하여 인스턴스를 자동으로 복구할 수 있습니다.
- 종료한 인스턴스는 복구할 수 없습니다.
- 복구된 인스턴스는 인스턴스 ID, 프라이빗 IP 주소, 탄력적 IP 주소 및 모든 인스턴스 메타데이터를 포함하여 원본 인스턴스와 동일합니다.

# 참조
- https://docs.aws.amazon.com/ko_kr/AWSEC2/latest/UserGuide/ec2-instance-recover.html
- https://docs.aws.amazon.com/ko_kr/AWSEC2/latest/UserGuide/UsingAlarmActions.html#AddingRecoverActions
```

## 6.
AWS Lambda를 서버리스 컴퓨팅 서비스로 사용하는 새로운 API 게이트웨이 서비스를 시작했습니다.
API 엔드 포인트는 어떤 유형의 프로토콜에 노출됩니까?
- (정답) HTTPS
- (선택) HTTP
- HTTP/2
- WebSocket
```markdown
- 해설: Amazon API Gateway를 통해 생성된 모든 API는 HTTPS 엔드포인트만 제공합니다.
```

## 7.
S3 버킷에 재무 데이터를 저장하는 온라인 거래 애플리케이션에는 매월 오래된 데이터를 Glacier로 이동하는 수명 주기 정책이 있습니다. 언제든지 감사가 발생할 수 있는 엄격한 규정 준수 요건이 있으며, 모든 상황에서 15분 이내에 필요한 데이터를 검색할 수 있어야 합니다. 관리자가 필요할 때 검색 용량을 사용할 수 있는지 확인하고 최대 150MB/s의 검색 처리량을 처리하도록 지시했습니다.
위의 요구 사항을 충족하려면 다음 중 무엇을 해야 합니까? (2개 선택)
- 벌크 검색을 사용하여 재무 데이터에 액세스합니다.
- (정답) 신속한 검색을 사용하여 재무 데이터에 액세스합니다.
- (선택) Amazon Glacier Select를 사용하여 데이터를 검색합니다.
- (정답) 프로비저닝된 검색 용량을 구입합니다.
- (선택) 검색할 재무 데이터 아카이브의 범위 또는 일부를 지정합니다.
```markdown
- 키워드: 매월 오래된 데이터를 Glacier로 이동(아카이브), 15분 이내에 필요한 데이터를 검색, 필요할 때 검색 용량을 사용, 최대 150MB/s의 검색 처리량

# S3 Glacier Archive 검색 옵션
- 표준 검색(Standard): 표준 검색은 보통 3~5시간 이내에 완료됨.
- 대량 검색(Bulk, 벌크): S3 Glacier에서 가장 저렴한 검색 옵션으로 이를 통해 페타바이트 규모의 데이터도 하루 만에 저렴하게 검색할 수 있습니다. 대량 검색은 보통 5~12시간 이내에 완료됨.
- 긴급 검색(Expedited, 신속): 긴급 검색을 사용하면 가장 큰 아카이브(250MB 이상)를 제외하고 모든 아카이브에 대해 보통 1~5분 이내에 데이터에 액세스할 수 있음. 긴급 검색에는 온디맨드와 프로비저닝된 요청이라는 2가지 유형이 있습니다. 온디맨드 요청은 AWS가 검색을 1~5분 이내에 완료할 수 있을 때 이행됩니다. 프로비저닝된 요청은 긴급 검색에 대한 검색 용량을 필요할 때 사용할 수 있도록 합니다.

# 참고
- https://docs.aws.amazon.com/ko_kr/amazonglacier/latest/dev/downloading-an-archive-two-steps.html
- https://arclab.tistory.com/315
```

## 8.
회사의 애플리케이션은 시작 시 데이터베이스 롤오버 스크립트를 실행하는 데 약 10분이 걸리는 서버리스 작업을 사용하여 데이터베이스 서버에 대해 매주 데이터베이스 롤오버를 수행하려고 합니다. 데이터베이스 롤오버는 프로덕션 데이터베이스의 지난 주 데이터를 아카이브하여 데이터베이스를 작게 유지하면서 데이터에 액세스할 수 있도록 합니다.
다음 중 가장 비용 효율적이고 신뢰할 수 있는 솔루션으로 추천할 만한 것은 무엇입니까?
- (선택) AWS Glue 작업 내에서 시간 기반 일정 옵션을 생성하여 매주 자체적으로 호출하고 데이터베이스 롤오버 스크립트를 실행합니다.
- OS 기반 주간 cron 표현식을 통해 데이터베이스 롤오버 스크립트를 실행하도록 EC2 예약 예약 인스턴스를 프로비저닝합니다.
- OS 기반 주간 cron 표현식을 통해 트리거 된 데이터베이스 롤오버 작업을 실행하도록 EC2 스팟 인스턴스를 프로비저닝합니다.
- (정답) 데이터베이스 롤오버 작업을 실행하는 Lambda 함수를 호출하도록 매주 CloudWatch 이벤트 cron 표현식을 예약합니다.
```markdown
- AWS Lambda는 분당 최대 한 번의 빈도에 대한 표준 속도 및 cron 표현식을 지원합니다.
- AWS Glue는 완전히 관리되는 ETL(Extract, Transform and Load) 서비스로, 고객이 분석을 위해 데이터를 쉽게 준비하고 로드할 수 있습니다. AWS Glue 작업은 일괄 ETL 데이터 처리에 사용되며 데이터베이스 롤오버 스크립트를 실행하는 데 적합하지 않습니다.
- 짧은 작업을 위해서 EC2 인스턴스를 프로비저닝하는 것은 서버리스를 쓰는 것보다 저렴하지 않습니다.
```

## 9.
글로벌 IT 회사에는 여러 AWS 계정이 있습니다. 관리자는 효율성을 개선하고 비용을 절감하기 위해 AWS 리소스를 중앙에서 관리하는 솔루션을 구축하려고 합니다. 이를 통해 중앙에서 AWS 리소스를 조달하고 다양한 계정에서 AWS Transit Gateway, AWS License Manager 구성 또는 Amazon Route 53 Resolver rules 같은 리소스를 공유 할 수 있습니다.
이 시나리오에서 어떤 옵션 조합을 구현해야 효율성이 개선되고 비용을 절감할 수 있습니까? (2개 선택)
- (선택/정답) AWS RAM(Resource Access Manager) 서비스를 사용하여 AWS 계정과 리소스를 쉽고 안전하게 공유할 수 있습니다.
- (선택) AWS Control Tower를 사용하여 리소스를 쉽고 안전하게 AWS 계정과 공유할 수 있습니다.
- AWS Identity and Access Management 서비스를 사용하여 리소스를 AWS 계정과 쉽고 안전하게 공유할 수 있는 교차 계정 액세스를 설정할 수 있습니다.
- (정답) AWS Organizations를 사용하여 회사의 모든 계정을 통합합니다.
- AWS ParallelCluster를 사용하여 회사의 모든 계정을 통합합니다.
```markdown
# 해설
- AWS Organizations는 AWS의 워크로드가 증가하고 확장됨에 따라 환경을 중앙에서 관리하는 데 도움이 됩니다.
- AWS Resource Access Manager(RAM)는 고객에게 AWS 계정 또는 AWS Organizations 내에서 리소스를 공유할 수 있는 간단한 방법을 제공합니다. 많은 AWS 고객이 여러 AWS 계정을 사용하여 팀에 관리 및 결제 자율성을 제공합니다. 고객은 이제 중앙 집중식으로 리소스를 생성하고 RAM을 사용하여 여러 계정 간에 공유할 수 있으므로 다중 계정 전략의 이점을 유지하면서 고객의 운영 오버헤드를 줄일 수 있습니다

# 오답
- WS Control Tower는 새롭고 안전한 다중 계정 AWS 환경을 설정하고 관리 할 수있는 가장 쉬운 방법을 제공합니다. AWS 계정 또는 조직 내에서 리소스를 공유하는 것과는 관련이 없습니다. 
```

## 10.
회사는 다양한 계정에 많은 VPC를 보유하고 있으며, 네트워크에서 서로 연결되고 직접 연결을 통해 온프레미스 네트워크에 연결 되어야 하는 다양한 VPC가 있습니다.
추천 솔루션은 무엇입니까?
- VPC 피어링
- PrivateLink
- (선택) VPN Gateway
- (정답) Transit Gateway
```markdown
- 키워드: 많은 VPC, 온프레미스 네트워크에 연결 되어야 하는 다양한 VPC

# AWS Transit Gateway
- AWS Transit Gateway는 중앙 허브를 통해 VPC와 온프레미스 네트워크를 연결합니다. 복잡한 피어링 관계를 제거하여 네트워크를 간소화합니다. 클라우드 라우터 역할을 하므로 새로운 연결을 한 번만 추가하면 됩니다.

# AWS Site-to-Site VPN & VPN Gateway
- Site-to-Site VPN 연결은 AWS 측의 가상 프라이빗 게이트웨이 또는 Transit Gateway와 원격(온프레미스) 측의 고객 게이트웨이(VPN 디바이스를 나타냄) 사이에 두 개의 VPN 터널을 제공
- 가상 프라이빗 게이트웨이(VPN Gateway)는 Site-to-Site VPN 연결의 Amazon 측에 있는 VPN 집선기(connection)입니다. 가상 프라이빗 게이트웨이를 생성하여 Site-to-Site VPN 연결을 생성할 VPC에 연결합니다.

# 참고
- https://dev.classmethod.jp/articles/different-from-vpc-peering-and-transit-gateway/
- https://docs.aws.amazon.com/ko_kr/vpn/latest/s2svpn/how_it_works.html#VPNGateway
```
- AWS Transit Gateway<br>
![img.png](https://lh4.googleusercontent.com/4Dyzf69eQbvhcZkmJ7NQJly7gpIaEjfHIjXH5H0x29VAyDDjibGaUkR32Kan4ctP-bRq_Qi3iSCCFauju1SV46yaN1Hxy_7YKcyZ_30C-fmA82dO0XFaINzo4rEMIjkpDHNbP1_3)
- VPN Gateway<br>
![img.png](https://docs.aws.amazon.com/ko_kr/vpn/latest/s2svpn/images/vpn-how-it-works-vgw.png)
  
## 11.
회사가 온프레미스 데이터 중 일부를 AWS 클라우드로 이전하고 있습니다. DevOps 팀은 인터넷을 통해 원격 온프레미스 네트워크와 Amazon VPC간에 AWS Managed IPSec VPN 연결을 설정했습니다.
다음 중 IPSec VPN 연결에 대한 올바른 구성을 나타내는 것은 무엇입니까?
- (정답) VPN의 AWS 측에서 Virtual Private Gateway를 만들고 온프레미스 측 VPN에서 고객 게이트웨이를 만듭니다.
- (선택) VPN의 AWS 측과 온프레미스 측 모두에 Virtual Private Gateway를 생성합니다.
- VPN의 온프레미스 측에 Virtual Private Gateway를 만들고 VPN의 AWS 측에 고객 게이트웨이를 만듭니다.
- VPN의 AWS 측과 온프레미스 측 모두에 고객 게이트웨이를 생성합니다.
```markdown
- AWS Site-to-Site VPN을 사용하면 Amazon VPC와 고객 원격 온프레미스 네트워크 간의 연결을 생성할 수 있습니다.
- 아래의 그림과 같이 AWS 네트워크에는 Virtual private gateway를 생서하고 고객 온프레미스 네트워크에는 Customer gateway를 생성합니다.

# 참고
- https://docs.aws.amazon.com/ko_kr/vpn/latest/s2svpn/how_it_works.html#VPNGateway
```
![img.png](https://docs.aws.amazon.com/ko_kr/vpn/latest/s2svpn/images/vpn-how-it-works-vgw.png)

## 12.
데이터를 실시간으로 수집, 처리 및 분석하는 분석 애플리케이션은 Kinesis Data Streams를 사용하고 있습니다. 생산자는 소비자가 실시간으로 데이터를 처리하는 동안 지속적으로 데이터를 Kinesis Data Streams로 푸시합니다.
Amazon Kinesis에서 소비자는 결과를 어디에 저장할 수 있습니까?
- (선택) AWS Glue
- (선택/정답) Amazon Redshift
- Glacier Select
- Amazon Athena
```markdown
- Amazon Kinesis Data Streams를 사용하여 대규모 데이터 레코드 스트림을 실시간으로 수집하고 처리할 수 있습니다.
- 처리된 레코드를 대시보드로 보내거나, 알림을 생성하는 데 사용하거나, 요금 및 광고 전략을 동적으로 변경하거나, 다른 여러 AWS 제품에 데이터를 보낼 수 있습니다.
- 아래의 그림과 같이 S3, DynamoDB, Redshift, EMR, Kinesis FIrehose 등으로 내보낼 수 있습니다.
```
![img.png](https://lh4.googleusercontent.com/_riQPUih9MUa0uqqfzX1S80_YaktP8hTj5Uk6XwcKfYt0iWLKgo614_2xw6KviP104W-BeD4Q5ZvstfZhjZFoGZxgMJbFseTH9qYtCNYkh3bA08gHcge-pBFxo90I-1kxWyq5gHa)

## 13.
회사는 Amazon S3에 로그 파일을 기록하는 거래 시스템을 사용합니다. 또한 시스템은 거의 실시간으로 이러한 로그 파일을 병렬로 읽으려고 시도합니다. 엔지니어링팀은 거래 시스템이 기존 로그 파일을 덮어쓴 다음 덮어쓴 특정 로그 파일을 읽으려고 할 때 데이터 불일치를 관찰했습니다.
다음 중 주어진 시나리오를 가장 잘 설명한 옵션은 무엇입니까?
- (정답) 프로세스는 기존 객체를 대체하고 즉시 읽으려고 합니다. 변경 사항이 완전히 전파될 때까지 Amazon S3가 이전 데이터를 반환 할 수 있습니다.
- 프로세스는 기존 객체를 대체하고 즉시 읽으려고 합니다. 변경 사항이 완전히 전파될 때까지 Amazon S3가 새 데이터를 반환 할 수 있습니다.
- (선택) 프로세스는 기존 객체를 대체하고 즉시 읽으려고 합니다. 변경 사항이 완전히 전파될 때까지 Amazon S3는 항상 이전 데이터를 반환합니다.
- 프로세스는 기존 객체를 대체하고 즉시 읽으려고 합니다. 변경 사항이 완전히 전파될 때까지 Amazon S3는 데이터를 반환하지 않습니다.
```markdown
- 키워드: 병렬로 읽으려고 시도
- Amazon S3에서는 AWS 데이터 센터 내의 여러 서버로 데이터를 복제함으로써 고가용성을 구현합니다. PUT 요청이 성공하면 데이터가 안전하게 저장됩니다.
- 그러나 변경 사항에 대한 정보를 Amazon S3로 복제해야 하는데 이 작업에는 일정 시간이 걸릴 수 있으며 변경사항이 전파되기 전까지는 불완전한 데이터가 아닌 이전 데이터를 반환합니다.
```

## 14.
데이터 센터의 재해로부터 서비스 중단을 방지하기 위해 동기식 복제 모드를 갖춘 데이터베이스 기술을 구현했습니다. 따라서 데이터베이스는 두 개의 가용 영역에서 두 개의 EC2 인스턴스에 배포됩니다. EC2 인스턴스를 퍼블릭 서브넷에 배포하려면 데이터베이스를 공개적으로 사용할 수 있어야 합니다. 복제 프로토콜은 현재 EC2 퍼블릭 IP 주소를 사용합니다.
복제 비용을 절감하려면 어떻게 해야 합니까?
- (선택) Elastic Fabric Adapter를 사용합니다.
- 두 EC2 인스턴스간에 Private Link를 생성합니다.
- (정답) 복제에 EC2 인스턴스 프라이빗 IP 사용합니다.
- EC2 인스턴스에 탄력적 IP를 할당하고 복제에 사용합니다.
```markdown
- 비용은 두 EC2 인스턴스 간의 트래픽이 퍼블릭 인터넷을 통해 전송되므로 높은 비용이 발생한다는 것입니다. 프라이빗 IP 주소를 사용하여 같은 가용 영역 내에서 트래픽이 이동하면 데이터 전송 요금은 발생하지 않습니다. 서로 다른 가용 영역을 사용하는 경우에는 데이터 전송 요금이 발생하나 그 비용을 최소화 할 수 있습니다.
- Elastic Fabric Adapter(EFA)는 Amazon EC2 인스턴스에 연결하여 고성능 컴퓨팅(HPC) 및 기계 학습 애플리케이션의 속도를 높일 수 있는 네트워크 디바이스입니다. 인스턴스 복제와는 관련이 없습니다.
- AWS PrivateLink는 Virtual Private Cloud(VPC)와 지원되는 AWS 서비스, 다른 AWS 계정에서 호스팅하는 서비스 및 지원되는 AWS Marketplace 서비스 간에 프라이빗 연결을 설정합니다. 인스턴스 복제와는 관련이 없습니다.
```

## 15.
신생 기업에는 웹 응용 프로그램을 호스팅하는 EC2 인스턴스가 있습니다. 향후 몇 개월 이내에 사용자 수가 증가할 것으로 예상되므로 수요에 대처하려면 AWS 아키텍처에 탄력성과 확장성을 더해야 합니다.
다음 중 주어진 시나리오에 대해 위의 요구 사항을 충족할 수 있는 옵션은 무엇입니까? (2개 선택)
- (선택/정답) EC2 인스턴스 두 개를 설정한 다음 ELB(Elastic Load Balancer) 뒤에 배치합니다.
- (정답) 두 개의 EC2 인스턴스를 설정하고 Route 53을 사용하여 가중치 라우팅 정책을 기반으로 트래픽을 라우팅합니다.
- 시작 템플릿(Launch Templates)를 사용하여 배포하고 AWS Glue와 통합되는 두 개의 EC2 인스턴스를 설정합니다.
- EC2 인스턴스 뒤에 AWS WAF를 설정합니다.
- (선택) EC2 인스턴스 앞에 S3 캐시를 설정합니다.
```markdown
- 가중치 라우팅 정책과 같은 Route53에 정책을 생성하여 트래픽을 2개 이상의 EC2 인스턴스로 균등하게 분산할 수도 있습니다. (Route53 -> EC2 연결도 가능!)
- 정적 컨텐츠를 서빙한다는 내용은 따로 없었기 때문에 S3 캐시와는 관련이 없음
```