# 10주차 과제

## 1. AWS 컨테이너

### 1) AWS Fargate

![image](https://user-images.githubusercontent.com/42667951/165192803-684cc172-1994-42d6-8561-de8acd868691.png)

**AWS Fargate란**

서버를 관리하지 않고도 애플리케이션 구축에 초점을 맞출 수 있도록 지원하는 종량제 서버리스 컴퓨팅 엔진이다. 즉, EC2인스턴스 없이 도커 컨테이너를 독립적으로 실행할 수 있어 컴퓨팅 자원에 대한 관리 없이 다양한 환경에서 애플리케이션을 실행할 수 있다. ECS(Elastic Container Service) 및 EKS(Elastic Kubernetes Service) 모두와 호환된다. 

문제에서는 인프라를 프로비저닝하거나 관리하지 않고 컨테이너를 실행시키는 기능을 물어보고 있으므로 정답은 Fargate이다.  

<br>

### 2) EC2 launch type VS Fargate launch type

![image](https://user-images.githubusercontent.com/42667951/165192886-4fc0bef3-8f48-4d24-b22d-63443fb25352.png)

**ECS란**

AWS에서 제공하는 컨테이너 오케스트레이션 서비스로 여러 어플리케이션 컨테이너를 쉽고 빠르게 실행하고, 컨테이너를 적절하게 분배 및 확장 & 축소 할 수 있도록 도와주는 서비스이다.

**ECS launch type 이란**

ECS를 실행할 때 두가지 launch type을 지정할 수 있다.

1) EC2 launch type

   Amazon ECS 클러스터에 EC2 인스턴스를 등록하고 직접관리하는 형식이다. 

   ![img](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/images/overview-standard.png)

2. Fargate launch type

   백엔드 인프라를 프로비저닝하고 관리할 필요 없이 컨테이너화된 애플리케이션을 실행하는데 사용할  수 있는 서버리스 방식이다.

   ![img](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/images/overview-fargate.png)

<br>

### 3) EFS 볼륨 공유 (EC2, ECS)

![image](https://user-images.githubusercontent.com/42667951/165193099-c93aa810-c7f0-4dd8-b415-e6f245daaf3d.png)

 EFS를 ECS 클러스터에서 사용 시 EC2 태스크에서 파일을 추가하고 제거할 때 마다 스토리지 용량이 탄력적으로 자동 확장 및 축소된다.

또한 ECS에서 EFS 파일시스템을 활용하여 파일 스토리지를 공유함으로써 동일한 영구 스토리지에 액세스할 수 있다. 해당 문제에서는 Docker 컨테이너가 동일한 웹 사이트 콘텐츠에 액세스하기를 원한다고 표현하였으므로 EFS 볼륨 마운트가 가장 적절하다.

<br>

### 단어 확인

ECS

Fargate

ECR

<br>

## 2. 서버리스 개요

### 1) DynamoDB (RCU, WCU)

![image](https://user-images.githubusercontent.com/42667951/165213819-ff2785e8-ba01-48a6-b825-82dc5cbdb684.png)

**DynamoDB란**

완전 관리형 NoSQL 데이터베이스 서비스로서 autoscaling 기능을 통해서 원활한 확장성과 빠른 성능을 제공한다. DynamoDB는 테이블의 데이터와 트래픽을 서버들로 자동 분산하여 처리량 및 스토리지 요구사항에 맞게 높은 성능으로 트래픽을 처리한다.

**DynamoDB Capacity mode(용량모드)란**

DynamoDB 용량 모드란 읽기 및 스기 처리량에 대한 청구 방법과 용량 관리 방법을 제어한다. 용량모드는 크게 온디맨드 모드와 프로비저닝된 모드 두 개가 존재한다.

- 온디맨드 모드

  용량 계획 없이 초당 수천 개의 요청을 처리할 수 있는 옵션이다. 읽기 및 쓰기 요청에 대해 요청당 지불 가격을 제공하므로 사용하는 만큼에 대해서만 비용을 지불하면 된다.

- 프로비저닝된 모드

  애플리케이션에 필요한 초당 읽기 및 쓰기 횟수를 지정한다. Auto Scailing을 통해서 트래픽 변경에 따라 테이블의 프로비저닝된 용량을 자동으로 조절할 수 있다. 애플리케이션 트래픽이 예측가능한 경우에 프로비저닝된 모드를 사용하는 것이 유리하다.

- RCU(Read Capacity Units) : 읽기의 처리량

- WCU(Write Capackty Units) : 쓰기의 처리량

해당 문제에서는 한달 후에 더 많은 **읽기** 트래픽을 처리한다고 하고 있으므로 읽기 용량모드인 RCU를 늘리고 WCU는 동일하게 유지하는 옵션이 적절하다.

<br>

### 2) DynamoDB (DAX-DynamoDB Accelerator)

![image](https://user-images.githubusercontent.com/42667951/165213974-91651a36-84a2-4d1f-8d56-2ec7b0ab9294.png)

**DAX란**

DynamoDB Accelerator(DAX)는 최대 10배의 성능 향상을 제공하는 DynamoDB용 완전 관리형 고가용성 인메모리 캐시이다. 

**ProvisionedThroughputExceedException 오류**

테이블 또는 하나 이상의 글로벌 보조 인덱스에 허용되는 최대 프로비저닝된 처리량을 초과하여 생기는 오류이다. 즉, 요청량이 너무 높아 재시도 대기열이 너무 많아져 처리하지 못하는 경우에 발생한다.

이럴 경우에는 최대 10배의 성능 향상을 제공하는 완전 관리형 고가용성 인메모리 캐시인 DAX 클러스터를 생성함으로써 가장 자주 사용되는 데이터를 캐싱하여 DynamoDB 테이블의 핫 키에 대한 대량 읽기를 오프로드하여 "ProvisionedThroughputExceededException" 예외를 방지해야 한다.

<br>

### 단어 확인

RCU

WCU

DAX

<br>

## 3. 서버리스 솔루션 아키텍처 토론

### 1) SQS, EC2

![image](https://user-images.githubusercontent.com/42667951/165214543-190206eb-16bf-408e-b399-184d2136077e.png)

**[문제에서 필요한 기능]**

인코딩 -> S3 버킷에 저장

실패 시 재시도 할 수 있는 기능

각 동영상을 처리하는데 25분 이상이 소요될 수 있음

서비스는 비동기식이며 아직 인코딩 되지 않은 비디오에서 다음날 다시 시작할 수 있는 기능 필요

**[SQS 특징 - 메시지 보관 주기]**

SQS 대기열 에 대해서 메시지 보존 기관을 설정할 수 있다. 범위는 1분에서 14일 사이이며 기본 값은 4일이다. 해당 특성을 활용하여 메시지를 보관한 후 실패 시 재시도를 할 수 있다.

[AWS lambda 함수 호출 시간]

AWS Lambda 함수의 최대 호출 시간 초과는 15분 이다. 문제에서는 동영상 처리에 25분 이상이 처리될 수 있다 하였으므로 lambda는 적절치 않다.

###### 

