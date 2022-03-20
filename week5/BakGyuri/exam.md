# EC2 퀴즈 

## 1) 전용 호스트

### 전용 호스트란?

Ec2 전용 호스트는 **고객 전용**의 EC2 인스턴스 용량을 갖춘 물리적 서버이다. 

전용 호스트는 **물리적 서버를 예약**하여 사용하며 **기존 보유 라이선스 사용(BYOL - Bring Your Own License)**이 가능하여 고객이 현재 보유하고 있는 라이선스를 Cloud 환경에 적용할 수 있다. 

전용 호스트에서 실행되는 인스턴스는 VPC 에서만 시작할 수 있으며, AWS RDS 인스턴스와 AWS 프리 티어는 전용 호스트에서 제공되지 않는다.

**cf ) 전용 호스트 VS 전용 인스턴스**

전용 호스트와 전용 인스턴스 모두 사용자 전용 물리적 서버이며 성능, 보안, 물리적 차이는 없으나 아래와 같은 차이점이 존재한다.

**[전용 호스트]**

- 사용자 전용의 EC2 인스턴스 용량을 갖춘 `물리적 서버`
- `물리적 서버`인 호스트 단위로 예약하고 결제하기 때문에 전용 인스턴스보다 비쌈
- 동일한 `물리적 서버`에 인스턴스 배포 허용
- BYOL(Bring Your Own License) 지원 O
- 소켓, 코어 및 호스트 ID 표시 O
- 물리 서버 내 인스턴스 배치 방법에 대한 가시성 제공 O
- 자동 인스턴스 복구 O

**[전용 인스턴스]**

- 단일 고객 전용 하드웨어의 `VPC`에서 실행되는 EC2 인스턴스 -> 인스턴스가 실행되는 동안 하드웨어는 공유되지 않으나, 인스턴스가 정지/기동되면 다른 물리적 서버로 이동할 수 있다.
- 인스턴스 단위 결제
- 동일한 AWS 계정의 다른 인스턴스와 하드웨어 공유가 가능
- BYOL(Bring Your Own License) 지원 X
- 소켓, 코어 및 호스트 ID 표시 X
- 물리 서버 내 인스턴스 배치 방법에 대한 가시성 제공 X
- 자동 인스턴스 복구 O

### Quiz 2  -  10

![KakaoTalk_20220320_104453650_09](https://user-images.githubusercontent.com/42667951/159151823-c2d5bdce-231f-4b25-a6aa-81a6e4652c28.jpg)

 **[문제의 keyword]**

- 전용 서버에서만 실행
- 자체 서버 바인딩 소프트웨어 라이선스 사용(BYOL)

위 keyword 모두 전용 호스트에 해당하는 keyword 이다.



### Quiz 2 - 11

![KakaoTalk_20220320_104453650_10](https://user-images.githubusercontent.com/42667951/159151826-9aedc1a3-6d16-4312-bfd3-3d934109d75a.jpg)

**[문제의 keyword]**

- 물리적 코어 및 기본 네트워크 소켓 가시성

전용 호스트는 소켓, 코어 및 호스트 ID를 표시하여 보여준다. (전용 인스턴스는 X)

  

## 2) 플릿(Fleet)

### 플릿이란?

EC2 Fleet 이란 한번에 수천 개의 온디맨드 및 스팟 인스턴스를 동시에 관리할 수 있는 기능이다.

단일 API 호출로 다양한 인스턴스 유형 및 가용영역에 걸쳐 온디맨드, 예약 인스턴스(RI) 및 스팟 인스턴스 모델에 대해 프로비저닝을 하여 규모, 성능, 비용 최적화가 가능하다.

고객이 용량 및 인스턴스에 대한 요구 사항만 설정하면 AWS에서 필요에 따라 온디맨드와 스팟 인스턴스를 최적화된 비용으로 프로비저닝하여 시작, 관리, 모니터링 및 확대를 시행한다.

[💛EC2 플릿 설명](https://aws.amazon.com/ko/blogs/korea/ec2-fleet-manage-thousands-of-on-demand-and-spot-instances-with-one-request/)

### Quiz 3 - 3

![KakaoTalk_20220320_104453650_13](https://user-images.githubusercontent.com/42667951/159156474-3965f818-cbec-45f1-ad72-f3fa1b354afa.jpg)

스팟 플릿은 스팟 인스턴스와 선택적 온디맨드 인스턴스의 집합이다.  

  

## 3) ENI(Elastic Network Interface)

ENI란 VPC에서 가상 네트워크 카드를 나타내는 논리적 네트워킹 구성 요소이다. -> 인스턴스 생성 시 설정하는 IP도 네트워크 인터페이스에 의해 관리되는 것

네트워크 인터페이스를 생성 및 구성하면 동일한 가용영역의 인스턴스에만 연결할 수 있다. 

각 인스턴스는 기본 네트워크 인터페이스를 갖게 되는데, 이 기본 네트워크 인터페이스는 인스턴스에서 분리할 수 없으며, 추가 인스턴스는 생성 및 연결이 가능하다.

네트워크 인터페이스에 보안 그룹을 직접 설정하여 네트워크 에 대한 트래픽 통제 및 관리가 가능하다.

[💛AWS ENI 개요 - AWSKRUG 구디모임](https://dev.classmethod.jp/articles/amazon-vpc-eni-deep-dive/)

### Quiz 3 - 6


![KakaoTalk_20220320_104453650_16](https://user-images.githubusercontent.com/42667951/159156476-211caef0-bdab-4afb-9afc-eda4d7bcc8ef.jpg)

 ENI는 특정 하나의 AZ에만 바인딩 되기 때문에 다른 AZ의 EC2 인스턴스에 연결할 수 없다.

  

## 4) EC2 Hibernate

EC2 인스턴스에 최대 절전 모드(Hibernate, 혹은 수면 모드)를 지정해두었다가 필요 시 다시 가동할 수 있는 기능이다.

Hibernate 기능은 향 후 다시 인스턴스를 기동할 때 동일한 환경에서 기동할 수 있도록 인스턴스의 인메모리 상태와 프라이빗 및 탄력적 IP 주소를 저장한다.

인스턴스를 최대 절전 모드 상태로 설정하면 인메모리 상태가 루트 EBS 볼륨에 저장된 다음 실질적으로 인스턴스가 종료된다.

인스턴스 시작시 사용한 AMI와 루트 EBS 볼륨은 암호화되기 때문에 민감한 데이터가 메모리에서 EBS로 복사 시 보호 기능을 제공한다.

인스턴스 최대 절전 상태에 있는 동안은 인스턴스 정지 상태와 마찬가지로 EBS 볼륨과 EIP에 대한 요금만 지불한다.

### Quiz 3 - 7

![KakaoTalk_20220320_104453650_17](https://user-images.githubusercontent.com/42667951/159156478-39c74e2d-3993-4290-b573-e02ce0818dd9.jpg)

  인스턴스 스토어 볼륨은 최고의 디스크 I/O를 제공하지만 인스턴스 중지 시 데이터를 보존할 수 없다. 따라서 인스턴스를 최대 절전 상태로 만드는 Hibernate는 루트 볼륨을 EBS로 사용한다.

  

## 5)  EBS

부트 볼륨 지원이 가능한 EBS 볼륨 유형은 다음과 같다.

### 1) SSD (Solid-State Drive) - 부트 볼륨 지원

SSD는 두 개의 범주로 나뉜다.

#### 1-1) 범용 SSD

가격과 성능 간의 균형을 제공한다. 대부분의 워크로드에 이 볼륨을 사용하게 된다.

- gp3, gp2가 이에 해당한다.
- AWS EBS 다중 연결이 지원되지 않는다.

#### 1-2) Provisioned IOPS SSD

지연 시간이 짧거나 처리량이 많은 미션 크리티컬 워크로드에 적합한 고성능을 제공한다.

- io1, io2가 이에 해당한다.
- AWS EBS 다중 연결이 지원된다.

<br>

### 2)  이전 세대 볼륨 유형(Magnetic - standard)

데이터에 자주 액세스하지 않는 워크로드에 사용하며 부트 볼륨을 지원한다.

성능이 낮기 때문에 우수한 성능 또는 성능 일관성이 필요한 경우 범용 SSD(gp2 , gp3) 를 사용하는 것이 좋다.

[💛EBS 볼륨 유형 설명](https://docs.aws.amazon.com/ko_kr/AWSEC2/latest/UserGuide/ebs-volume-types.html)



### Quiz 4 - 3

![KakaoTalk_20220320_104453650_20](https://user-images.githubusercontent.com/42667951/159157726-5632ba81-e486-4b80-93c8-a020802cd19e.jpg)

부팅 볼륨으로 사용할 수 있는 EBS 유형은 범용 SSD인 gp2,gp3, Provisioned IOPS SSD 인 io1,io2 그리고 마그네틱(standard) 이다.

st1과 sc1은 HDD로 부팅 볼륨으로 사용되지 않는다.

**cf) st1 & sc1**

- st1 : 처리량 최적화 HDD : 자주 액세스 하는 처리량 집약적 워크로드에 적합한 저비용 HDD
- sc1 : 콜드 HDD : 자주 액세스하지 않는 워크로드에 적합한 가장 저렴한 HDD

  

### Quiz 4 - 6

![KakaoTalk_20220320_104453650_23](https://user-images.githubusercontent.com/42667951/159157723-db1e5b8d-f162-415f-925b-1111f148ae82.jpg)

EBS 볼륨의 암호화 상태는 볼륨을 생성할 때 결정되기 때문에 기존 볼륨의 암호화 상태는 변경할 수 없다.

따라서 EBS 볼륨을 선택하고 KMS로 암호화 옵션을 변경한다는 2번 선택지는 정답이 아니다. (KMS로 EBS 생성 시 볼륨 암호화는 가능함)

[EBS & KMS 암호화](https://docs.aws.amazon.com/ko_kr/kms/latest/developerguide/services-ebs.html)

