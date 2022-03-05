# AWS Certification Official Practice Question Sets (Korean)

---

문제 1.

![Untitled](questions/q01.png)

---

**전용 인스턴스**

- 기존 서버 바인딩 소프트웨어 라이선스 사용 - 비용절감
- 피크 소비에 맞춰 구매할 필요 없음
- 온디맨드 확장 가능

**온디맨드 스케일링 : 동적 공급**

[https://docs.aws.amazon.com/wellarchitected/latest/cost-optimization-pillar/dynamic-supply.html](https://docs.aws.amazon.com/wellarchitected/latest/cost-optimization-pillar/dynamic-supply.html)

**SQS FIFO**

- 메세지 선입선출 기능
- SQS 대기열 생성 이후 변환이 불가

Lambda

- 15분의 운영 제한 시간 존재
- [람다의 제약사항](https://docs.aws.amazon.com/lambda/latest/dg/gettingstarted-limits.html)

ASG 와 SQS

- CloudWatch 에 ApproximateNumberOfMessages 지표 존재
- 이를 통한 EC2 스케일링 그룹 구성 가능
- [Amazon SQS에 따른 조정](https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-using-sqs-queue.html)

정답 : D

---

문제 2.

![Untitled](questions/Untitled%201.png)

---

**ALB 라우팅**

- URL 기반 라우팅 시 동일한 리스너 포트 사용

Route 53

- 장애 조치 라우팅
    - 기본 인스턴스 장애 시 백업 인스턴스로 라우팅 가능
- 가중치 기반 라우팅
    - 트래픽을 지정한 비율로 라우팅 가능
- [라우팅 정책 선택](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-policy.html) 을 참조

정답 : B

---

문제 3.

![Untitled](questions/Untitled%202.png)

---

**다중 AZ**

- 고가용성 확보
- ASG 는 여러 가용 영역 간 확장 가능

정답 : D

---

문제 4.

![Untitled](questions/Untitled%203.png)

---

S3

- 버저닝 지원
- MFA 로 추가 객체 보안 계층 구성 가능
- 리전 간 복제 가능 - 버전관리가 전제 조건
- 수명 주기 정책 구성 지원

정답 : A

---

문제 5.

![Untitled](questions/Untitled%204.png)

---

**ASG 쿨다운**

- 활동 후 인스턴스 시작 혹은 종료하지 않은 기간

**ELB 등록 취소 지연 ( 커넥션 드레이닝, 디레지스터 딜레이 )**

- 기본 300 초
- 해당 시간 동안 진행 중인 요청을 완료 시킬 수 있음

정답 : D

---

문제 6.

![Untitled](questions/Untitled%205.png)

---

스팟 인스턴스 제거

- 스팟 요청 취소 → 스팟 인스턴스 종료
- 스팟 요청이 있는 한, 최소할 때까지 새 인스턴스가 시작됨

정답 : C

---

문제 7.

![Untitled](questions/Untitled%206.png)

---

인스턴스 메타데이터

- curl http://169.254.169.254/latest/meta-data

정답 : A

---

문제 8.

![Untitled](questions/Untitled%207.png)

---

S3

- 단일 PUT 에 대해 5GB 제한 존재
- S3 Transfer Acceleration
    - 엣지 로케이션 → S3 복제 - 업로드 시간 단축
    - 단일 PUT 제한 ( 5GB ) 를 해결할 순 없음
- 멀티파트 업로드로 5GB 제한 극복 가능

정답 : C

---

문제 9.

![Untitled](questions/Untitled%208.png)

---

EBS 처리량

- HDD : < 500 IPOS
- 프로비저닝 IOPS SSD : < 64000 IPOS
- 범용 SSD : < 16000 IOPS
- 콜드 HDD : IOPS 로 정의하지 않음. 대용량 콜드 데이터 워크로드에 적합

정답 : B

---

문제 10.

![Untitled](questions/Untitled%209.png)

---

게이트웨이

- 인터넷 GW
    - VPC 에 연결
    - VPC 안팎으로 트래픽 흐르도록 허용
    - 인터넷 GW 는 개방형 인터넷 트래픽을 위해 설계됨
    - VPN 연결 생성 불가
- NAT GW
    - 프라이빗 EC2 에서 인터넷에 요청 보낼 수 있음
    - VPN 연결 생성 불가
- 고객 GW
    - VPN 연결 생성 가능
- Amazon API GW
    - API 액세스 정문 역할
    - 매니지드 서비스
- 가상 프라이빗 GW
    - VPC 에 연결되어 개방형 퍼블릭 인터넷 통과 필요 없이 Site-to-Site VPN 연결 생성 가능

정답 : C, E

---

문제 11.

![Untitled](questions/Untitled%2010.png)

---

오로라

- 관계형 디비
- 마이크로초 대기 시간 일관 유지 못할 수 있음

다이나모디비

- 키-밸류 NoSQL
- Accelerator(DAX) 지원
    - 마이크로초 단위 응답 시간 제공

넵튠

- 그래프 디비

정답 : B

---

문제 12.

![Untitled](questions/Untitled%2011.png)

---

정답 : B

---

문제 13.

![Untitled](questions/Untitled%2012.png)

---

Amazon Cognito

- 웹 및 모바일 앱에 대한 인증, 권한 부여 및 사용자 관리 서비스
- 이름과 암호를 통한 직접 로그인 지원
- 서드 파티 로그인 지원

AWS STS

- AWS 리소스 액세스 제어를 위한 임시 보안 자격 증명 생성 및 제공 가능
- 애플리케이션에 대한 액세스와 무관

정답 : C

---

문제 14.

![Untitled](questions/Untitled%2013.png)

---

프라이빗 서브넷

- 인터넷 트래픽은 이 서브넷에 라우팅 되지 않음
- 여기에 DB 인스턴스를 배치하여 보안 계층 추가 가능

탄력적 네트워크 인터페이스

- VPC 에서 가능 네트워크 카드를 나타네는 논리 네트워킹 구성 요소

AWS Shield

- 디도스 공격 보호
- 라우팅 테이블에 있는 경로의 대상 될 수 없음

AWS Direct Connect

- AWS 에 대한 전용 연결 제공

정답 : A, E

---

문제 15.

![Untitled](questions/Untitled%2014.png)

---

보호 서비스

- Shield : DDoS 공격 보호
- Firewall Manager
    - WAF, Shield 및 기타 서비스 관리
    - EC2 에 설치되지 않는 관리형 서비스
- WAF : 크로스 사이트 스크립팅, SQL 인젝션 공격 감지, 차단

정답 : C

---

문제 16.

![Untitled](questions/Untitled%2015.png)

---

- 파일 시스템에 요구 사항이 없는 경우 비용면에서 S3 > EFS
- S3 Glacier : 장기 백업 목적의 저렴한 스토리지 클래스

정답 : B

---

문제 17.

![Untitled](questions/Untitled%2016.png)

---

정답 : A

---

문제 18.

![Untitled](questions/Untitled%2017.png)

---

Amazon SNS

- 애플리케이션 간 통신 지원
- 애플리케이션과 사용자 간 통신 지원
- 완전관리형 메시징 서비스

정답 : D

---

문제 19.

![Untitled](questions/Untitled%2018.png)

---

Fragate + Serverless : 유휴상태 비용 X

Redshift : 온라인 분석 처리 (OLAP) 를 위해 설계됨

정답 : A

---

문제 20.

![Untitled](questions/Untitled%2019.png)

---

AWS Snowball

- S3 <> 온사이트 데이터 스토리지 대량 데이터 전송
- 인터넷보다 빠른 속도
- 작업 상태 추적 인터페이스 지원

CloudFront 로의 전송은 무료이나, 온프레미스로 전송 시 비용 발생. 60TB 기준으로 Snowball 대비 2배

정답 : A