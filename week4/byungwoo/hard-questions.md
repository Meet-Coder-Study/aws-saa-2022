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

## 36.
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