# 4주차 모의고사 풀이

## 1.
소매 기관에서 일부 온-프레미스 데이터를 AWS 클라우드로 이동하고 있습니다. 조직의 DevOps 팀은 인터넷을 통해 원격 온-프레미스 네트워크와 Amazon VPC 간에 AWS Managed IPSec VPN 연결을 설정했습니다.
다음 중 IPSec VPN 연결에 대한 올바른 구성을 나타내는 것은 무엇일까요?
- VPN의 AWS 측에 Virtual Private Gateway 생성 및 VPN의 온프레미스 측에 고객 게이트웨이 생성
- (관련?) https://blog.bespinglobal.com/post/aws-site-to-site-vpn-with-openswam/

## 2.
최근 AWS 리소스의 보안을 개선하기 위해 한 금융 서비스 회사는 이니셔티브를 시작했으며 회사가 소유한 여러 AWS 계정에서 AWS Shield Advanced를 활성화했습니다. 분석을 통해 회사는 예상보다 훨씬 높은 비용이 발생했다는 것을 발견했습니다.

다음 중 AWS Shield Advanced 서비스에 대해 예상치 못한 높은 비용의 근본적인 이유는 무엇일까요?
- 비용절감 계획은 모든 AWS 계정에서 AWS Shiled Advanced 서비스에 대해서 활성화되지 않았습니다.

## 3.
사이버 보안 회사는 EC2 인스턴스의 단일 Spread 배치 그룹을 사용하여 mission critical 애플리케이션을 실행하고 있습니다. 회사는 최적의 성능을 위해 15개의 Amazon EC2 인스턴스가 필요합니다.
회사는 주어진 사용 사례 당 이러한 EC2 인스턴스를 배포하는 데 몇 개의 가용 영역(AZ)이 필요합니까?
- 3

## 4. 
한 IT 회사는 Amazon Redshift를 사용하여 소매 조직을 위한 사용자 지정 데이터 웨어하우징 솔루션을 구축했습니다. 비용 최적화의 일환으로 회사는 일일 분석 보고서가 지난 1년 동안의 데이터를 사용하기 때문에 모든 과거 데이터(1년보다 오래된 모든 데이터)를 S3로 이동하려고 합니다. 그러나 분석가는 일일 보고서와 함께 이 과거 데이터를 상호 참조할 수 있는 기능을 유지하기를 원합니다.
회사는 최소한의 노력과 최소 비용으로 솔루션을 개발하고자 합니다. 솔루션 아키텍트로서 이 사용 사례를 촉진하기 위해 어떤 옵션을 추천하시겠습니까?
- Redshift Spectrum을 사용하여 S3의 기본 기록 데이터를 가리키는 Redshift 클러스터 테이블을 생성합니다. 그런 다음 분석 팀은 이 기록 데이터를 쿼리하여 Redshift의 일일 보고서와 상호 참조할 수 있습니다.

## 5.
한 뉴스 네트워크는 Amazon S3를 사용해 미국 전역의 보고 팀의 원본 영상을 합칩니다. 뉴스 네트워크는 최근 유럽과 아시아의 새로운 지역으로 확장되었습니다. 해외 지사의 기술 팀은 목적지인 S3 버킷에 대용량 비디오 파일을 업로드할 때 상당한 지연이 있다고 보고했습니다.
다음 중 S3로의 파일 업로드 속도 향상에 가장 비용 효율적인 옵션은 무엇일까요? (2개 선택)
- AWS S3 Trancfer Acceleration 사용
- AWS 글로벌 액셀러레이터 사용 

## 6.
Elastic Load Balancer 배후의 EC2 인스턴스에서 호스팅되는 소셜 사진 공유 웹 애플리케이션이 있습니다. 이 앱은 사용자에게 사진 업로드 기능을 제공하고 앱 홈페이지에 리더보드를 표시합니다. 업로드된 사진은 S3에 저장되고 리더보드 데이터는 DynamoDB에 유지됩니다. 이러한 기능을 위해 EC2 인스턴스는 S3와 DynamoDB에 모두 액세스해야 합니다.
솔루션 아키텍트로서 다음 솔루션 중 가장 안전한 옵션은 무엇일까요?
- 인스턴스가 S3 및 DynamoDB에 액세스할 수 있도록 적절한 IAM 역할을 EC2 인스턴스 프로파일에 연결합니다.

## 7.
한 선도적인 소셜 미디어 분석 회사는 고정된 애플리케이션 스택을 AWS 클라우드로 이전하는 것을 고려하고 있습니다. 해당 회사는 Fargate 시작 유형의 Elastic Container Service(ECS)와 비교해 EC2 시작 유형의 Elastic Container Service(ECS) 사용 요금에 대해 확신하지 못합니다.
이 두 서비스의 가격 책정에 대한 설명으로 옳은 것은?

EC2 시작 유형의 ECS는 사용된 EC2 인스턴스 및 EBS 볼륨에 따라 요금이 부과됩니다. Fargate 시작 유형의 ECS는 컨테이너화된 애플리케이션이 요청하는 vCPU 및 메모리 리소스에 따라 요금이 부과됩니다.

## 8.
개발 팀이 ECS에 마이크로서비스를 배포했습니다. 애플리케이션 계층은 애플리케이션 로드 밸런서를 통해 static 및 동적 콘텐츠를 모두 제공하는 Docker 컨테이너에 있습니다. 로드가 증가함에 따라 ECS 클러스터는 더 높은 네트워크 사용량을 경험하고 있습니다. 개발 팀은 네트워크 사용을 조사한 결과 90%가 애플리케이션의 static 콘텐츠 배포로 인한 것임을 발견했습니다.
솔루션 아키텍트로서 애플리케이션의 네트워크 사용량을 개선하고 비용을 절감하기 위해 무엇을 권장하시겠습니까?
- Amazon S3를 통해 static 콘텐츠 배포

## 9.
한 의료 스타트업은 Amazon S3에 저장된 객체에 대한 규정 준수 및 규제 지침을 시행해야 합니다. 주요 요구 사항 중 하나는 적절한 보호를 제공해 실수로 개체를 삭제하지 않도록 하는 것입니다.
솔루션 아키텍으로서 이러한 지침을 다루기 위해 무엇을 권장하시겠습니까? (2개 선택)
- 버킷에서 버전 관리 활성화
- 버킷에서 MFA 삭제 활성화

## 10.
한 매체 회사는 자체 IT 인프라를 소유하고 유지 관리하는 비즈니스에서 벗어나고 싶어합니다. 이 디지털 혁신의 일환으로 매체 회사는 온-프레미스 데이터 센터에 있는 약 5PB의 데이터를 내구성 있는 장기 스토리지에 보관하기를 원합니다.
솔루션 아키텍트로서 가장 비용 최적화된 방식으로 이 데이터를 마이그레이션하기 위해 무엇을 권장하시겠습니까
- 온-프레미스 데이터를 여러 Snowball Edge Storage Optimized 디바이스로 전송합니다. Snowball Edge 데이터를 AWS Glacier로 복사

## 11.
한 빅 데이터 분석 회사는 Amazon S3 버킷에 데이터와 로그 파일을 write합니다. 이제 회사는 기존 데이터 파일과 진행 중인 파일 업데이트를 Amazon S3에서 Amazon Kinesis Data Streams로 스트리밍하려고 합니다.
솔루션 아키텍트로서 다음 중 이 요구 사항에 대한 솔루션을 구축하는 가장 빠른 방법으로 제안할 수 있는 것은 무엇일까요?
- AWS Database Migration Service(AWS DMS)를 Amazon S3와 Amazon Kinesis Data Streams 간의 다리 역할로 활용합니다.

## 12. 
빅 데이터 분석 회사는 Kinesis Data Streams(KDS)를 사용하여 농업 과학 회사의 필드 장치에서 IoT 데이터를 처리하고 있습니다. 여러 소비자 애플리케이션이 들어오는 데이터 스트림을 사용하고 있으며 엔지니어는 데이터 스트림의 생산자와 소비자 간의 데이터 전달 속도에서 성능 지연을 발견했습니다.

솔루션 아키텍트로서 주어진 사용 사례의 성능을 개선하기 위해 다음 중 어떤 것을 권장하시겠습니까?

- Kinesis Data Firehose로 Kinesis Data Streams 교체


## 13.
전자 상거래 회사에 소속된 엔지니어링 팀은 서버리스 아키텍처로 마이그레이션하는 임무를 받았습니다. 팀은 이 아키텍처의 중추 역할로 Lambda를 사용할 때 고려해야 할 핵심 사항에 중점을 두고자 합니다.
솔루션 아키텍트로서 다음 중 주어진 요구 사항에 맞는 것으로 식별할 수 있는 옵션은 무엇일까요? (3개 선택)
- Lambda 함수는 매우 빠르게 스케일될 수 있으므로 ConcurrentExecutions 또는 Invocations와 같은 함수 metrics가 예상 임계값을 초과할 때 팀에 알리는 CloudWatch 경보를 배포하는 것이 좋습니다.
- 배포 패키지가 클수록 Lambda 함수가 콜드 스타트하는 속도가 느려집니다. 따라서 AWS는 종속성을 실제 Lambda 패키지와 별도의 패키지로 패키징할 것을 제안합니다.
- 둘 이상의 Lambda 함수에서 코드를 재사용하려는 경우 재사용 가능한 코드에 대한 Lambda 계층 생성을 고려해야 합니다.


## 14. 
스타트업의 클라우드 인프라는 몇 개의 Amazon EC2 인스턴스, Amazon RDS 인스턴스 및 Amazon S3 스토리지로 구성됩니다. 사업 운영을 시작한 지 1년이 되었을 때 이 신생 기업은 비즈니스 요구 사항에 비해 너무 높아 보이는 비용을 발생시키고 있습니다.

다음 중 유효한 비용 최적화 솔루션을 나타내는 옵션은 무엇일까요?
- AWS Cost Explorer Resource Optimization을 사용하여 유휴 상태이거나 사용률이 낮은 EC2 인스턴스에 대한 보고서를 받고 AWS Compute Optimizer를 사용하여 인스턴스 유형 권장 사항을 확인합니다.


## 15. 
한 매체 회사는 UDP 프로토콜을 사용하는 독점 응용 프로그램을 통해 전달되는 라이브 스포츠 결과를 배포하기 위해 대기 시간이 짧은 방법을 원합니다.

솔루션 아키텍트로서 다음 중 이 사용 사례에 대해 최상의 성능을 제공하도록 권장하는 솔루션은 무엇일까요?
- Global Accelerator를 사용하여 실시간 스포츠 결과를 배포하는 짧은 대기 시간 방법 제공


## 16.
한 빅 데이터 분석 회사는 AWS 클라우드 아키텍처를 설정해 갑작스러운 트래픽 급증 시 요청을 조절하려고 합니다. 회사는 이러한 트래픽 변동을 대비한 버퍼링 또는 조절에 사용할 수 있는 AWS 서비스를 찾고 있습니다.

다음 중 이 요구 사항을 지원할 수 있는 서비스는 무엇일까요?
- Elastic 로드 밸런서, Amazon SQS, AWS Lambda


## 17.
회사는 EC2 인스턴스와 독립적인 영구 스토리지를 제공하는 EBS 볼륨에 비즈니스 크리티컬 데이터를 저장하려고 합니다. 테스트 실행 중에 개발 팀은 예상과 달리 EC2 인스턴스를 종료할 때 첨부된 EBS 볼륨도 손실되는 것을 발견했습니다.

솔루션 아키텍트로서 이 문제를 설명해 주시겠습니까?
- EBS 볼륨은 Amazon EC2 인스턴스의 루트 볼륨으로 구성되었습니다. 인스턴스 종료 시 기본 동작은 연결된 루트 볼륨도 종료하는 것입니다.

## 18.
전자 상거래 스타트업의 개발 팀은 Elastic Load Balancer의 EC2 인스턴스에서 실행되는 여러 마이크로서비스를 설정했습니다. 팀은 요청 내용을 기반으로 트래픽을 여러 백엔드 서비스로 라우팅하려고 합니다.

다음 중 요청 내용에 따라 라우팅을 허용하는 로드 밸런서 유형은 무엇일까요?
- ALB

## 19. 
선도적인 온라인 게임 회사는 자사의 온라인 게임을 전 세계 사용자에게 제공하기 위해 주력 애플리케이션을 AWS 클라우드로 마이그레이션하고 있습니다. 이 회사는 Network Load Balancer, NLB (네트워크 로드 밸런서)를 사용하여 초당 수백만 건의 요청을 처리하려고 합니다. 엔지니어링 팀은 퍼블릭 서브넷에 여러 인스턴스를 프로비저닝하고 이러한 인스턴스 ID를 NLB의 대상으로 지정했습니다.

솔루션 아키텍트로서 엔지니어링 팀이 이러한 대상 인스턴스에 대한 올바른 라우팅 메커니즘을 이해하도록 도울 수 있을까요?
- 트래픽은 인스턴스의 기본 네트워크 인터페이스에 지정된 기본 프라이빗 IP 주소를 사용하여 인스턴스로 라우팅됩니다.

## 20.
회사는 Auto Scaling 그룹과 함께 애플리케이션 로드 밸런서 배후에서 EC2 서버를 실행합니다. 회사의 엔지니어는 각 인스턴스에 독점 도구를 설치하고 Auto Scaling 정책의 스케일 이벤트로 인해 인스턴스가 프로비저닝될 때마다 이러한 도구의 사전 활성화 상태 확인을 수행할 수 있기를 원합니다.

다음 중 이 사용자 지정 작업을 활성화하는 데 사용할 수 있는 옵션은 무엇일까요?
- Auto Scaling 그룹 수명 주기 후크를 사용하여 인스턴스를 대기 상태로 전환하고 독점 forensic 도구를 설치하고 사전 활성화 상태 확인을 수행하는 사용자 지정 스크립트를 시작합니다.