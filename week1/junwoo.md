# 섹션8. 고가용성 및 스케일링성: ELB 및 ASG

## 목차

* Elastic Load Balancing (ELB)에 대해서
* Classic Load Balaner (CLB)
* Application Load Balancer (ALB)
* Network Load Balancer (NLB)
* Gateway Load Balancer (GWLB) - 강의에 자세한 내용 설명 x
* SSL
* Auto Scailing Group (ASG)

------

### **Elastic Load Balancing (ELB)에 대해서**

#### 특징

ELB는 둘 이상의 가용 영역에서 EC2 인스턴스, 컨테이너 , IP 주소 등 여러 대상에 걸쳐 수신되는 트래픽을 <u>자동으로 **분산**</u> 
등록된 대상의 상태를 헬스체크하면서 <u>양호한 대상으로만</u> 트래픽을 라우팅한다.
"즉 한 대의 서버로 부하가 집중되지 않도록 트래픽을 해주는 특징을 가지고 있다."

​	기타 특징

* 오토스케일링
* 인스턴스 상태를 감지하여 Fail된 인스턴스는 배제
* 사용자 세션을 특정 인스턴스에 고정(세션 어피니티)
  * 세션 중 사용자로부터 들어오는 모든 요청이 동일한 대상으로 전송 - 사용자의 쿠키가 필수적
* SSL 암호화 지원
* IPV4, IPV6 지원
* Cloud Watch를 통해 모니터링
* 사용한 시간과 트래픽에 따라 과금 발생

#### 종류

* Classic Load Balancer
* Application Load Balancer
* Network Load Balancer
* Gateway Load Balancer

------

### **Classic Load Balaner (CLB)**

#### 특징

* CLB는  ELB 이전 세대의 로드 밸런서
  (현재는 잘 쓰이지 않는 추세)
* TCP, SSL, HTTP, HTTPS 등 다양한 프로토콜 지원
* Sticky Session 지원
* 로드밸런서에 인스턴스 등록

#### 단점

* 서버의 기본주소가 바뀌면 LB를 새로 생성해야된다.
* 하나의 주소에 하나의 타겟그룹으로 보내게 된다.

*(Ex) 쿠팡에서 회원관리 인스턴스와 주문 인스턴스가 따로 존재한다고 하자. 로그인 후 주문을 하기 위해서는 각각 다른 Load Balancer를 거쳐 해당 인스턴스로 접속해야 하므로 서버 개수, 비용이 증가하게 된다!*

------

### **Application Load Balancer (ALB)**

#### 특징

* CLB와 달리 하나의 로드밸런서로 **하나 이상의** 인스턴스의 트래픽을 분산
* 자체 Security Group을 가지고 있다.
* ALB 하나에 여러 리스너 설정 가능
  : 리스너의 특정 룰에 따라서 타겟 그룹으로 리다이렉트 가능
     (이러한 이유로 첫 번째 요건이 가능해진다.)
  * Listener1 : /order -> order 타겟 그룹을 포워딩
  * Listener2: /login -> login 타겟 그룹을 포워딩

<img width="579" alt="image" src="https://user-images.githubusercontent.com/33277588/155826959-81c3ac81-ebf9-49f9-ba4e-cb569bb30eff.png">

* Application 7 Layer (Http / Https) 에서 동작

------

### **Network Load Balancer (NLB)**

### 특징

* 극도의 성능을 원할 때 사용

* TCP / UDP 레벨의 트래픽을 원할 때 사용

* 자체 Security Group이 없다.

  **GLB만의 Security Group이 없다. **
  **인스턴스의 Security Group을 따라간다.**

* 타겟 그룹 설정 가능

------

### **Sticky Session**

클라이언트가 특정 인스턴스에 최초 접근하였을 때 해당 인스턴스 세션정보를 저장하고
클라이언트가 다음 요청을 보낼 때 기억된 세션정보를 통해여 같은 인스턴스에 요청할 수 있는 것을 Sticky Session  이라고 한다.

문제점

* 특정 인스턴스에 과부하 우려
* 특정 서버 Fail Over시 해당 서버에 붙어 있는 세션들이 유실될 수 있다.
* 해당 문제 발생 시 **Session Clustering** 고려

------

## **오토 스케일링**

ELB에 연결된 인스턴스를 늘렸다가 줄였다 하는 것
유저가 적을 땐 비용을 아끼고 유저가 많을 땐 서버 과부하를 막는것이 목적



#### 오토 스케일링 설정 프로세스

* 서버 세팅
* 이미지 생성
* 시작 템플릿 생성
* 대상 그룹 생성
* ALB 생성
* 오토 스케일링 그룹 생성

------

#### 나의 포스팅

[IP와 서브넷](https://jwdeveloper.tistory.com/298)

[SSL 인증서](https://jwdeveloper.tistory.com/232)

------

### **고가용성 및 스케일링성 퀴즈**

[퀴즈 내용](https://elderly-yak-238.notion.site/ELB-ASG-0f3aa50818e94065a73d4ea4621cd115)

------

## References

https://docs.aws.amazon.com/ko_kr/elasticloadbalancing/latest/userguide/what-is-load-balancing.html

https://docs.aws.amazon.com/ko_kr/AWSEC2/latest/UserGuide/ec2-instances-and-amis.html

https://docs.aws.amazon.com/ko_kr/elasticloadbalancing/latest/application/sticky-sessions.html

https://m.post.naver.com/viewer/postView.naver?volumeNo=27046347&memberNo=2521903

https://hwan-shell.tistory.com/271

https://alden-kang.tistory.com/8

https://velog.io/@kimdukbae/ELB-Elastic-Load-Balancing-AWS

https://aws.amazon.com/ko/blogs/aws/new-elastic-load-balancing-feature-sticky-sessions/

https://smjeon.dev/web/sticky-session/
