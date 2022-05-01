# Quiz 18: AWS 퀴즈의 데이터베이스
## Question 3:
온프레미스 MongoDB NoSQL 데이터베이스를 AWS로 마이그레이션하려고 합니다. 데이터베이스 서버를 관리하고 싶지 않으므로 고가용성, 내구성 및 안정성을 제공하는 관리형 NoSQL 데이터베이스, 가급적이면 서버리스를 사용하려고 합니다. 어떤 데이터베이스를 선택해야 할까요?
- Amazon RDS
- (정답) Amazon DynamoDB
- Amazon Redshift
- Amazon Aurora
```markdown
- 키워드: 서버리스
# DynamoDB vs. DocumentDB
- MongoDB 기반으로 만들어졌음 (호환되지는 않음) vs. MongoDB 호환
- 서버리스 vs. 서버리스X
- DocumentDB가 있었다면 헷갈릴 수 있으나 '서버리스'를 사용한다는 점에서 DynamoDB가 더 적절   
- https://jane-aeiou.tistory.com/57
```

## Question 10:
Redshift의 어떤 기능이 VPC를 통해 클러스터와 데이터 리포지토리 간에 이동하는 모든 COPY 및 UNLOAD 트래픽을 강제할까요?
Which feature in Redshift forces all COPY and UNLOAD traffic moving between your cluster and data repositories through your VPCs?
- (정답) 향상된 VPC 라우팅 (Enhaced VPC Routing)
- 향상된 VPC 라우팅 (Improved VPC Routing)
- Redshift 스펙트럼 (Redshift Spectrum)
```markdown
# AWS Redshift
- AWS에서 완전관리형으로 제공해주는 클라우드 데이터웨어하우스
- 클러스터(노드집합)를 생성하고, 클러스터가 사용할 준비가 되면(프로비저닝 완료) 데이터 적재 및 분석가능
- PostgreSQL을 기반으로 해서 표준SQL을 이용한 데이터처리를 지원하고, BI도구로 분석할 수 있음
- OLAP: online analytical processing (analytics and data warehousing)
- 데이터웨어하우스: 수집한 여러가지 데이터를 추출 및 변환 과정(ETL)을 거쳐 적재하는 관계형 데이터베이스
- Redshift의 UPLOAD 구문은 query결과를 s3 서버에 파일의 형식으로 업로드할 수 있게 해줌
- Redshift의 COPY 구문은 반대로 s3 서버에 있는 파일을 불러와 database 내의 table로 만들 수 있도록 해줌
-Redshift Enhanced VPC Routing을 사용하면 Amazon Redshift는 클러스터와 데이터 리포지토리 사이의 COPY 및 UNLOAD 트래픽이 모두 Amazon VPC 서비스를 기반으로 하는 Virtual Private Cloud(VPC)를 통과하도록 강제
```

# Quiz 19: 미디엄 모니터링 및 감사 퀴즈
## Question 12:
여러분은 시간이 지남에 따라 리소스 구성의 규정 준수를 평가하려고 합니다. 어떤 AWS 서비스를 선택하시겠습니까?
You would like to evaluate the compliance of your resource's configurations over time. Which AWS service will you choose?
- (정답) AWS 구성
- NS 마존 CloudWatch (Amazon CloudWatch)
- NS WS CloudTrail (AWS CloudTrail)
```markdown
# AWS Clouwatch
- 모니터링 및 관찰 서비스
- 모니터링 및 운영 데이터를 로그, 지표 및 이벤트 형태로 수집
- 이상 동작을 감지하며, 경보를 설정하고, 로그와 지표를 나란히 시각화하며, 자동화된 작업을 수행

# AWS CloudTrail
• AWS 인프라 전체의 계정 활동을 모니터링하고 기록
• Provides governance, compliance and audit for your AWS Account
• CloudTrail is enabled by default!
• Get an history of events / API calls made within your AWS Account by:
  • Console
  • SDK
  • CLI
  • AWS Services
• Can put logs from CloudTrail into CloudWatch Logs or S3
• A trail can be applied to All Regions (default) or a single Region.
• If a resource is deleted in AWS, investigate CloudTrail first!

# AWS Config
• AWS 설정 이력을 모니터링하고 구성의 변경을 통지해주는 서비스
• Helps with auditing and recording compliance of your AWS resources
• Helps record configurations and changes over time
• Questions that can be solved by AWS Config:
  • Is there unrestricted SSH access to my security groups?
  • Do my buckets have any public access?
  • How has my ALB configuration changed over time?
• You can receive alerts (SNS notifications) for any changes
• AWS Config is a per-region service
• Can be aggregated across regions and accounts
• Possibility of storing the configuration data into S3 (analyzed by Athena)
```