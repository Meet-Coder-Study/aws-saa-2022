# 과제



## 1. 시험 안내서 읽기



**문제1. 응시자는 다음과 같은 지식을 가지고 있어야 합니다. (6개)**

1. 컴퓨팅, 네트워킹, 스토리지, 관리 및 데이터베이스 AWS 서비스를 사용한 실무 경험
2. AWS 기술이 포함된 솔루션에 대한 기술 요구 사항을 식별하고 정의할 수 있는 능력
3. 특정 기술 요구 사항을 충족하는 AWS 서비스를 식별하는 능력
4. AWS 에서 잘 설계된 솔루션을 빌드하기 위한 모범 사례에 대한 이해
5. AWS 글로벌 인프라에 대한 이해
6. 기존 서비스와 관련된 AWS 보안 서비스 및 기능에 대한 이해

<br>



**문제2. 다음 항목은 시험에 포함되지 않습니다. (6개)**

1. 복잡한 하이브리드 네트워크 아키텍처 설계
2. 여러 계정 내의 자격 증명 연동 설계
3. 규정 준수 요구 사항을 충족하는 아키텍처 설계
4. 설계에 전문 서비스 통합
5. 배포 전략 개발
6. 복잡한 멀티 티어 애플리케이션을 위한 마이그레이션 전략 수립

<br>



**문제3. 출제 영역과 시험비율은 다음과 같습니다.**

영역 1. 복원력을 갖춘 아키텍처 설계 (30%)

- 멀티 티어 아키텍처 솔루션 설계
    - 액세스 패턴을 기반으로 솔루션 설계를 결정
    - 설계에 사용되는 구성 요소에 대한 조정 전략을 결정
    - 요구 사항에 따라 적절한 데이터베이스를 선택
    - 요구 사항에 따라 적절한 컴퓨팅 및 스토리지 서비스를 선택

- 고가용성 및/또는 내결함성 아키텍처 설계
    - 가용 영역 전반에 내결함성 아키텍처를 제공하는 데 필요한 리소스의 양을 결정
    - 단일 장애 지점을 완화하는 고가용성 구성을 선택
    - 애플리케이션을 변경할 수 없는 경우 레거시 애플리케이션의 안정성을 개선하는 AWS 서비스를 적용
    - 비즈니스 요구 사항을 충족하는 데 적절한 재해 복구 전략을 선택
    - 솔루션의 고가용성을 보장하는 주요 성능 지표를 식별

- AWS 서비스를 사용하여 결합 해제 메커니즘 설계
    - 구성 요소의 소결합을 달성하기 위해 활용할 수 있는 AWS 서비스를 결정
    - 결합 해제를 활성화하기 위해 서버리스 기술을 활용할 시기를 결정

- 적절한 복원력을 갖춘 스토리지 선택
    - 데이터의 내구성을 보장하는 전략을 정의
    - 데이터 서비스 일관성이 애플리케이션 운영에 미치는 영향을 파악
    - 애플리케이션의 액세스 요구 사항을 충족하는 데이터 서비스를 선택
    - 하이브리드 또는 비클라우드 네이티브 애플리케이션과 함께 사용할 수 있는 스토리지 서비스를 식별

<br>



영역 2. 고성능 아키텍처 설계 (28%)

- 워크로드를 위한 탄력적이고 확장 가능한 컴퓨팅 솔루션 식별
    - 컴퓨팅, 스토리지 및 네트워킹 요구 사항에 따라 적절한 인스턴스를 선택
    - 성능 요구 사항을 충족하도록 확장 가능한 적절한 아키텍처 및 서비스를 선택
    - 솔루션의 성능을 모니터링하는 지표를 식별
- 워크로드를 위한 확장 가능한 고성능 스토리지 솔루션 선택
    - 성능 요구 사항을 충족하는 스토리지 서비스 및 구성을 선택
    - 향후 요구 사항을 수용하도록 확장 가능한 스토리지 서비스를 결정합니다.
- 워크로드를 위한 고성능 네트워킹 솔루션 선택
    - 성능 요구 사항을 충족하는 데 적절한 AWS 연결 옵션을 선택
    - AWS 퍼블릭 서비스에 대한 연결을 최적화하는 데 적절한 기능을 선택
    - 성능 이점을 제공하는 엣지 캐싱 전략을 결정
    - 마이그레이션 및/또는 수집에 적합한 데이터 전송 서비스를 선택

<br>



영역 3. 안전한 애플리케이션 및 아키텍처 설계 (24%)

- AWS 리소스에 대한 보안 액세스 설계
    - 사용자, 그룹, 역할 간에 선택할 시점을 결정합니다.
    - 지정된 액세스 정책의 순 효과를 해석
    - 루트 계정을 보호하는 데 적절한 기술을 선택
    - AWS IAM 의 기능을 사용하여 자격 증명을 보호하는 방법을 결정
    - 애플리케이션이 AWS API 에 액세스할 수 있는 안전한 방법을 결정
    - AWS 리소스에 대한 액세스 추적 가능성을 생성하는 데 적절한 서비스를 선택
- 보안 애플리케이션 계층 설계
    - 주어진 트래픽 제어 요구 사항에 따라 보안 그룹 및 네트워크 ACL 을 사용할 시점 및 방법을 결정
    - 퍼블릭 서브넷과 프라이빗 서브넷을 사용하여 네트워크 세분화 전략을 결정
    - Amazon VPC 에서 AWS 서비스 엔드포인트 또는 인터넷 기반 리소스에 안전하게 액세스하는 데 적절한 라우팅 메커니즘을 선택
    - 외부 위협으로부터 애플리케이션을 보호하는 데 적절한 AWS 서비스를 선택

- 적절한 데이터 보안 옵션 선택
    - 액세스 패턴을 기반으로 개체에 적용해야 하는 정책을 결정합니다.
    - AWS 서비스의 저장 데이터 및 전송 중 데이터에 적절한 암호화 옵션을 선택
    - 요구 사항에 따라 적절한 키 관리 옵션을 선택

<br>



영역 4. 비용에 최적화된 아키텍처 설계 (18%)

- 비용 효율적인 스토리지 솔루션 식별
    - 요구 사항에 따라 가장 비용 효율적인 데이터 스토리지 옵션을 결정
    - 비용을 최소화하기 위해 시간 경과에 따라 데이터를 스토리지 계층에 저장하는 자동화된 프로세스를 적용

- 비용 효율적인 컴퓨팅 및 데이터베이스 서비스 식별
    - 워크로드의 각 측면에 대해 가장 비용 효율적인 Amazon EC2 결제 옵션을 결정
    - 요구 사항에 따라 가장 비용 효율적인 데이터베이스 옵션을 결정
    - 비용 관점에서 적절한 조정 전략을 선택
    - 워크로드에 가장 적합한 컴퓨팅 리소스를 선택하고 크기를 조정
    - 관리형 서비스 및 서버리스 아키텍처를 통해 TCO(총 소유 비용)를 최소화하는 옵션을 결정
- 비용에 최적화된 네트워크 아키텍처 설계
    - 비용을 절감하기 위해 콘텐츠 전송을 사용할 수 있는 시점을 파악
    - AWS 내에서 데이터 전송 비용을 절감하기 위한 전략을 결정
    - AWS 환경과 온프레미스 환경 간에 가장 비용 효율적인 연결 옵션을 결정

<br>

<br>



# 2.  AWS SAA C02 샘플 문항 풀기

[AWS SAA C-02 연습문제](https://d1.awsstatic.com/ko_KR/training-and-certification/docs-sa-assoc/AWS-Certified-Solutions-Architect-Associate_Sample-Questions.pdf)  <br>

(6 of 10) 5, 8, 9, 10 틀림

1. CRM(고객 관계 관리) 애플리케이션은 Application Load Balancer 뒤의 여러 가용 영역에 있는 Amazon EC2 인스턴스에서 실행됩니다. 이러한 인스턴스 중 하나에 장애가 발생하면 어떻게 됩니까?

   **A. 로드 밸런서가 장애 발생 인스턴스로 요청을 보내는 것을 중지합니다.**

   B. 로드 밸런서가 장애 발생 인스턴스를 종료합니다.

   C. 로드 밸런서가 장애 발생 인스턴스를 자동으로 교체합니다.

   D. 인스턴스가 교체될 때까지 로드 밸런서가 504 게이트웨이 시간 초과 오류를 반환합니다.

```
alb 생성시 헬스체크용 url을 설정하는 것으로 알고있다.
그래서 로드 밸런싱시 헬스체크하면서 장애가 발생하지 않은 인스턴스에 요청을 보내는 것으로 안다.

B는 로드밸런서가 할 수 없는 행위라고 생각

C는 lb가 아닌 AutoScailing이 비정상으로 종료된 인스턴스를 종료하고 교체하는것으로 알고있음

D는 504는 보통 요청 타임아웃 발생시 뱉는 에러라고 알고있는데, 인스턴스 교체될때의 내용은 아닌 것 같다.
```

**`정답 : (A)`**

<br>

2. Amazon SQS 를 분리된 아키텍처로 갖추고 있는 회사에서 비동기 처리를 수행해야 합니다. 이 회사는 폴링 요청의 빈 응답 수를 최소로 유지하려고 합니다. 빈 응답을 줄이려면 솔루션 아키텍트는 어떻게 해야 합니까?

   A. 큐의 메시지 최대 보존 기간을 늘립니다.

   B. 큐의 재드라이브 정책에서 최대 수신 수를 늘립니다.

   C. 큐의 기본 가시성 제한 시간을 늘립니다.

   **D.  큐의 수신 메시지 대기 시간을 늘립니다**

```
빈 응답을 줄인다는것은 아마 제대로된 응답을 받지 못하는 상황을 줄여야 한다는 것으로 이해
그래서 메시지를 큐에서 잘 보관해야 올바른 응답이든, 서킷브레이커같은 응답을 내려줄 수 있다고 생각함.
그래서 메시지의 보존기간을 늘려 삭제하지 못하도록 첫번째인 A의 보존기간을 후보로 선택을 하였고

큐에 담을 수 있는 메시지 갯수는 매우 많다고 알고있어서 재드라이브 정책이 뭔진 모르겠지만 갯수와 상관이 없다고 생각하여 B는 제외

C는 가시성이라하면 하나의 큐에 여러 서버가 동일 메시지 처리하는 것을 방지하고자 특정 시간동안 다른곳에서 해당 메시지를 볼 수 없는 것으로 알고있어서 c도 제외

D는 문제에서 폴링 요청이라고 했으니 숏폴링으로 분산된 큐에 유효한 메시지가 없어도 무조건 응답을 하는 상황을 방지하려고 하는 것 같아 메시지 수신 대기 시간을 늘려 유효한 msg를 처리할때까지 기다리도록 하는 D를 선택
```

**`정답 : (D)`**

<br>

3. 회사에서 현재 로컬 드라이브에 온프레미스 애플리케이션의 데이터를 저장합니다.
   CTO(Chief Technology Officer)는 Amazon S3 에 데이터를 저장하여 하드웨어 비용을 절감하려고 하지만 애플리케이션 수정은 원치 않습니다. 대기 시간을 최소화하려면 자주 액세스하는 데이터를 로컬에서 사용할 수 있도록 해야 합니다. 로컬 스토리지 비용을 절감하기 위하 솔루션 아키텍트가 구현할 수 있는 안정적이고 내구성 있는 솔루션은 무엇입니까?

   A. 로컬 서버에 SFTP 클라이언트를 배포하고 SFTP 용 AWS Transfer 를 사용하여 Amazon S3 로 데이터를 전송합니다.

   **B. 캐시된 볼륨 모드로 구성된 AWS Storage Gateway 볼륨 게이트웨이를 배포합니다.**

   C. 로컬 서버에 AWS DataSync 에이전트를 배포하고 S3 버킷을 대상으로 구성합니다.

   D. 저장된 볼륨 모드로 구성된 AWS Storage Gateway 볼륨 게이트웨이를 배포합니다.

```
문제에서 대기시간을 최소화 및 엑세스 시간을 줄이려고 한다고 나와있다.
해당 문구를 통해 캐싱이 떠올랐으며 AWS Storage Gateway 볼륨 게이트웨이가 뭔지는 모르겠지만 캐시된 볼륨이라 하여 B를 선택

공부가 필요해보이는 키워드
- SFTP 클라이언트
- AWS Transfer
- AWS Storage Gateway 볼륨 게이트웨이
- AWS DataSync
```

**`정답 : (B)`**

<br>

4. 회사가 여러 가용 영역에 걸친 VPC 에서 퍼블릭 3 계층 웹 애플리케이션을 실행합니다. 프라이빗 서브넷에서 실행되는 애플리케이션 계층의 Amazon EC2 인스턴스가 인터넷에서 소프트웨어 패치를 다운로드해야 합니다. 하지만 인스턴스는 인터넷에서 직접 액세스할 수 없습니다. 인스턴스가 필요한 패치를 다운로드할 수 있도록 하려면 어떤 조치를 취해야 합니까? (2 개 항목 선택)

   **A. 퍼블릭 서브넷에서 NAT 게이트웨이를 구성합니다.**

   **B. 인터넷 트래픽을 위해 NAT 게이트웨이로 라우팅되는 사용자 지정 라우팅 테이블을 정의하고 이를 애플리케이션 계층의 프라이빗 서브넷과 연결합니다.**

   C. 애플리케이션 인스턴스에 Elastic IP 주소를 할당합니다.

   D. 인터넷 트래픽을 위해 인터넷 게이트웨이로 라우팅되는 사용자 지정 라우팅 테이블을 정의하고 이를 애플리케이션 계층의 프라이빗 서브넷과 연결합니다.

   E. 프라이빗 서브넷에 NAT 인스턴스를 구성합니다.



```
private subnet에 인스턴스가 존재, private에는 말그대로 보안을 위해 제한된 공간이라 결국 public subnet을 통해 패치를 다운해야한다고 생각, 다이렉트 접근은 금지해야한다.

A, B는 결국 인터넷 연결을 위해 public 서브넷에 NAT 게이트웨이를 둬야한다는 말을 뜻하여 선택
C는 고정 ip 부여를 뜻함으로 제외
D는 B랑 비슷해보이는 말이지만 IGW 와 프라이빗 서브넷을 연결한다는 뜻이기에 제거
E는 애초에 퍼블릭을 통해 private를 접근해야하므로 E 제거
```

**`정답 : (A, B)`**

<br>

5. 솔루션 아키텍트가 2 주간의 회사 휴무 기간 동안 실행할 필요가 없는 Amazon EC2 인스턴스의 비용을 절약하는 솔루션을 설계하려고 합니다. 인스턴스에서 실행되는 애플리케이션은 인스턴스 작업이 재개될 때 필요한 데이터를 인스턴스 메모리(RAM)에 저장합니다. 솔루션 아키텍트는 인스턴스의 종료 및 재개를 위해 어떤 방법을 권장해야 합니까?

   **A. 인스턴스 저장소 볼륨에 데이터를 저장하도록 애플리케이션을 수정합니다. 다시 시작할 때 볼륨을 다시 연결합니다.**

   B. 인스턴스를 중지하기 전에 스냅샷을 만듭니다. 인스턴스를 다시 시작한 후 스냅샷을 복원합니다.

   C. 최대 절전 모드가 활성화된 인스턴스에서 애플리케이션을 실행합니다. 종료하기 전에 인스턴스를 최대 절전 모드로 전환합니다.

   D. 각 인스턴스의 가용 영역을 기록한 후 인스턴스를 중지합니다. 종료 후 동일한 가용 영역에서 인스턴스를 다시 시작합니다.

```
데이터를 RAM에 저장한다는 것은 비휘발성인 스토리지를 선택해야된다고 판단으로
EBS를 떠올렸고 온디맨드 인스턴스에 상관없이 데이터를 반 영구적으로 저장할 수 있는 A를 선택함

답은 C인데 해설을 보니, 최대 절전 모드로 전환하면 알아서 RAM 내용을 EBS에 저장하고, 다시 시작되면 RAM 내용이 로드 된다고 한다.

뒤늦게 생각났는데 EBS엔 두가지 방식이 있는데
1. EBS based 방식은 반 영구적이고
2. 인스턴스 스토리지는 휘발성인데

아무래도 인스턴스 스토리지 == 인스턴스 저장소 볼륨이라고 생각해야되는 것 같다.
```

**`정답 : (C)`**

<br>

6. 회사에서 VPC 의 Amazon EC2 인스턴스에서 모니터링 애플리케이션을 실행할 계획입니다.
   인스턴스에 연결 시 프라이빗 IPv4 주소를 사용합니다. 솔루션 아키텍트는 애플리케이션에 장애가 발생하여 도달할 수 없을 때 트래픽이 대기 인스턴스로 신속하게 전달될 수 있는 솔루션을 설계해야 합니다. 이러한 요구 사항을 충족하려면 어떻게 해야 합니까?

   A. 프라이빗 IP 주소에 대한 리스너로 구성된 Application Load Balancer 를 배포하고 기본 인스턴스를 로드 밸런서에 등록합니다. 장애 발생 시 인스턴스를 등록 취소하고 보조 인스턴스를 등록합니다.

   B. 사용자 지정 DHCP 옵션 세트를 구성합니다. 기본 인스턴스에 장애가 발생하면 동일한 프라이빗 IP 주소를 보조 인스턴스에 할당하도록 DHCP 를 구성합니다.

   **C. 프라이빗 IP 주소로 구성된 인스턴스에 보조 ENI(탄력적 네트워크 인터페이스)를 연결합니다. 기본 인스턴스에 도달할 수 없는 경우 ENI 를 대기 인스턴스로 이동합니다.**

   D. Elastic IP 주소를 기본 인스턴스의 네트워크 인터페이스와 연결합니다. 발생 시 Elastic IP 를 기본 인스턴스에서 분리하고 보조 인스턴스와 연결합니다

```
문제에서 장애가 발생했을 경우 트래픽을 대기 인스턴스로 전달한다는 것인데 이때 프라이빗 IPv4로 연결한다는 것으로 이해하였다.

A는 장애 발생시 인스턴스 등록을 취소하고 보조 인스턴스를 등록하는 것 자체가 트래픽 제어가 힘들어 보여 제거
B는 DHCP가 뭔지 몰라 패스
C는 ENI가 뭔지 몰라 패스
D는 EIP 자체가 프라이빗하지 않기 때문에 보조인스턴스에 EIP를 연결하는것 자체가 모순이라고 생각

그래서 답은 B 아님 C라고 생각하며, C로 찍음
```

**`정답 : (C)`**

<br>

7. 애널리틱스 회사에서 사용자에게 사이트 애널리틱스 서비스를 제공할 계획입니다. 이 서비스를 사용하려면 사용자의 웹 페이지에 회사의 Amazon S3 버킷에 인증된 GET 요청을 하는 JavaScript 스크립트가 있어야 합니다. 이 스크립트가 성공적으로 실행되도록 하기 위해 솔루션 아키텍트는 무엇을 해야 합니까?

   **A. S3 버킷에서 CORS(Cross-Origin Resource Sharing)를 활성화합니다.**

   B. S3 버킷에서 S3 버전 관리를 활성화합니다.

   C. 사용자에게 스크립트의 서명된 URL 을 제공합니다.

   D. 퍼블릭 실행 권한을 허용하도록 버킷 정책을 구성합니다.

```
A - 서로 다른 도메인 간에 통신을 해야 하는 경우 브라우저의 보안 정책으로 인하여 통신이 불가능하다. 
이런 경우 CORS 설정으로 해결할 수 있는데 문제가 CORS를 말하는 것인지 헷갈렸지만 문제에서 HTTP METHOD GET을 어필하기에 A 선택
B - 버전 관리 이야기라 제거
C - 미리 서명된 URL을 사용하면 S3 버킷에 액세스하는 데 사용할 수 있는 URL을 생성하고 접근이 가능하기에 고민
D - 퍼블릭 실행 권한은 S3 버킷 객체 소유권에 관련된 말 같아서 제거
```

**`정답 : (A)`**

<br>

8. 회사 보안팀은 클라우드에 저장된 모든 데이터가 미사용 시 온프레미스에 저장된 암호화 키로 항상 암호화되도록 요구합니다.
   이러한 요구 사항을 충족하는 암호화 옵션은 무엇입니까?  (2 개 항목 선택)
   **A. Amazon S3 관리 키(SSE-S3)와 함께 서버 측 암호화를 사용합니다.**

   **B. AWS KMS 관리 키(SSE-KMS)와 함께 서버 측 암호화를 사용합니다.**

   C. 고객 제공 키(SSE-C)와 함께 서버 측 암호화를 사용합니다.

   D. 클라이언트 측 암호화를 통해 미사용 시 암호화를 제공합니다.

   E. Amazon S3 이벤트에 의해 트리거된 AWS Lambda 함수를 사용하여 고객 키로 데이터를 암호화합니다.

```
A. S3는 기본적으로 비공개 버킷으로 되어있으니 S3에서 관리해도 괜찮을 것 같아 A 선택
B. KMS가 뭔진 모르겠지만 나머지 문항들은 다 고객이 제공해주는 키를 이용하여 암호화하기에 B 선택
C. 고객이 제공해주는 키로 암호화라 제거
D. 암호화는 클라이언트가 알면 암호화가 아님 얄짤없이 제거
E. C, D와 마찬가지 이유로 제거

답은 C, D이다
암호화 서비스를 공부 해야겠다.
```

**`정답 : (C, D)`**

<br>

9. 회사에서 규정 요구 사항으로 인해 최소 5 년간 액세스 로그를 유지해야 합니다. 한번 저장된 데이터는 거의 액세스되지 않지만 필요한 경우 하루 전에 통지를 받으면 액세스할 수 있어야 합니다. 이러한 요구 사항을 충족하는 가장 비용 효율적인 데이터 스토리지 솔루션은 무엇입니까?

   A. Amazon S3 Glacier Deep Archive 스토리지에 데이터를 저장하고 수명주기 규칙을 사용하여 5 년 후 객체를 삭제합니다.

   B. Amazon S3 Standard 스토리지에 데이터를 저장하고 수명주기 규칙을 사용하여 30 일 후 Amazon S3 Glacier 로 전환합니다.

   C. Amazon CloudWatch Logs 를 사용하여 데이터를 로그에 저장하고 보존 기간을 5 년으로 설정합니다.

   D. **Amazon S3 Standard-Infrequent Access(S3 Standard-IA) 스토리지에 데이터를 저장하고 수명주기규칙을 사용하여 5 년 후 객체를 삭제합니다**

```
문제가 말하는 엑세스 로그는 무엇일까? 로그에 대한 접근을 뜻하는건지, 데이터 접근에 대한 로그인건지
CloudWatch Logs는 로그 모니터링 및 저장, 엑세스 관리하는 서비스라서 C는 맞을 것 같음.
A, B, D는 처음들어봐서 이중에 답이 있을 것..
A, B 둘다  Amazon S3 Glacier을 어필하는것 같아 D를 선택
```

**`정답 : (A)`**

<br>

10. 회사에서 예약된 인스턴스를 사용하여 데이터 처리 워크로드를 실행하고 있습니다.
    야간 작업은 일반적으로 실행하는 데 7 시간이 걸리며 10 시간 내에 완료되어야 합니다.
    이 회사는 매달 말 일시적인 수요 증가로 인해 현재 리소스의 용량에 따른 제한 시간을 초과해서 작업이 실행될 것으로 예상합니다.
    일단 시작된 처리 작업은 완료 전에 중단할 수 없습니다. 이 회사는 가능한 한 비용 효율적으로 용량을 늘릴 수 있는 솔루션을 구현하려고 합니다.
    이를 위해 솔루션 아키텍트는 어떻게 해야 합니까?

    A. 수요가 늘어나는 동안 온디맨드 인스턴스를 배포합니다.

    **B. 추가 인스턴스에 대하여 두 번째 Amazon EC2 예약을 생성합니다.**

    C. 수요가 늘어나는 동안 스팟 인스턴스를 배포합니다.

    D. 증가된 워크로드를 지원하도록 Amazon EC2 예약에서 인스턴스의 인스턴스 크기를 늘립니다.

```
문제의 포인트는 비용을 효율적으로 사용할 수 있는 인스턴스를 구하는 것.

A. 온디맨드 인스턴스는 실행하는 인스턴스에 따라 시간 또는 초당 측정된 가격을 지불하고 OS별로 가격 정책이 다름
B. 예약 인스턴스는 할인권을 사서 할인권을 적용하여 저렴하게 서비스를 운영할 수 있는 약정 정책이라 수요 예측이 잘 알고있어서
계약 기간을 정할 수 있으면 온디맨드 보다 쌈
C. 스팟 인스턴스는 AWS 내에 특정 인스턴스를 선택하는것이 아닌, 놀고있는 컴퓨터를 인스턴스로 하는 정책.
노는 컴퓨터를 많을때 가격이 저렴, 노는 컴퓨터가 없으면 가격이 일반가격보다 비싼 가변적 요금
D. 인스턴스 크기 늘리는거 자체가 비용이 많이 드는 작업

현재 매달 말에 일시적인 수요가 증가한다는 예측을 할 수 있으므로 예약 인스턴스가 스팟 인스턴스와 온디맨드 인스턴스보다 쌀 것으로 예상하여
B를 선택
```

**`정답 : (A)`**

<br>
<br>

# 3. AWS SAA C01 샘플 문항 풀기

[AWS SAA C01 샘플 문항](https://d1.awsstatic.com/training-and-certification/docs/AWS_Certified_Solutions_Architect_Associate_Sample_Questions.pdf)

(9 of 10) 8 틀림

1. A company is storing an access key (access key ID and secret access key) in a text file on a custom AMI.
   The company uses the access key to access DynamoDB tables from instances created from the AMI.
   The security team has mandated a more secure solution.
   Which solution will meet the security team’s mandate?

   A. Put the access key in an S3 bucket, and retrieve the access key on boot from the instance.

   B. Pass the access key to the instances through instance user data.

   C. Obtain the access key from a key server launched in a private subnet.

   **D. Create an IAM role with permissions to access the table, and launch all instances with the new role.**

```
문제에서 회사가 AMI의 텍스트 파일에 엑세스 키를 저장하는데 보다 어떤 시큐어 서비스를 사용하는게 좋을지 묻는 것 같다.

보자마자 시큐어 매니저 서비스가 떠올랐지만 지문에 없었기에 엑세스키를 어떻게 관리하는게 좋을지 고민했다.
이 엑세스키를 통해 다이나모디비 테이블을 접근한다고 했으니, 

A - S3는 기존적으로 버킷 접근에 대해 private하게 되어있어서 S3에 보관하고, 인스턴스가 부팅할때 검색하는 방법이 괜찮지 않을까 A 후보군
B - 인스턴스 사용자 데이터만을 판단하기에는 위험성이 따라보인다.
C - 키서버를 별도로 두는 것, 그리고 private subnet 내에서 관리하는것도 괜찮아 보여서 C도 후보군
D - 문제에서 테이블을 접근하기 위해서 저장하는 것으로 보아 테이블만 접근할 수 있는 IAM롤을 부여하는것도 괜찮아 D도 후보군

A, B, D 중 문제 포인트는 현재 방법보다 더 안전한걸 원한다. 더 안전하다는 걸 원한다는 것은 엑세스키를 통해 디비 접근하는게 안전하지 않다고 생각하여 별도로 관리하는 A, B 보다 권한을 부여하는 D를 선택

```

**`정답 : (D)`**

<br>

2. A company is developing a highly available web application using stateless web servers. Which services are suitable for storing session state data? (Select TWO.)

   A. CloudWatch

   **B. DynamoDB**

   C. Elastic Load Balancing

   **D. ElastiCache**

   E. Storage Gateway

```
세션 데이터를 저장하기 적합한 서비스를 고르는 문제 같다.
A - 로그 모니터링 서비스로 부적합
B - DB
C - 트래픽 분산
D - 엘라스틱캐시, 세션 데이터를 저장하기 적합한 캐시 같다.
E - 스토리지 게이트웨이

B, E 둘중 하나 고민하다가 B 선택
이유는 Storage Gateway가 무엇인지 모르기에 키-벨류 디비인 DynamoDB 선택
```

**`정답 : (B, D)`**

<br>

3. Company salespeople upload their sales figures daily. A Solutions Architect needs a durable storage solution for these documents that also protects against users accidentally deleting important documents.
   Which action will protect against unintended user actions?

   A. Store data in an EBS volume and create snapshots once a week.

   B. **Store data in an S3 bucket and enable versioning.**

   C. Store data in two S3 buckets in different AWS regions.

   D. Store data on EC2 instance storage.

```
갑작스런 데이터 삭제를 방지하고자 적절한 솔루션을 찾는 문제 같다.
A - 주마다 스냅샷 생성과 EBS 볼륨, 스냅샷은 좋아보이지만 주마다 1번 스냅샷을 뜨면 그 사이에 지워버린 데이터들은 관리하지 못할 것 같아 패스
B - S3 버킷 버저닝, 매일마다 버전 관리를 통해 이전 버전을 통해 지워진 데이터 관리도 가능할 것 같다.
C - 다른 AWS 지역에 위치한 S3 버킷 2개 -> 데이터 정합성 문제가 생길 수 있다.
D - 인스턴스 스토리지, A, B보다 비효율적인 서비스 같다. 
```

**`정답 : (B)`**

<br>

4. An application requires a highly available relational database with an initial storage capacity of 8 TB. The database will grow by 8 GB every day. To support expected traffic, at least eight read replicas will be required to handle database reads.
   Which option will meet these requirements?

   A. DynamoDB

   B. Amazon S3

   **C. Amazon Aurora**

   D. Amazon Redshift

```
8테라정도 관리할 수 있는 RDB, 레플리카 관리를 위한 적절한 db는?

A - NOSQL 이라 RDB가 아님
B - S3는 파일, 텍스트, 사진 등 Object 저장소임
C - RDB
D - 뭔지 모르겠음
```

**`정답 : (C)`**

<br>

5. A Solutions Architect is designing a critical business application with a relational database that runs on an EC2 instance.
   It requires a single EBS volume that can support up to 16,000 IOPS.
   Which Amazon EBS volume type can meet the performance requirements of this application?

   **A. EBS Provisioned IOPS SSD**

   B. EBS Throughput Optimized HDD

   C. EBS General Purpose SSD

   D. EBS Cold HDD

```
IOPS가 뭔지 모르겠지만, 인스턴스 내 디비도 같이 있는 것 같고 16,000 이상 IOPS를 지원하는 싱글 블록 스토리지가 필요해보인다고 한다.
스토리지 퍼포먼스 관련해서 선택하는 문제 같음, 하나의 인스턴스에 어플리케이션과 디비가 있다는 것은 속도 측면에서 HHD보다 SSD가 더 효율적이라 생각한다.
A - 모르겠지만 SSD라 후보군
B - HDD라 제거
C - 일반적인 목적 SSD 같음
D - HDD라 제거

A 로 찍음
```

**`정답 : (A)`**

<br>

6. A web application allows customers to upload orders to an S3 bucket. The resulting Amazon S3 events trigger a Lambda function that inserts a message to an SQS queue. A single EC2 instance reads messages from the queue, processes them, and stores them in an DynamoDB table partitioned by unique order ID. Next month traffic is expected to increase by a factor of 10 and a Solutions Architect is reviewing the architecture for possible scaling problems. Which component is MOST likely to need re-architecting to be able to scale to accommodate the new traffic?

   A. Lambda function

   B. SQS queue

   **C. EC2 instance**

   D. DynamoDB table

```
문제에서 사용자들은 S3 버킷에 업로드를 하고, S3 이벤트 결과를 람다 함수가 트리거하여 SQS 큐에 메시지를 삽입해주고,
EC2 인스턴스는 큐로부터 메시지를 읽고, 다이나모 디비에 저장한다.
이때, 트래픽 증가시 스케일 확장하는 문제가 있는데 어느 부분을 재설계를 하는게 좋을까 물어보는 문제 같다.
이 문제의 포인트는 현재 많은 트래픽을 감당하지 못하고 있는 서비스를 고르는 것 같다.

우선,
D는 트래픽을 떠나 마지막에 데이터를 저장하는 단계이기 때문에, 트래픽과 크게 관련있어보이지 않아 제거
A는 많은 트래픽이 발생할 경우 수천개까지 자동 확장이 가능한 것으로 알고있다.
B도 많은 메시지를 보관할 수 있는것으로 알고있다.
C는 오토스케일링으로 확장시키면 될 것 같다고 생각하여 제거하였으니 문제에서 A Single EC2라고 명시가 되어있어서 EC2에서 병목현상이 발생할 수 있다고 판단하여 C 선택
```

**`정답 : (C)`**

<br>

7. An application saves the logs to an S3 bucket. A user wants to keep the logs for one month for troubleshooting purposes, and then purge the logs. What feature will enable this?

   A. Adding a bucket policy on the S3 bucket.

   **B. Configuring lifecycle configuration rules on the S3 bucket.**

   C. Creating an IAM policy for the S3 bucket.

   D. Enabling CORS on the S3 bucket.

```
문제는 S3에 로그를 저장하는데, 한달동안 로그를 저장하는 것을 원한다. 이때 원하는 서비스를 고르는게 문제 같다.
A - S3 버킷 정책을 추가한다. - 버킷 정책에 뭐가 있는지 모르겠어서 일단 후보군
B - S3 버킷의 라이프사이클을 설정한다. 라이프사이클을 잘 몰라서 후보군.
C - IAM 정책을 생성한다. - 접근 권한 관점이기에 저장 관점이랑 다른 내용이라 제거
D - CORS를 활성화한다. -> 통신관점이기에 저장 관점이랑 다른 내용이라 제거

A, B랑 고민하다가 저장관점이면 버킷 정책보다 라이프사이클에 좀 더 관련이 있을 것 같아 B 선택
```

**`정답 : (B)`**

<br>

8. An application running on EC2 instances processes sensitive information stored on Amazon S3.
   The information is accessd over the Internet. The security team is concerned that the Internet connectivity to Amazon S3 is a security risk. Which solution will resolve the security concern?

   A. Access the data through an Internet Gateway.

   B. Access the data through a VPN connection.

   **C. Access the data through a NAT Gateay.**

   D. Access the data through a VPC endpoint for Amazon S3.

```
EC2가 민감한 정보를 S3에 저장한다. 해당 정보는 인터넷에서 접근이 가능하다.
시큐리티 팀이 S3에 인터넷 접근이 가능한 것에 민감하며, 어떻게 해결할 수 있는지 묻고 있다.
A - IGW를 통해 데이터 접근을 한다고 하는데 IGW는 결국 인터넷 허용이라 문제에서 제기하는 문제랑 같은 내용이라 제거
B - VPN 접속을 통해 데이터 접근
C - NAT 게이트웨이를 통해 접근
D - VPC를 통해 S3 엔드포인트로 데이터 접근

인터넷이라 하면 결국 퍼블릭한 접근이 문제라고 생각하여 퍼블릭에 대한 A, D는 제거
B, C 중에 NAT 게이트웨이가 보통 보안을 위한 용도로 많이 쓰이기에 EC2 인스턴스가 S3에 접근할 때 NAT 게이트웨이를 통해 데이터를 저장할 수 있도록 생각하여 C 선택
```

**`정답 : (D)`**

<br>

9. An organization is building an Amazon Redshift cluster in their shared services VPC.
   The cluster will host sensitive data. How can the organization control which networks can access the cluster?

   A. Run the cluster in a different VPC and connect through VPC peering.

   B. Create a database user inside the Amazon Redshift cluster only for users on the network.

   **C. Define a cluster security group for the cluster that allows access from the allowed networks.**

   D. Only allow access to networks that connect with the shared services network via VPN.

```
문제에서 말하는 AWS RedShift가 어떤 서비스인지 모르겠으나 같은 VPC 내 클러스터에서
공유하고 있는 서비스 간 민감한 정보를 어떻게 접근하도록 다룰 수 있는지 여쭤보는 것 같다.
A - VPC 피어링은 서로 다른 VPC끼리 통신하기 위함으로 알고있기에 제거
B - 데이터베이스 관련 얘기 같아서 쌩둥맞아 제거
C - 시큐리티 그룹을 정의해서 네트워크 허락하는 방법
D - VPN을 통해 공유된 서비스들에 대한 접근 허락하는 방법

C, D 둘다 네트워크 접속을 컨트롤 할 수 있는 방법이라 둘 중에 하나 같다.
시큐리티 그룹을 통해 클러스터간 허용된 IP만 접근할 수 있도록 할 수 있기에 C선택
```

**`정답 : (C)`**

<br>

10. A Solutions Architect is designing an online shopping application running in a VPC on EC2 instances behind an ELB Application Load Balancer. The instances run in an Auto Scaling group across multiple Availability Zones.
    The application tier must read and write data to a customer managed database cluster.
    There should be no access to the database from the Internet, but the cluster must be able to obtain software patches from the Internet. Which VPC design meets these requirements?

    A. Public subnets for both the application tier and the database cluster

    B. Public subnets for the application tier, and private subnets for the database cluster

    **C. Public subnets for the application tier and NAT Gateway, and private subnets for the database cluster**

    D. Public subnets for the application tier, and private subnets for the database cluster and NAT Gateway

```
쇼핑몰 어플리케이션을 EC2에 운영중이고 ec2는 로드 밸런서 뒤에 있다. 어플리케이션은 디비에 io 가능
이때 인터넷 -> DB에 엑세스 할 수 없지만 클러스터는 인터넷으로부터 소프트웨어 패치를 가져올 수 있어야 한다고 할때
어떤 VPC 디자인이 필요로 하는지 묻고 있는 것 같다.
이럴땐 보통 private subnet에 보안관련 서비스 (디비포함)을 두고 NAT Gateway를 이용하여 하는 것으로 알고있따.
A - 어플리케이션, 디비를 둘다 public에 위치한다는 말에 제거 
B - 어플리케이션은 publc, 디비는 prviate ok, 하지만 디비에서 인터넷 접근을 못하므로 제거
C - NAT 게이트웨를 public, 디비는 private ok
D - 어플리케이션을 public, NAT Gateway랑 디비를 private subnet에 private subnet에는 보통 igw를 두지 않기 때문에
NAT Gateway를 두더라도 public에 두어야 하므로 제거

C 선택
```

**`정답 : (C)`**

<br>
<br>



# 4. 강의 콘텐츠 선정

```
1. IAM
2. EC2 기초
3. EC2 - 솔ㄹ션스 아키텍트 어소시에이트 레벨
4. EC2 인스턴스 스토리지
5. 고가용성 및 스케일링성 : ELB 및 ASG
6. AWS 기초 : RDS + Aurora + ElasticCache
7. Route53
8. Amazon S3 소개
9. 고급 S3 및 Athena
10. CloudFront 및 AWS 글로벌 엑셀러레이터
11. 디커플링 어플리케이션 : SQS, SNS, Kinesis, Active MQ
12. 솔루션 설계자 관점의 서버리스 개요
13. AWS의 데이터베이스
14. AWS 모니터링 및 감사 : CloudWatch, CloudTrail 및 Config
15. 네트워킹 VPC 
```

- 선정 이유
    - **출제 비율 고려** 및 현재 **실무에서 다루는 혹은 다뤄야할 서비스 위주**로 선정