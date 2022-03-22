# Quiz2
## Question 3:
EC2 예약 인스턴스의 가능한 예약 기간은?
```
- 1년 또는 3년
- 2년 또는 4년
- 6개월 또는 1년
- 1년에서 3년 사이
```
- 1년 또는 3년
- [예약 인스턴스](https://docs.aws.amazon.com/ko_kr/AWSEC2/latest/UserGuide/ec2-reserved-instances.html#ri-overview)는 사용 비용을 절감해주는 결제 할인 혜택입니다. 예약 인스턴스를 구매할 때 인스턴스 유형, 플랫폼, 테넌시, 리전 또는 가용 영역(선택 사항)과 같은 속성을 설정할 수 있습니다.
- 1년 또는 3년의 기간 약정을 가지고 있습니다.
- 예약 인스턴스는 [표준 유형과 Convertible Reserved Instance 으로 나누어져 있으며](https://docs.aws.amazon.com/ko_kr/AWSEC2/latest/UserGuide/reserved-instances-types.html) 주된 차이는 인스턴스의 변경 가능 여부입니다.

# Quiz3
## Question 2:
EC2 인스턴스 세트가 필요한 뱃치 작업을 실행하려고 합니다. 이 일괄 작업은 약 4시간 동안 실행되어야 하며 도중에 중단되어서는 안 됩니다. 가장 저렴한 비용으로 이 뱃치 작업을 실행하려면 다음 중 어떤 EC2 구매 옵션을 선택해야 할까요?
```
- 온디맨드 인스턴스
- 예약 인스턴스
- 스팟 인스턴스
- 스팟 블록 인스턴스
```
- [스팟 블록 인스턴스란 지속 시간이 정의된 스팟 인스턴습니다.](https://docs.aws.amazon.com/ko_kr/AWSEC2/latest/UserGuide/spot-requests.html#fixed-duration-spot-instances)
- 스팟 블록 인스턴스를 사용하면 도중 중단 없이 지정된 기간(1-6시간) 동안 스팟 EC2 인스턴스 세트를 예약할 수 있습니다.
- 스팟 블록 인스턴스는 2021년 7월 1일부터 더 이상 신규 고객에게 제공되지 않습니다.

# Quiz4
## Question 5:
EBS 다중 연결이란 무엇일까요?
```
- 여러 AZ의 여러 EC2 인스턴스에 동일한 EBS 볼륨 연결
- 동일한 AZ의 여러 EBS 볼륨을 동일한 EC2 인스턴스에 연결
- 동일한 AZ의 여러 EC2 인스턴스에 동일한 EBS 볼륨 연결
- 여러 AZ의 여러 EBS 볼륨을 동일한 EC2 인스턴스에 연결
```
- 동일한 AZ의 여러 EC2 인스턴스에 동일한 EBS 볼륨 연결
- EBS는 하나의 AZ에 종속되어 있음 (복사는 가능)
- [EBS 다중 연결](https://docs.aws.amazon.com/ko_kr/AWSEC2/latest/UserGuide/ebs-volumes-multi.html)을 사용하여 동일한 EBS 볼륨을 동일한 AZ의 여러 EC2 인스턴스에 연결할 수 있습니다. 각 EC2 인스턴스에는 전체 읽기/쓰기 권한이 있습니다.
- [Provisioned IOPS SSD볼륨에만 지원됩니다.](https://docs.aws.amazon.com/ko_kr/AWSEC2/latest/UserGuide/ebs-volume-types.html#EBSVolumeTypes_piops)