# 4주차 모의고사

## 61.
AWS 계정 B의 Amazon S3 버킷에 액세스하는 AWS 계정 A의 Lambda 함수를 개발자는 구현해야 합니다.
솔루션 아키텍트로서 이 요구 사항을 충족하기 위해 다음 중 어느 것을 권장하시겠습니까?
- S3 버킷에 대한 액세스 권한을 부여하는 Lambda 함수에 대한 IAM 역할을 생성합니다. IAM 역할을 Lambda 함수의 실행 역할로 설정합니다. 버킷 정책이 Lambda 함수의 실행 역할에 대한 액세스 권한 또한 부여하는지 확인합니다.

## 62.
빅데이터 처리 회사는 처리 기계 간의 네트워크 성능이 높을 때 가장 잘 수행되는 분산 데이터 처리 프레임워크를 만들었습니다. 애플리케이션은 AWS에 배포해야 하며 회사는 성능을 핵심 측정 기준으로만 보고 있습니다.
솔루션 아키텍트로서 어떤 배포를 권장합니까?
- 클러스터 배치 그룹 사용
- [클러스터 배치 그룹](https://docs.aws.amazon.com/ko_kr/AWSEC2/latest/UserGuide/placement-groups.html#placement-groups-cluster)
- [Spread 배피 그룹](https://docs.aws.amazon.com/ko_kr/AWSEC2/latest/UserGuide/placement-groups.html#placement-groups-spread)

## 63.
다국적 소매 회사에는 여러 사업부가 있으며 각 사업부에는 자체 AWS 계정이 있습니다. 회사의 엔지니어링 팀은 이러한 AWS 계정에서 데이터를 디버그 및 추적하고 중앙 집중식 계정에서 시각화하려고 합니다.
솔루션 아키텍트로서 다음 중 주어진 사용 사례에 대해 어떤 솔루션을 제안하시겠습니까?
- AWS X-Ray

## 64.
한 소매업 회사는 Amazon EC2 인스턴스, API Gateway, Amazon RDS, Elastic Load Balancer 및 CloudFront 서비스를 사용합니다. 이러한 서비스의 보안을 개선하기 위해 리스크 고문 그룹은 Amazon GuardDuty 서비스 사용의 타당성 확인을 제안했습니다.
다음 중 GuardDuty에서 지원하는 데이터 소스로 식별할 수 있는 것은 무엇일까요?
- VPC 플로우 로그, DNS 로그, CloudTrail 이벤트
- https://docs.aws.amazon.com/guardduty/latest/ug/guardduty_data-sources.html

## 65.
한 회사는 여러 EC2 인스턴스에서 액세스할 Amazon EFS 파일 시스템으로 비즈니스 크리티컬 데이터를 옮겼습니다.
다음 중 AWS 공인 솔루션스 아키텍트 어소시에이트로서 허용된 EC2 인스턴스만 EFS 파일 시스템에서 읽을 수 있도록 액세스 제어하도록 무엇을 권장합니까? (3개 선택)
- EFS 액세스 포인트를 사용하여 애플리케이션 액세스를 관리
- 네트워크 ACL을 사용하여 Amazon EC2 인스턴스로 들어오고 나가는 네트워크 트래픽을 제어
- IAM 정책 루트 자격 증명을 설정하여 EFS 파일 시스템에 액세스하는 클라이언트를 제어 및 구성
- https://docs.aws.amazon.com/ko_kr/efs/latest/ug/security-considerations.html

