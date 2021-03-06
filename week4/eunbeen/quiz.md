### 1. 질문 ( 3 )

> 한 회사는 여러 EC2 인스턴스에서 액세스할 Amazon EFS 파일 시스템으로 비즈니스 크리티컬 데이터를 옮겼습니다.
다음 중 AWS 공인 솔루션스 아키텍트 어소시에이트로서 허용된 EC2 인스턴스만 EFS 파일 시스템에서 읽을 수 있도록 액세스 제어하도록 무엇을 권장합니까? (3개 선택)
> 
- IAM 정책 루트 자격 증명을 설정하여 EFS 파일 시스템에 액세스하는 클라이언트를 제어 및 구성
- **VPC 보안 그룹을 사용해 파일 시스템과 주고받는 네트워크 트래픽을 제어**
- 네트워크 ACL을 사용하여 Amazon EC2 인스턴스로 들어오고 나가는 네트워크 트래픽을 제어
- Amazon GuardDuty를 사용하여 EFS 파일 시스템에 대한 원치 않는 액세스를 억제
- **파일 시스템에 IAM 정책을 부착해 필요한 권한으로 파일 시스템을 들어갈 수 있는 클라이언트를 제어**
- **EFS 액세스 포인트를 사용하여 애플리케이션 액세스를 관리**

```
Amazon EFS 파일 시스템
- 서버리스 Elastic File SystemAWS 클라우드서비스 및 온프레미스 소스
- 애플리케이션ㅇ르 중단하지 않고 온디맨드 방식으로 페타바이트 규모까지 확장되도록 구축되어, 사용자가 파일을 추가하고 제거할 떄 자동으로 확장/축소
- 파일 시스템을 빠르고 쉽게 만들고 구성할 수 있는 웹 서비스 인터페이스 존재

VPC

오답 이유
IAM 정책 루트 자격 증명을 설정하여 EFS 파일 시스템에 액세스하는 클라이언트를 제어 및 구성
- IAM 정책 루트 자격 증명과 같은 것은 없으며 이 문은 방해하기 위해 추가되었습니다.
네트워크 ACL을 사용하여 Amazon EC2 인스턴스로 들어오고 나가는 네트워크 트래픽을 제어
- 네트워크 ACL은 인스턴스 수준이 아닌 서브넷 수준에서 작동합니다.
Amazon GuardDuty를 사용하여 EFS 파일 시스템에 대한 원치 않는 액세스를 억제
- Amazon GuardDuty 위협 감지 서비스로 AWS 계정, 워크로드 및 Amazon S3에 저장된 데이터를 보호하기 위해 악의적인 활동 및 무단 동작을 지속적으로 모니터링합니다.
EFS 파일 시스템에 대한 액세스 제어에는 사용할 수 없습니다.
```

### 2. 질문 ( 6 )

> 여러분의 회사에서는 Elastic Beanstalk에서 실행되는 웹 사이트를 배포하고 있습니다. 웹사이트 설치에 45분 이상이 소요되며 과정에서 생성되어야 하는 static 및 동적 파일이 모두 포함되어 있습니다.
> 
> 
> 솔루션 아키텍트로서 여러분은 Elastic Beanstalk 배포에서 새 인스턴스를 생성하는 시간을 2분 미만으로 만들고 싶습니다. 이 요구 사항에 대한 솔루션을 구축하려면 다음 중 어떤 옵션을 결합해야 할까요? (2개 선택)
> 
- **EC2 사용자 데이터를 사용하여 부팅 시 동적 설치 부분을 사용자 지정**
- EC2 사용자 데이터를 사용하여 부팅 시 애플리케이션 설치
- Elastic Beanstalk 배포 캐싱 기능5 사용
- 설치 파일을 S3에 저장하여 신속하게 검색
- **Static 설치 구성 요소가 이미 설정된 Golden AMI 생성**

```
Elastic Beanstalk
- 애플리케이션을 실행하는 인프라에 대해 자세히 알지 못해도 AWS 클라우드에서 애플리케이션을 신속하게 배포하고 관리할 수 있음
- 선택 또는 제어에 대한 제한없이 관리 복잡성을 줄일 수  있음
- 용량 프로비저닝, 로드 밸런싱 등 세부 정보를 자동으로 처리
- 추가 비용이 없고 AWS 리소스에 대한 비용만 지불하면 됨

AMI
- Amazon Machine Image로 인스턴스를 시작하는 데 필요한 정보를 제공

사용자 지정 AMI
- 표준 AMI에 포함되어 있지 않은 여러 소프트웨어를 설치해야 할 경우 환경에서 인스턴스 시작시 프로비저닝 시간 향상 가능
- 구성 파일에 적용하기까지 오래 걸리거나 구현 어려운 하위 수준 구성 요소(Linux 커널) 변경 가능
- 생성 방법 : Elastic Beanstalk 플랫폼 AMI를 시작 (표준 AMI 대신 사용 가능)

Golden AMI
- OS 영역을 포함해 필수 패키지가 설치된 일종의 표준화하는 AMI

EC2 사용자 데이터
- 인스턴스 시작할 떄 구성 스크립트 형식으로 지정한 데이터
- 부팅 시 애플리케이션 자체를 설치하는 대신 EC2 사용자 데이터 사용해 부팅 시 동적 설치 부분 사용자 지정 가능

[오답]
S3
- 환경이 아니라 스토리지 서비스 => 동적 파일 실행하거나 생성하는데 사용할 수 없음
EC2 사용자 데이터를 사용하여 부팅 시 애플리케이션 설치
- 설치 프로세스 중 생성되어야 하는 파일이 포함된 설치에는 오래 걸림
Elastic Beanstalk 배포 캐싱 기능5 사용
- 구성 옵션?
```

### 3. 질문 ( 7 )

> 최근 AWS 리소스의 보안을 개선하기 위해 한 금융 서비스 회사는 이니셔티브를 시작했으며 회사가 소유한 여러 AWS 계정에서 AWS Shield Advanced를 활성화했습니다. 분석을 통해 회사는 예상보다 훨씬 높은 비용이 발생했다는 것을 발견했습니다.
> 
> 
> 다음 중 AWS Shield Advanced 서비스에 대해 예상치 못한 높은 비용의 근본적인 이유는 무엇일까요?
> 
- 비용 절감 계획은 모든 AWS 계정에서 AWS Shield Advanced 서비스에 대해 활성화되지 않았습니다.
- **통합 결제가 활성화되지 않았습니다. 모든 AWS 계정은 월별 요금이 한 번만 청구되는 1회 통합 결제를 해야 합니다.**
- AWS Shield Advanced는 AWS 클라우드의 일부가 아닌 사용자 지정 서버에 사용되므로 증가한 비용이 발생합니다.
- AWS Shield Advanced는 AWS Shield Standard 플랜도 포함하므로 증가한 비용이 발생합니다.

```
AWS Shield
- AWS에서 실행되는 웹 애플리케이션을 DDoS 공격으로부터 보호하는 관리형 서비스
- AWS Shield Standard : 추가 비용없이 모든 AWS 고객에게 자동으로 활성화

AWS Shield Advanced
- 선택 가능한 유료 서비스 (EC2, ELB, Route 53등에 실행되는 애플리케이션을 목표로하는 정교하고 큰 규모 공격 대한 추가적인 보호)
- 여러 AWS 계정을 개별적으로 활성화 해 AWS Shield Advanced에 구독할 수 있음

Savings Plans
- 1년 또는 3년 기간에 특정 사용량 약성(시간당 USD 요금)을 조건으로, 온디맨드 요금에 비해 보다 저렴한 요금을 제공하는 유연한 요금 모델
- EC2, Lambda 및 Fargate 사용량에 제공함 ?

```

### 4. 질문 ( 11 )

> 한 선도적인 소셜 미디어 회사에 속한 DevOps 팀은 완전 관리형 구성 관리 서비스인 AWS OpsWorks를 사용합니다. OpsWorks를 사용하면 구성 관리 시스템을 운영하거나 인프라 유지 관리에 대해 걱정할 필요가 없습니다.
> 
> 
> 여러분은 OpsWorks가 관리형 인스턴스를 제공하는 구성 관리 도구를 식별할 수 있을까요? (2개 선택)
> 
- Ansible
- Salt
- CFEngine
- **Chef**
- **Puppet**

```
AWS OpsWorks
- Chef및 Puppet의 관리형 인스턴스를 제공하는 구성 관리 서비스
- Chef및 Puppeㅅ을 통해 EC2 인스턴스 및 온프레미스 컴퓨팅 환경 전체에서 서버가 구성, 배포 밎 관리되는 방법을 자동화 가능

Chef 및 Puppet
- 코드를 사용해 서버 구성을 자동화할 수 있게 해주는 자동화 플랫폼
```

### 5. 질문 ( 12 )

> 한 소매 회사는 향후 48시간 내에 글로벌 애플리케이션을 위한 블루-그린 배포를 롤아웃하고 테스트하려고 합니다. 대부분의 고객은 휴대폰을 사용해 DNS 캐싱에 취약합니다. 이 회사는 연례 추수감사절 세일이 시작되기까지 단 이틀밖에 남지 않았습니다.
> 
> 
> 솔루션 아키텍트로서 주어진 시간 내에 최대한 많은 사용자를 대상으로 배포를 테스트하기 위해 다음 중 어떤 옵션을 권장하시겠습니까?
> 
- Elastic Load Balancer를 사용하여 배포 간에 트래픽 분산
- Route 53 가중 라우팅을 사용하여 여러 배포에 트래픽
- **AWS Global Accelerator를 사용하여 트래픽의 일부를 특정 배포에 배포**
- AWS CodeDeploy 배포 옵션을 사용하여 올바른 배포 선택

```
블루/그린 배포
- 서로 다른 버전의 애플리케이션을 실행하는 두 개의 동일한 환경 간에 트래픽을 이용해 애플리케이션을 릴리스 하는 기술
- 블루 : 현재 실행 중인 버전
- 그린 : 새 버전
- 그린 버전이 제대로 작동하는 것으로 확인되면 이전 블루 환경에서 새 그린 환경으로 트래픽을 점진적으로 다시 라우팅
- 단점 : 레코드를 업데이트하거나 라우팅 기본 설정을 변경하거나 애플리케이션 오류가 있을 경우 사용자가 업데이트 된 IP 주소를 받기까지 얼마나 걸릴지 모름

AWS Global Accelerator
- AWS 글로벌 네트워크를 통해 트래픽을 최적의 엔드포인트로 보내는 네트워크 계층 서비스
- 인터넷 애플리케이션의 가용성과 성능을 향상
- 클라이언트 디바이스 및 인터넷 리졸버의 DNS 캐싱에 영향 받지 않고 블루/그린 환경 간에 트래픽 점진적 이동 가능

Route53 가중 라우딩
- DNS 캐싱과 관련없음
- 여러 리소스를 단일 도메인 이름 또는 하위 도메인 이름과 연결 후 각 리소스로 라우팅되는 트래픽 양 선택 가능

Elastic Load Balancer
- DNS 서비스에 의존하지 않음
- 다중지역 솔루션에 사용 불가

AWS CodeDeploy
- 배포는 하나 이상의 인스턴스에 콘텐츠를 설치하는 프로세스 및 프로세스와 관련된 구성 요소
- 인스턴스간 실시간 트래픽 분산 기능 x 
- 배포만 담당
```

### 6. 질문 ( 14 )

> 매체 회사는 AWS VPC에 대한 AWS Direct Connect 연결을 사용하는 온프레미스 데이터 센터와 함께 로스앤젤레스에 본사를 두고 있습니다. 샌프란시스코와 마이애미에 위치한 지사는 Site-to-Site VPN 연결을 사용하여 AWS VPC에 연결합니다. 회사는 지사는 물론이고 지점 간에도 데이터를 주고받을 수 있는 솔루션을 찾고 있습니다.
> 
> 
> 솔루션 아키텍트로서 다음 AWS 서비스 중 이 사용 사례를 처리하는 것에 무엇이 좋을까요?
> 
- **VPN 클라우드허브**
- 소프트웨어 VPN
- VPC 엔드포인트
- VPC 피어링

```
AWS VPC
- 사용자의 AWS 계정 전용 가상 네트워크
- 사용자가 정의한 가상 네트워크로 AWS 리소스를 시작할 수 있음

VPN 클라우드허브
- Site-to-Site VPN 연결이 여러개 있을 경우 클라우드 허브를 사용해 사이트 간에 보안 통신 제공 가능
- 원격 사이트가 VPC뿐 아니라 서로 통신도 가능!

소프트웨어 VPN
- 원격 네트워크와 Amaxon VPC 간의 연결만 처리 -> 원격 지사 간 데이터 주고 받기 제어 X

VPC 엔드포인트
- VPC와 다른 AWS 서비스 간의 트래픽은 Amazon 네트워크를 벗어나지 않으므로 옵션 사용해 회사 원격 지사 간 데이터 주고받기 X

VPC 피어링
- AWS 네트워크 내에서 두 VPC 간의 연결을 용이하게 하므로 옵션 사용해 회사의 원격 지사 간 데이터 주고받기 X

```

### 7. 질문 ( 15 )

> 전자 상거래 회사의 엔지니어링 팀은 일괄 처리를 통해 SQS 표준 Queues에서 FIFO Queues로 마이그레이션하려고 합니다.
> 
> 
> 솔루션 아키텍트로서 마이그레이션 체크리스트에 다음 단계 중 어떤 단계를 포함하시겠습니까? (3개 선택)
> 
- 대상 FIFO Queues의 처리량이 초당 300개 메시지를 초과하지 않는지 확인
- 기존 표준 Queues을 FIFO Queues로 변환
- **FIFO Queues의 이름이.fifo 접미사로 끝나는지 확인**
- **기존 표준 Queues을 삭제하고 FIFO Queues로 다시 생성**
- **대상 FIFO Queues의 처리량이 초당 3,000개 메시지를 초과하지 않는지 확인**
- FIFO Queues의 이름이 표준 Queues과 동일한지 확인

```
Amazon Simple Queue Service(SQS)
- 마이크로서비스, 분산 시스템 및 서버리스 애플리케이션을 분리하고 스케일할 수 있는 완전관리형 메시지 Queues 서비스
- 메시지 손실이나 다른 서비슬르 사용할 필요 없이 모든 볼륨의 소프트웨어 구성 요소 간에 메시지 보내고, 저장하고, 받을 수 있음

표준 Queues
- 최대 처리량, 최선형 주문 및 최소 한 번 배달 요청

SQS FIFO Queues
- 메시지가 전송된 정확한 순서로 정확히 한 번 처리
- 일괄 처리 사용 : 초당 최대 3000개의 메시지 지원
- 일괄 처리 사용 x : 초당 최대 300개의 메시지 지원
- 이름은 .fifo 접미사로 끝내야 함(접미사는 80자 이름 제한 존재) -> queues가 fifo인지 확인하기 위함
- 기존 queues를 FIFO Queues로 변호나 분가(삭제 후 재 생성)
```

### 8. 질문 ( 19 )

> 한 IT 회사는 Amazon Redshift를 사용하여 소매 조직을 위한 사용자 지정 데이터 웨어하우징 솔루션을 구축했습니다. 비용 최적화의 일환으로 회사는 일일 분석 보고서가 지난 1년 동안의 데이터를 사용하기 때문에 모든 과거 데이터(1년보다 오래된 모든 데이터)를 S3로 이동하려고 합니다. 그러나 분석가는 일일 보고서와 함께 이 과거 데이터를 상호 참조할 수 있는 기능을 유지하기를 원합니다.
> 
> 
> 회사는 최소한의 노력과 최소 비용으로 솔루션을 개발하고자 합니다. 솔루션 아키텍트로서 이 사용 사례를 촉진하기 위해 어떤 옵션을 추천하시겠습니까?
> 
- Redshift COPY 명령을 사용하여 S3 기반 기록 데이터를 Redshift로 로드합니다. 기록 데이터에 대해 임시 쿼리가 실행되면 Redshift에서 제거할 수 있습니다.
- **Redshift Spectrum을 사용하여 S3의 기본 기록 데이터를 가리키는 Redshift 클러스터 테이블을 생성합니다. 그런 다음 분석 팀은 이 기록 데이터를 쿼리하여 Redshift의 일일 보고서와 상호 참조할 수 있습니다.**
- Athena를 통해 기록 데이터에 대한 액세스를 설정합니다. 분석 팀은 Athena에서 과거 데이터 쿼리를 실행하고 Redshift에서 일일 보고를 계속할 수 있습니다. 보고서를 상호 참조해야 하는 경우 분석 팀은 이를 플랫 파일로 내보낸 다음 추가 분석을 수행해야 합니다.
- Glue ETL 작업을 사용하여 S3 기반 기록 데이터를 Redshift로 로드합니다. 기록 데이터에 대해 임시 쿼리가 실행되면 Redshift에서 제거할 수 있습니다.

```
Amazon Redshift
- 대규모 데이터 세트 저장 및 분석을 위해 설계된 완전 관리형 페타바이트 규모의 클라우드 기반 데이터 웨어하우스 제품

Amazon Redshift Spectrum
- Amazon Redshift 테이블에 데이터를 로드할 필요 없이 Amazon S3의 파일에서 구조화 및 반구조화 데이터를 효율적으로 쿼리하고 검색 가능
- 클러스터와 독립적인 전용 Amazon Redshift 서버에 존재
- 동일한 결과를 보다 비용 효율적으로 얻을 수 있음

모르겠네요..😥
```

### 9. 질문 ( 24 )

> 빅 데이터 분석 회사는 Kinesis Data Streams(KDS)를 사용하여 농업 과학 회사의 필드 장치에서 IoT 데이터를 처리하고 있습니다. 여러 소비자 애플리케이션이 들어오는 데이터 스트림을 사용하고 있으며 엔지니어는 데이터 스트림의 생산자와 소비자 간의 데이터 전달 속도에서 성능 지연을 발견했습니다.
> 
> 
> 솔루션 아키텍트로서 주어진 사용 사례의 성능을 개선하기 위해 다음 중 어떤 것을 권장하시겠습니까?
> 
- Kinesis Data Firehose로 Kinesis Data Streams 교체
- SQS 표준 Queues로 Kinesis Data Streams 교체
- **Kinesis Data Streams의 향상된 팬아웃 기능 사용**
- SQS FIFO Queues로 Kinesis Data Streams 교체

```
Amazon Kinesis Data Streams(KDS)
- 스케일성과 내구성이 뛰어난 실시간 데이터 스트리밍 서비스
- 웹사이트 클릭스트림, 데이터베이스 이벤트 스트림, 금융 거래, 소셜 미디어 피드, IT 로그 및 위치 추적 이벤트와
  같은 수십만 개의 소스에서 초당 기가바이트의 데이터를 지속적으로 캡처 가능

팬아웃 기능
- 특정 채널을 통해 input이 들어왔을 때 여러 개의 task로 분산 처리
- 여러 소비자가 스트림에서 병렬로 데이터를 검색하는 경우 향상된 팬아웃 사용해야 함

너무 어렵네요...😥
```

### 10. 질문 ( 27 )

> 팀의 새 개발자에게 DynamoDB의 전체 액세스 권한이 할당된 사건이 보고된 이후 한 IT 회사는 보안 모범 사례를 검토하려고 합니다. 개발자는 새로운 기능을 구축하는 동안 실수로 프로덕션 환경에서 몇 개의 테이블을 삭제했습니다.
> 
> 
> 이러한 사고가 다시 발생하지 않도록 이 문제를 해결하는 **가장** 효과적인 방법은 무엇일까요?
> 
- 루트 사용자만 조직에서 전체 데이터베이스 액세스 권한을 가져야 한다.
- 조직의 모든 IAM 사용자에 대한 전체 데이터베이스 액세스를 제거한다.
- CTO는 이러한 인시던트가 반복되지 않도록 각 새 개발자의 IAM 사용자에 대한 권한을 검토한다.
- **권한 경계를 사용하여 직원이 IAM 보안 주체에게 부여할 수 있는 최대 권한을 제어한다.**

```
권한 경계
- 직원이 만들고 관리하는 IAM 보안 주체(즉, 사용자 및 역할)에 부여할 수 있는 최대 권한을 제어하는 데 사용

IAM 관리자
- 관리형 정책을 사용하여 하나 이상의 권한 경계를 정의하고 직원이 이 경계로 보안 주체를 생성하도록 허용 가능
```
