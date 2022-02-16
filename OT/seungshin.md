## 1. 시험 안내서 읽기

### 문제1. 대상 응시자는 다음과 같은 지식을 가지고 있어야 합니다. (6개)

- 컴퓨팅, 네트워킹, 스토리지, 관리 및 데이터베이스 AWS 서비스를 사용한 실무 경험
- AWS 기술이 포함된 솔루션에 대한 기술 요구 사항을 식별하고 정의할 수 있는 능력
- 특정 기술 요구 사항을 충족하는 AWS 서비스를 식별하는 능력
- AWS 에서 잘 설계된 솔루션을 빌드하기 위한 모범 사례에 대한 이해
- AWS 글로벌 인프라에 대한 이해
- 기존 서비스와 관련된 AWS 보안 서비스 및 기능에 대한 이해

### 문제2. 다음 항목은 시험에 포함되지 않습니다. (6개)

- 복잡한 하이브리드 네트워크 아키텍처 설계
- 여러 계정 내의 자격 증명 연동 설계
- 규정 준수 요구 사항을 충족하는 아키텍처 설계
- 설계에 전문 서비스 통합
- 배포 전략 개발
- 복잡한 멀티 티어 애플리케이션을 위한 마이그레이션 전략 수립

### 문제3. 출체 영역과 시험비율은 다음과 같습니다.

- 영역 1. 복원력을 갖춘 아키텍처 설계. 30%
- 영역 2. 고성능 아키텍처 설계. 28%
- 영역 3. 안전한 애플리케이션 및 아키텍처 설계. 24%
- 영역 4. 비용에 최적화된 아키텍처 설계. 18%

## 2. AWS SAA C02 샘플 문항

1) CRM(고객 관계 관리) 애플리케이션은 Application Load Balancer 뒤의 여러 가용 영역에 있는 Amazon EC2
   인스턴스에서 실행됩니다. 이러한 인스턴스 중 하나에 장애가 발생하면 어떻게 됩니까?


       A) 로드 밸런서가 장애 발생 인스턴스로 요청을 보내는 것을 중지합니다.
       B) 로드 밸런서가 장애 발생 인스턴스를 종료합니다.
       C) 로드 밸런서가 장애 발생 인스턴스를 자동으로 교체합니다.
       D) 인스턴스가 교체될 때까지 로드 밸런서가 504 게이트웨이 시간 초과 오류를 반환합니다

정답 : A

ALB 는 대상 그룹에 대해 health check request 를 주기적으로 수행하고,
http 의 경우 연속 횟수 동안 200 대 응답이 아니면 비정상 인스턴스로 간주, 요청을 보내지 않는다.
alb 에 응답으로 http 가 아닌 패킷을 보낼 수 있는지는 모르겠다. (확인 필요)
B, C 에 상응하는 옵션이 있는지는 모르겠지만, 그런 니즈가 과연 있을까 싶다. (확인 필요)
살아있는 인스턴스가 있는데 로드밸런서가 504 를 반환하는 건 말이 안된다.


2) Amazon SQS 를 분리된 아키텍처로 갖추고 있는 회사에서 비동기 처리를 수행해야 합니다. 이 회사는 폴링
   요청의 빈 응답 수를 최소로 유지하려고 합니다. 빈 응답을 줄이려면 솔루션 아키텍트는 어떻게 해야 합니까?


      A) 큐의 메시지 최대 보존 기간을 늘립니다.
      B) 큐의 재드라이브 정책에서 최대 수신 수를 늘립니다.
      C) 큐의 기본 가시성 제한 시간을 늘립니다.
      D) 큐의 수신 메시지 대기 시간을 늘립니다.

정답 : D

수신 메세지 대기 시간 만큼 메세지를 받아 봤는데, 메세지가 없으니까 빈 응답을 주는 것이다.
수신 메세지 대기 시간을 늘려주면 대기 시간만큼 받은 메세지들을 응답해줄 수 있을 것이다.
메세지 보존 기간을 늘리는 것은 클라이언트의 폴링 간격을 넓게 가져가고 싶을 때 써야할 방법일 것 같다.
재드라이브가 뭔지 모르겠다. 기본 가시성 제한 시간도 아직 모르겠다.

3) 회사에서 현재 로컬 드라이브에 온프레미스 애플리케이션의 데이터를 저장합니다. CTO(Chief Technology
   Officer)는 Amazon S3 에 데이터를 저장하여 하드웨어 비용을 절감하려고 하지만 애플리케이션 수정은 원치
   않습니다. 대기 시간을 최소화하려면 자주 액세스하는 데이터를 로컬에서 사용할 수 있도록 해야 합니다.

   로컬 스토리지 비용을 절감하기 위하 솔루션 아키텍트가 구현할 수 있는 안정적이고 내구성 있는 솔루션은
   무엇입니까?


      A) 로컬 서버에 SFTP 클라이언트를 배포하고 SFTP 용 AWS Transfer 를 사용하여 Amazon S3 로 데이터를
      전송합니다.
      B) 캐시된 볼륨 모드로 구성된 AWS Storage Gateway 볼륨 게이트웨이를 배포합니다.
      C) 로컬 서버에 AWS DataSync 에이전트를 배포하고 S3 버킷을 대상으로 구성합니다.
      D) 저장된 볼륨 모드로 구성된 AWS Storage Gateway 볼륨 게이트웨이를 배포합니다.

정답 : D? -> B 였음.

자주 액세스하는 걸 로컬에서 쓰고 싶다하니, A 랑 C 는 아니다. A, C 는 데이터 mig 를 어떻게 할까요에 대한 답변일 듯.
B 아니면 D 인데, B 는 캐시니까 어플리케이션이 캐시 인발리드랑 다 해줘야될꺼고 D 인거같다.

근데 B 였다. 캐시된 볼륨모드와 저장된 볼륨 모드 차이는

- 캐시 : s3 에 직접 저장. 로컬에 캐싱
- 저장 : 로컬 에 저장. s3 에 비동기 업데이트

캐시 인발리드는 해주는 갑다. aws 는 역시 짱인 것 같다.

4) 회사가 여러 가용 영역에 걸친 VPC 에서 퍼블릭 3 계층 웹 애플리케이션을 실행합니다. 프라이빗 서브넷에서
   실행되는 애플리케이션 계층의 Amazon EC2 인스턴스가 인터넷에서 소프트웨어 패치를 다운로드해야 합니다.
   하지만 인스턴스는 인터넷에서 직접 액세스할 수 없습니다.

   인스턴스가 필요한 패치를 다운로드할 수 있도록 하려면 어떤 조치를 취해야 합니까? (2 개 항목 선택)


      A) 퍼블릭 서브넷에서 NAT 게이트웨이를 구성합니다.
      B) 인터넷 트래픽을 위해 NAT 게이트웨이로 라우팅되는 사용자 지정 라우팅 테이블을 정의하고 이를
         애플리케이션 계층의 프라이빗 서브넷과 연결합니다.
      C) 애플리케이션 인스턴스에 Elastic IP 주소를 할당합니다.
      D) 인터넷 트래픽을 위해 인터넷 게이트웨이로 라우팅되는 사용자 지정 라우팅 테이블을 정의하고 이를
         애플리케이션 계층의 프라이빗 서브넷과 연결합니다.
      E) 프라이빗 서브넷에 NAT 인스턴스를 구성합니다.

정답 : A, B ?

프라이빗 서브넷에 NAT 인스턴스가 있는게 이상해서 A, B 로 찍었다.
C 는 인터넷이 인바운드로 들어와야할 때 필요할 것이다.

5) 솔루션 아키텍트가 2 주간의 회사 휴무 기간 동안 실행할 필요가 없는 Amazon EC2 인스턴스의 비용을
   절약하는 솔루션을 설계하려고 합니다. 인스턴스에서 실행되는 애플리케이션은 인스턴스 작업이 재개될 때 필요한
   데이터를 인스턴스 메모리(RAM)에 저장합니다.

   솔루션 아키텍트는 인스턴스의 종료 및 재개를 위해 어떤 방법을 권장해야 합니까?


      A) 인스턴스 저장소 볼륨에 데이터를 저장하도록 애플리케이션을 수정합니다. 다시 시작할 때 볼륨을 다시
      연결합니다.
      B) 인스턴스를 중지하기 전에 스냅샷을 만듭니다. 인스턴스를 다시 시작한 후 스냅샷을 복원합니다.
      C) 최대 절전 모드가 활성화된 인스턴스에서 애플리케이션을 실행합니다. 종료하기 전에 인스턴스를 최대
      절전 모드로 전환합니다.
      D) 각 인스턴스의 가용 영역을 기록한 후 인스턴스를 중지합니다. 종료 후 동일한 가용 영역에서
      인스턴스를 다시 시작합니다.

정답 : B ? -> C

램을 살린 채로 종료하고 싶단 말인데, 스냅샷을 뜨는 것에 램이 포함될 것 같은 느낌적인 느낌이 들어서 찍었다.

근데 아니었다.

6) 회사에서 VPC 의 Amazon EC2 인스턴스에서 모니터링 애플리케이션을 실행할 계획입니다. 인스턴스에 연결 시
   프라이빗 IPv4 주소를 사용합니다. 솔루션 아키텍트는 애플리케이션에 장애가 발생하여 도달할 수 없을 때 트래픽이
   대기 인스턴스로 신속하게 전달될 수 있는 솔루션을 설계해야 합니다.

   이러한 요구 사항을 충족하려면 어떻게 해야 합니까?


      A) 프라이빗 IP 주소에 대한 리스너로 구성된 Application Load Balancer 를 배포하고 기본 인스턴스를 로드
      밸런서에 등록합니다. 장애 발생 시 인스턴스를 등록 취소하고 보조 인스턴스를 등록합니다.
      B) 사용자 지정 DHCP 옵션 세트를 구성합니다. 기본 인스턴스에 장애가 발생하면 동일한 프라이빗 IP
      주소를 보조 인스턴스에 할당하도록 DHCP 를 구성합니다.
      C) 프라이빗 IP 주소로 구성된 인스턴스에 보조 ENI(탄력적 네트워크 인터페이스)를 연결합니다. 기본
      인스턴스에 도달할 수 없는 경우 ENI 를 대기 인스턴스로 이동합니다.
      D) Elastic IP 주소를 기본 인스턴스의 네트워크 인터페이스와 연결합니다. 발생 시 Elastic IP 를 기본
      인스턴스에서 분리하고 보조 인스턴스와 연결합니다.

정답 : B -> C

C 의 ENI 는 뭔지 모르겠고, A, D 는 손을 거쳐야한다. DHCP 가 장애를 감지할 수 있는지는 모르겠다. 그럼 C 로 해야하나;

근데 C 였다. ENI 는 공부해봐야 할 것 같다.

7) 애널리틱스 회사에서 사용자에게 사이트 애널리틱스 서비스를 제공할 계획입니다. 이 서비스를 사용하려면
   사용자의 웹 페이지에 회사의 Amazon S3 버킷에 인증된 GET 요청을 하는 JavaScript 스크립트가 있어야 합니다.

   이 스크립트가 성공적으로 실행되도록 하기 위해 솔루션 아키텍트는 무엇을 해야 합니까?


      A) S3 버킷에서 CORS(Cross-Origin Resource Sharing)를 활성화합니다.
      B) S3 버킷에서 S3 버전 관리를 활성화합니다.
      C) 사용자에게 스크립트의 서명된 URL 을 제공합니다.
      D) 퍼블릭 실행 권한을 허용하도록 버킷 정책을 구성합니다.

정답 : A

A 가 안되면 애초에 실패하니 A

8) 회사 보안팀은 클라우드에 저장된 모든 데이터가 미사용 시 온프레미스에 저장된 암호화 키로 항상 암호화되도록
   요구합니다.

   이러한 요구 사항을 충족하는 암호화 옵션은 무엇입니까? (2 개 항목 선택)


      A) Amazon S3 관리 키(SSE-S3)와 함께 서버 측 암호화를 사용합니다.
      B) AWS KMS 관리 키(SSE-KMS)와 함께 서버 측 암호화를 사용합니다.
      C) 고객 제공 키(SSE-C)와 함께 서버 측 암호화를 사용합니다.
      D) 클라이언트 측 암호화를 통해 미사용 시 암호화를 제공합니다.
      E) Amazon S3 이벤트에 의해 트리거된 AWS Lambda 함수를 사용하여 고객 키로 데이터를 암호화합니다.

정답 : B, C ? -> C, D

잘 모르는 내용이다.

9) 회사에서 규정 요구 사항으로 인해 최소 5 년간 액세스 로그를 유지해야 합니다. 한번 저장된 데이터는 거의
   액세스되지 않지만 필요한 경우 하루 전에 통지를 받으면 액세스할 수 있어야 합니다.

   이러한 요구 사항을 충족하는 가장 비용 효율적인 데이터 스토리지 솔루션은 무엇입니까?


       A) Amazon S3 Glacier Deep Archive 스토리지에 데이터를 저장하고 수명주기 규칙을 사용하여 5 년 후
       객체를 삭제합니다.
       B) Amazon S3 Standard 스토리지에 데이터를 저장하고 수명주기 규칙을 사용하여 30 일 후 Amazon S3
       Glacier 로 전환합니다.
       C) Amazon CloudWatch Logs 를 사용하여 데이터를 로그에 저장하고 보존 기간을 5 년으로 설정합니다.
       D) Amazon S3 Standard-Infrequent Access(S3 Standard-IA) 스토리지에 데이터를 저장하고 수명주기규칙을
       사용하여 5 년 후 객체를 삭제합니다

정답 : C ? -> A

CloudWatch 가 비효율적인 것 같은데 다른 서비스는 애초에 잘 모르겠으므로 C

역시나 아니었고 A 였다.


10) 회사에서 예약된 인스턴스를 사용하여 데이터 처리 워크로드를 실행하고 있습니다. 야간 작업은 일반적으로
    실행하는 데 7 시간이 걸리며 10 시간 내에 완료되어야 합니다. 이 회사는 매달 말 일시적인 수요 증가로 인해 현재
    리소스의 용량에 따른 제한 시간을 초과해서 작업이 실행될 것으로 예상합니다. 일단 시작된 처리 작업은 완료 전에
    중단할 수 없습니다. 이 회사는 가능한 한 비용 효율적으로 용량을 늘릴 수 있는 솔루션을 구현하려고 합니다.

    이를 위해 솔루션 아키텍트는 어떻게 해야 합니까?


       A) 수요가 늘어나는 동안 온디맨드 인스턴스를 배포합니다.
       B) 추가 인스턴스에 대하여 두 번째 Amazon EC2 예약을 생성합니다.
       C) 수요가 늘어나는 동안 스팟 인스턴스를 배포합니다.
       D) 증가된 워크로드를 지원하도록 Amazon EC2 예약에서 인스턴스의 인스턴스 크기를 늘립니다.

정답 : C -> A

스팟 인스턴스는 싸니까! 근데 갑자기 꺼질 수 있으니 아닌 건 확실할 듯 하지만 다른 답은 잘 모르겠다.

역시 아니었다!

## 3. AWS SAA C01 샘플 문항

다음 기회에

1) A company is storing an access key (access key ID and secret access key) in a text file on a custom
   AMI. The company uses the access key to access DynamoDB tables from instances created from the
   AMI. The security team has mandated a more secure solution.

   Which solution will meet the security team’s mandate?


      A. Put the access key in an S3 bucket, and retrieve the access key on boot from the instance.
      B. Pass the access key to the instances through instance user data.
      C. Obtain the access key from a key server launched in a private subnet.
      D. Create an IAM role with permissions to access the table, and launch all instances with the new role.

정답 :

2) A company is developing a highly available web application using stateless web servers. Which
   services are suitable for storing session state data? (Select TWO.)


      A. CloudWatch
      B. DynamoDB
      C. Elastic Load Balancing
      D. ElastiCache
      E. Storage Gateway

정답 :

3) Company salespeople upload their sales figures daily. A Solutions Architect needs a durable storage
   solution for these documents that also protects against users accidentally deleting important
   documents.

   Which action will protect against unintended user actions?


      A. Store data in an EBS volume and create snapshots once a week.
      B. Store data in an S3 bucket and enable versioning.
      C. Store data in two S3 buckets in different AWS regions.
      D. Store data on EC2 instance storage.

정답 :

4) An application requires a highly available relational database with an initial storage capacity of 8 TB.
   The database will grow by 8 GB every day. To support expected traffic, at least eight read replicas will
   be required to handle database reads.

   Which option will meet these requirements?


      A. DynamoDB
      B. Amazon S3
      C. Amazon Aurora
      D. Amazona Redshift

정답 :

5) A Solutions Architect is designing a critical business application with a relational database that runs
   on an EC2 instance. It requires a single EBS volume that can support up to 16,000 IOPS.

   Which Amazon EBS volume type can meet the performance requirements of this application?


      A. EBS Provisioned IOPS SSD
      B. EBS Throughput Optimized HDD
      C. EBS General Purpose SSD
      D. EBS Cold HDD

정답 :

6) A web application allows customers to upload orders to an S3 bucket. The resulting Amazon S3
   events trigger a Lambda function that inserts a message to an SQS queue. A single EC2 instance
   reads messages from the queue, processes them, and stores them in an DynamoDB table partitioned
   by unique order ID. Next month traffic is expected to increase by a factor of 10 and a Solutions
   Architect is reviewing the architecture for possible scaling problems.

   Which component is MOST likely to need re-architecting to be able to scale to accommodate the new
   traffic?


      A. Lambda function
      B. SQS queue
      C. EC2 instance
      D. DynamoDB table

정답 :

7) An application saves the logs to an S3 bucket. A user wants to keep the logs for one month for
   troubleshooting purposes, and then purge the logs.

   What feature will enable this?


      A. Adding a bucket policy on the S3 bucket.
      B. Configuring lifecycle configuration rules on the S3 bucket.
      C. Creating an IAM policy for the S3 bucket.
      D. Enabling CORS on the S3 bucket.

정답 :

8) An application running on EC2 instances processes sensitive information stored on Amazon S3. The
   information is accessed over the Internet. The security team is concerned that the Internet
   connectivity to Amazon S3 is a security risk.

   Which solution will resolve the security concern?


       A. Access the data through an Internet Gateway.
       B. Access the data through a VPN connection.
       C. Access the data through a NAT Gateway.
       D. Access the data through a VPC endpoint for Amazon S3.

정답 :

9) An organization is building an Amazon Redshift cluster in their shared services VPC. The cluster will
   host sensitive data.

   How can the organization control which networks can access the cluster?


        A. Run the cluster in a different VPC and connect through VPC peering.
        B. Create a database user inside the Amazon Redshift cluster only for users on the network.
        C. Define a cluster security group for the cluster that allows access from the allowed networks.
        D. Only allow access to networks that connect with the shared services network via VPN.

정답 :

10) A Solutions Architect is designing an online shopping application running in a VPC on EC2 instances
    behind an ELB Application Load Balancer. The instances run in an Auto Scaling group across
    multiple Availability Zones. The application tier must read and write data to a customer managed
    database cluster. There should be no access to the database from the Internet, but the cluster must
    be able to obtain software patches from the Internet.

    Which VPC design meets these requirements?


       A. Public subnets for both the application tier and the database cluster
       B. Public subnets for the application tier, and private subnets for the database cluster
       C. Public subnets for the application tier and NAT Gateway, and private subnets for the database cluster
       D. Public subnets for the application tier, and private subnets for the database cluster and NAT Gateway

정답 :

## 4. 강의 콘텐츠 설정

1. 섹션 8: 고가용성 및 스케일링성 : ELB 및 ASG
2. 섹션 14: 고급 S3 및 Athena
3. 섹션 17: 디커플링 애플리케이션 : SQS, SNS, Kinesis, Active MQ
4. 섹션 18: AWS의 컨테이너
5. 섹션 21: AWS의 데이터베이스
6. 섹션 22: AWS의 모니터링 및 감사
7. 섹션 25: 네트워킹 - VPC
8. 섹션 6: EC2 - 솔루션스 아키텍스 어소시에이트 레벨
9. 섹션 20: 서버리스
10. 섹션 26: 재해 복구 및 마이그레이션