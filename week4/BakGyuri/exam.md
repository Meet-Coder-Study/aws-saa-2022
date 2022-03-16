

#  Section 30 > Practice Test 1 풀이

맞힌 문제 비율이 가장 적은 Design High-Performing Architecturs 분야에 대해 정리한다.

## 1)
![image](https://user-images.githubusercontent.com/42667951/158130363-ea947096-f745-40a9-8c9c-c734554ab68e.png)

**[풀이]**

- 문제의 Keyword : 기본 관계형 데이터베이스 스키마, 성능 관련 문제 해결, 글로벌 규모

  문제의 Keyword가 모두 **Aurora 글로벌 데이터베이스**의 대표적인 특징이다.

### 1-1) AWS Aurora

- 클라우드용으로 구축된 MySQL 및 PostgreSQL 호환 **관계형 데이터베이스**
- 성능 및 가용성(엔터프라이즈 DB) + 단순성 및 비용 효율성(오픈소스 DB)
- 데이터베이스 인스턴스 당 최대 64TB까지 자동 스케일 되는 분산형 내결함성 자가 복구 스토리지 시스템
- **Aurora 글로벌 데이터베이스** : 단일 Aurora 데이터베이스가 여러 AWS 리전에 걸쳐 있을 수 있으며, 각 리전에서 짧은 지연 시간으로 빠른 로컬 읽기를 활성화한다. 또한 DB성능에 영향을 주지 않고 데이터를 복제하고, 지역 전체의 중단으로부터 재해 복구를 제공한다.

### 1-2) AWS DynamoDB

- 모든 규모에서 한 자릿수 밀리세컨드 성능을 제공하는 **키-값 및 문서 데이터베이스** (NoSQL DB)
- 보안, 백업 및 복원, in-memory 캐싱(메인 메모리에 데이터를 저장하여 메모리와 디스크 간 병목 현상이 없어 빠른 속도를 제공), 다중 지역, 다중 마스터, 내구성 데이터베이스
- **DynamoDB 글로벌 테이블** : 선택한 AWS리전에서 DynamoDB 테이블을 자동으로 복제한다.

### 1-3) Redshift 클러스터

- 대규모 데이터 세트 저장 및 분석을 위해 설계된 **완전 관리형 페타바이트 규모**의 클라우드 기반 데이터 웨어하우스 제품



## 2)

![image](https://user-images.githubusercontent.com/42667951/158130390-e07b132c-4fea-4a94-80a5-c9d264a39a9c.png)

  **[풀이]**

- 문제의 keyword : `hot data`와 `cold data`를 모두 **빠르게** 처리

  hot data와 cold data를 빠르게 처리할 수 있는 것은 Lustre용 Amazon FSx이다.

### 2-1) Lustre용 Amazon FSx

- **Lustre란?** Linux와 Cluster의 혼성어로, HPC(고성능 컴퓨팅) 클러스터 및 환경에 사용되는 오픈소스 병렬 분산 파일 시스템을 의미함. 주로 **고성능 컴퓨팅**의 대용량 파일 시스템으로 사용됨
- 스토리지가 컴퓨팅 속도를 따라갈 만큼 **빠른 스토리지**가 필요한 애플리케이션을 위해 설계됨
- `hot data`를 병렬 및 분산 방식으로 처리하고, `cold data`는 Amazon S3에 저장. `cold data`같은 경우에도 Lustre용 Amazon FSx가 S3와 통합되어 Lustre 파일시스템으로 데이터 세트를 처리할 수 있음
- S3객체를 파일로 표시하며, 변경된 데이터를 S3에 다시 쓸 수 있음
- **hot data란?** 주어진 시스템 내에서 자주 액세스하고 전송되는 데이터
- **cold data란?** 자주 액세스 하지 않거나 적극적으로 사용하지 않는 데이터

### 2-2) Windows용 Amazon FSx

- 업계 표준 SMB(Service Message Block)프로토콜을 통해 액세스할 수 있는 **매우 안정적인 완전 관리형 파일 스토리지**를 제공
- Windows server에 구축되어 사용자 할당량, 최종 사용자 파일 복원 등 광범위한 관리 기능 제공
- S3와 연동이 되지 않음

### 2-3) Amazon EMR

- **방대한 양**의 데이터를 처리하기 위한 클라우드 **빅데이터** 플랫폼
- Apache Spark, Apache Hive, Apache HBase, Apache Flink, Apache Hudi 등 오픈소스를 사용

### 2-4) AWS Glue

- 고객이 분석을 위해 데이터를 쉽게 준비하고 로드할 수 있는 완전 관리형 서비스 (추출, 변환 및 로드)

- 일괄 ETL 데이터 처리에 사용(고성능 워크플로우 시나리오에 적합하지 않음)



## 3)

![image](https://user-images.githubusercontent.com/42667951/158130419-cd85d9c6-1885-4f6e-900b-5fd43c5fbfde.png)

**[풀이]**

- 문제의 keyword : S3에서 Kinesis로 스트리밍 하는 가장 빠른 방법 제안
- 사용자 지정 개발 시 가능한 선택지들이 존재하지만 문제에서 가장 빠른 방법을 원하였기 때문에 AWS DMS를 사용하는 것이 정답이다.

### 3-1) AWS DMS(Database Migration Service)

- 지원되는 소스에서 관계형 데이터베이스, 데이터 웨어하우스, 스트리밍 플랫폼 및 AWS 클라우드의 기타 데이터 스토리지로 마이그레이션을 돕는 도구
- 새로운 코드를 작성하고 유지 관리를 하지 않고도 애플리케이션을 확장할 수 있음

### 3-2) Lambda & Kinesis

- Lambda함수에서 Kinesis에 데이터를 보내기위해서는 사용자 지정 개발이 필요하다.
- Lambda란? 이벤트에 대한 응답으로 코드를 실행하고 자동으로 기본 컴퓨팅 리소스를 관리하는 서버리스 컴퓨팅 서비스
- Kinesis란? **실시간 스트리밍** 데이터 수집, 처리 및 분석 가능한 서비스

### 3-3) S3 & SNS&Kinesis

- S3에서 직접 SNS에 데이터를 쓰는 것은 불가능하다

- S3 이벤트 알림을 사용하여 SNS 이벤트를 보낼 수 있다

- SNS가 Kinesis에 직접 메시지를 보낼 수 없다

  

## 4)

![image](https://user-images.githubusercontent.com/42667951/158130444-24cae2dd-0e3b-4726-9f98-38e4b4c3c3d7.png)

**[풀이]**

- 문제의 keyword : 1년 이상의 과거 데이터를 S3로 이동, 과거 데이터를 상호 참조할 수 있는 기능 유지

### 4-1) Redshift Spectrum

- Redshift란 : 대규모 데이터 세트 저장 및 분석을 위해 설계된 **완전 관리형 페타바이트 규모**의 클라우드 기반 데이터 웨어하우스 제품

- Reshift Spectrum이란 : Redshift 테이블에 데이터를 로드할 필요 없이 **S3에서 데이터를 쿼리하고 검색할 수 있는 기능**

  클러스터와 독립적인 Redshift 서버에 존재하기 때문에, 필터링 및 집계와 같은 컴퓨팅 집약적 작업을 Redshift Spectrum에서 처리하게 됨

### 4-2) Glue ETL

- AWS 클라우드 데이터를 데이터 스토어로 변환하고 이동 가능
- 데이터 웨어하우스 혹은 데이터 레이크를 구축할 때 많은 작업을 단순화 함
- 데이터 웨어하우스 혹은 데이터 레이크의 스토리지에 데이터를 구성, 정리, 검증 및 포맷 하는 역할

### 4-3) Athena

- 표준 SQL을 사용해서 S3에서 직접 데이터를 쉽게 분석할 수 있는 대화형 쿼리 서비스
- 서버리스 형태

  

## 5)

![image](https://user-images.githubusercontent.com/42667951/158130474-ced623a8-7e55-494e-808b-8ca3a68f7a29.png)

**[해설]**

- 문제의 keyword : 데이터 디버그 및 추적, 중앙 집중식 계정, 시각화
- X-Ray는 MSA에서 분산 애플리케이션을 디버그 및 분석할 수 있으며, Service map을 시각화하여 볼 수 있으므로 정답이다.

### 5-1) X-Ray

- 애플리케이션이 처리하는 요청에 대한 데이터를 수집하는 서비스
- 분산 애플리케이션을 분석하고 디버그하는데 도움이 됨

### 5-2)  CloudTrail

- AWS 인프라 전반에서 작업과 관련된 계정 활동을 기록하고 지속적으로 모니터링하고 유지 가능
- AWS 계정 활동의 이벤트 기록을 제공하여 AWS 계정계정 감사가 가능
- 계정 간의 데이터를 디버그하고 추적할 수 는 없다

  

## 6)

![image](https://user-images.githubusercontent.com/42667951/158130497-8db6f40e-a840-4fc0-b59b-8e9a7e216ade.png)

### 6-1)  NLB 라우팅 및 IP 주소 요청 

- 기본 Private IP주소를 사용하여 인스턴스로 라우팅



## 7)

![image](https://user-images.githubusercontent.com/42667951/158130579-01da2d1f-773b-4841-a4a1-f2146b9e9a47.png)

### 7-1) 사용자 데이터란?

EC2 인스턴스 생성 시 지정할 수있는 데이터로, 일반적인 자동화 구성 작업을 수행하고 인스턴스가 시작된 후 스크립트를 실행하는데 사용된다. 

다음은 사용자 데이터의 특징이다.

- 사용자 데이터로 입력된 스크립트는 **루트 사용자 권한**으로 실행된다.

  루트가 아닌 사용자에게 파일 액세스 권한이 필요한 경우 스크립트에서 권한 수정이 필요함

- 사용자 데이터는 인스턴스를 **처음** 시작할 때 부팅 주기 동안만 실행된다.

  추가 설정을 통해 인스턴스를 시작할 때마다 스크립트가 실행되도록 설정이 가능하다.

- 인스턴스 실행 중에 사용자 데이터 **변경은 불가능**하다.



## 8)

![image](https://user-images.githubusercontent.com/42667951/158130608-2cc96c2d-bd3c-4328-b625-6908a82e5eb0.png)

**[풀이]**

- 문제의 keyword : 복잡한 쿼리 처리
- 고도로 연결된 데이터 세트와 함께 작동하는 애플리케이션을 쉽게 구축하고 실행시키는 완전 관리형 그래프 데이터베이스 서비스인 Neptune이 적절하다

### 8-1) AWS Neptune

- 고성능 그래프 데이터베이스 엔진
- 수십억개의 관계를 저장하고 밀리세컨드의 지연시간으로 그래프를 쿼리
- 소셜 네트워킹 애플리케이션 구축에 유리함



## 9)

![image](https://user-images.githubusercontent.com/42667951/158130656-28951dba-05b2-4c9f-be60-7030115e049d.png)

**[풀이]**

- 문제의 keyword : 네트워크 성능이 높을 때 수행, 성능이 핵심 측정 기준

### 9-1)  클러스터 배치

- 단일 가용 영역 내 인스턴스의 논리적 그룹
- 네트워크 대기시간이 짧거나 네트워크 처리량이 높은 애플리케이션에 권장
- 가장 짧은 지연시간과 가장 높은 초당 패킷 네트워크 성능

### 9-2) 스팟 인스턴스

- 미사용 EC2 인스턴스를 매우 저렴하게 할인된 가격으로 사용 가능

### 9-3) Spread 배치 그룹 

- 개별 랙에 각각 배치되는 인스턴스 그룹
- 동일한 리전의 여러 가용영역에 걸쳐 있을 수 있으며, 그룹 가용영역당 최대 7개의 인스턴스를 실행할 수 있음



## 10) - Update 필요

![image](https://user-images.githubusercontent.com/42667951/158130717-a562572a-9d4b-4965-83f0-de533dbb43eb.png)

## 11)- Update 필요
![image](https://user-images.githubusercontent.com/42667951/158130745-7fe65256-d1a0-4491-bc33-ef7b56ec8145.png)

## 12)
![image](https://user-images.githubusercontent.com/42667951/158130780-c8385fa2-1de8-4dbf-955b-fe014444af36.png)

### 12-1) NAT 게이트웨이

- NAT 게이트웨이는 프라이빗 서브넷의 인스턴스가 인터넷으로 아웃바운드 IPv4 트래픽을 시작할 수 있도록 함

- NAT 게이트 웨이의 특징

  1) 포트 포워딩 미지원

  2) 보안 그룹을 직접 연결 불가능 : NAT 게이트웨이 뒤 리소스와 연결하여 제어

  3) bation 서버로 사용 불가능

  4) 고가용성으로, NAT 게이트웨이는 이중화로 구현됨

  5) AWS에서 관리하며, NAT 트래픽처리에 최적화된 소프트웨어 사용

  6) CloudWatch로 트래픽 측정 시 NAT 게이트웨이에 대해 측정

  

### 12-2) NAT 인스턴스

- 2020년 12월 31일에 표준 지원이 종료됨 > NAT 게이트웨이로 마이그레이션하는 것을 추천
- 가용성과 대역폭 측면에서 NAT 게이트웨이가 더 유용함

- NAT 인스턴스의 특징

  1) 포트 포워딩 지원 - 수동으로 사용자 지정

  2) 보안 그룹 연결 가능

  3) bation 서버로 사용할 수 있음

  4) 스크립트로 인스턴스 장애 조치 관리

  5) 고객이 직접 관리

  6) CloudWatch로 트래픽 측정 시 인스턴스에 대해 측정

[NAT 인스턴스 vs NAT 게이트웨이](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-nat-comparison.html)

  

## 13)- Update 필요

![image](https://user-images.githubusercontent.com/42667951/158130813-ef745982-15c6-4476-b3c6-1ec1d1791a49.png)

## 14)- Update 필요
![image](https://user-images.githubusercontent.com/42667951/158130849-9f627a94-fe2c-4186-a206-b67d199c0659.png)