## 2.
최근 AWS 리소스의 보안을 개선하기 위해 한 금융 서비스 회사는 이니셔티브를 시작했으며 회사가 소유한 여러 AWS 계정에서 AWS Shield Advanced를 활성화했습니다. 분석을 통해 회사는 예상보다 훨씬 높은 비용이 발생했다는 것을 발견했습니다.
다음 중 AWS Shield Advanced 서비스에 대해 예상치 못한 높은 비용의 근본적인 이유는 무엇일까요?
- AWS Shield Advanced는 AWS Shield Standard 플랜도 포함하므로 증가한 비용이 발생합니다.
- (선택) 비용 절감 계획은 모든 AWS 계정에서 AWS Shield Advanced 서비스에 대해 활성화되지 않았습니다.
- (정답) 통합 결제가 활성화되지 않았습니다. 모든 AWS 계정은 월별 요금이 한 번만 청구되는 1회 통합 결제를 해야 합니다.
- AWS Shield Advanced는 AWS 클라우드의 일부가 아닌 사용자 지정 서버에 사용되므로 증가한 비용이 발생합니다.
```
AWS 계정이 모두 1회 통합 결제에 속해 있는 동안 월별 요금을 한 번만 지불하면 해당 계정에 속한 모든 AWS 계정과 리소스를 소유할 수 있습니다. 기관이 여러 AWS 계정이 있다면 AWS Management Console이나 API를 사용해 각 계정에서 개별적으로 활성화해 여러 AWS 계정을 AWS Shield Advanced에 구독할 수 있습니다.
```
- [AWS Shield FAQ](https://aws.amazon.com/ko/shield/faqs/)
- [비용 절감 계획](https://aws.amazon.com/ko/savingsplans/faq/)은 AWS Shield Advanced 서비스에 적용되지 않습니다.


## 5.
한 뉴스 네트워크는 Amazon S3를 사용해 미국 전역의 보고 팀의 원본 영상을 합칩니다. 뉴스 네트워크는 최근 유럽과 아시아의 새로운 지역으로 확장되었습니다. 해외 지사의 기술 팀은 목적지인 S3 버킷에 대용량 비디오 파일을 업로드할 때 상당한 지연이 있다고 보고했습니다.
다음 중 S3로의 파일 업로드 속도 향상에 가장 비용 효율적인 옵션은 무엇일까요? (2개 선택)
- (선택/정답) Amazon S3 Transfer Acceleration을 사용하여 대상 S3 버킷으로 파일을 더 빠르게 업로드하게 합니다.
- (선택) AWS 글로벌 액셀러레이터를 사용하여 대상 S3 버킷으로 더 빠르게 파일을 업로드합니다.
- AWS 클라우드와 유럽 및 아시아의 지사 간에 여러 AWS Direct Connect 연결을 생성합니다. S3에 더 빠른 파일 업로드를 위해 Direct Connect 연결을 사용합니다.
- AWS 클라우드와 유럽 및 아시아 지사 간에 여러 site-to-site VPN 연결을 생성합니다. 이 VPN 연결을 사용하여 S3에 더 빠른 파일을 업로드합니다.
- (정답) 대상 S3 버킷에 더 빠른 파일 업로드를 위해 멀티파트 업로드를 사용합니다.
```
- Amazon S3 Transfer Acceleration을 사용하면 클라이언트와 S3 버킷 간 장거리를 빠르고 쉽고 안전하게 파일 전송이 가능합니다. Transfer Acceleration은 전 세계적으로 분산된 엣지 로케이션을 Amazon CloudFront를 활용합니다. 데이터가 엣지 로케이션에 도착하면 데이터는 최적화된 네트워크 경로를 통해 Amazon S3로 라우팅됩니다.
- 멀티파트 업로드를 사용하면 개체 한 개를 부분 집합으로 업로드할 수 있습니다. 각 부분은 개체 데이터의 연속 부분입니다. 이러한 개체 부분을 개별로 그리고 어떤 순서로든 업로드할 수 있습니다. 어떤 부분의 전송이 실패하면 다른 부분에 영향을 주지 않고 다시 해당 부분을 재전송할 수 있습니다. 객체의 모든 부분이 업로드되면 Amazon S3가 해당 부분을 조합하고 객체를 생성합니다. 일반적으로 객체 크기가 100MB에 도달하면 작업 한 번으로 객체를 업로드하는 대신 멀티파트 업로드 사용을 고려해야 합니다. 멀티파트 업로드는 향상된 처리량을 제공하므로 더 빠른 파일 업로드가 가능합니다.
[오답]
- AWS 글로벌 액셀러레이터는 요청을 보내는 '사용자' 측면에서 어플리케이션의 가용성과 성능을 향상시키는 서비스
- Direct Connect는 온프레미스에서 AWS으로의 전용 네트워크 설정을 쉽게 설정할 수 있는 솔루션
  - https://aws.amazon.com/ko/directconnect/
- site-to-site VPN은 온프레미스 네트워크를 VPC로 안전하게 연결할 수 있는 서비스
  - https://docs.aws.amazon.com/ko_kr/vpn/latest/s2svpn/VPC_VPN.html
```

## 10.
한 매체 회사는 자체 IT 인프라를 소유하고 유지 관리하는 비즈니스에서 벗어나고 싶어합니다. 이 디지털 혁신의 일환으로 매체 회사는 온-프레미스 데이터 센터에 있는 약 5PB의 데이터를 내구성 있는 장기 스토리지에 보관하기를 원합니다.
솔루션 아키텍트로서 가장 비용 최적화된 방식으로 이 데이터를 마이그레이션하기 위해 무엇을 권장하시겠습니까?
- 온-프레미스 데이터 센터와 AWS 클라우드 간에 Site-to-Site VPN 연결을 설정합니다. 이 연결을 사용하여 데이터를 AWS Glacier로 전송
- (선택) 온-프레미스 데이터를 여러 Snowball Edge Storage Optimized 디바이스로 전송합니다. Snowball Edge 데이터를 AWS Glacier로 복사
- 온-프레미스 데이터 센터와 AWS 클라우드 간에 AWS Direct Connect을 설정합니다. 이 연결을 사용하여 데이터를 AWS Glacier로 전송
- (정답) 온프레미스 데이터를 여러 Snowball Edge Storage Optimized 디바이스로 전송합니다. Snowball Edge 데이터를 Amazon S3로 복사하고 수명 주기 정책을 생성하여 데이터를 AWS Glacier로 전환
```
최종적으로 장기 스토리지 용도로 Glacier를 선택해야 함
Snowball Edge Storage Optimized는 S3를 거쳐서 Glacier로 저장해야 함 
Snowball Edge Storage Optimized는 수십 테라바이트에서 페타바이트 규모의 데이터를 AWS로 안전하고 빠르게 전송해야 하는 경우 최적의 선택입니다. 최대 80TB의 사용 가능한 HDD 스토리지, 40개의 vCPU, 1TB의 SATA SSD 스토리지 및 최대 40Gb 네트워크 연결을 제공하여 대규모 데이터 전송 및 사전 처리 사용 사례를 처리합니다. Snowball Edge 디바이스에 저장된 데이터는 S3 버킷에 복사할 수 있으며 나중에 수명 주기 정책을 통해 AWS Glacier로 전환할 수 있습니다. Snowball Edge 디바이스에서 AWS Glacier로 데이터를 직접 복사할 수 없습니다. 
- https://docs.aws.amazon.com/ko_kr/snowball/latest/developer-guide/whatisedge.html
```

## 12.
빅 데이터 분석 회사는 Kinesis Data Streams(KDS)를 사용하여 농업 과학 회사의 필드 장치에서 IoT 데이터를 처리하고 있습니다. 여러 소비자 애플리케이션이 들어오는 데이터 스트림을 사용하고 있으며 엔지니어는 데이터 스트림의 생산자와 소비자 간의 데이터 전달 속도에서 성능 지연을 발견했습니다.
솔루션 아키텍트로서 주어진 사용 사례의 성능을 개선하기 위해 다음 중 어떤 것을 권장하시겠습니까?
- SQS 표준 Queues로 Kinesis Data Streams 교체
- (선택) Kinesis Data Firehose로 Kinesis Data Streams 교체
- SQS FIFO Queues로 Kinesis Data Streams 교체
- (정답) Kinesis Data Streams의 향상된 팬아웃 기능 사용
```
Amazon Kinesis Data Streams(KDS)는 스케일성과 내구성이 뛰어난 실시간 데이터 스트리밍 서비스입니다. 여러 소비자가 스트림에서 병렬로 데이터를 검색하는 경우 향상된 팬아웃을 사용해야 합니다.
https://aws.amazon.com/blogs/aws/kds-enhanced-fanout/
Kinesis Data Firehose는 S3, Redshift, Elasticsearch 또는 Splunk에만 쓸 수 있습니다.
https://docs.aws.amazon.com/ko_kr/firehose/latest/dev/create-name.html
```

## 13.
전자 상거래 회사에 소속된 엔지니어링 팀은 서버리스 아키텍처로 마이그레이션하는 임무를 받았습니다. 팀은 이 아키텍처의 중추 역할로 Lambda를 사용할 때 고려해야 할 핵심 사항에 중점을 두고자 합니다.
솔루션 아키텍트로서 다음 중 주어진 요구 사항에 맞는 것으로 식별할 수 있는 옵션은 무엇일까요? (3개 선택)
- Lambda는 함수에 할당한 메모리에 비례하여 컴퓨팅 성능을 할당합니다. 따라서 AWS는 Lambda 함수의 적절한 성능을 위해 함수 시간 초과 설정을 과도하게 프로비저닝할 것을 권장합니다.
- (선택/정답) Lambda 함수는 매우 빠르게 스케일될 수 있으므로 ConcurrentExecutions 또는 Invocations와 같은 함수 metrics가 예상 임계값을 초과할 때 팀에 알리는 CloudWatch 경보를 배포하는 것이 좋습니다.
- (정답) 기본적으로 Lambda 함수는 항상 AWS 소유 VPC에서 작동하므로 모든 공용 인터넷 주소 또는 공용 AWS API에 액세스할 수 있습니다. Lambda 함수가 VPC를 활성화하면 퍼블릭 리소스에 액세스하려면 퍼블릭 서브넷의 NAT 게이트웨이를 통한 경로가 필요합니다.
- (선택) 배포 패키지가 클수록 Lambda 함수가 콜드 스타트하는 속도가 느려집니다. 따라서 AWS는 종속성을 실제 Lambda 패키지와 별도의 패키지로 패키징할 것을 제안합니다.
- (선택/정답) 둘 이상의 Lambda 함수에서 코드를 재사용하려는 경우 재사용 가능한 코드에 대한 Lambda 계층 생성을 고려해야 합니다.
- 서버리스 아키텍처와 컨테이너는 서로를 보완하여 Lambda 함수 내에서 Docker 컨테이너를 활용해야 합니다.
```
- Lambda 함수는 매우 빠르게 스케일할 수 있으므로 동시성이 급증할 때 이를 알리는 제어 장치가 있어야 합니다.
- 추가 코드와 콘텐츠를 계층 형태로 가져오도록 Lambda 함수를 구성할 수 있습니다.
```

## 16.
한 빅 데이터 분석 회사는 AWS 클라우드 아키텍처를 설정해 갑작스러운 트래픽 급증 시 요청을 조절하려고 합니다. 회사는 이러한 트래픽 변동을 대비한 버퍼링 또는 조절에 사용할 수 있는 AWS 서비스를 찾고 있습니다.
다음 중 이 요구 사항을 지원할 수 있는 서비스는 무엇일까요?
- (정답) Amazon API Gateway, Amazon SQS 및 Amazon Kinesis
- Amazon SQS, Amazon SNS 및 AWS Lambda
- Amazon 게이트웨이 엔드포인트, Amazon SQS 및 Amazon Kinesis
- (선택) Elastic 로드 밸런서, Amazon SQS, AWS Lambda
```
키워드는 트래픽 변동을 대비한 버퍼링 또는 조절. 스케일링이나 로드밸런싱이 이 아닌 요청에 대한 버퍼링 조절이 필요.
API Gateway는 계정의 모든 API에 대한 안정적인 속도와 요청 제출 버스트에 대한 제한을 설정합니다. (버스트는 토큰 버킷 알고리즘에서 최대 버킷 크기입니다.)
Amazon SQS는 일시적인 볼륨 급증을 완화하는 버퍼 기능을 제공하며 메시지 손실이나 지연 시간 증가는 발생하지 않습니다.
Amazon Kinesis - Amazon Kinesis는 스케일 가능한 완전 관리형 서비스로 스트리밍 데이터를 실시간으로 수집, 버퍼링 및 처리할 수 있습니다.
ELB는 요청을 조절할 수 없고 Lambda는 버퍼링에 사용할 수 없습니다.
```

## 21.
한 IT 회사는 동일한 계정 내의 특정 사용자에게 프로젝트별 작업을 완료하기 위해 S3 버킷 액세스를 제공합니다. 비즈니스 요구 사항이 변화함에 따라 교차 계정 S3 액세스 요청도 매월 증가하고 있습니다. 회사는 S3 버킷에 저장된 데이터에 대한 사용자 수준 및 계정 수준 액세스 권한을 제공할 수 있는 솔루션을 찾고 있습니다.
솔루션 아키텍트로서 다음 중 이 사용 사례에 대한 액세스를 제어하는 데 가장 최적화된 방법으로 제안할 수 있는 것은 무엇일까요?
- ACL(액세스 제어 목록) 사용
- (정답) Amazon S3 버킷 정책 사용
- 보안 그룹 사용
- (선택) Identity and Access Management, IAM(ID 및 액세스 관리) 정책 사용
```
'교차 계정 S3 액세스 요청도 매월 증가'가 키워드
Amazon S3의 버킷 정책을 사용하여 단일 버킷 내의 일부 또는 모든 객체에 대한 권한을 추가하거나 거부할 수 있습니다. 버킷 정책을 사용하면 AWS 계정 또는 다른 AWS 계정 내 사용자에게 Amazon S3 리소스에 대한 액세스 권한을 부여할 수 있습니다.
IAM 정책을 사용하면 자체 'AWS 계정 내의 사용자'에게만 Amazon S3 리소스에 액세스할 수 있는 권한을 부여할 수 있습니다.
```

## 29.
한 매체 에이전시는 Amazon S3 버킷에 재생 가능한 자산을 저장합니다. 자산은 처음 며칠 동안 많은 사용자가 액세스하고 일주일 후에 액세스 빈도가 급격히 떨어집니다. 자산은 첫 주 이후부턴 가끔씩 액세스되지만 필요할 때는 즉시 액세스할 수 있어야 합니다. S3 스토리지의 모든 자산을 유지 관리하는 데 드는 비용이 매우 비싸다는 것이 밝혀져 에이전시에서는 최대한 비용을 절감하는 방안을 모색하고 있습니다.
솔루션 아키텍으로서 비즈니스 요구 사항을 충족하면서 스토리지 비용을 절감할 수 있는 방법이 무엇이 있습니까?
- (정답) 30일 후에 객체를 Amazon S3 One Zone-Infrequent Access(S3 One Zone-IA)로 전환하도록 수명 주기 정책을 구성
- 30일 후에 객체를 Amazon S3 Standard-Infrequent Access(S3 Standard-IA)로 전환하도록 수명 주기 정책을 구성
- 7일 후에 객체를 Amazon S3 Standard-Infrequent Access(S3 Standard-IA)로 전환하도록 수명 주기 정책을 구성
- (선택) 7일 후에 객체를 Amazon S3 One Zone-Infrequent Access(S3 One Zone-IA)로 전환하도록 수명 주기 정책을 구성
```
최대한 비용을 절감하는 방안 -> 땃히 가용성과 복원력이 별로 필요하지 않음 -> S3 One Zone-IA
그리고 S3 IA로 옮기려면 최소 30일 필요
https://docs.aws.amazon.com/ko_kr/AmazonS3/latest/userguide/lifecycle-transition-general-considerations.html -> 객체를 S3 Standard 스토리지 클래스에서 S3 Standard-IA로 또는 S3 Standard-IA 스토리지 클래스에서 S3 One Zone-IA로 전환하기 전에 객체를 S3 Standard 스토리지 클래스에 30일 이상 보관해야 합니다
```

## 34.
전자 상거래 회사는 AWS Direct Connect 링크를 사용하여 온-프레미스 데이터 센터에서 us-west-1 리전의 Amazon S3 버킷으로 1PB의 데이터를 복사했습니다. 이제 회사는 us-east-1 리전의 다른 S3 버킷에 데이터를 복사하려고 합니다. 온-프레미스 데이터 센터에서는 AWS Snowball을 사용할 수 없습니다.
솔루션 아키텍트로서 이를 수행하기 위해 다음 중 어느 것을 권장하시겠습니까?
- Snowball Edge 디바이스를 사용하여 한 리전에서 다른 리전으로 데이터 복사
- (선택) 다른 리전의 S3 버킷 간에 객체를 복사하도록 교차 리전 복제 설정
- (정답) AWS S3 sync 명령을 사용하여 소스 버킷에서 대상 버킷으로 데이터 복사
- S3 콘솔을 사용하여 소스 S3 버킷에서 대상 S3 버킷으로 데이터 복사
```
하나의 리전에서 다른 리전으로 복사하는 것이므로 S3 sync 명령어 사용 가능
데이터가 소스 버킷에 이미 존재하므로 기본적으로 복제가 활성화된 후에만 새 Amazon S3 객체 복사를 지원하기 때문에 교차 리전 복제를 사용할 수 없음 
```

## 36. (review required)
여러분의 회사에서는 Elastic Beanstalk에서 실행되는 웹 사이트를 배포하고 있습니다. 웹사이트 설치에 45분 이상이 소요되며 과정에서 생성되어야 하는 static 및 동적 파일이 모두 포함되어 있습니다.
솔루션 아키텍트로서 여러분은 Elastic Beanstalk 배포에서 새 인스턴스를 생성하는 시간을 2분 미만으로 만들고 싶습니다. 이 요구 사항에 대한 솔루션을 구축하려면 다음 중 어떤 옵션을 결합해야 할까요? (2개 선택)
- 설치 파일을 S3에 저장하여 신속하게 검색
- EC2 사용자 데이터를 사용하여 부팅 시 애플리케이션 설치
- (선택/정답) Static 설치 구성 요소가 이미 설정된 Golden AMI 생성
- (선택) Elastic Beanstalk 배포 캐싱 기능5 사용
- (정답) EC2 사용자 데이터를 사용하여 부팅 시 동적 설치 부분을 사용자 지정
```
동적 파일? 소스파일을 이야기하는 것 같음. 영어로 된 지문을 보는게 도움 될 것 같음
정답
- 골든 AMI는 구성, 일관된 보안 패치 및 강화를 통해 표준화하는 AMI이며 static 설치 구성 요소를 미리 설치할 수 있습니다.
- 부팅 시 애플리케이션 자체를 설치하는 대신 EC2 사용자 데이터를 사용하여 부팅 시 동적 설치 부분을 사용자 지정할 수 있습니다.
오답
- Elastic Beanstalk 배포 캐싱 기능 사용 -> 헷갈리게 만드려는 선택지라고 함
- EC2 사용자 데이터를 사용하여 부팅 시 애플리케이션 설치 -> 사용자 데이터를 사용하여 어플리케이션을 설치하는 것은 배포시간을 줄이는 것에는 도움을 줄 것 같지 않음
```

## 40.
전자 상거래 회사는 온-프레미스 인프라에서 AWS 클라우드로 2계층 애플리케이션을 마이그레이션할 계획입니다. 회사의 엔지니어링 팀은 AWS 클라우드를 처음 사용하기 때문에 Amazon VPC 콘솔 마법사를 사용하여 공용 웹 서버와 개인 데이터베이스 서버가 있는 2계층 애플리케이션에 대한 네트워킹 구성을 설정할 계획입니다.
Amazon VPC 콘솔 마법사에서 지원하지 않는 구성을 찾을 수 있습니까?
- (정답) 퍼블릭 서브넷만 있고 AWS Site-to-Site VPN 액세스 권한이 있는 VPC
- (선택) 퍼블릭 및 프라이빗 서브넷이 있는 VPC(NAT)
- 단일 퍼블릭 서브넷이 있는 VPC
- 퍼블릭 및 프라이빗 서브넷과 AWS Site-to-Site VPN 액세스가 있는 VPC
```
퍼블릭 서브넷만 있고 AWS Site-to-Site VPN 액세스 권한이 있는 VPC는 VPC 콘솔 마법사를 사용하여 구성할 수 없음
https://docs.aws.amazon.com/ko_kr/vpc/latest/userguide/VPC_wizard.html
```

## 43.
소매 회사는 IT 인프라를 관리하기 위해 AWS 클라우드를 사용합니다. 회사는 AWS 계정을 실행하고 EC2 인스턴스 및 RDS 데이터베이스와 같은 리소스를 사용하는 여러 부서를 관리하기 위해 “AWS 기관”을 설정했습니다. 이 회사는 높은 수준의 상호 연결이 필요한 애플리케이션을 사용하여 모든 부서에 중앙에서 관리되는 공유 VPC를 제공하려고 합니다.
솔루션 아키텍트로서 이 사용 사례를 촉진하기 위해 다음 중 어떤 옵션을 선택하시겠습니까?
- VPC 피어링을 사용하여 AWS Organizations의 동일한 상위 조직에 속한 다른 AWS 계정과 하나 이상의 서브넷을 공유합니다.
- (정답) VPC 공유를 사용하여 AWS Organizations의 동일한 상위 조직에 속한 다른 AWS 계정과 하나 이상의 서브넷을 공유합니다.
- VPC 공유를 사용하여 AWS Organizations의 동일한 상위 조직에 속한 다른 AWS 계정과 VPC를 공유합니다.
- (선택) VPC 피어링을 사용하여 AWS Organizations의 동일한 상위 조직에 속한 다른 AWS 계정과 VPC를 공유합니다.
```
Resource Access Manager(RAM) 내 VPC 공유를 사용하면 여러 AWS 계정에서 EC2 인스턴스, RDS 데이터베이스, Redshift 클러스터 및 Lambda 함수와 같은 애플리케이션 리소스를 공유 및 중앙 관리형 Amazon Virtual Private Cloud(VPC)에 생성할 수 있습니다. VPC 자체를 공유할 수는 없고 서브넷을 공유할 수 있습니다.
https://docs.aws.amazon.com/ko_kr/ram/latest/userguide/shareable.html#shareable-vpc
VPC 피어링 연결은 프라이빗 IPv4 주소 또는 IPv6 주소를 사용하여 두 VPC 간에 트래픽을 라우팅할 수 있는 두 VPC 간의 네트워킹 연결이며 중앙관리를 제공하지 않습니다.
https://docs.aws.amazon.com/ko_kr/vpc/latest/peering/what-is-vpc-peering.html
```

## 47
IT 회사의 DevOps 팀은 퍼블릭 서브넷과 프라이빗 서브넷이 있는 VPC에서 2계층 애플리케이션을 프로비저닝하고 있습니다. 팀은 퍼블릭 서브넷의 NAT 인스턴스 또는 NAT 게이트웨이를 사용하여 프라이빗 서브넷의 인스턴스가 인터넷에 대한 아웃바운드 IPv4 트래픽을 시작할 수 있도록 하려고 하지만 NAT 인스턴스 및 NAT 게이트웨이를 사용할 수 있는 구성 옵션 차원의 기술적 도움이 필요합니다..
솔루션 아키텍트로서 다음 중 어떤 옵션이 올바른가요? (3개 선택)
- NAT 게이트웨이를 bastion 서버로 사용할 수 있습니다.
- (정답) 인스턴스는 포트 전달을 지원합니다.
- (선택/정답) 보안 그룹은 NAT 인스턴스와 연결할 수 있습니다.
- (선택) 보안 그룹은 NAT 게이트웨이와 연결할 수 있습니다.
- (선택) NAT 게이트웨이는 포트 포워딩을 지원합니다.
- (정답) NAT 인스턴스를 bastion 서버로 사용할 수 있습니다.
```
NAT 인스턴스 또는 NAT 게이트웨이는 VPC의 퍼블릭 서브넷에서 사용하여 프라이빗 서브넷의 인스턴스가 인터넷으로 아웃바운드 IPv4 트래픽을 시작할 수 있도록 함.
NAT 인스턴스는 NAT 역할을 하는 EC2 인스턴스이므로 보안그룹이 있고 bastion 서버로 사용 가능.
https://docs.aws.amazon.com/ko_kr/vpc/latest/userguide/vpc-nat-gateway.html
https://docs.aws.amazon.com/ko_kr/vpc/latest/userguide/VPC_NAT_Instance.html
```
- NAT 게이트웨이
  ![nat-gateway-diagram](https://docs.aws.amazon.com/vpc/latest/userguide/images/nat-gateway-diagram.png)
- NAT 인스턴스 vs. NAT 게이트웨이
  ![nat-gateway-vs-nat-instance](https://assets-pt.media.datacumulus.com/aws-saa-pt/assets/pt4-q12-i1.jpg)

## 48.
전자 상거래 회사의 엔지니어링 팀은 EC2 인스턴스의 비용 최적화 작업을 하고 있습니다. 팀은 여러 인스턴스 유형에서 온디맨드 및 스팟 인스턴스를 혼합하여 워크로드를 관리하려고 합니다. 그들은 이러한 인스턴스를 혼합하여 Auto Scaling 그룹을 만들고자 합니다.
다음 중 엔지니어링 팀이 이 사용 사례에 대한 인스턴스를 프로비저닝할 수 있는 옵션은 무엇일까요?
- (정답) 원하는 규모, 성능 및 비용을 달성하기 위해 온디맨드 인스턴스와 스팟 인스턴스를 모두 사용하여 여러 인스턴스 유형에 용량을 프로비저닝하는 시작 템플릿만 사용할 수 있습니다.
- 원하는 규모, 성능 및 비용을 달성하기 위해 온디맨드 인스턴스와 스팟 인스턴스를 모두 사용하여 여러 인스턴스 유형에 용량을 프로비저닝하는 시작 구성만 사용할 수 있습니다.
- 원하는 규모, 성능 및 비용을 달성하기 위해 온디맨드 인스턴스와 스팟 인스턴스를 모두 사용하여 여러 인스턴스 유형에 용량을 프로비저닝하는 시작 구성 또는 시작 템플릿을 사용할 수 없습니다.
- (선택) 원하는 규모, 성능 및 비용을 달성하기 위해 온디맨드 인스턴스와 스팟 인스턴스를 모두 사용하여 여러 인스턴스 유형에 용량을 프로비저닝하는 시작 구성 또는 시작 템플릿을 사용할 수 있습니다.
```
시작 템플릿을 사용하면 온디맨드 인스턴스와 스팟 인스턴스를 모두 사용하여 여러 인스턴스 유형에 용량을 프로비저닝 가능
시작 구성은 불가
```

## 50. (review required)
한 회사는 애플리케이션 로드 밸런서 배후의 EC2 인스턴스에서 실행되는 여러 계층 소셜 미디어 애플리케이션을 관리합니다. 인스턴스는 여러 가용 영역에 걸쳐 EC2 Auto Scaling 그룹에서 실행되며 Amazon Aurora 데이터베이스를 사용합니다. 솔루션 아키텍으로서 애플리케이션을 요청 속도의 주기적인 급증에 대해 보다 탄력적으로 대처할 수 있도록 업무 요청을 받았습니다.
다음 중 주어진 사용 사례에 권장하는 솔루션은 무엇일까요? (2개 선택)
- AWS 쉴드 사용
- (정답) 애플리케이션 로드 밸런서 앞에서 CloudFront 배포 사용
- (선택/정답) Aurora 복제본 (Replica) 사용
- (선택) AWS 글로벌 액셀러레이터
- AWS Direct Connect 사용
```
키워드: 여러 가용 영역에 걸쳐있음, 요청 속도의 주기적인 급증에 대해 보다 탄력적으로 대처
- Aurora 복제본 (Replica) 사용하여 읽기 작업의 성능을 확보할 수 있음
- CloudFront는 짧은 지연 시간, 높은 전송 속도로 Points of Presence(POP, 접속 지점) (엣지 로케이션)은 인기 있는 콘텐츠가 시청자에게 빠르게 제공될 수 있도록 함
오답
- 글로벌 액셀러레이터는 게임(UDP), IoT(MQTT) 또는 Voice over IP와 같은 비 HTTP 사용 사례와 특히 static IP 주소 또는 결정적으로 빠른 지역 장애 조치가 필요한 HTTP 사용 사례에 적합합니다.
```

## 53.
전자 상거래 회사의 엔지니어링 팀은 일괄 처리를 통해 SQS 표준 Queues에서 FIFO Queues로 마이그레이션하려고 합니다.
솔루션 아키텍트로서 마이그레이션 체크리스트에 다음 단계 중 어떤 단계를 포함하시겠습니까? (3개 선택)
- (선택) FIFO Queues의 이름이 표준 Queues과 동일한지 확인
- (정답) 기존 표준 Queues을 삭제하고 FIFO Queues로 다시 생성
- 대상 FIFO Queues의 처리량이 초당 300개 메시지를 초과하지 않는지 확인
- (선택/정답) FIFO Queues의 이름이.fifo 접미사로 끝나는지 확인
- (선택) 기존 표준 Queues을 FIFO Queues로 변환
- (정답) 대상 FIFO Queues의 처리량이 초당 3,000개 메시지를 초과하지 않는지 확인
```
SQS는 두 가지 유형의 메시지 Queues을 제공합니다.
표준 Queues은 최대 처리량, 최선형 주문 및 최소 한 번 배달을 제공합니다.
SQS FIFO Queues은 메시지가 전송된 정확한 순서로 정확히 한 번 처리되도록 설계되었습니다.
FIFO Queues의 이름은.fifo 접미사로 끝나야 합니다.
기본적으로 FIFO Queues은 일괄 처리를 사용하여 초당 최대 3,000개의 메시지를 지원하거나 일괄 처리를 사용하지 않을 경우 초당 최대 300개의 메시지(초당 300개의 보내기, 받기 또는 삭제 작업)를 지원합니다.

요약하자면
- 표준 Queues에서 FIFO Queues로는 수정이 불가하고 삭제 후 다시 생성 필요
- .fifo 접미사로 인해서 Queues 이름도 달라야 함
- 필요한 메시지 처리량이 300~3000 사이인지 확인 필요

https://docs.aws.amazon.com/ko_kr/AWSSimpleQueueService/latest/SQSDeveloperGuide/standard-queues.html
https://docs.aws.amazon.com/ko_kr/AWSSimpleQueueService/latest/SQSDeveloperGuide/FIFO-queues.html
```

## 57.
회사의 비즈니스 분석 팀은 고위 경영진을 위한 일일 보고서를 위해 Amazon RDS에서 Oracle 및 PostgreSQL 서비스에 대한 임시 쿼리를 실행해 왔습니다. 이제 엔지니어링 팀은 비즈니스 분석 보고를 용이하게 하기 위해 Amazon Redshift로 데이터를 스트리밍하여 이 데이터를 지속적으로 복제하고 해당 데이터베이스를 페타바이트 규모의 데이터 웨어하우스로 통합하려고 합니다.
솔루션 아키텍트로서 다음 중 기본 인프라를 관리할 필요 없이 개발 시간이 가장 적게 소요되는 가장 리소스 효율적인 솔루션으로 무엇을 추천하시겠습니까?
- (정답) AWS Database Migration Service를 사용하여 데이터베이스에서 Amazon Redshift로 데이터 복제
- AWS EMR을 사용하여 데이터베이스에서 Amazon Redshift로 데이터 복제
- Amazon Kinesis Data Streams를 사용하여 데이터베이스에서 Amazon Redshift로 데이터 복제
- (오답) AWS Glue를 사용하여 데이터베이스의 데이터를 Amazon Redshift로 복제
```
AWS Database Migration Service를 사용하여 데이터를 Amazon Redshift 데이터베이스로 마이그레이션할 수 있습니다. Amazon Redshift는 클라우드에서 페타바이트 규모의 완전 관리형 데이터 웨어하우스 서비스입니다. Amazon Redshift 데이터베이스를 대상으로 사용하면 지원되는 다른 모든 소스 데이터베이스에서 데이터를 마이그레이션할 수 있습니다.

오답
- EMR은 맵/리듀스 서비스임
- Kinesis는 실시간 데이터 스트리밍 서비스임
- Glue는 고객이 분석을 위해 데이터를 쉽게 준비하고 로드할 수 있는 완전 관리형 ETL(추출, 변환 및 로드) 서비스입니다. AWS Glue 작업은 일괄 ETL 데이터 처리에 사용됩니다. AWS Glue를 사용하려면 데이터베이스 데이터를 Redshift로 복사하는 사용자 지정 마이그레이션 스크립트를 작성하기 위한 상당한 개발 노력이 필요합니다.
```

## 65. (review required)
한 회사는 여러 EC2 인스턴스에서 액세스할 Amazon EFS 파일 시스템으로 비즈니스 크리티컬 데이터를 옮겼습니다.
다음 중 AWS 공인 솔루션스 아키텍트 어소시에이트로서 허용된 EC2 인스턴스만 EFS 파일 시스템에서 읽을 수 있도록 액세스 제어하도록 무엇을 권장합니까? (3개 선택)
- (정답) 파일 시스템에 IAM 정책을 부착해 필요한 권한으로 파일 시스템을 들어갈 수 있는 클라이언트를 제어
- (선택/정답) EFS 액세스 포인트를 사용하여 애플리케이션 액세스를 관리
- Amazon GuardDuty를 사용하여 EFS 파일 시스템에 대한 원치 않는 액세스를 억제
- (선택) 네트워크 ACL을 사용하여 Amazon EC2 인스턴스로 들어오고 나가는 네트워크 트래픽을 제어
- IAM 정책 루트 자격 증명을 설정하여 EFS 파일 시스템에 액세스하는 클라이언트를 제어 및 구성
- (정답) VPC 보안 그룹을 사용해 파일 시스템과 주고받는 네트워크 트래픽을 제어
```
EFS 파일 시스템에 액세스할 수 있는 EC2 인스턴스를 제어하기 위해 VPC 보안 그룹 규칙과 IAM 정책을 사용합니다.
파일 시스템과 주고받는 네트워크 트래픽을 제어하기 위해 VPC 보안 그룹을 사용합니다.
파일 시스템에 들어갈 수 있는 클라이언트와 해당 권한을 제어하기 위해 IAM 정책을 파일 시스템에 연결하고 애플리케이션 액세스 관리를 위해서 EFS 액세스 포인트를 사용합니다.
파일 및 디렉토리에 대한 액세스를 POSIX 호환 사용자 및 그룹 수준 권한으로 제어합니다.

오답
- GuardDuty는 계정, 워크로드 및 Amazon S3에 저장된 데이터를 보호하기 위한 서비스이며 EFS는 해당하지 않음
- 네트워크 ACL은 인스턴스 수준(보안그룹)이 아닌 서브넷 수준에서 작동 (https://docs.aws.amazon.com/ko_kr/vpc/latest/userguide/VPC_Security.html#VPC_Security_Comparison)

[참고] Amazon EFS의 보안
https://docs.aws.amazon.com/ko_kr/efs/latest/ug/security-considerations.html
```