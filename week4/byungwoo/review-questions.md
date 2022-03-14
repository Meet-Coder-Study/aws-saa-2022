## 36. (review required)
여러분의 회사에서는 Elastic Beanstalk에서 실행되는 웹 사이트를 배포하고 있습니다. 웹사이트 설치에 45분 이상이 소요되며 과정에서 생성되어야 하는 static 및 동적 파일이 모두 포함되어 있습니다.
솔루션 아키텍트로서 여러분은 Elastic Beanstalk 배포에서 새 인스턴스를 생성하는 시간을 2분 미만으로 만들고 싶습니다. 이 요구 사항에 대한 솔루션을 구축하려면 다음 중 어떤 옵션을 결합해야 할까요? (2개 선택)

Your company is deploying a website running on Elastic Beanstalk. The website takes over 45 minutes for the installation and contains both static as well as dynamic files that must be generated during the installation process.
As a Solutions Architect, you would like to bring the time to create a new instance in your Elastic Beanstalk deployment to be less than 2 minutes. Which of the following options should be combined to build a solution for this requirement? (Select two)

- 설치 파일을 S3에 저장하여 신속하게 검색
  - Store the installation files in S3 so they can be quickly retrieved
- EC2 사용자 데이터를 사용하여 부팅 시 애플리케이션 설치
  - Use EC2 user data to install the application at boot time
- (선택/정답) Static 설치 구성 요소가 이미 설정된 Golden AMI 생성
  - Create a Golden AMI with the static installation components already setup
- (선택) Elastic Beanstalk 배포 캐싱 기능5 사용
  - Use Elastic Beanstalk deployment caching feature
- (정답) EC2 사용자 데이터를 사용하여 부팅 시 동적 설치 부분을 사용자 지정
  - Use EC2 user data to customize the dynamic installation parts at boot time
### 해설
- [AWS Elastic Beanstalk](https://docs.aws.amazon.com/ko_kr/elasticbeanstalk/latest/dg/Welcome.html)는 Java, .NET, PHP, Node.js, Python, Ruby, Go, Docker를 사용하여 Apache, Nginx, Passenger, IIS와 같은 친숙한 서버에서 개발된 웹 애플리케이션 및 서비스를 간편하게 배포하고 조정할 수 있는 서비스 (PaaS)
- 배포가 오래걸린다는 것은 의존성 패키지 설치와 같은 정적 부분과 소스코드를 가져와서 실행하는 동적 부분이 결합되어 오래 걸린다는 의미로 볼 수 있음
- (번역이 무언가 깔끔한 것 같지 않음...)

#### 정답
- [Golden AMI(Image)](https://hyup2423.tistory.com/27)는 OS 영역을 포함해 필수 패키지가 설치된 일종의 표준 이미지 개념입니다. 공통 부분을 미리(패키징) 해둠으로써 인스턴스 프로비저닝 시간을 최소화할 수 있음
- 사용자 데이터를 사용하여 동적 부분만 Elastic Beanstalk 배포시 실행하도록 설정할 수 있음
  - [AMI, Platform Hooks를 사용할 수 있다고 함](https://stackoverflow.com/a/62705623)

#### 오답
- Elastic Beanstalk 배포 캐싱 기능은 따로 없는 것 같음
- 설치파일을 S3에서 가져온다고 할지라도 S3에서 가져와서 실행하는 시간을 줄이지는 못함
- EC2 사용자 데이터를 사용하여 부팅 시 애플리케이션 설치 -> 어플리케이션 설치하는 부분에 정적파일과 의존성 등이 포함되면 배포시간을 줄이는 데에 소용이 없음


## 50. (review required)
한 회사는 애플리케이션 로드 밸런서 배후의 EC2 인스턴스에서 실행되는 여러 계층 소셜 미디어 애플리케이션을 관리합니다. 인스턴스는 여러 가용 영역에 걸쳐 EC2 Auto Scaling 그룹에서 실행되며 Amazon Aurora 데이터베이스를 사용합니다. 솔루션 아키텍으로서 애플리케이션을 요청 속도의 주기적인 급증에 대해 보다 탄력적으로 대처할 수 있도록 업무 요청을 받았습니다.
다음 중 주어진 사용 사례에 권장하는 솔루션은 무엇일까요? (2개 선택)
- AWS 쉴드 사용
- (정답) 애플리케이션 로드 밸런서 앞에서 CloudFront 배포 사용
- (선택/정답) Aurora 복제본 (Replica) 사용
- (선택) AWS 글로벌 액셀러레이터
- AWS Direct Connect 사용
```
키워드: 여러 가용 영역에 걸쳐있음, 요청 속도의 주기적인 급증에 대해 보다 탄력적으로 대처
- Aurora 복제본 (Replica) 사용하여 읽기 작업의 성능을 확보할 수 있음
- CloudFront는 짧은 지연 시간, 높은 전송 속도로 Points of Presence(POP, 접속 지점) (엣지 로케이션)은 인기 있는 콘텐츠가 시청자에게 빠르게 제공될 수 있도록 함
오답
- 글로벌 액셀러레이터는 게임(UDP), IoT(MQTT) 또는 Voice over IP와 같은 비 HTTP 사용 사례와 특히 static IP 주소 또는 결정적으로 빠른 지역 장애 조치가 필요한 HTTP 사용 사례에 적합합니다.
```