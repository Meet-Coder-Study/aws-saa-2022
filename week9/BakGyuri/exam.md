# AWS Study

### 1) CloudFront : 서명된 Url
![image](https://user-images.githubusercontent.com/42667951/163708205-b7302f34-672d-41ed-b224-67cf9ecdcf3c.png)

#### 해설
CloudFront의 서명된 Url은 CloudFront에서 새 배포를 생성하여 Url을 배포할 때 배포에 대해서 대상 제한 혹은 다운 일자를 지정할 수 있는 설정이다.
해당 설정을 활용하면 유효한 키가 있어야 해당 url 에 접속할 수 있거나 혹은 특정 IP에 대해서만 접속을 허용할 수 있으며, 일정 시간이 지나면 다운로드가 불가능하도록 설정할 수 있다. 문제에서 CloudFront 배포를 안전하게 하는 방안을 물어보고 있으므로 정답은 CloudFront의 서명된 Url이다.

#### 서명된 URL
1. CDN 에 접속할 수 있는 서명자 (Signer) 를 구체화한다.

2. 어플리케이션을 개발한 후에 content에 접근하기 위해서 signed URL 을 발급하여 해당 어플리케이션만 접근가능하도록 처리한다.

3. User가 파일을 요청할 때 어플리케이션이 유저를 검증한다.

4. 검증이 끝나면 유저에게 어플리케이션이 signed url을 제공한다. 

5. 해당 유저에게 제한된 데이터가 허용이 된다.

6. CDN는 public key를 이용하여 서명을 검증하고 서명이 올바르지 않을 경우에는 요청을 거절한다.





#### Cloud Front란
Amazon CloudFront는 .html, .css, .js 및 이미지 파일과 같은 정적 및 동적 웹 콘텐츠를 사용자에게 더 빨리 배포하도록 지원하는 웹 서비스이다. CloudFront는 엣지 로케이션이라고 하는 데이터 센터의 전 세계 네트워크를 통해 콘텐츠를 제공한다. CloudFront를 통해 서비스하는 콘텐츠를 사용자가 요청하면 지연 시간이 가장 낮은 엣지 로케이션으로 요청이 라우팅되므로 높은 성능으로 컨텐츠가 제공된다.

#### Cloud Front  동작 방법
![image](https://user-images.githubusercontent.com/42667951/163709087-b345bb0d-c6b3-45c2-b1e0-cee3a66c4f2d.png)
1) 원본 데이터가 저장되는 오리진 서버를 지정한다. (S3 버킷, EC2, 고유 HTTP 서버 등)
2) 오리진 서버에 파일을 업로드한다.
3) 사용자가 웹 사이트나 어플리케이션을 통해서 파일을 요청한다.
4) Cloud Front에서 어떠한 오리진 서버에서 데이터를 가져올지 정보를 알려주는 새 배포를 생성한다. : 새 배포에 도메인 이름 지정
5) 생성한 배포의 구성을 지연 시간이 가장 낮은 엣지로케이션으로 요청을 라우팅한다.
6) CloudFront는 엣지로케이션 즉, 캐시서버에 요청된 객체가 있는지 확인한다. 객체가 캐시에 있으면 이를 사용자가 반환한다.
7) 객체가 캐시에 없을 경우 배포 요청을 오리진 서버에 전달한다.
8) 오리진 서버가 객체를 엣지 로케이션에게 보내고, CloudFront는 엣지 로케이션에서 객체를 사용자에게 전달한다. 이후 캐시에 해당 객체를 추가한다.

[서명된 Url 설정](https://blog.leedoing.com/87)

[CloudFront  캐시 서버](https://docs.aws.amazon.com/ko_kr/AmazonCloudFront/latest/DeveloperGuide/HowCloudFrontWorks.html)

   

### 2) CloudFront : 서명 쿠키

![image](https://user-images.githubusercontent.com/42667951/163715868-9f650b28-7c4e-42f8-82b9-c0e56e5901b4.png)

#### 해설
수 백개의 비공개 파일에 대한 액세스를 제공한다는 말이 핵심이다. CloudFront의 서명 쿠키는 현재의 URL을 변경하지 않으려는 경우나 여러 제한된 파일에 대한 액세스 권한을 제공하는 경우에 콘텐츠 액세스를 제어하기 위해서 사용된다.

#### 서명 쿠키
1. 접근을 허용할 신뢰있는 서명자를 구체화한다.

2. 앱이 개발이 끝나면 three set-cookie headers (CloudFront-Key-pari-id, CloudFront-Signature, CloudFront-Policy) 를 user에게 보낸다. 해당 유저가 접근을 요청하기 전에 해당 header들이 반드시 제공되어야 한다.

3. 유저가 private content에 접속을 요청한다.

4. 앱은 유저에게 set-cookie header를 return한다.

5. 해더가 더해지고 나면 유저는 해당 파일에 접근이 가능해지며 서버에서 signature와 expiry date를 확인하고 데이터 접근을 허용한다.



#### 서명된 url vs 서명된 쿠키
서명된 url이 서명된 쿠키보다 우선됨.
같은 파일에 대한 액세스를 제어할 때 서명된 URL과 서명된 쿠키를 모두 사용하고 최종 사용자는 서명된 URL로 파일을 요청하는 경우, CloudFront는 서명된 URL만을 기준으로 최종 사용자에게 파일을 반환할지 여부를 판단한다.

[서명된 url 사용]
애플리케이션 설치 파일을 다운로드하는 등 개별 파일에 대한 액세스를 제한하고 싶은 경우
사용자가 쿠키를 지원하지 않는 클라이언트(예: 사용자 지정 HTTP 클라이언트)를 사용하는 경우


[서명된 쿠키 사용]
HLS 형식의 비디오 파일 전체 또는 웹 사이트의 구독자 영역에 있는 파일 전체 등 제한된 파일 여러 개에 대한 액세스 권한을 제공하려는 경우
현재의 URL을 변경하고 싶지 않은 경우


## 3) SQS : 가시성 시간 
![image](https://user-images.githubusercontent.com/42667951/163716461-505ab487-a81c-4c94-b992-bd53dc7cca47.png)

#### 해설
SQS는 수신한 메시지를 규칙대로 전송하는 역할을 하는 분산 시스템일 뿐, 전송한 메시지를 자동으로 삭제하지 않는다. 사용자(서버)가 메시지를 수신 및 처리시에 큐로부터 메시지를 제거하는 요청을 보내야 큐에서 메시지가 삭제된다. 
메시지 가시성 시간이란 메시지 소비자가 대기열에서 수신한 메시지가 다른 메시지 소비자에게 보이지 않게 되는 시간을 의미한다. 메시지 가시성 시간이 너무 짧게 되면 한 메시지 소비자가 수신하 이후 짧은 시간이 지난 후에 다른 메시지 소비자에게도 전송이 되기 때문에 동일한 메시지가 두번 이상 전송되는 문제점이 생길 수 있다. 이를 방지하기 위해서는 메시지 가시성 시간을 증가시키는 방안이 있다.
(기본값 : 30초, 최소값 : 0초, 최대값 : 12시간)

* 참고 : 표준 문자열에서 메시지 가시성 시간을 늘린다고 메시지가 두 번 이상 전송 되는 것을 완전히 방지할 수는 없다.

####  SQS란
![image](https://user-images.githubusercontent.com/42667951/163717973-8f304af5-a976-4cd8-a8ce-6dfb52c5503a.png)


[SQS 전반 정리 참조](https://devocean.sk.com/blog/techBoardDetail.do?ID=163290)

-------------------------

kinesis

aws transfer family

cloudfront distribution

cloudfront signed url

mqtt
