# OT 과제 (이병우)

## 1. 시험 안내서 읽기

- [국문](https://d1.awsstatic.com/ko_KR/training-and-certification/docs-sa-assoc/AWS-Certified-Solutions-Architect-Associate_Exam-Guide.pdf)
- [영문](https://d1.awsstatic.com/training-and-certification/docs-sa-assoc/AWS-Certified-Solutions-Architect-Associate_Exam-Guide.pdf)

### 문제1. 대상 응시자는 다음과 같은 지식을 가지고 있어햐 합니다. (6개)

- 컴퓨팅, 네트워킹, 스토리지, 관리 및 데이터베이스 AWS 서비스를 사용한 실무 경험
  - Hands-on experience using compute, networking, storage, management, and database AWS services
- AWS 기술이 포함된 솔루션에 대한 기술 요구 사항을 식별하고 정의할 수 있는 능력
  - The ability to identify and define technical requirements for a solution that involves AWS technology
- 특정 기술 요구 사항을 충족하는 AWS 서비스를 식별하는 능력
  - The ability to identify which AWS services meet a given technical requirement
- AWS 에서 잘 설계된 솔루션을 빌드하기 위한 모범 사례에 대한 이해
  - An understanding of best practices for building well-architected solutions on AWS
- AWS 글로벌 인프라에 대한 이해
  - An understanding of the AWS global infrastructure
- 기존 서비스와 관련된 AWS 보안 서비스 및 기능에 대한 이해
  - An understanding of AWS security services and features in relation to traditional services

### 문제2. 다음 항목은 시험에 포함되지 않습니다. (6개)

- 복잡한 하이브리 네트워크 아키텍처 설계
  - Design a complex, hybrid network architecture
- 여러 계정 내의 자격 증명 연동 설계
  - Design identity federation within multiple accounts
- 규정 준수 요구 사항을 충족하는 아키텍처 설계
  - Design an architecture that meets compliance requirements
- 설계에 전문 서비스 통합
  - Incorporate specialized services in a design
- 배포 전략 개발
  - Develop deployment strategies
- 복잡한 멀티 티어 애플리케이션을 위한 마이그레이션 전략 수립
  - Create a migration strategy for complex multi-tier applications

### 문제3. 출제 영역과 시험비율은 다음과 같습니다.

- 영역 1: 복원력을 갖춘 아키텍처 설계, 30%
  - Design Resilient Architectures
- 영역 2: 고성능 아키텍처 설계, 28%
  - Design High-Performing Architectures
- 영역 3: 안전한 애플리케이션 및 아키텍처 설계, 24%
  - Design Secure Applications and Architectures
- 영역 4: 비용에 최적화된 아키텍처 설계, 18%
  - Design Cost-Optimized Architectures

## 2. AWS SAA C02 샘플 문항

[AWS SAA C02 샘플 문항 (국문)](https://d1.awsstatic.com/ko_KR/training-and-certification/docs-sa-assoc/AWS-Certified-Solutions-Architect-Associate_Sample-Questions.pdf)
[AWS SAA C02 샘플 문항 (영문)](https://d1.awsstatic.com/ko_KR/training-and-certification/docs-sa-assoc/AWS-Certified-Solutions-Architect-Associate_Exam-Guide.pdf)

1. CRM(고객 관계 관리) 애플리케이션은 Application Load Balancer 뒤의 여러 가용 영역에 있는 Amazon EC2 인스턴스에서 실행됩니다. 이러한 인스턴스 중 하나에 장애가 발생하면 어떻게 됩니까?
   A) 로드 밸런서가 장애 발생 인스턴스로 요청을 보내는 것을 중지합니다.
   B) 로드 밸런서가 장애 발생 인스턴스를 종료합니다.
   C) 로드 밸런서가 장애 발생 인스턴스를 자동으로 교체합니다.
   D) 인스턴스가 교체될 때까지 로드 밸런서가 504 게이트웨이 시간 초과 오류를 반환합니다.

```
선택 A, 정답 A 
A) ALB는 healthcheck를 정기적으로 수행한다.
```

2. Amazon SQS 를 분리된 아키텍처로 갖추고 있는 회사에서 비동기 처리를 수행해야 합니다. 이 회사는 폴링 요청의 빈 응답 수를 최소로 유지하려고 합니다. 빈 응답을 줄이려면 솔루션 아키텍트는 어떻게 해야 합니까?
   A) 큐의 메시지 최대 보존 기간을 늘립니다.
   B) 큐의 재드라이브 정책에서 최대 수신 수를 늘립니다.
   C) 큐의 기본 가시성 제한 시간을 늘립니다.
   D) 큐의 수신 메시지 대기 시간을 늘립니다.
```
선택 A, 정답 D
단순히 메시지 보존기간(시간)을 늘리면 된다고 생각했는데 출제의도는 Long Polling을 하도록 설정하는 방법에 대해서 질문하는 것 같다.
http://pyrasis.com/book/TheArtOfAmazonWebServices/Chapter28
```

3. 회사에서 현재 로컬 드라이브에 온프레미스 애플리케이션의 데이터를 저장합니다. CTO(Chief Technology Officer)는 Amazon S3 에 데이터를 저장하여 하드웨어 비용을 절감하려고 하지만 애플리케이션 수정은 원치 않습니다. 대기 시간을 최소화하려면 자주 액세스하는 데이터를 로컬에서 사용할 수 있도록 해야 합니다. 로컬 스토리지 비용을 절감하기 위하 솔루션 아키텍트가 구현할 수 있는 안정적이고 내구성 있는 솔루션은 무엇입니까?
   A) 로컬 서버에 SFTP 클라이언트를 배포하고 SFTP 용 AWS Transfer 를 사용하여 Amazon S3 로 데이터를 전송합니다.
   B) 캐시된 볼륨 모드로 구성된 AWS Storage Gateway 볼륨 게이트웨이를 배포합니다.
   C) 로컬 서버에 AWS DataSync 에이전트를 배포하고 S3 버킷을 대상으로 구성합니다.
   D) 저장된 볼륨 모드로 구성된 AWS Storage Gateway 볼륨 게이트웨이를 배포합니다.

```
선택 B, 정답 B
AWS Storage Gateway 잘 모르나 자주 액세스하는 데이터를 로컬에서 사용한다고 해서 '캐시된 볼륨'을 근거로 선택하였다.
```

4. 회사가 여러 가용 영역에 걸친 VPC 에서 퍼블릭 3 계층 웹 애플리케이션을 실행합니다. 프라이빗 서브넷에서 실행되는 애플리케이션 계층의 Amazon EC2 인스턴스가 인터넷에서 소프트웨어 패치를 다운로드해야 합니다. 하지만 인스턴스는 인터넷에서 직접 액세스할 수 없습니다. 인스턴스가 필요한 패치를 다운로드할 수 있도록 하려면 어떤 조치를 취해야 합니까? (2 개 항목 선택)
   A) 퍼블릭 서브넷에서 NAT 게이트웨이를 구성합니다.
   B) 인터넷 트래픽을 위해 NAT 게이트웨이로 라우팅되는 사용자 지정 라우팅 테이블을 정의하고 이를 애플리케이션 계층의 프라이빗 서브넷과 연결합니다.
   C) 애플리케이션 인스턴스에 Elastic IP 주소를 할당합니다.
   D) 인터넷 트래픽을 위해 인터넷 게이트웨이로 라우팅되는 사용자 지정 라우팅 테이블을 정의하고 이를 애플리케이션 계층의 프라이빗 서브넷과 연결합니다.
   E) 프라이빗 서브넷에 NAT 인스턴스를 구성합니다.

```
선택 AB, 정답 AB
C) 프라이빗 인스턴스에 퍼블릭 고정 IP 할당할 수 없는 것으로 알 수 있음
D) 인터넷 게이트웨이를 프라이빗 서브넷과 연결할 수 없는 것으로 알고 있음
E) NAT 인스턴스는 퍼블릭 서브넷에 구성해야 함
```

5. 솔루션 아키텍트가 2 주간의 회사 휴무 기간 동안 실행할 필요가 없는 Amazon EC2 인스턴스의 비용을 절약하는 솔루션을 설계하려고 합니다. 인스턴스에서 실행되는 애플리케이션은 인스턴스 작업이 재개될 때 필요한 데이터를 인스턴스 메모리(RAM)에 저장합니다. 솔루션 아키텍트는 인스턴스의 종료 및 재개를 위해 어떤 방법을 권장해야 합니까?
   A) 인스턴스 저장소 볼륨에 데이터를 저장하도록 애플리케이션을 수정합니다. 다시 시작할 때 볼륨을 다시 연결합니다.
   B) 인스턴스를 중지하기 전에 스냅샷을 만듭니다. 인스턴스를 다시 시작한 후 스냅샷을 복원합니다.
   C) 최대 절전 모드가 활성화된 인스턴스에서 애플리케이션을 실행합니다. 종료하기 전에 인스턴스를 최대 절전 모드로 전환합니다.
   D) 각 인스턴스의 가용 영역을 기록한 후 인스턴스를 중지합니다. 종료 후 동일한 가용 영역에서 인스턴스를 다시 시작합니다.
```
선택 A, 정답 C
B로도 고민하였으나 보존하려는 데이터가 있는데 휘발성인 RAM에 둔다는게 말이 안된다고 생각해서 볼륨에 저장하도록 수정하는 A를 선택
그러나 최대 절전 모드를 사용하면 EBS에 저장된다는 것을 처음 알았음
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Hibernate.html#enabling-hibernation
```

6. 회사에서 VPC의 Amazon EC2 인스턴스에서 모니터링 애플리케이션을 실행할 계획입니다. 인스턴스에 연결 시 프라이빗 IPv4 주소를 사용합니다. 솔루션 아키텍트는 애플리케이션에 장애가 발생하여 도달할 수 없을 때 트래픽이 대기 인스턴스로 신속하게 전달될 수 있는 솔루션을 설계해야 합니다. 이러한 요구 사항을 충족하려면 어떻게 해야 합니까?
   A) 프라이빗 IP 주소에 대한 리스너로 구성된 Application Load Balancer 를 배포하고 기본 인스턴스를 로드 밸런서에 등록합니다. 장애 발생 시 인스턴스를 등록 취소하고 보조 인스턴스를 등록합니다.
   B) 사용자 지정 DHCP 옵션 세트를 구성합니다. 기본 인스턴스에 장애가 발생하면 동일한 프라이빗 IP 주소를 보조 인스턴스에 할당하도록 DHCP 를 구성합니다.
   C) 프라이빗 IP 주소로 구성된 인스턴스에 보조 ENI(탄력적 네트워크 인터페이스)를 연결합니다. 기본 인스턴스에 도달할 수 없는 경우 ENI 를 대기 인스턴스로 이동합니다.
   D) Elastic IP 주소를 기본 인스턴스의 네트워크 인터페이스와 연결합니다. 발생 시 Elastic IP 를 기본 인스턴스에서 분리하고 보조 인스턴스와 연결합니다

```
선택 C, 정답 C
A) 장애가 발생했는데 수동으로 대응하는 방안 같음
B) DHCP가 애초에 변동IP인데 동일한 IP 주소를 다른 인스턴스에 할당한다고 하는게 말이 되는 것 같지 않음
C) https://docs.aws.amazon.com/ko_kr/AWSEC2/latest/UserGuide/using-eni.html
D) 장애가 발생했는데 수동으로 대응하는 방안 같음
```

7. 애널리틱스 회사에서 사용자에게 사이트 애널리틱스 서비스를 제공할 계획입니다. 이 서비스를 사용하려면 사용자의 웹 페이지에 회사의 Amazon S3 버킷에 인증된 GET 요청을 하는 JavaScript 스크립트가 있어야 합니다. 이 스크립트가 성공적으로 실행되도록 하기 위해 솔루션 아키텍트는 무엇을 해야 합니까?
   A) S3 버킷에서 CORS(Cross-Origin Resource Sharing)를 활성화합니다.
   B) S3 버킷에서 S3 버전 관리를 활성화합니다.
   C) 사용자에게 스크립트의 서명된 URL 을 제공합니다.
   D) 퍼블릭 실행 권한을 허용하도록 버킷 정책을 구성합니다.

```
선택 A, 정답 A
A) 사용자 웹페이지에서 회사 S3 버킷이라는 다른 도메인에 요청을 보내기 위해서는 CORS가 필요한 것으로 알고 있음
D) GET 요청인데 실행 권한과는 관계없어 보임 
```

8. 회사 보안팀은 클라우드에 저장된 모든 데이터가 미사용시 온프레미스에 저장된 암호화 키로 항상 암호화되도록 요구합니다. 이러한 요구 사항을 충족하는 암호화 옵션은 무엇입니까? (2개 항목 선택)
   A) Amazon S3 관리 키(SSE-S3)와 함께 서버 측 암호화를 사용합니다.
   B) AWS KMS 관리 키(SSE-KMS)와 함께 서버 측 암호화를 사용합니다.
   C) 고객 제공 키(SSE-C)와 함께 서버 측 암호화를 사용합니다.
   D) 클라이언트 측 암호화를 통해 미사용 시 암호화를 제공합니다.
   E) Amazon S3 이벤트에 의해 트리거된 AWS Lambda 함수를 사용하여 고객 키로 데이터를 암호화합니다.

```
선택 CE, 정답 CD
일단 암호화 키를 AWS가 아닌 고객이 관리하는 경우만 선택하였음
서버/클라이언트측 둘 다 암호화가 가능한지 몰랐음...
```

9. 회사에서 규정 요구 사항으로 인해 최소 5 년간 액세스 로그를 유지해야 합니다. 한번 저장된 데이터는 거의 액세스되지 않지만 필요한 경우 하루 전에 통지를 받으면 액세스할 수 있어야 합니다. 이러한 요구 사항을 충족하는 가장 비용 효율적인 데이터 스토리지 솔루션은 무엇입니까?

   A) Amazon S3 Glacier Deep Archive 스토리지에 데이터를 저장하고 수명주기 규칙을 사용하여 5 년 후 객체를 삭제합니다.
   B) Amazon S3 Standard 스토리지에 데이터를 저장하고 수명주기 규칙을 사용하여 30 일 후 Amazon S3 Glacier 로 전환합니다.
   C) Amazon CloudWatch Logs 를 사용하여 데이터를 로그에 저장하고 보존 기간을 5 년으로 설정합니다.
   D) Amazon S3 Standard-Infrequent Access(S3 Standard-IA) 스토리지에 데이터를 저장하고 수명주기규칙을 사용하여 5 년 후 객체를 삭제합니다

```
선택 D, 정답 A
S3 시리즈 서비스에 대한 종류를 이해하지 못하고 있었음
```

10. 회사에서 예약된 인스턴스를 사용하여 데이터 처리 워크로드를 실행하고 있습니다. 야간 작업은 일반적으로 실행하는 데 7 시간이 걸리며 10 시간 내에 완료되어야 합니다. 이 회사는 매달 말 일시적인 수요 증가로 인해 현재 리소스의 용량에 따른 제한 시간을 초과해서 작업이 실행될 것으로 예상합니다. 일단 시작된 처리 작업은 완료 전에 중단할 수 없습니다. 이 회사는 가능한 한 비용 효율적으로 용량을 늘릴 수 있는 솔루션을 구현하려고 합니다. 이를 위해 솔루션 아키텍트는 어떻게 해야 합니까?
  A) 수요가 늘어나는 동안 온디맨드 인스턴스를 배포합니다.
  B) 추가 인스턴스에 대하여 두 번째 Amazon EC2 예약을 생성합니다.
  C) 수요가 늘어나는 동안 스팟 인스턴스를 배포합니다.
  D) 증가된 워크로드를 지원하도록 Amazon EC2 예약에서 인스턴스의 인스턴스 크기를 늘립니다.
```
선택 B, 정답 A
스팟 인스턴스가 저렴하다고 들었으나 정확한 특징에 대해서는 이해하지 못하고 있었음
```

### 3. (Optional) AWS SAA C01 샘플 문항
[AWS SAA C01 샘플 문항](https://d1.awsstatic.com/training-and-certification/docs/AWS_Certified_Solutions_Architect_Associate_Sample_Questions.pdf)을 풀이하고 자신만의 풀이와 해설을 작성합니다.

### 4. 강의 콘텐츠 선정
[Udemy AWS SAA 강의](https://www.udemy.com/course/best-aws-certified-solutions-architect-associate/)
```
EC2 - 솔루션스 아키텍트 어소시에이트 레벨
EC2 인스턴스 스토리지
고가용성 및 스케일링성: ELB 및 ASG
AWS 기초: RDS + Aurora + ElasticCache
Route 53
Amazon S3 소개 
고급 S3 및 Athena
CloudFront 및 AWS 글로벌 액셀러레이터
AWS 스토리지 추가 기능
디커플링 어플리케이션: SQS, SNS, Kinesis, Active MQ
AWS의 데이터베이스
AWS의 모니터링 및 감사: CloudWatch, CloudTrail 및 Config
IAM 고급
AWS의 보안 및 암호화: KMS, SSM Parameter Store, CloudHSM, Sheild, WAF
네트워킹 - VPC
```
