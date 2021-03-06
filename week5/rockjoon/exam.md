
퀴즈 3 - 2

>EC2 인스턴스 세트가 필요한 뱃치 작업을 실행하려고 합니다. 이 일괄 작업은 약 4시간 동안 실행되어야 하며 도중에 중단되어서는 안 됩니다. 가장 저렴한 비용으로 이 뱃치 작업을 실행하려면 다음 중 어떤 EC2 구매 옵션을 선택해야 할까요?
* 온디맨드 인스턴스
* 예약 인스턴스
* 스팟 인스턴스
* 스팟 블록 인스턴스

정답 : D

## 요구사항
* **4시간 동안 중단 없이** 실행해야 하는 배치 작업
* **가장 저렴한 비용**으로 실행 할 수 있는 EC2 구매 옵션

## SPOT 인스턴스

### 정의 및 특징
* 저렴한 가격으로 제공되는 여분의 EC2 용량을 사용하는 인스턴스
* max spot price < current spot price 일 경우 종료됨.

### 사용
* 배치, 데이터 분석, 백그라운드 프로세스와 같은 작업에 유리(장애에 유연한 작업)
* DB와 같이 critical한 작업에 비추천

### 종료
* request type : one-time 일 경우
  * 인스턴스가 launch 되자마자 spot request 가 종료된다.
  * 따라서 launch 이후에는 인스턴스만 종료시키면 된다.
* request type : persistant 일 경우
  * 인스턴스가 종료되더라도 validation에 만족하면 spot request가 인스턴스를 재시작 시킨다.
  * 따라서 종료할 경우 spot request를 먼저 종료 시킨 후에 인스턴스를 종료시켜야 한다.

## Spot Block
* 지정된 시간 (1 ~ 6 시간) 동안 interrupt 없이 스팟 인스턴스를 사용.

## Spot Fleet
* 사용자가 지정한 기준에 따라 시작되는 Spot 인스턴스의 집합 + (선택) On-Demand 인스턴스의 집합
* spot fleet은 사용자의 요구사항을 충족하는 스팟 용량 풀을 선택하고, 목표 용량을 충족하는 스팟 인스턴스를 시작함.

### Spot fleet 할당 전략
* lowestprice : 스팟 인스턴스를 최저 가격의 풀에서 가져옴. 기본값
* diversified : 모든 풀에서 고루 가져옴. 가용성 상승, 하나의 풀의 가격 이슈에 둔감해짐.