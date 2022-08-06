# AWS 공인 솔루션스 아키텍트 – 어소시에이트 SAA-C02 연습문제 5 오답노트
## 1.
회사에서 IoT 데이터를 위한 실시간 데이터 분석 툴을 구축하기 위해 추진하고 있습니다. IoT 데이터는 Kinesis Data Streams로 유입되어 Kinesis Firehose의 전달 스트림의 소스가 됩니다. 이제 엔지니어링 팀에서 다른 장치 집합의 IoT 데이터를 동일한 Firehose 전송 스트림으로 전송하도록 Kinesis 에이전트를 구성했습니다. 그들은 데이터가 예상대로 Firehose에 도달하지 못하고 있다는 것을 확인 했습니다.
다음 중 이 문제의 가장 타당한 근본 원인으로 간주할 수 있는 옵션은 무엇입니까?
- (선택) Kinesis Firehose 전송 스트림이 한도에 도달했으며 수동으로 확장해야 합니다.
- Kinesis Agent는 Kinesis Firehose가 아닌 Kinesis Data Streams에만 쓸 수 있습니다.
- (정답) Kinesis 에이전트는 전송 스트림 소스가 이미 Kinesis Data Stream으로 설정된 Kinesis Firehose에 쓸 수 없습니다.
- 구성 오류로 인해 Kinesis Agent가 전송한 데이터가 손실됩니다.
```markdown
- Kinesis 데이터 스트림이 Firehose 전송 스트림의 소스로 구성되면 Firehose에 다른 Kinesis Agent가 Put 작업을 할 수 없음
```

## 2.
현재 일하고 있는 회사가 Amazon S3 사용을 평가하고 더 많은 스토리지 하드웨어를 확보하는 데 필요한 총 소유 비용 (TCO) 분석을 수행했습니다. 그 결과 모든 1,000명의 직원에게 개인 문서를 저장하기 위해 Amazon S3를 사용할 수있는 액세스 권한이 부여되었습니다.
다음 중 회사 AD 또는 LDAP 디렉토리의 Single Sign-On 기능을 통합하고 S3 버킷의 지정된 사용자 폴더로 각 사용자의 액세스를 제한하는 솔루션을 설정할 수 있도록 고려해야 할 사항은 무엇입니까? (2개 선택)
- Amazon WorkDocs를 사용하여 S3의 각 사용자를 지정된 사용자 폴더에 매핑하여 개인 문서에 액세스 합니다.
- OKTA, OneLogin 등과 같은 타사 Single Sign-On 솔루션 사용합니다.
- (선택) S3 버킷의 폴더에 액세스 해야 하는 회사 디렉토리의 각 1,000명의 사용자에 대해 일치하는 IAM 사용자를 설정합니다.
- (선택/정답) 버킷에 액세스하도록 IAM 역할 및 IAM 정책을 구성합니다.
- (정답) 페더레이션 프록시 또는 자격 증명 공급자를 설정하고 AWS Security Token Service를 사용하여 임시 자격을 생성합니다.
```markdown
- STS를 사용하면 AWS 리소스에 대한 액세스를 제어할 수 있는 임시 보안 자격 증명을 생성하하여 신뢰받는 사용자에게 제공할 수 있음. 주로 권장되는 방법.
- 1,000명의 사용자에 대해 일치하는 IAM 사용자를 설정하는 것은 비효율적. 차라리 AD, LDAP을 통합하는 것이 좋음.
```

## 3.
회사가 IT 인프라를 AWS Cloud로 이전하고 있으며 컴플라이언스 지침을 충족하기 위해 Amazon S3에 적절한 데이터 보호 메커니즘을 적용하려고 합니다. 운영팀 S3의 암호화 기능을 구현하려고 합니다.
보기에서 잘못된 옵션은 무엇입니까?
- (선택) S3는 HTTPS (TLS)를 사용하여 전송 중인 데이터를 암호화 할 수 있습니다.
- S3는 클라이언트 측 암호화를 사용하여 유휴 데이터를 보호 할 수 있습니다.
- (정답) S3는 서버 측 암호화를 사용하여 객체 메타데이터를 암호화 할 수 있습니다.
- S3는 서버 측 암호화를 사용하여 유휴 데이터를 보호 할 수 있습니다.
```markdown
- 유휴 데이터 = data at rest (while it is stored on disks in Amazon S3 data centers)
- 서버 측 암호화는 저장된 데이터를 보호하기 위한 것입니다. 서버 측 암호화는 객체 메타데이터가 아니라 객체 데이터만 암호화합니다
```

## 4.
회사는 AWS 클라우드로 마이그레이션하려는 온프레미스 인프라에서 호스팅되는 웹 애플리케이션을 보유하고 있습니다. 관리자가 마이그레이션 프로세스가 진행되는 동안 다운타임이 발생하지 않도록 하라고 지시했습니다. 이를 위해 팀은 트래픽의 50%를 AWS의 새 애플리케이션으로, 나머지 50%는 온프레미스 인프라에서 호스팅되는 애플리케이션으로 전환하기로 결정했습니다. 마이그레이션이 완료되고 애플리케이션이 문제 없이 작동하면 AWS로 완전히 전환됩니다.
다음 중 위의 요구 사항을 충족하기 위해 구현할 수 있는 솔루션은 무엇입니까? (2개 선택)
- 가중치 기반 대상 그룹과 함께 네트워크 로드 밸런서를 사용하여 온프레미스 애플리케이션과 AWS 호스팅 애플리케이션 간의 트래픽을 전환하십시오. 트래픽의 50%를 AWS의 새 애플리케이션으로 전환하고 다른 50%를 온프레미스 인프라에서 호스팅 되는 애플리케이션으로 전환하십시오.
- AWS Global Accelerator를 사용하여 온 프레미스 애플리케이션과 AWS 호스팅 애플리케이션간에 HTTP 및 HTTPS 트래픽을 전환하고 비율을 조정하십시오. 온 프레미스 네트워크에 AnyCast 고정 IP 주소가 있고 Direct Connect Gateway를 통해 VPC에 연결되어 있는지 확인하십시오.
- (선택) 온프레미스 애플리케이션과 AWS 호스팅 애플리케이션 간의 트래픽을 전환하고 비율을 조정하려면 장애 조치 라우팅 정책과 함께 Route 53을 사용하십시오. 트래픽의 50%를 AWS의 새 애플리케이션으로 전환하고 다른 50%를 온 프레미스 인프라에서 호스팅 되는 애플리케이션으로 전환하십시오.
- (정답) 가중치 기반 대상 그룹과 함께 애플리케이션 Elastic Load Balancer를 사용하여 온프레미스 애플리케이션과 AWS 호스팅 애플리케이션 간의 트래픽을 전환하고 비율을 조정하십시오. 트래픽의 50%를 AWS의 새 애플리케이션으로 전환하고 다른 50%를 온프레미스 인프라에서 호스팅 되는 애플리케이션으로 전환하십시오.
- (선택/정답) 가중 라우팅 정책과 함께 Route 53을 사용하여 온프레미스 애플리케이션과 AWS 호스팅 애플리케이션 간의 트래픽을 전환하십시오. 트래픽의 50%를 AWS의 새 애플리케이션으로 전환하고 다른 50%를 온프레미스 인프라에서 호스팅 되는 애플리케이션으로 전환하십시오.
```markdown
- ELB에서도 TargetGroup을 IP 주소 유형으로 설정하면 온프레미스 리소스로 로드밸런싱 할 수 있음
- Route53 장애조치 라우팅 정책은 온프레미스-AWS 간 트래픽 전환/분산과는 관계 없음
```

## 5.
회사는 몇 가지 데이터베이스 메트릭을 모니터링한 후 문제가 발생할 경우 운영 팀에 이메일 알림을 전송해야 합니다.
이 요구 사항을 충족할 수 있는 AWS 서비스는 무엇입니까? (2개 선택)
- (선택/정답) Amazon CloudWatch
- Amazon Simple Queue Service (SQS)
- (정답) Amazon Simple Notification Service (SNS)
- (선택) Amazon Simple Email Service
- Amazon Simple Workflow Service (SWF)
```markdown
- CloudWatch Alarm 대상: EC2(중지/종료/재부팅/복구), Auto Scaling(증설/축소), SNS(알림)
- SES는 대량 이메일 발송. 주로 마케팅용.
```

## 6.
회사에서는 API 개발을 위한 글로벌 협업 플랫폼이 되고자 합니다. 제품팀은 API 구축의 각 단계를 간소화하고 협업을 간소화하여 더 나은 API를 만들 수 있는 기능을 구축하려고 합니다. 조사의 일환으로 제품 팀은 플랫폼을 사용하여 개발한 API를 통해 상태 저장 및 상태 비저장 클라이언트-서버 통신을 모두 지원해야 하는 시장의 필요성을 파악했습니다. 당신은 AWS API Gateway를 사용하여 이러한 시장의 요구를 충족하기 위한 개념 증명(Proof-of-Concept)을 구축하기 위해 AWS 솔루션 아키텍트로 회사에 고용되었습니다.
다음 중 시작 시 권장되는 항목은 무엇입니까?
- API Gateway는 상태 저장 클라이언트-서버 통신을 지원하는 RESTful API를 생성하고, API Gateway는 WebSocket 프로토콜을 준수하는 WebSocket API도 생성합니다. 이 API는 클라이언트와 서버 간의 상태 비저장, 전이중 통신을 가능하게 합니다.
- (정답) API Gateway는 상태 비저장 클라이언트-서버 통신을 지원하는 RESTful API를 생성하고, API Gateway는 WebSocket 프로토콜을 준수하는 WebSocket API도 생성합니다. 이 API는 클라이언트와 서버 간의 상태 저장, 전이중 통신을 가능하게 합니다.
- API Gateway는 상태 저장 클라이언트-서버 통신을 지원하는 RESTful API를 생성하고, API Gateway는 WebSocket 프로토콜을 준수하는 WebSocket API도 생성합니다. 이 API는 클라이언트와 서버 간의 상태 저장, 전이중 통신을 지원합니다.
- (선택) API Gateway는 상태 비저장 클라이언트-서버 통신을 지원하는 RESTful API를 생성하고, API Gateway는 WebSocket 프로토콜을 준수하는 WebSocket API도 생성합니다. 이 API는 클라이언트와 서버 간의 상태 비저장 전이중 통신을 지원합니다.
```markdown
- AWS API Gateway는 상태 저장(WebSocket) 및 상태 비저장(HTTP 및 REST) API를 모두 지원한다.
- WebSocket은 상태저장, REST API는 상태 비저장
- 전이중 통신(full-duplex communication): 두 지점 사이에서 저옵를 주고 받는 전자 통신 시스템
```

## 7.
Amazon S3 Standard 버킷에 호스팅되는 정적 회사 웹 사이트와 Route 53을 사용하여 등록된 새 웹 도메인 이름이 있습니다. 당신은 회사 웹 사이트를 성공적으로 시작하기 위해 관리자로부터 이 두 서비스를 통합하라는 지시를 받습니다.
Amazon Route 53을 사용하여 Amazon S3 버킷에서 호스팅되는 웹 사이트로 트래픽을 라우팅할 때 필요한 필수 구성 요소는 무엇입니까? (2개 선택)
- 레코드 세트는 "MX" 유형이어야 합니다.
- (정답) 등록된 도메인 네임이어야 합니다.
- (정답) S3 버킷 이름은 도메인 이름과 동일해야 합니다.
- (선택) CORS(Cross-Origin Resource Sharing) 옵션을 S3 버킷에서 사용하도록 설정해야 합니다.
- (선택) S3 버킷은 호스트 영역과 동일한 리전에 있어야 합니다.
```markdown
S3 버킷에서 호스팅되는 웹 사이트로 트래픽을 라우팅하기 위한 필수 구성 요소
- 정적 웹 사이트로 호스팅하도록 구성되어 있는 S3 버킷 (버킷은 도메인 또는 하위 도메인과 이름이 동일)
- 등록된 도메인 이름
- 도메인의 DNS 서비스가 될 Route53
- https://docs.aws.amazon.com/ko_kr/Route53/latest/DeveloperGuide/RoutingToS3Bucket.html

오답
- 한 도메인의 클라이언트 웹 응용 프로그램이 다른 도메인의 리소스와 상호 작용할 때만 CORS 사용
- Route53 서비스가 트래픽을 호스트 영역으로 라우팅하려면 S3 버킷이 호스트 영역과 동일한 리전에 있어야 한다는 제약 조건이 없습니다.
```

## 8.
애플리케이션은 EC2 인스턴스의 Auto Scaling 그룹과 Amazon RDS의 Microsoft SQL Server에서 호스팅 됩니다. 웹 서버와 RDS 간의 모든 전송 데이터를 보호해야 합니다.
다음 중 가장 적합한 솔루션 중 어떤 옵션을 구현해야 합니까? (2개 선택)
- (정답) rds.force_ssl 파라미터를 true로 설정하여 DB 인스턴스에 대한 모든 연결에서 SSL을 사용하도록 합니다. 완료되면 DB 인스턴스를 재부팅 합니다. 포트 443의 트래픽만 허용하도록 RDS의 보안 그룹을 구성합니다.
- (선택) 포트 443과의 트래픽만 허용하도록 EC2 인스턴스 및 RDS의 보안 그룹 구성합니다.
- AWS Management Console을 사용하여 RDS에서 IAM DB 인증을 활성화합니다.
- TDE (투명한 데이터 암호화)를 활성화하기 위해 해당 DB 인스턴스와 연결된 RDS 옵션 그룹에서 TDE 옵션을 지정합니다.
- (정답) Amazon RDS Root CA 인증서를 다운로드합니다. 인증서를 서버로 가져오고 SSL을 사용하여 RDS에 대한 연결을 암호화하도록 애플리케이션을 구성합니다.
```markdown
SSL을 사용하여 SQL Server DB 인스턴스에 연결하는 방법은 두 가지 (In-flight encryption)
- 모든 연결에 대해 SSL 지정 (DB에서 설정)
  - rds.force_ssl 파라미터를 사용
- 특정 연결 암호화 (클라이언트에서 설정)
  - 특정 클라이언트에서 SSL을 사용하려면, 클라이언트 컴퓨터의 인증서를 획득하고 클라이언트 컴퓨터에서 인증서를 가져온 다음 클라이언트 컴퓨터 연결을 암호화해야 함
- https://docs.aws.amazon.com/ko_kr/AmazonRDS/latest/UserGuide/SQLServer.Concepts.General.SSL.Using.html
 
오답
- TDE(Transparent Data Encryption, 투명한 데이터 암호화)는 주로 전송 중인 데이터가 아니라 SQL Server를 실행하는 DB 인스턴스에서 저장된 데이터를 암호화하는 데 사용 (At rest encryption)
- 포트 443과의 트래픽만 허용하도록 EC2 인스턴스 및 RDS의 보안 그룹 구성하는 것은 DB 인스턴스에 대한 모든 연결을 암호화하는 데에 충분하지 않음
```

## 9.
회사의 비즈니스 연속성 계획의 일환으로 IT 관리자는 EC2 인스턴스에 대한 모든 EBS 볼륨의 자동 백업을 가능한 빨리 설정하도록 지시 했습니다.
모든 EBS 볼륨을 자동으로 백업할 수 있는 가장 빠르고 비용 효율적인 솔루션은 무엇입니까?
- (선택) AWS CLI를 통해 create-snapshot 명령을 호출하여 프로덕션 EBS 볼륨의 스냅샷을 주기적으로 생성하는 예약된 작업을 생성합니다.
- Amazon S3에서 EBS 주기 정책을 사용하여 EBS 볼륨을 자동으로 백업합니다.
- (정답) Amazon DLM(Amazon Data Lifecycle Manager)을 사용하여 EBS 스냅샷 생성을 자동화합니다.
- EBS 볼륨을 데이터 소스로 사용하여 Amazon Storage Gateway를 설정하고 Storage Gateway를 통해 온프레미스 서버에 백업을 저장합니다.
```markdown
Amazon Data Lifecycle Manager
- EBS 스냅샷 및 EBS-backed AMI의 생성, 보존 및 삭제를 자동화할 수 있습니다.
- EBS 볼륨을 백업하기 위해 만든 스냅샷의 생성, 보관, 삭제를 Amazon 데이터 수명 주기 관리자로 자동화할 수 있습니다.
- https://docs.aws.amazon.com/ko_kr/AWSEC2/latest/UserGuide/snapshot-lifecycle.html
```

## 10.
회사에는 지난 몇 달 동안 활용되지 않은 기존 VPC가 있으며 이를 관리자가 온프레미스 데이터 센터와 VPC를 통합하도록 지시했습니다. 이 통합을 VPN으로 수행하려고 합니다.
AWS에서 VPN을 사용하면 얻을 수있는 주요 이점 중 하나는 무엇입니까?
- (선택) 네트워크와 VPC간에 사설 전용 네트워크 연결을 설정할 수 있습니다.
- 프라이빗 IPv4 주소 또는 IPv6 주소를 사용하여 두 VPC간에 트래픽을 라우팅 할 수 있는 두 VPC 간의 네트워킹 연결을 제공합니다.
- (정답) IPSec (IP Security) 또는 TLS (Transport Layer Security) 터널이 있는 보안 및 프라이빗 세션을 사용하여 AWS 클라우드 리소스를 온프레미스 데이터 센터에 연결할 수 있습니다.
- VPC와 퍼블릭 인터넷을 우회하는 온프레미스 데이터 센터로의 비용 효율적인 하이브리드 연결을 제공합니다.
```markdown
- IPsec VPN(Site-to-Site VPN) 혹은 TLS VPN(Client VPN) 연결을 할 수 있음
- https://docs.aws.amazon.com/ko_kr/vpc/latest/userguide/vpn-connections.html

오답
- 네트워크와 VPC간에 사설 '전용' 네트워크 연결을 설정할 수 있습니다 -> VPN이 아닌 AWS Direct Connect 연결의 이점
- 프라이빗 IPv4 주소 또는 IPv6 주소를 사용하여 두 VPC간에 트래픽을 라우팅 할 수 있는 두 VPC 간의 네트워킹 연결을 제공합니다. -> VPC 피어링에 대한 설명
```

## 11.
회사에서는 비용을 절감하기 위해 AWS 클라우드 인프라의 설정을 분석하고 검토하도록 지시했습니다. 또한 회사가 사용 중인 모든 AWS 리소스에 대해 얼마를 지불할 것인지에 대한 견적을 제공해야 합니다.
이 시나리오에서 다음 중 비용이 발생하는 것은 무엇입니까? (2개 선택)
- stopping 된 온디맨드 EC2 인스턴스
- (선택) Amazon VPC 사용
- (정답) running EC2 인스턴스
- 공개 데이터 세트
- (정답) 중지 된 EC2 인스턴스에 연결된 EBS 볼륨
```markdown
- VPC 자체를 생성 및 사용하는 데에는 별도의 비용이 없습니다.
- EBS 스토리지는 계정에 프로비저닝된 스토리지 용량(월별 기가바이트 단위로 측정)에 대해 요금이 청구됩니다. 
- EC2 인스턴스는 실행 중인 동안에만 요금이 발생하지만, 인스턴스에 연결된 EBS 볼륨은 인스턴스가 중지된 경우에도 계속 정보를 유지하고 요금이 발생합니다.
- https://docs.aws.amazon.com/ko_kr/AWSEC2/latest/UserGuide/ec2-instance-lifecycle.html
- https://aws.amazon.com/ko/premiumsupport/knowledge-center/ebs-charge-stopped-instance/
```

## 12.
회사의 데이터 엔지니어링팀이 클릭스트림 데이터를 S3 데이터 레이크의 원시 영역으로 수집하는 워크플로우를 설정했습니다. 팀은 데이터 레이크의 원시 영역에 대해 몇 가지 SQL 기반 데이터 무결성 검사를 실행하려고 합니다.
솔루션이 비용 효율적이고 유지 관리가 쉽도록 이 사용 사례에 대해 어떤 AWS 서비스를 권장합니까?
- (선택) 증분 원시 영역 데이터를 시간 단위로 Redshift에 로드하고 SQL 기반 무결성 검사를 실행합니다.
- 증분 원시 영역 데이터를 RDS에 시간 단위로 로드하고 SQL 기반 무결성 검사를 실행합니다.
- 증분 원시 영역 데이터를 시간 단위로 EMR 기반 스파크 클러스터에 로드하고 SparkSQL을 사용하여 SQL 기반 무결성 검사를 실행합니다.
- (정답) Glue 크롤러를 사용하여 원시 영역 데이터를 Glue 카탈로그에서 일회성 프로세스로 읽은 다음 Athena를 사용하여 SQL 기반 무결성 검사를 실행합니다.
```markdown
- AWS Glue 콘솔을 사용하여 데이터를 발견하고 변환하며 검색 및 쿼리가 가능하도록 만들 수 있습니다. 콘솔은 기초 서비스를 호출하여 필요한 작업을 조직하고 데이터를 변환합니다. 크롤러를 사용하여 테이블로 AWS Glue 데이터 카탈로그를 채웁니다. 
- Redshift는 대규모 데이터 세트 저장 및 분석을 위해 설계된 페타바이트 규모의 클라우드 기반 데이터 웨어하우스 제품입니다. Redshift 클러스터 크기를 유지 및 모니터링해야 하고, 정기적으로 데이터를 소비하는 프로세스를 설정하는 데 상당한 개발 시간이 필요하므로 이 옵션은 제외됩니다.
```

## 13.
EC2에서 호스팅 되는 애플리케이션은 SQS 대기열에서 메시지를 소비하고 프로세스가 완료되면 SNS와 통합되어 이메일을 보냅니다. 운영팀은 5개의 주문을 받았지만 몇 시간 후 받은 편지함에 20개의 이메일 알림이 표시되었습니다.
다음 중 이 문제의 가능한 원인은 무엇입니까?
- (정답) 웹 애플리케이션이 메시지를 처리 한 후 SQS 대기열에서 메시지를 삭제하지 않습니다.
- (선택) 웹 애플리케이션은 긴 폴링으로 설정되어 메시지가 두 번 전송됩니다.
- 웹 애플리케이션에는 SQS 대기열에서 메시지를 사용할 권한이 없습니다.
- 웹 애플리케이션이 짧은 폴링으로 설정되어 일부 메시지가 수신되지 않습니다.
```markdown
- 메시지를 삭제하려면, 메시지를 성공적으로 수신하여 처리하였으므로 이제 메시지가 필요없다는 것을 승인하는 별도의 요청을 전송해야 합니다.
- 긴 폴링은 빈 응답을 제거하여 SQS 사용 비용을 줄이는 데 도움이 됩니다. 긴 폴링으로 구성된 SQS 대기열에서 두 번 전송되는 메시지는 거의 없습니다.
```

## 14.
회사는 새로운 개발자에게 DynamoDB에 대한 모든 액세스 권한이 할당된 사고가 보고 된 후 보안 모범 사례를 검토하려고 합니다. 개발자는 새로운 기능을 구축하는 동안 실수로 프로덕션 환경에서 몇 개의 테이블을 삭제했습니다.
이러한 문제가 재발하지 않도록 이 문제를 해결하는 가장 효과적인 방법은 무엇입니까?
- 조직의 모든 IAM 사용자에 대한 전체 데이터베이스 액세스 권한을 제거합니다.
- 루트 사용자만 조직에서 전체 데이터베이스 액세스 권한을 가져야 합니다.
- (선택) 관리자는 새로운 개발자의 IAM 사용자 각각에 대한 권한을 검토하여 그러한 사고가 재발하지 않도록 해야 합니다.
- (정답) 권한 경계를 사용하여 직원이 IAM 보안 주체에게 부여 할 수있는 최대 권한을 제어합니다.
```markdown
- 키워드: 새로운 개발자에게 DynamoDB에 대한 모든 액세스 권한이 '할당'된 사고
- 권한 경계를 도입해야 함
```

## 15.
게임 회사는 주요 데이터베이스 서비스로 Amazon Aurora를 사용합니다. Amazon Aurora의 빠른 페일오버 기능과 스토리지 내구성으로 인해 온라인 게임 서비스의 기술적 장애가 최소화되었습니다. 처음 3주 동안 1,000 만회 이상의 다운로드를 달성한 그들의 대표 게임을 출시한 후, 높은 내구성으로 인해 어떠한 유지보수 긴급 상황 없이 안정적인 서비스 운영을 할 수 있었습니다. 이 회사는 이제 읽기 처리량을 늘리고 페일오버 대상으로 사용하기 위해 5개의 다중 AZ 읽기 전용 복제본을 배치했습니다. 복제본에는 다음과 같은 장애 복구 우선 순위 티어가 할당되고 해당 크기는 괄호 안에 표시됩니다.
티어 -1 (16TB), 티어-1 (32TB), 티어-10 (16TB), 티어-15 (16TB), 티어-15 (32TB). 장애 복구 시 Amazon RDS는 다음 읽기 전용 복제본 중 어떤 것을 승격합니까?
- (선택) 티어 -1 (16TB)
- 티어 -15 ( 32TB)
- 티어 -10 (16TB)
- (정답) 티어 -1 (32TB)
```markdown
- Aurora 읽기 복제본은 티어(0-15)를 제공할 수 있습니다.
- 장애 복구 시 Amazon RDS는 가장 우선 순위의 티어(낮은 숫자)를 기반으로 장애 복구를 시작합니다.
- 둘 이상의 Aurora 복제본이 동일한 우선 순위를 공유하면 Amazon RDS는 크기가 가장 큰 복제본을 승격시킵니다.
- https://docs.aws.amazon.com/ko_kr/AmazonRDS/latest/AuroraUserGuide/Concepts.AuroraHighAvailability.html#Aurora.Managing.FaultTolerance
```

## 16.
회사는 고객이 공개적으로 액세스할 수 있는 고성능 컴퓨팅(HPC) 애플리케이션을 설계하고 있습니다. 보안팀은 애플리케이션에 대한 DDoS(분산 서비스 거부) 공격을 완화하려고 합니다.
다음 중 이 시나리오에서 구현하기에 적합하지 않은 옵션은 무엇입니까? (2개 선택)
- 정적 및 동적 콘텐츠를 모두 배포하려면 Amazon CloudFront 서비스를 사용합니다.
- (정답) 전용 EC2 인스턴스를 사용하여 각 인스턴스가 가능한 최대 성능을 갖도록 합니다.
- (정답) 각 EC2 인스턴스에 여러 EFA(Elastic Fabric Adapter)를 추가하여 네트워크 대역폭을 늘립니다.
- (선택) EC2 인스턴스에 대해 Auto Scaling 그룹에 Application Load Balancer를 사용한 다음 프라이빗 서브넷에 배포하여 Amazon RDS 데이터베이스에 대한 직접 인터넷 트래픽을 제한합니다.
- (선택) AWS Shield 및 AWS WAF를 사용합니다.
```markdown
- 문제 잘못 읽음: 적합하지 '않은' 옵션...
- https://aws.amazon.com/ko/shield/ddos-attack-protection/
- EC2 인스턴스의 성능을 높이는 것은 DDos 공격 완화와는 거리가 있음
- CloudFront는 Shield와 연동되어 DDoS 완화를 수행합니다.
- AWS Shield는 AWS에서 실행되는 애플리케이션을 보호하는 디도스(DDoS) 보호 서비스입니다. (Shield Advanced는 AWS 기술지원을 받을 수 있습니다.) 
- WAF는 가용성에 영향을 주거나, 보안을 위협하거나, 리소스를 과도하게 사용하는 일반적인 웹 공격으로부터 웹 애플리케이션이나 API를 보호하는 데 도움이 되는 웹 애플리케이션 방화벽입니다. 
```

## 17.
당신은 Windows AMI를 사용하여 EC2 인스턴스로 모놀리식 애플리케이션을 관리하는 유틸리티 공급자를 위해 일하는 AWS 네트워크 엔지니어입니다. 실행 상태에 있는 Windows 서버의 정확한 복제본이 있는 애플리케이션에 대해 비용 효율적이고 고가용성 아키텍처를 구현하려고 합니다. 기본 인스턴스가 종료되면 ENI를 대기 보조 인스턴스에 연결하여 몇 초 내에 트래픽 흐름을 재개 할 수 있습니다.
EC2 인스턴스에 대한 ENI 첨부와 관련하여 '웜 연결'란 무엇입니까?
- (선택) 인스턴스가 실행될 때 ENI를 인스턴스에 연결하는 것입니다.
- 유휴 상태 일 때 ENI를 인스턴스에 연결하는 것입니다.
- (정답) 인스턴스가 중지 상태일 때 ENI를 인스턴스에 연결하는 것입니다.
- 시작 프로세스 중 ENI를 인스턴스에 연결하는 것입니다.
```markdown
- 탄력적 네트워크 인터페이스(elastic network interface, ENI)는 VPC에서 가상 네트워크 카드를 나타내는 논리적 네트워킹 구성 요소입니다.
- 다음과 같은 방법으로 EC2 인스턴스에 ENI를 연결할 수 있습니다.
- 실행 중 상태(핫 연결), 중지 상태(웜 연결) 또는 시작 중 상태(콜드 연결)의 인스턴스에 네트워크 인터페이스를 연결할 수 있습니다.
- https://docs.aws.amazon.com/ko_kr/AWSEC2/latest/WindowsGuide/best-practices-for-configuring-network-interfaces.html
```

## 18.
CloudWatch에서 기본 모니터링을 사용하도록 설정한 Linux EC2 인스턴스의 Auto Scaling 그룹이 생성됩니다. 애플리케이션이 느려서 엔지니어 중 한 명에게 모든 EC2 인스턴스를 확인하도록 요청했습니다. 인스턴스를 확인한 후 서버 메모리 사용량이 이미 높은데도 자동 Auto Scaling이 필요한 만큼 더 많은 인스턴스를 시작하지 않는 것을 발견했습니다.
다음 중 이 문제를 해결하기 위해 구현할 수 있는 가능한 솔루션은 무엇입니까? (2개 선택)
- 인스턴스 수를 늘리려면 임계 값을 늘리도록 조정 정책을 수정합니다.
- EC2 인스턴스에 AWS SDK를 설치하십시오. 메모리 사용량이 많은 경우 Auto Scaling 이벤트를 트리거하는 스크립트를 생성합니다.
- (선택/정답) 인스턴스에 CloudWatch 모니터링 스크립트를 설치하십시오. CloudWatch에 사용자 지정 지표를 보내면 Auto Scaling 그룹이 확장됩니다.
- (선택) 인스턴스에서 세부 모니터링을 활성화 합니다.
- (정답) EC2 인스턴스에 CloudWatch 에이전트를 설치하면 Auto Scaling 그룹이 확장됩니다.
```markdown
- CloudWatch는 EC2 메모리 사용량과 디스크 공간 사용량을 모니터링하지 않습니다.
- 스크립트(derprecated)를 사용하거나 CloudWatch 에이전트를 사용하여 지표를 수집한 다음 CloudWatch로 데이터를 보내야 합니다.
- https://docs.aws.amazon.com/ko_kr/AWSEC2/latest/UserGuide/mon-scripts.html
```

## 19.
당신은 RDS로 호스팅되는 대학의 온라인 등록 시스템 데이터베이스를 처리하는 빅 데이터 엔지니어입니다. 등록 시스템의 가용성을 보장하기 위해 Amazon CloudWatch에서 데이터베이스 메트릭을 모니터링해야 합니다.
Amazon CloudWatch가 Amazon RDS DB 인스턴스를 통해 수집하는 확장 모니터링 메트릭은 무엇입니까? (2 개 선택)
- Freeable Memory
- (선택) Database Connections
- (정답) OS processes
- (선택/정답) RDS child processes
- CPU Utilization
```markdown
RDS에서 프로세스 목록 보기에 표시되는 확장 모니터링 지표는 다음과 같이 구성됩니다.
- RDS child processes(RDS 하위 프로세스)
- RDS processes 
- OS processes

오답
- CPU Utilization, Database Connections, Freeable Memory는 RDS 기본 모니터링 지표입니다.
```

## 20.
회사의 인프라팀은 여러 EC2 인스턴스를 관리하고 있으며 이를 문서화하고 있습니다. 인프라팀은 부팅 볼륨으로 사용할 수 없는 볼륨 유형을 강조 표시하려고 합니다.
인스턴스를 생성하는 동안 부팅 볼륨으로 사용할 수 없는 스토리지 볼륨 유형은 어떤 것이 있습니까? (2개 선택)
- (선택) EBS 프로비저닝된 IOPS SSD(io1)
- (정답) Cold HDD (sc1)
- (정답) 처리량에 최적화된 HDD (st1)
- (선택) EBS 범용 SSD(gp2)
- 인스턴스 스토어
```markdown
- EBS HDD는 부트 볼륨이 될 수 없음
- https://docs.aws.amazon.com/ko_kr/AWSEC2/latest/UserGuide/ebs-volume-types.html

- 인스턴스 스토어는 인스턴스에 블록 수준의 임시 스토리지를 제공합니다.
- 인스턴스 스토어는 버퍼, 캐시, 스크래치 데이터 및 기타 임시 콘텐츠와 같이 자주 변경되는 정보의 임시 스토리지나 로드가 분산된 웹 서버 풀과 같은 여러 인스턴스상에서 복제되는 데이터에 가장 적합합니다.
- https://docs.aws.amazon.com/ko_kr/AWSEC2/latest/UserGuide/InstanceStorage.html
```

## 21.
당신은 회사의 전 세계 부서에서 모든 AWS 리소스에 대한 기업의 IT 거버넌스와 비용 감독을 필요로 하는 글로벌 투자 은행에서 솔루션 아키텍트로 일하고 있습니다. 각 기업 부서는 자신이 사용하는 개별 AWS 리소스에 대한 관리 제어를 유지하고 이러한 리소스가 다른 부서와 분리되도록 보장하려고 합니다.
다음 중 기업 IT가 거버넌스 및 비용 감시를 유지하면서 각 기업 부서의 자율성을 지원하는 옵션은 무엇입니까? (2개 선택)
- (정답) 각 하위 계정의 모든 기업 IT 관리자에 대해 IAM 교차 계정 액세스를 활성화 합니다.
- 회사 IT AWS 계정 내의 각 부서에 대해 별도의 VPC 생성합니다.
- (선택) AWS Trusted Advisor 사용합니다.
- (선택/정답) 부서의 계정을 모기업 계정에 연결하기 위해 AWS Organizations를 생성하여 AWS 통합 결제를 사용합니다.
- 회사 IT AWS 계정 내의 각 부서에 대해 별도의 가용 영역 생성합니다.
```markdown
- AWS Organizations의 통합 결제 기능을 사용하여 여러 AWS 계정 또는 여러 Amazon Internet Services Pvt. Ltd(AISPL) 계정의 결제를 통합할 수 있습니다.
- https://docs.aws.amazon.com/ko_kr/awsaccountbilling/latest/aboutv2/consolidated-billing.html
- IAM 역할을 사용하여 소유한 서로 다른 AWS 계정에 있는 리소스에 대한 액세스를 위임할 수 있습니다. 한 계정의 리소스를 다른 계정의 사용자와 공유할 수 있습니다.이러한 방식으로 교차 계정 액세스를 설정하면 각 계정에 개별 IAM 사용자를 만들 필요가 없습니다. 또한 사용자가 서로 다른 AWS 계정에 있는 리소스에 액세스하기 위해 한 계정에서 로그아웃하고 다른 계정으로 로그인할 필요가 없습니다.
- https://docs.aws.amazon.com/ko_kr/IAM/latest/UserGuide/tutorial_cross-account-with-roles.html

오답
- Trusted Advisor는 AWS 모범 사례에 따라 리소스를 프로비저닝하는 데 도움이 되는 실시간 지침을 제공하는 온라인 도구입니다. 거버넌스와 관계 없습니다.
```


## 22.
HTTP 애플리케이션은 Auto Scaling 그룹에 배포되고 HTTPS 종료를 제공하는 Application Load Balancer에서 액세스 할 수 있으며, RDS에서 관리하는 PostgreSQL 데이터베이스에 액세스합니다.
보안 그룹을 어떻게 구성해야 합니까? (2개 선택)
- EC2 인스턴스의 보안 그룹에는 포트 5432의 RDS 데이터베이스 보안 그룹의 인바운드 규칙이 있어야 합니다.
- (선택) RDS의 보안 그룹에는 포트 80의 Auto Scaling 그룹에 있는 EC2 인스턴스의 보안 그룹으로부터의 인바운드 규칙이 있어야 합니다.
- (선택/정답) EC2 인스턴스의 보안 그룹에는 포트 80에 있는 Application Load Balancer의 보안 그룹에 인바운드 규칙이 있어야 합니다.
- Application Load Balancer의 보안 그룹에는 포트 80의 어느 곳에서나 인바운드 규칙이 있어야 합니다.
- (정답) Application Load Balancer의 보안 그룹에는 포트 443의 모든 위치에서 인바운드 규칙이 있어야 합니다.
```markdown
- ALB에는 443의 모든위치에서 -> 헷갈릴 수는 있으나 틀린 규칙은 아님
- 다음과 같이 보안그룹 규칙이 설정되어야 함: any 443 -> ALB -(ALB 80)-> ASG(EC2) -(EC2 5432)-> RDS 
```

