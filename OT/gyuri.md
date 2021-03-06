## 1. 시험 안내서 읽기

> 문제1. 대상 응시자는 다음과 같은 지식을 가지고 있어야 합니다.
>
> - 컴퓨팅, 네트워킹, 스토리지, 관리 및 데이터베이스 AWS 서비스를 사용한 실무 경험
> -  AWS 기술이 포함된 솔루션에 대한 기술 요구 사항을 식별하고 정의할 수 있는 능력
> - 특정 기술 요구 사항을 충족하는 AWS 서비스를 식별하는 능력
> - AWS 에서 잘 설계된 솔루션을 빌드하기 위한 모범 사례에 대한 이해
> - AWS 글로벌 인프라에 대한 이해
> - 기존 서비스와 관련된 AWS 보안 서비스 및 기능에 대한 이해

> 문제2. 다음 항목은 시험에 포함되지 않습니다.
>
> - 복잡한 하이브리드 네트워크 아키텍처 설계
> - 여러 계정 내의 자격 증명 연동 설계
> - 규정 준수 요구 사항을 충족하는 아키텍처 설계
> - 설계에 전문 서비스 통합
> - 배포 전략 개발
> - 복잡한 멀티 티어 애플리케이션을 위한 마이그레이션 전략 수립

> 문제3. 출제 영역과 시험비율은 다음과 같습니다.
>
> | 영역                                         | 시험 비율(%) |
> | -------------------------------------------- | ------------ |
> | 영역 1: 복원력을 갖춘 아키텍처 설계          | 30%          |
> | 영역 2: 고성능 아키텍처 설계                 | 28%          |
> | 영역 3: 안전한 애플리케이션 및 아키텍처 설계 | 24%          |
> | 영역 4: 비용에 최적화된 아키텍처 설계        | 18%          |
> | **합계**                                     | **100%**     |

<br>

## 2. AWS SAA C02 샘플 문항

**🟣 1) CRM(고객 관계 관리) 애플리케이션은 Application Load Balancer 뒤의 여러 가용 영역에 있는 Amazon EC2 인스턴스에서 실행됩니다. 이러한 인스턴스 중 하나에 장애가 발생하면 어떻게 됩니까?**

> A) 로드 밸런서가 장애 발생 인스턴스로 요청을 보내는 것을 중지합니다.  
> B) 로드 밸런서가 장애 발생 인스턴스를 종료합니다.  
> C) 로드 밸런서가 장애 발생 인스턴스를 자동으로 교체합니다.  
> D) 인스턴스가 교체될 때까지 로드 밸런서가 504 게이트웨이 시간 초과 오류를 반환합니다.  

**정답 : A**

ALB는 등록된 대상으로 health check 요청을 주기적으로 전송함으로써 등록 대상의 상태를 확인한다. 사용자가 설정한 프로토콜, 포트, 경로로 상태 확인을 하게 되며, 지정된 횟수 및 시간 동안 정상 상태 확인이 되지 않으면 대상을 비정상 상태로 간주하고 장애 발생 인스턴스로 요청을 보내는 것을 중지한다.

<br>

🟣 **2) Amazon SQS 를 분리된 아키텍처로 갖추고 있는 회사에서 비동기 처리를 수행해야 합니다. 이 회사는 폴링 요청의 빈 응답 수를 최소로 유지하려고 합니다. 빈 응답을 줄이려면 솔루션 아키텍트는 어떻게 해야 합니까?**

> A) 큐의 메시지 최대 보존 기간을 늘립니다.  
> B) 큐의 재드라이브 정책에서 최대 수신 수를 늘립니다.  
> C) 큐의 기본 가시성 제한 시간을 늘립니다.  
> D) 큐의 수신 메시지 대기 시간을 늘립니다.   

**정답 : D**

SQS에는 짧은 폴링과 긴 폴링이라는 개념이 있다. 

- 짧은 폴링 : 메시지 받기 요청을 하면 특정 서버를 샘플링한 후 해당 서버에서만 메시지를 반환하여 즉각적으로 결과를 받는 설정이다. 메시지가 있으면 메시지를 바로 가져오게 되고 없을 경우엔 빈 응답을 가져오게 된다. 

  > ReceiveMessage 요청에서 WaitTimeSeconds를 0으로 설정했을 때
    >
      > 큐 설정의 ReceiveMessageWaitTimeSeconds를 0으로 설정했을 때

        

	- 긴 폴링 : 모든 SQS서버를 쿼리하며, 메시지가 있으면 메시지를 바로 가져오고, 메시지가 없으면 최대 20초 동안 메시지가 올 때까지 대기하는 설정이다. 빈 응답의 수를 최소로 유지하고 싶을 때 사용하는 설정이다.

	  > ReceiveMessage요청의 WaitTimeSeconds가 0보다 큰 경우 유효

	  긴 폴링 설정을 사용하여 수신 메시지 대기 시간을 늘림으로써 빈 응답의 수를 최소화 할 수 있다.

	  <br>

🟣 **3) 회사에서 현재 로컬 드라이브에 온프레미스 애플리케이션의 데이터를 저장합니다. CTO(Chief Technology Officer)는 Amazon S3 에 데이터를 저장하여 하드웨어 비용을 절감하려고 하지만 애플리케이션 수정은 원치 않습니다. 대기 시간을 최소화하려면 자주 액세스하는 데이터를 로컬에서 사용할 수 있도록 해야 합니다.**
  **로컬 스토리지 비용을 절감하기 위하 솔루션 아키텍트가 구현할 수 있는 안정적이고 내구성 있는 솔루션은 무엇입니까?**

  > A) 로컬 서버에 SFTP 클라이언트를 배포하고 SFTP 용 AWS Transfer 를 사용하여 Amazon S3 로 데이터를 전송합니다.  
  > B) 캐시된 볼륨 모드로 구성된 AWS Storage Gateway 볼륨 게이트웨이를 배포합니다.  
  > C) 로컬 서버에 AWS DataSync 에이전트를 배포하고 S3 버킷을 대상으로 구성합니다.  
  > D) 저장된 볼륨 모드로 구성된 AWS Storage Gateway 볼륨 게이트웨이를 배포합니다.   

  **정답 : B**

  AWS Storage Gateway란 온프레미스 소프트웨어 어플라이언스를 클라우드 기반 스토리지에 연결하여 온프레미스 IT환경에서도 AWS  스토리지를 사용할 수 있게 하는 상품이다. NFS, SMB, iSCSI 등 표준 스토리지 프로토콜을 지원하기 때문에 기존 애플리케이션 변경 없이 AWS 클라우드 스토리지를 사용할 수 있다.

  <br>

  🟣**4) 회사가 여러 가용 영역에 걸친 VPC 에서 퍼블릭 3 계층 웹 애플리케이션을 실행합니다. 프라이빗 서브넷에서 실행되는 애플리케이션 계층의 Amazon EC2 인스턴스가 인터넷에서 소프트웨어 패치를 다운로드해야 합니다.  하지만 인스턴스는 인터넷에서 직접 액세스할 수 없습니다.**
  **인스턴스가 필요한 패치를 다운로드할 수 있도록 하려면 어떤 조치를 취해야 합니까? (2 개 항목 선택)**

  > A) 퍼블릭 서브넷에서 NAT 게이트웨이를 구성합니다.  
  > B) 인터넷 트래픽을 위해 NAT 게이트웨이로 라우팅되는 사용자 지정 라우팅 테이블을 정의하고 이를 애플리케이션 계층의 프라이빗 서브넷과 연결합니다.  
  > C) 애플리케이션 인스턴스에 Elastic IP 주소를 할당합니다.  
  > D) 인터넷 트래픽을 위해 인터넷 게이트웨이로 라우팅되는 사용자 지정 라우팅 테이블을 정의하고 이를 애플리케이션 계층의 프라이빗 서브넷과 연결합니다.  
  > E) 프라이빗 서브넷에 NAT 인스턴스를 구성합니다.  

  **정답 : A,B**

  NAT 게이트웨이란 네트워크 주소를 변환해주는 서비스로, 프라이빗 서브넷의 인스턴스가 VPC 외부로 통신을 내보낼 수 는 있지만, 외부에서는 프라이빗 서브넷으로 직접적인 통신을 못하도록 제어하는 역할이다.

  프라이빗 서브넷에서 외부로 요청하는 아웃바운드 트래픽을 NAT 게이트웨이가 받게 되며 NAT 게이트웨이의 EIP를 src IP로 사용하여 인터넷 게이트웨이로 트래픽을 보내 외부와 통신하게 된다. 이 때 프라이빗 서브넷과 연결된 라우팅 테이블에 인터넷 바운드 트래픽이 NAT 게이트웨이를 바라보도록 설정해야 외부와 통신이 가능하다.

  <br>

  🟣**5) 솔루션 아키텍트가 2 주간의 회사 휴무 기간 동안 실행할 필요가 없는 Amazon EC2 인스턴스의 비용을 절약하는 솔루션을 설계하려고 합니다. 인스턴스에서 실행되는 애플리케이션은 인스턴스 작업이 재개될 때 필요한 데이터를 인스턴스 메모리(RAM)에 저장합니다.**
  **솔루션 아키텍트는 인스턴스의 종료 및 재개를 위해 어떤 방법을 권장해야 합니까?**

  > A) 인스턴스 저장소 볼륨에 데이터를 저장하도록 애플리케이션을 수정합니다. 다시 시작할 때 볼륨을 다시 연결합니다.  
  > B) 인스턴스를 중지하기 전에 스냅샷을 만듭니다. 인스턴스를 다시 시작한 후 스냅샷을 복원합니다.  
  > C) 최대 절전 모드가 활성화된 인스턴스에서 애플리케이션을 실행합니다. 종료하기 전에 인스턴스를 최대 절전 모드로 전환합니다.  
  > D) 각 인스턴스의 가용 영역을 기록한 후 인스턴스를 중지합니다. 종료 후 동일한 가용 영역에서 인스턴스를 다시 시작합니다   

  **정답 : C**

  EC2 최대 절전모드란 인스턴스 메모리(RAM)의 내용을 EBS 루트 볼륨에 저장하는 기능이다. 최대 절전모드에 의해 `stopped` 상태가 되었을 때는 인스턴스 사용량에 대해 요금이 청구되지 않는다. (볼륨 스토리지에 대한 요금은 부과된다) 

   인스턴스를 다시 시작해야할 때 EBS 루트 볼륨이 이전 상태로 복원되며 RAM 내용이 다시 로드되기 때문에 비용을 절약하면서 회사 휴무 전 상태를 유지할 수 있다.

   <br>

   🟣**6) 회사에서 VPC 의 Amazon EC2 인스턴스에서 모니터링 애플리케이션을 실행할 계획입니다. 인스턴스에 연결 시 프라이빗 IPv4 주소를 사용합니다. 솔루션 아키텍트는 애플리케이션에 장애가 발생하여 도달할 수 없을 때 트래픽이 대기 인스턴스로 신속하게 전달될 수 있는 솔루션을 설계해야 합니다. 이러한 요구 사항을 충족하려면 어떻게 해야 합니까?**

   > A) 프라이빗 IP 주소에 대한 리스너로 구성된 Application Load Balancer 를 배포하고 기본 인스턴스를 로드 밸런서에 등록합니다. 장애 발생 시 인스턴스를 등록 취소하고 보조 인스턴스를 등록합니다.  
   > B) 사용자 지정 DHCP 옵션 세트를 구성합니다. 기본 인스턴스에 장애가 발생하면 동일한 프라이빗 IP 주소를 보조 인스턴스에 할당하도록 DHCP 를 구성합니다.  
   > C) 프라이빗 IP 주소로 구성된 인스턴스에 보조 ENI(탄력적 네트워크 인터페이스)를 연결합니다. 기본 인스턴스에 도달할 수 없는 경우 ENI 를 대기 인스턴스로 이동합니다.  
   > D) Elastic IP 주소를 기본 인스턴스의 네트워크 인터페이스와 연결합니다. 발생 시 Elastic IP 를 기본 인스턴스에서 분리하고 보조 인스턴스와 연결합니다.  

   **정답 : C**

   보조 ENI를 연결함으로써 장애가 났을 경우 장애가 난 인스턴스에서 보조 ENI를 분리하여 다른 인스턴스에 연결할 수 있다.

   <br>

   🟣**7) 애널리틱스 회사에서 사용자에게 사이트 애널리틱스 서비스를 제공할 계획입니다. 이 서비스를 사용하려면 사용자의 웹 페이지에 회사의 Amazon S3 버킷에 인증된 GET 요청을 하는 JavaScript 스크립트가 있어야 합니다. 이 스크립트가 성공적으로 실행되도록 하기 위해 솔루션 아키텍트는 무엇을 해야 합니까?**

   > A) S3 버킷에서 CORS(Cross-Origin Resource Sharing)를 활성화합니다.  
   > B) S3 버킷에서 S3 버전 관리를 활성화합니다.  
   > C) 사용자에게 스크립트의 서명된 URL 을 제공합니다.  
   > D) 퍼블릭 실행 권한을 허용하도록 버킷 정책을 구성합니다.  

   **정답 : A**

   CORS(Cross-Origin Resource Sharing)이란 한 도메인에서 로드되어 다른 도메인에 있는 리소스와 상호 작용할 수 있도록 웹 어플리케이션과 연결 및 구성하는 기능이다.

   대표적인 사용 예시는 다음과 같다.

   1) Amazon S3버킷에서 웹 사이트를 호스팅한다. S3버킷에 저장된 웹사이트의 JavaScript를 사용하여 S3버킷에 GET 및 PUT 요청 기능을 보내야 한다. 브라우저에서 해당 요청을 허용할 수 있게 하기 위해 CORS를 사용하여 S3버킷으로부터의 cross-origin 요청을 활성화 시킬 수 있다.

   <br>

   🟣**8) 회사 보안팀은 클라우드에 저장된 모든 데이터가 미사용 시 온프레미스에 저장된 암호화 키로 항상 암호화되도록 요구합니다. 이러한 요구 사항을 충족하는 암호화 옵션은 무엇입니까? (2 개 항목 선택)**

   > A) Amazon S3 관리 키(SSE-S3)와 함께 서버 측 암호화를 사용합니다.  
   > B) AWS KMS 관리 키(SSE-KMS)와 함께 서버 측 암호화를 사용합니다.  
   > C) 고객 제공 키(SSE-C)와 함께 서버 측 암호화를 사용합니다.  
   > D) 클라이언트 측 암호화를 통해 미사용 시 암호화를 제공합니다.  
   > E) Amazon S3 이벤트에 의해 트리거된 AWS Lambda 함수를 사용하여 고객 키로 데이터를 암호화합니다  

   **정답 : C, D**

   고객 제공 암호화 키(SSE-C)를 사용하게 되면 사용자가 직접 암호화 키를 관리하게 된다. Amazon S3에서 암호화 키를 저장하지 않기 때문에 키 관련된 관리 및 추적은 사용자가 직접 해야 한다.

   클라이언트 측 암호화란 데이터가 Amazon S3로 전달될 때 보안을 보장하기 위해서 로컬에서 데이터를 암호화하는 작업이다. AWS KMS(Key Management Service)에 저장된 키를 사용하거나 애플리케이션 내에 저장된 키를 사용할 수 있다.

   <br>

   🟣**9) 회사에서 규정 요구 사항으로 인해 최소 5 년간 액세스 로그를 유지해야 합니다. 한번 저장된 데이터는 거의 액세스되지 않지만 필요한 경우 하루 전에 통지를 받으면 액세스할 수 있어야 합니다. 이러한 요구 사항을 충족하는 가장 비용 효율적인 데이터 스토리지 솔루션은 무엇입니까?**

   > A) Amazon S3 Glacier Deep Archive 스토리지에 데이터를 저장하고 수명주기 규칙을 사용하여 5 년 후 객체를 삭제합니다.  
   > B) Amazon S3 Standard 스토리지에 데이터를 저장하고 수명주기 규칙을 사용하여 30 일 후 Amazon S3 Glacier 로 전환합니다.  
   > C) Amazon CloudWatch Logs 를 사용하여 데이터를 로그에 저장하고 보존 기간을 5 년으로 설정합니다.  
   > D) Amazon S3 Standard-Infrequent Access(S3 Standard-IA) 스토리지에 데이터를 저장하고 수명주기 규칙을 사용하여 5 년 후 객체를 삭제합니다  

   **정답 : A**

   Amazon S3 Glacier Deep Archive란 장기 데이터 보존 및 디지털 보존을 위한 안전하고 안정적인 객체 스토리지를 제공하는 새로운 Amazon S3 스토리지 클래스이다. 

   해당 스토리지는 1년에 한 번 미만으로 액세스하고 비동기식으로 검색되는 수명이 긴 아카이브 데이터에 대해 S3 Glacier보다 최대 75% 저렴한 비용으로 저렴한 스토리지를 제공한다. 

   <br>

   🟣**10) 회사에서 예약된 인스턴스를 사용하여 데이터 처리 워크로드를 실행하고 있습니다. 야간 작업은 일반적으로 실행하는 데 7 시간이 걸리며 10 시간 내에 완료되어야 합니다. 이 회사는 매달 말 일시적인 수요 증가로 인해 현재 리소스의 용량에 따른 제한 시간을 초과해서 작업이 실행될 것으로 예상합니다. 일단 시작된 처리 작업은 완료 전에 중단할 수 없습니다. 이 회사는 가능한 한 비용 효율적으로 용량을 늘릴 수 있는 솔루션을 구현하려고 합니다. 이를 위해 솔루션 아키텍트는 어떻게 해야 합니까?**

   > A) 수요가 늘어나는 동안 온디맨드 인스턴스를 배포합니다.  
   > B) 추가 인스턴스에 대하여 두 번째 Amazon EC2 예약을 생성합니다.  
   > C) 수요가 늘어나는 동안 스팟 인스턴스를 배포합니다.  
   > D) 증가된 워크로드를 지원하도록 Amazon EC2 예약에서 인스턴스의 인스턴스 크기를 늘립니다.  

   **정답 : A**

   스팟 인스턴스는 저렴하지만 스팟 인스턴스가 중단될 가능성이 있기 때문에 중단될 수 있는 작업에 대해서는 유효하지 않다.

   따라서 실행 시간에 따라 비용이 발생하는 온디맨드 인스턴스르 배포한다.

   <br>

   ## 3. 강의 콘텐츠 선정

   - EC2 인스턴스 스토리지
   - 고가용성 및 스케일링성
   - AWS 데이터베이스
   - AWS 네트워킹
   - 재해 복구 및 마이그레이션
   - 디커플링 애플리케이션 (SQS, SNS, Kinesis, Active MQ)
   - EC2 기초
   - AWS S3 및 고급 S3
   - 모니터링
   - IAM
