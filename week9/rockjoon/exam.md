9주차 키워드

```
CloudFront OAI  
Signed URL/cookie  
Lustre
AWS snowball
```

# 1. 

> 여러분은 S3 버킷에서 호스팅되는 정적 웹 사이트가 있습니다. 요청을 더 잘 처리하고 성능을 개선하기 위해 S3 버킷을 가리키는 CloudFront Distribution를 생성했습니다. 잠시 후 사용자가 여전히 S3 버킷에서 직접 웹사이트에 액세스할 수 있음을 알게 되었습니다. 사용자가 CloudFront를 통해서만 웹 사이트에 액세스하도록 하려고 합니다. 어떻게 달성하시겠습니까?

a. 클라이언트에게 이메일을 보내고 S3 Endpoint를 사용하지 말라고 지시합니다.

b. CloudFront Distribution를 구성하고 오리진 액세스 ID를 생성한 다음 CloudFront Distribution OAI 사용자의 요청만 수락하도록 S3 버킷 정책을 업데이트합니다

c. S3 액세스 포인트를 사용하여 클라이언트를 CloudFront로 리디렉션

정답 : b

## 요구 사항
* S3 버킷을 가리키는 CloudFront Distribution을 생성했으나 사용자가 S3에서 직접 액세스
* 사용자가 CloudFront를 통해서만 액세스 해야함

## 문제 풀이

### CloudFront Distribution OAI
* CloudFront의 사용자로 이를 Distribution과 연동 시킬 수 있다.
* 이후 S3버킷의 권한을 OAI에서만 접근하도록 설정하면 사용자가 S3에 직접 접근할 수 없게 된다.

### 2.

> 애플리케이션 로드 밸런서 (ALB) 내 일련의 EC2 인스턴스에서 호스팅되는 웹사이트가 있습니다. CloudFront Distribution을 생성하고 ALB를 가리키도록 오리진을 설정했습니다. CloudFront Distribution에서 제공하는 수백 개의 비공개 파일에 대한 액세스를 제공하려면 무엇을 사용해야 할까요?

a. CloundFront 서명된 URL

b. CloudFront 오리진 액세스 ID

c. CloudFront 서명 쿠키

d. CloudFront HTTPS 암호화

정답 : c

## 요구 사항
* CloudFront Distribution 생성 후 ALB에 연결
* CloudFront Distribution에서 제공하는 수백 개의 비공개 파일에 대한 액세스를 제공해야 함

## 문제 풀이
### signed url vs signed cookie
* 둘 다 CloudFront를 통해 프라이빗 콘텐트를 제어하기 위한 목적
* signed url는 애플리케이션 설치 파일을 다운로드하는 등 개별 파일에 대한 액세스를 제한하고 싶은 경우에 적합하다.
* signed cookie는 HLS 형식의 비디오 파일 전체 또는 웹 사이트의 구독자 영역에 있는 파일 전체 등 제한된 파일 여러 개에 대한 액세스 권한을 제공하려는 경우에 적합하다.

# 3.

> 여러분은 고성능 컴퓨팅(HPC) 및 유전체학 계산 연구를 수행하기 위해 IOPS를 최대화할 수 있는 분산 POSIX 호환 파일 시스템을 원합니다. 이 파일 시스템은 수백만 IOPS로 쉽게 스케일링 되어야 합니다. 무엇을 사용하시겠습니까?

a. 최대로 IO를 활성화한 EFS

b. Lustre용 Amazon FSx

c. EC2 인스턴스에 탑재된 Amazon S3

d. EC2 인스턴스 스토어

## 요구 사항
* HPC 수행을 위해 IOPS를 최대화할 수 있는 POSIX호환 파일 시스템
* 수백만 IOPS로 스케일링 될 수 있음

## 문제 풀이
### Amazon FSx for Lustre 
* Lustre란 병렬 분산 파일 시스템으로, 주로 HPC의 대용량 파일 시스으로 사용된다.
* Amazon FSx for Lustre는 수백 GB/초의 처리량과 수백만 IOPS를 제공