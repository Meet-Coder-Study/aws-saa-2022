# 1. 퀴즈 8 클래식 솔루션 아키텍쳐 토론 퀴즈

> 여러분의 웹 사이트 TriangleSunglasses.com은 오토 스케일링 그룹 (ASG)에서 관리하고 애플리케이션 로드 밸런서 (ALB)가 전면에 있는 EC2 인스턴스 집합에서 호스팅됩니다. ASG는 웹사이트로 이동하는 트래픽을 기반으로 주문형으로 스케일링하도록 구성되었습니다. 비용을 줄이기 위해 ALB를 통과하는 트래픽을 기반으로 스케일링하도록 ASG를 구성했습니다. 솔루션을 고가용성으로 만들기 위해 ASG를 업데이트하고 최소 용량을 2로 설정했습니다. 요구 사항을 준수하면서 어떻게 비용을 더 줄일 수 있을까요?

a. ALB를 제거하고 대신 탄력적 IP를 사용  
b. 2개의 EC2 인스턴스 예약  
c. 최소 용량을 1로 줄입니다.  
d. 최소 용량을 2로 줄입니다.  

답 : b

## 요구사항
* 솔루션을 고가용성으로 만들기 위해 ASG 최소 용량을 2로 설정
* 비용을 더 줄일 수 있는 방법

## 문제 풀이

### EC2 예약 인스턴스

* 일반 EC2 인스턴스는 한 달 기준 사용량에 따라 요금이 책정
* 예약 인스턴스는 최소 1년 이상 사용해야 하지만 시간당 요금이 할인 됨.

> 최소 용량이 2이므로 2개의 인스턴스는 무조건 돌아간다는 뜻이므로 
> 해당 되는 2개의 인스턴스를 예약하여 비용을 절감 할 수 있다.

# 2. 퀴즈 9 amazon S3 퀴즈

> 여러분은 IAM 사용자가 S3 버킷의 파일을 읽고 쓸 수 있도록 S3 버킷 정책을 업데이트했지만 사용자 중 한 명이 PutObject API 호출을 수행할 수 없다고 불평합니다. 이것의 가능한 원인은 무엇일까요?

a. S3 버킷 정책이 잘못되었습니다.  
b. 사용자에게 권한이 없습니다.  
c. iam 사용은 연결된 iam 정책에 명시적 DENY가 있어야 합니다.  
d. 이 한도를 해제하려면 aws support에 문해야 합니다.  

답 : c

## 요구 사항
* IAM 사용자가 S3버킷을 읽고 쓸수 있도록 버킷 정책 변경
* 그럼에도 사용자에게 권한이 없다면?

## 문제 풀이
an IAM principal can access an S3 object if  
the user IAM permissions allow it **OR** the resource policy **ALLOWS** it  
**AND** there's no explicit **DENY**

IAM 권한은 S3에 다음과 같은 경우 접근할 수 있다.
* IAM 권한이 허용된 경우 또는 resource policy(버켓 정책 등)에서 허용된 경우
* 반드시 명시적 DENY가 없어야 함.
