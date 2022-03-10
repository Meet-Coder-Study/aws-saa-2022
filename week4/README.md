# 4주차 과제 
## 과제 1
- [Udemy AWS SAA 강의](https://www.udemy.com/course/best-aws-certified-solutions-architect-associate/)의 `Section 30 > Practice Test 1 연습시험`을 풀이합니다.
- Question 1이 다음과 같다면 맞게 선택하셨습니다!
```
전자 상거래 회사는 온-프레미스 인프라에서 AWS 클라우드로 2계층 애플리케이션을 마이그레이션할 계획입니다.
회사의 엔지니어링 팀은 AWS 클라우드를 처음 사용하기 때문에 Amazon VPC 콘솔 마법사를 사용하여 공용 웹 서버와 개인 데이터베이스 서버가 있는 2계층 애플리케이션에 대한 네트워킹 구성을 설정할 계획입니다.
Amazon VPC 콘솔 마법사에서 지원하지 않는 구성을 찾을 수 있습니까?
```
- 본인이 생각하기에 **어렵거나 중요한 문제를 10개**를 선정하여 풀이/해설을 제출합니다.
- 물론 10개 이상을 제출하셔도 됩니다!
- 제출기한: 3/13(일) 23:59 (정기밋업: 3/15(화) 20:00)

### 제출방법
- 본인의 이름으로 하위에 폴더를 생성하여 파일을 작성하고 PR을 올립니다.
- ex) week4/HonGilDong/exam.md

---

## 과제 2 - EBS Hands On

---

1. EC2 를 만들고 ( 혹은 기존 인스턴스에 ) 새로운 볼륨을 추가합니다. 이후 EBS 목록을 캡쳐하여 제출합니다.
2. 생성한 EC2 를 삭제하고 EBS 목록의 변화를 확인한 뒤, 캡쳐하여 제출합니다.

**( 선택사항 - 시험과 무관하므로 정말 흥미 있으신 분만. 스크린샷** 제출 X **)**
[https://devopscube.com/mount-ebs-volume-ec2-instance/](https://devopscube.com/mount-ebs-volume-ec2-instance/) 를 참고하여, 생성한 볼륨을 실제로 마운트하고 확인해봅시다. 참고 차원에서 의미있어 보여 선택사항으로 남겨둡니다.

## (선택) 과제 3. EBS SnapShot Hands On

---

1. EBS 스냅샷을 생성하고, 스냅샷으로부터 새로운 EBS 볼륨 생성을 시도합니다. 이 때, AZ 를 다르게 설정해보고 그 결과를 캡쳐, 제출합니다.

## 과제 4. AMI Hands On

---

1. EC2 를 생성하고, User data 값을 `예시 1)` 같이 입력한 뒤, AMI 를 생성합니다.
2. 새로운 EC2 를 `예시 2` User data 를 입력하여 생성하되, 직접적인 설치 없이 httpd 를 사용할 수 있도록 생성합니다.
3. 두번째 아파치 http 테스트 페이지를 캡처하여 제출합니다.

예제 1)

```jsx
#!/bin/bash
yum update -y
yum install -y httpd
systemctl start httpd
systemctl enable httpd
```

예제 2)

```jsx
#!/bin/bash
echo "<h1>Hello World from $(hostname -f)</h1>" > /var/www/html/index.html
```

## 과제 5. EBS 암호화 Hands On

---

1. EBS 스냅샷을 통해 암호화된 EBS 볼륨을 생성하고, 볼륨 암호화 여부 속성을 캡쳐하여 제출합니다.

(주의) 프리티어라도, 스냅샷은 돈이 나갑니다. 큰 비용은 아니지만 주의해주세요.

## 과제 6. EFS Hands On

---

1. EFS 를 생성하고, 서로 다른 AZ 의 두 EC2 에 마운트합니다.
2. 하나의 EC2 인스턴스에서 해당 EFS 의 디렉토리에 파일을 생성하고, 문자열을 씁니다.
3. 다른 EC2 에서 해당 파일을 읽습니다. 두 인스턴스의 콘솔을 캡처하여 제출합니다.

**과제를 수행한 뒤, 불필요한 리소스들을 잘 정리하는 것을 잊지 맙시다.**

## 과제 7. EC2 데이터 관리 퀴즈 9문제

---

1. 강의의 마지막 퀴즈 섹션을 풀고 해설과 답안을 제출합니다.

## 과제 8. (선택) 문제풀이 5 문항

---

아래 5문제를 풀어봅니다. (참조링크) [https://acloudxpert.com/practice-test-2-aws-certified-solutions-architect-associate-saa-c02-dumps-mock-test/](https://acloudxpert.com/practice-test-2-aws-certified-solutions-architect-associate-saa-c02-dumps-mock-test/)

A customer wants to create EBS Volumes in AWS. The data on the volume is required to be encrypted at rest. How could this be achieved?

A. Create an SSL Certificate and attach it to the EBS Volume.

B. Use KMS to generate encryption keys which can be used to encrypt the volume.

C. Use CloudFront in front of the EBS Volume to encrypt all requests.

D. Use EBS Snapshots to encrypt the requests.

---

A company plans to have their application hosted in AWS. This application has users uploading files and then using a public URL for downloading them at a later stage. Which of the following designs would help fulfill this requirement?

A. Have EBS Volumes hosted on EC2 Instances to store the files.

B. Use Amazon S3 to host the files.

C. Use Amazon Glacier to host the files since this would be the cheapest storageoption.

D. Use EBS Snapshots attached to EC2 Instances to store the files.

---

A company has a sales team and each member of this team uploads their sales figures daily. A Solutions Architect needs a durable storage solution for these documents and also a way to preserve documents from accidental deletions. What among the following choices would deliver protection against unintended user actions?

A. Store data in an EBS Volume and create snapshots once a week.

B. Store data in an S3 bucket and enable versioning.

C. Store data in two S3 buckets in different AWS regions.

D. Store data on EC2 Instance storage.

---

You plan on hosting an application on EC2 Instances which will be used toprocess logs. The application is  not very critical and can resume operation even after an interruption. Which of the following steps can help provide a cost-effectivesolution?

A. Use Reserved Instances for the underlying EC2 Instances.

B. Use Provisioned IOPS for the underlying EBS Volumes.

C. Use Spot Instances for the underlying EC2 Instances.

D. Use S3 as the underlying data layer.

---

A Solution Architect is designing an application that uses Amazon EBS volumes. The volumes must be backed up to a different region.How should the Architect meet this requirement?

A. Create EBS snapshots and then copy them to the desired region.

B. Move the data to an Amazon S3 bucket and enable cross-region replication.

C. Use a script to copy data from the current Amazon EBS volume to the destination Amazon EBS volume.

D. Create EBS snapshots directly from one region to another.