# 02. AWS Skill Builder

```
한 회사의 이미지 처리 애플리케이션 사용량이 설정된 패턴 없이 갑자기 증가하고 있습니다. 
애플리케이션의 처리 시간은 이미지 크기에 따라 선형적으로 증가합니다. 
대용량 이미지 파일의 경우 처리에 최대 20분이 소요될 수 있습니다.
아키텍처는 웹 티어, Amazon Simple Queue Service(Amazon SQS) 표준 대기열 및 Amazon EC2 인스턴스에서 이미지를 처리하는 메시지 소비자로 구성됩니다. 대량의 요청이 발생하면 Amazon SQS의 메시지 백로그가 증가합니다. 사용자가 처리 지연을 보고하고 있습니다. 솔루션스 아키텍트는 클라우드 모범 사례에 따라 애플리케이션의 성능을 개선해야 합니다.
다음 중 이러한 요구 사항을 충족하는 솔루션은 무엇인가요

정답 ) C
풀이 ) labmda에서 처리하면 될줄 알았음

찐정답 ) D
풀이 ) Lambda에는 15분의 운영 제한이 있습니다.
Amazon EC2 Auto Scaling을 사용하면 처리 용량이 수요를 충족할 수 있습니다.
```

- [https://docs.aws.amazon.com/lambda/latest/dg/gettingstarted-limits.html](https://docs.aws.amazon.com/lambda/latest/dg/gettingstarted-limits.html)

```
Amazon Elastic Container Service(Amazon ECS)를 사용하여 컨테이너식 웹 애플리케이션을 실행하는 솔루션을 설계 중인 한 솔루션스 아키텍트가 있습니다. 솔루션스 아키텍트는 각 컨테이너 인스턴스에서 여러 작업 사본을 실행하여 비용을 최소화하려고 합니다. 로드의 증가 및 감소에 따라 작업 사본의 수가 조정되어야 합니다.

로드를 여러 작업으로 분산하는 라우팅 솔루션은 무엇인가요?

정답 ) B 동적 호스트 포트 매핑을 사용하여 요청을 분산하도록 Application Load Balancer를 구성합니다.
풀이 ) 동적 호스트 포트 매핑을 사용하면 컨테이너 인스턴스마다 동일 서비스의 여러 작업이 허용됩니다.

경로 기반 라우팅을 사용하면 여러 서비스가 단일 Application Load Balancer(ALB)에서 동일한 리스너 포트를 사용할 수 있습니다. ALB는 URL 경로에 기반하여 특정 대상 그룹으로 요청을 전달합니다. 하지만 이 솔루션은 동일한 서비스의 여러 작업 간 로드 배포에 도움이 되지 않습니다.
```

```
네트워크 로드 밸런서를 사용하여 두 Amazon EC2 인스턴스에서 실행되는 한 애플리케이션이 있습니다. EC2 인스턴스는 단일 가용 영역에 있습니다.

솔루션스 아키텍트는 이 아키텍처의 가용성을 더욱 높이기 위해 무엇을 해야 하나요?

정답 ) D 여러 가용 영역 간에 확장되는 Auto Scaling 그룹에 EC2 인스턴스를 배치하고 Auto Scaling 그룹을 네트워크 로드 밸런서의 대상으로 지정합니다.
풀이 ) 이 솔루션은 여러 가용 영역 간에 EC2 인스턴스를 확장하고 추가 용량이 필요할 경우 자동으로 용량을 추가합니다.
```

```
한 회사에서 법률 문서를 저장하기 위해 Amazon S3 버킷을 사용하고 있습니다. 이 회사는 문서를 자주 수정하고 동일한 객체 키를 사용하여 S3 버킷에 다시 업로드합니다. 이 회사는 문서의 이전 사본을 다운로드할 수 있어야 합니다. 또한 문서를 실수로 삭제하지 않도록 보호해야 합니다.

이러한 요구 사항을 충족하는 가장 운영 효율성이 높은 솔루션은 무엇인가요?

정답 ) A S3 버킷에서 S3 버전 관리를 활성화합니다.
풀이 ) S3 버전 관리를 사용하면 동일한 S3 버킷에 객체의 여러 변형을 유지할 수 있으며 S3 버킷에 저장된 모든 버전의 객체를 모두 보존, 검색 및 복원할 수 있습니다. 또한 의도하지 않은 사용자 작업 및 애플리케이션 장애로부터 복구할 수 있습니다.
```

- [https://docs.aws.amazon.com/AmazonS3/latest/userguide/versioning-workflows.html](https://docs.aws.amazon.com/AmazonS3/latest/userguide/versioning-workflows.html)

```
Application Load Balancer를 사용해 Amazon EC2 인스턴스에서 실행되는 한 보고 애플리케이션이 있습니다. 인스턴스는 여러 가용 영역 간의 Amazon EC2 Auto Scaling 그룹에서 실행됩니다. 복잡한 보고서의 경우 애플리케이션이 요청에 응답하는 데 최대 15분이 걸릴 수 있습니다. 한 솔루션스 아키텍트는 축소 이벤트 중 보고서 요청이 처리될 경우 HTTP 5xx 오류가 발생하는 것에 대해 우려하고 있습니다.

 

인스턴스가 종료되기 전에 사용자 요청이 완료되도록 하려면 솔루션스 아키텍트가 어떻게 해야 하나요?

정답 ) C Auto Scaling 그룹의 휴지 기간을 가장 오래 실행되는 응답에 필요한 것보다 더 긴 시간으로 늘립니다.
풀이 ) Amazon EC2 Auto Scaling 휴지 기간을 지정하여 이전 활동의 효과가 나타나기 전에 Auto Scaling 그룹에서 추가 인스턴스를 시작하거나 종료하지 않도록 할 수 있습니다.

찐정답 ) D 인스턴스의 대상 그룹에 대한 등록 취소 지연 시간 제한을 900초 이상으로 늘립니다.
풀이 ) 기본적으로 Elastic Load Balancing은 등록 취소 프로세스가 완료되기 전에 300초 동안 대기하는데, 이는 대상에 대해 진행 중인 요청을 완료하는 데 도움이 될 수 있습니다. Elastic Load Balancing이 대기하는 시간을 변경하려면 등록 취소 지연 값을 업데이트합니다.
```

- [https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html#deregistration-delay](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html#deregistration-delay)

```
한 회사에서 방금 완성된 데모에 Amazon EC2 스팟 인스턴스를 사용했습니다. 솔루션스 아키텍트는 비용 발생을 막기 위해 스팟 인스턴스를 제거해야 합니다.

솔루션스 아키텍트는 이 요구 사항을 충족하기 위해 무엇을 해야 하나요?

정답 ) C 스팟 요청을 취소한 후 스팟 인스턴스를 종료합니다.
풀이 ) 스팟 인스턴스를 제거하려면 적절한 단계에 따라 스팟 요청을 취소한 다음 스팟 인스턴스를 종료해야 합니다.
```

- [https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/spot-requests.html#terminating-a-spot-instance](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/spot-requests.html#terminating-a-spot-instance)

```
한 회사에서 Linux 기반 Amazon EC2 인스턴스가 시작된 방법에 대한 구성 세부 정보를 조회해야 합니다.

솔루션스 아키텍트는 시스템 메타데이터를 수집하기 위해 EC2 인스턴스에서 어떤 명령을 실행해야 합니까?

정답 ) B curl http://localhost/latest/meta-data
풀이 ) 이 솔루션은 127.0.0.1 IP 주소를 확인하므로 localhost를 사용할 수 없습니다. localhost 이름을 활용하여 메타데이터를 사용할 수 없습니다.

찐정답 ) A curl http://169.254.169.254/latest/meta-data
풀이 ) 인스턴스 메타데이터를 검색하는 유일한 방법은 링크-로컬 주소(169.254.169.254)를 사용하는 것입니다.
```

- [https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instancedata-data-retrieval.html](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instancedata-data-retrieval.html)

```
한 회사에 웹 사이트 사용자에 대한 로그 파일을 내보내는 온프레미스 애플리케이션이 있습니다. 이러한 로그 파일의 크기는 20~30GB입니다. 한 솔루션스 아키텍트가 이러한 파일을 저장하기 위해 Amazon S3 버킷을 생성했습니다. 파일은 애플리케이션에서 직접 업로드됩니다. 네트워크 연결에 간헐적인 오류가 발생하여 업로드가 실패하는 경우가 있습니다.

솔루션스 아키텍트는 이 문제를 해결하는 솔루션을 설계해야 합니다. 솔루션은 운영 오버헤드를 최소화해야 합니다.

다음 중 이러한 요구 사항을 충족하는 솔루션은 무엇인가요?

정답 ) C Amazon S3에 멀티파트 업로드를 사용합니다.
```

- [https://docs.aws.amazon.com/AmazonS3/latest/userguide/mpuoverview.html](https://docs.aws.amazon.com/AmazonS3/latest/userguide/mpuoverview.html)

```
한 회사에서 새 Amazon EC2 인스턴스에 새 데이터베이스를 배포하고 있습니다. 이 데이터베이스의 워크로드에는 최대 20,000IOPS를 지원할 수 있는 단일 Amazon Elastic Block Store(Amazon EBS) 볼륨이 필요합니다.

이 요구 사항을 충족하는 EBS 볼륨 유형은 무엇인가요?

정답 ) B 프로비저닝된 IOPS SSD
풀이 ) 프로비저닝된 IOPS SSD EBS 볼륨은 각 볼륨에 대해 최대 64,000IOPS를 제공합니다.
```

```
AWS에서 Site-to-Site VPN 연결을 구축하는 데 필요한 구성 요소는 무엇인가요? (정답은 2개입니다.)

정답 ) ?

찐정답 ) C 고객 게이트웨이 / E 가상 프라이빗 게이트웨이
- VPN 연결을 설정하려면 고객 게이트웨이가 필요합니다. 고객 게이트웨이 디바이스는 고객의 데이터 센터에서 설정 및 구성됩니다.
- 가상 프라이빗 게이트웨이는 VPC에 연결되어 AWS에서 Site-to-Site VPN 연결을 생성합니다. 개방형 퍼블릭 인터넷을 통과할 필요 없이 온프레미스 데이터 센터에서 VPC로 암호화된 프라이빗 네트워크 트래픽을 수락할 수 있습니다.
```

- [https://docs.aws.amazon.com/vpn/latest/s2svpn/VPC_VPN.html](https://docs.aws.amazon.com/vpn/latest/s2svpn/VPC_VPN.html)

```
한 회사에서 AWS에 배포할 채팅 애플리케이션을 개발하고 있습니다. 이 애플리케이션은 키 값 데이터 모델을 사용하여 메시지를 저장합니다. 일반적으로 사용자 그룹은 메시지를 여러 번 읽습니다. 솔루션스 아키텍트는 높은 비율의 읽기를 지원하도록 확장되고 마이크로초 단위 대기 시간으로 메시지를 전달하는 데이터베이스 솔루션을 선택해야 합니다.

이러한 요구 사항을 충족하는 데이터베이스 솔루션은 무엇인가요?

정답 ) B DynamoDB Accelerator(DAX)가 포함된 Amazon DynamoDB
풀이 ) DynamoDB는 키 값 레코드를 지원하는 NoSQL 데이터베이스입니다. DAX는 마이크로초 단위로 응답 시간을 제공합니다.
```

- [https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Introduction.html](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Introduction.html)
- [https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/DAX.html](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/DAX.html)

```
한 회사에서 AWS 계정 하나를 사용하여 프로덕션 워크로드를 실행합니다. 이 회사는 보안 팀을 위한 별도의 AWS 계정을 보유하고 있습니다. 보안 팀은 정기 감사 중에 프로덕션 워크로드를 실행하는 AWS 계정의 특정 계정 설정 및 리소스 구성을 조회해야 합니다. 솔루션스 아키텍트는 AWS 보안 모범 사례를 따르는 솔루션을 설계하여 보안 팀에 필요한 액세스 권한을 제공해야 합니다.

다음 중 이러한 요구 사항을 충족하는 솔루션은 무엇인가요?

정답 ) B 프로덕션 계정에서 IAM 역할을 생성합니다. 그런 다음 보안 팀에 필요한 권한을 제공하는 권한 정책을 연결한 후 보안 팀 계정을 신뢰 정책에 추가합니다.
풀이 ) 이 솔루션은 역할을 사용하여 최소 권한 액세스로 구성된 권한을 위임함으로써 보안 모범 사례를 따릅니다.
```

- [https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html#grant-least-privilege](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html#grant-least-privilege)

```
한 회사에서 AWS Cloud에서 인기 있는 자사 웹 애플리케이션의 새 모바일 버전을 개발하고 있습니다. 내부 및 외부 사용자가 모바일 앱에 액세스할 수 있어야 합니다. 모바일 앱은 단일 중앙 소스에서 권한 부여, 인증 및 사용자 관리를 처리해야 합니다.

 

이러한 요구 사항을 충족하는 솔루션은 무엇인가요?

정답 ) B IAM 사용자 및 그룹
풀이 ) IAM 사용자 및 그룹을 사용하여 AWS 서비스를 사용하도록 인증되고 권한이 부여된 사용자를 제어할 수 있습니다. 하지만 사용자 및 그룹은 애플리케이션에 대한 액세스를 제어하지 않습니다.

찐정답 ) Amazon Cognito 사용자 풀
풀이 ) Amazon Cognito는 웹 및 모바일 앱에 대한 인증, 권한 부여 및 사용자 관리를 제공합니다. 사용자는 사용자 이름과 암호를 사용하여 직접 로그인하거나 신뢰할 수 있는 서드 파티를 통해 로그인할 수 있습니다.
```

- [https://docs.aws.amazon.com/cognito/latest/developerguide/what-is-amazon-cognito.html](https://docs.aws.amazon.com/cognito/latest/developerguide/what-is-amazon-cognito.html)

```
엄격한 데이터 보호 요구 사항이 있는 한 회사가 있습니다. 솔루션스 아키텍트는 인터넷에서 백엔드 Amazon RDS DB 인스턴스에 액세스할 수 없도록 VPC에 대한 보안을 구성해야 합니다. 또한 솔루션스 아키텍트는 애플리케이션 티어에서 지정된 포트를 통해서만 DB 인스턴스에 액세스할 수 있는지 확인해야 합니다.

솔루션스 아키텍트는 이러한 요구 사항을 충족하기 위해 어떤 조치를 취해야 하나요? (정답은 2개입니다.)

정답1 ) A DB 인스턴스에 대한 프라이빗 서브넷만 포함하는 DB 서브넷 그룹을 지정합니다.
풀이1 ) 프라이빗 서브넷은 데이터베이스 티어를 보호하는 데 사용되는 구성 요소 중 하나입니다. 인터넷 트래픽은 프라이빗 서브넷에 라우팅되지 않습니다. 프라이빗 서브넷에 DB 인스턴스를 배치하면 보안 계층이 추가됩니다.

정답2 ) E 데이터베이스 포트를 통해 애플리케이션 티어의 보안 그룹에서 보내는 요청을 허용하는 인바운드 규칙을 데이터베이스 보안 그룹에 추가합니다. 그런 다음 다른 인바운드 규칙을 제거합니다.
풀이2 ) 보안 그룹은 DB 인스턴스에 대한 액세스를 제한할 수 있습니다. 또한 보안 그룹은 특정 포트의 애플리케이션 티어에서만 액세스를 제공합니다.
```

```
한 회사에서 Amazon CloudFront 배포를 위한 원본으로 구성된 Application Load Balancer를 사용하여 Amazon EC2 인스턴스에서 웹 사이트를 실행합니다. 이 회사는 크로스 사이트 스크립팅 및 SQL 명령어 삽입 공격으로부터 보호하려고 합니다.

 

이러한 요구 사항을 충족하기 위해 솔루션스 아키텍트가 추천해야 하는 접근 방식은 무엇인가요?

정답 ) C CloudFront 배포에서 AWS WAF를 설정하고 크로스 사이트 스크립팅 및 SQL 명령어 삽입 공격을 차단하는 조건 및 규칙을 사용합니다.
풀이 ) AWS WAF는 악성일 가능성이 있는 SQL 코드(SQL 명령어 삽입이라고 함)의 존재를 감지할 수 있습니다. 또한 AWS WAF는 악성일 가능성이 있는 스크립트(크로스 사이트 스크립팅이라고 함)의 존재를 감지할 수 있습니다.
```

- [https://docs.aws.amazon.com/waf/latest/developerguide/waf-chapter.html](https://docs.aws.amazon.com/waf/latest/developerguide/waf-chapter.html)

```
최소 5년 동안 데이터 레코드를 유지 관리해야 하는 한 회사가 있습니다. 데이터는 저장된 후에 거의 액세스되지 않습니다. 데이터는 2시간 이내에 액세스할 수 있어야 합니다.

이러한 요구 사항을 가장 비용 효율적으로 충족할 수 있는 솔루션은 무엇인가요?

정답 ) B Amazon S3 버킷에 데이터를 저장하고 S3 수명 주기 정책을 사용하여 데이터를 S3 Glacier로 이동합니다.
풀이 ) S3 버킷에 데이터를 저장하면 데이터를 위한 비용 효율적인 초기 위치가 제공됩니다. S3 Glacier는 2시간 검색 시간 요구 사항을 충족하는 가장 비용 효율적인 아카이브 스토리지 솔루션입니다
```

```
한 미디어 회사에서 그래픽 렌더링을 위한 새로운 솔루션을 설계하고 있습니다. 애플리케이션에는 프레임이 렌더링된 이후에 삭제되는 임시 데이터를 위해 최대 400GB의 스토리지가 필요합니다. 이 애플리케이션에서 렌더링을 수행하려면 임의로 약 40,000IOPS가 필요합니다.

이 렌더링 애플리케이션에 대해 가장 비용 효율적인 스토리지 옵션은 무엇인가요?

정답 ) 프로비저닝된 IOPS SSD(io1 또는 io2) Amazon Elastic Block Store(Amazon EBS) 볼륨을 사용하는 스토리지 최적화 Amazon EC2 인스턴스
풀이 ) 프로비저닝된 IOPS SSD(io1 또는 io2) EBS 볼륨은 시나리오에 필요한 40,000IOPS 이상을 제공할 수 있습니다. 하지만 Amazon EBS는 시간당 인스턴스 요금에 비용을 추가하므로 이 솔루션은 인스턴스 스토어만큼 비용 효율적이지 않습니다. 이 솔루션은 인스턴스 수명 주기 이상의 데이터 지속성을 제공하지만 이 사용 사례에서는 지속성이 필요하지 않습니다.

찐정답 ) A 인스턴스 스토어 스토리지를 사용하는 스토리지 최적화 Amazon EC2 인스턴스
풀이 ) SSD 지원 스토리지 최적화(i2) 인스턴스는 임의로 365,000IOPS 이상을 제공합니다. 인스턴스 스토어는 인스턴스의 정규 시간당 요금에 비해 추가 비용이 없습니다.
```

- [https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-volume-types.html#EBSVolumeTypes_piops](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-volume-types.html#EBSVolumeTypes_piops)

```
한 솔루션스 아키텍트가 회사 환경을 AWS Cloud로 마이그레이션하려고 합니다. 회사 환경의 핵심 구성 요소는 고객에게 이메일 알림을 보내는 애플리케이션 서버입니다. 이 마이그레이션의 일환으로 솔루션스 아키텍트는 관리형 AWS 서비스만 사용해야 합니다.

이러한 요구 사항을 충족하는 솔루션은 무엇인가요?

정답 ) D 이메일 프로토콜을 사용하여 Amazon Simple Notification Service(Amazon SNS)를 구성합니다.
풀이 ) Amazon SNS는 애플리케이션 간 통신 및 애플리케이션과 사용자 간 통신을 위한 완전관리형 메시징 서비스입니다.
```

- [https://aws.amazon.com/ko/sns/faqs/](https://aws.amazon.com/ko/sns/faqs/)

```
한 회사에서 애플리케이션 계층과 온라인 트랜잭션 처리(OLTP) 관계형 데이터베이스로 구성되는 새 애플리케이션을 배포하고 있습니다. 애플리케이션은 항상 사용할 수 있어야 합니다. 그러나 애플리케이션에는 비활성 기간이 있습니다. 이 회사는 이러한 유휴 기간 동안 지불하는 컴퓨팅 비용을 최소화하려고 합니다.

이러한 요구 사항을 가장 비용 효율적으로 충족할 수 있는 솔루션은 무엇인가요?

정답 ) D Application Load Balancer를 사용하여 Auto Scaling 그룹의 Amazon EC2 인스턴스에 애플리케이션을 배포합니다. 그런 다음 데이터베이스에 Amazon RDS for MySQL을 사용합니다.
풀이 ) 이 솔루션을 사용하면 비활성 기간 동안 하나 이상의 인스턴스와 데이터베이스가 실행됩니다. 그러나 이 솔루션은 비활성 기간 동안 비용을 최소화하지 않으므로 가장 비용 효율적인 옵션이 아닙니다.

찐정답 ) A AWS Fargate에서 Amazon Elastic Container Service(Amazon ECS)를 사용하여 컨테이너에서 애플리케이션을 실행합니다. 그런 다음 데이터베이스에 Amazon Aurora Serverless를 사용합니다.
풀이 ) Amazon ECS에서 컴퓨팅에 Fargate를 사용하는 경우 애플리케이션이 유휴 상태일 때 비용이 발생하지 않습니다. 또한 Aurora Serverless는 유휴 상태일 때 컴퓨팅 비용이 발생하지 않습니다
```

```
위성 이미지를 처리하는 한 회사에 AWS에서 실행되는 애플리케이션이 있습니다. 이 회사에서는 Amazon S3 버킷에 이미지를 저장합니다. 규정 준수를 위해 이 회사는 한 달에 한 번 모든 데이터를 온프레미스 위치로 복제해야 합니다. 회사에서 전송해야 하는 평균 데이터 양은 60TB입니다.

이 데이터를 전송하는 가장 비용 효율적인 방법은 무엇인가요?

정답 ) A 기존 S3 버킷에서 AWS Snowball Edge Storage Optimized 디바이스로 매월 데이터를 내보냅니다. 그런 다음 온프레미스 위치로 디바이스를 배송하고 데이터를 전송합니다. 일주일 후에 디바이스를 반환합니다.
풀이 ) 기본 가격에는 디바이스와 10일간의 온프레미스 위치 사용 기간이 포함됩니다. 회사에서 1주일 이내에 디바이스를 반환할 경우 기본 가격과 AWS에서 데이터를 전송하는 데 필요한 가격을 지불합니다.
```