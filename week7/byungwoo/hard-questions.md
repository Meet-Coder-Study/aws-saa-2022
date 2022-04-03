# Quiz 8. 클래식 솔루션 아키텍처 토론 퀴즈
- 없음

# Quiz 9. Amazon S3 퀴즈
```markdown
# S3 객체 암호화 방법 4가지
- SSE-S3: encrypts S3 objects using keys handled & managed by AWS
- SSE-KMS: leverage AWS Key Management Service to manage encryption keys
- SSE-C: when you want to manage your own encryption keys
- Client Side Encryption
```

## Question 4:
여러분의 클라이언트는 파일 암호화가 S3에서 발생하는지 확인하기를 원하지만 암호화 키를 완전히 관리하고 AWS에 저장하지 않기를 원합니다. 그렇다면 ..................................를 사용하도록 권장해야 합니다
- (정답) SSE-C
```markdown
- 키워드: 암호화가 S3에서 발생, 암호화 키를 완전히 관리하고 AWS에 저장하지 않기를 원합니다
- SSE-C (Server-Side Encryption with Customer-provided encryption key) 
```

## Question 5:
여러분이 일하는 회사는 S3에 저장된 데이터가 암호화되기를 원합니다. 그들은 AWS에서 저장하고 관리하는 암호화 키를 신경 쓰지 않지만 암호화 키의 교체 정책에 대한 제어를 유지하기를 원합니다. 그렇다면 ..................................사용을 권장합니다.
- (정답) SSE-KMS
```markdown
- 키워드: 암호화 키의 교체 정책에 대한 제어를 유지
- SSE-KMS (Server-Side Encryption with Key Management Service)
```

## Question 6:
여러분의 회사는 암호화 프로세스에 대해 AWS를 신뢰하지 않으며 애플리케이션에서 수행되기를 원합니다. 사용을 권장합니다 ..................................
- (정답) 클라이언트 측 암호화 키
```markdown
- 키워드: 애플리케이션에서 수행
- Client Side Encryption
- 클라이언트 측 암호화를 사용하면 암호화를 직접 수행해야 하며 암호화 키를 완전히 제어할 수 있습니다. 암호화를 직접 수행하고 암호화된 데이터를 AWS로 보냅니다. AWS는 암호화 키를 알지 못하며 데이터를 해독할 수 없습니다.
```

## Question 7:
여러분은 IAM 사용자가 S3 버킷의 파일을 읽고 쓸 수 있도록 S3 버킷 정책을 업데이트했지만 사용자 중 한 명이 PutObject API 호출을 수행할 수 없다고 불평합니다. 이것의 가능한 원인은 무엇일까요?
- (정답) IAM 사용자는 연결된 IAM 정책에 명시적 DENY가 있어야 합니다. (The IAM user must have an explicit DENY in the attached IAM Policy)
```markdown
- must have -> 당위성이 아닌 강한 추측인데 번역이 이상한 것 같음
- 해설: IAM 정책의 명시적 DENY는 S3 버킷 정책보다 우선합니다.
```

# Quiz 10. AWS IAM, CLI 및 SDK 퀴즈
- 없음

# Quiz 11. Amazon S3 고급 및 Athena 퀴즈
## Question 2:
여러분은 기본값으로 S3 버킷의 모든 파일이 암호화가 되길 원합니다. 이를 위한 최적의 방법은 무엇일까요?
- HTTPS 연결을 강제하는 버킷 정책 사용
- (정답) 기본 암호화 활성화
- 버전 관리 사용
```markdown
# S3 기본 암호화 vs. 버킷 정책
- S3 객체 암호화는 다음 두 가지 방법으로 가능
- s3 default encryption: 기본 암호화 옵션을 S3에서 활성화
- bucket policy: s3:PutObject 실행시 encrpytion header를 포함하지 않을 경우 거부 (기본 암호화 옵션을 override)
```

## Question 5:
여러분은 3개의 S3 버킷을 가지고 있습니다. 소스 버킷 A 1개와 다른 AWS 리전에 있는 대상 버킷 B 및 C 2개가 있습니다. 여러분은 버킷 A에서 버킷 B와 C 둘 모두에게로 객체를 복제하려 합니다. 이를 어떻게 실행하시겠습니까?
- (정답) 버킷 A에서 버킷 B로 복제를 구성한 다음 버킷 A에서 버킷 C로 복제 구성
```markdown
# S3 복제
- 먼저 src와 dest의 버전관리 기능 활성화 필요
- 계정 간 복제 가능
- 복제는 비동기로 이루어짐
- IAM 권한 설정 필요 
## Cross Region Replication (CRR)
- 용도: 규정준수, lower latency access, 계정 간 복사
## Same Region Replication (SRR)
- 용도: 로그 집계, 상용/테스트 계정 간 실시간 복사
Must enable versioning in source and destination
• Cross Region Replication (CRR)
• Same Region Replication (SRR)  

## 유의사항
- 새로운 객체에 대하서만 복제 적용 (소급적용 불가)
- 삭제시
  - 삭제 마커도 복제 가능 (선택)
  - src에서 버전ID 기준 삭제는 복제되지 않음 (악의적 삭제 방지 목적)
- 체인닝(chaining) 불가
  - A -> B -> C 복제 불가
  - A -> B, A -> C 복제 형태로 구현 필요 
```

## Question 6:
다음 중 Glacier Deep Archive 회수 모드가 아닌 것은 무엇일까요?
- (정답) Expedited (1 - 5분)
- Standard (12시간)
- Bulk (48시간)
```markdown
- 회수 모드: retrieval mode
# Amazon Glacier 회수모드 3가지
- Expedited (1 to 5 minutes)
- Standard (3 to 5 hours)
- Bulk (5 to 12 hours)
- 최소 저장 기간 90일
# Amazon Glacier Deep Archive 회수모드 2가지
- Standard (12 hours)
- Bulk (48 hours)
- 최소 저장 기간 180일
```

## Question 7:
S3 버킷에 업로드된 객체가 있는 경우, 여러분은 어떻게 알림을 받을 수 있을까요?
- S3 Select
- S3 Access Logs
- (정답) S3 Event Notifications
- S3 Analytics
```markdown
- S3 버킷 객체 이벤트는 SNS, SQS, Lamda로 전달할 수 있음
- 객체명 기준 필터링 가능 (ex. *.jpg)
- 사용 사례: S3에 업로드된 이미지에 대해서 썸네일을 만들 경우
- 원하는 만큼 많은 S3 이벤트 생성 가능
- 이벤트 알림은 수초에서 수분까지 소요
- 모든 변화에 대해서 알림을 받기 위해서는 S3 버킷 버전관리 활성화 필요 
```

## Question 9:
여러분은 S3 버전 관리가 활성화되고 객체가 많은 S3 버킷의 비용을 줄이기 위해 이전 객체 버전을 제거하고 싶습니다. 이러한 이전 객체 버전의 삭제를 자동화하는 가장 좋은 방법은 무엇일까요?
- S3 수명 주기 규칙 - 만료 작업
- (정답) S3 수명 주기 규칙 - 전환 작업
- S3 액세스 로그
```markdown
# S3 수명주기 규칙
## 전환 작업: 이동시 사용 (ex. 객체 생성 60일 후에 Standard IA로 이동)
## 만료 작업: 삭제시 사용 (ex. 365일 이후에 접근로그 파일 삭제)
```

## Question 11:
다음 중 Glacier 회수 모드가 아닌 것은 무엇일까요?
- (정답) Instant (10초)
- Expedited (1~5분)
- Standard (3~5시간)
- Bulik (5~12시간)
```markdown
- 회수 모드: retrieval mode
# Amazon Glacier 회수모드 3가지
- Expedited (1 to 5 minutes)
- Standard (3 to 5 hours)
- Bulk (5 to 12 hours)
- 최소 저장 기간 90일
# Amazon Glacier Deep Archive 회수모드 2가지
- Standard (12 hours)
- Bulk (48 hours)
- 최소 저장 기간 180일
```

## Question 14:
여러분은 S3 수명 주기 규칙에 대한 권장 사항을 찾고 있습니다. 서로 다른 스토리지 계층 간에 객체를 이동하는 데 필요한 최적의 일 수를 어떻게 분석할 수 있을까요?
- (정답) S3 Analytics
```markdown
# S3 Analytics – Storage Class Analysis
- Standard to Standard_IA으로의 객체 전환 작업에 대한 분석 가능 
- ONEZONE_IA, GLACIER에서는 불가
- 일 단위 업데이트
- 최초 실행시 24 ~ 48 시간 소요
- 수명 주기 규칙에 대한 개선을 위한 좋은 시작
```

## Question 15:
여러분은 Amazon RDS PostgreSQL로 S3에서 파일 인덱스를 구축 중입니다. 이 인덱스를 작성하려면 S3에 있는 각 객체의 처음 250바이트를 읽어야 하며 각 객체는 파일 자체의 일부 내용에 관한 메타데이터를 가지고 있습니다. S3 버킷에는 50TB의 데이터에 해당하는 100,000개가 넘는 파일이 있습니다. 이 인덱스를 어떻게 효율적으로 구축할 수 있을까요?
- RDS 가져오기 기능을 사용하여 S3에서 PostgreSQL로 데이터를 로드하고 SQL 쿼리를 실행하여 인덱스 구축
- (정답) S3 버킷을 트래버스할 애플리케이션을 만들고 처음 250바이트에 대해 바이트 범위 가져오기를 실행하고 해당 정보를 RDS에 저장합니다.
- S3 버킷을 트래버스할 애플리케이션을 만들고 처음 250바이트에 대해 바이트 범위 가져오기를 실행하고 해당 정보를 RDS에 저장합니다.
- S3 버킷을 트래버스할 애플리케이션을 만들고 S3 Select를 사용하여 처음 250바이트를 가져온 다음 해당 정보를 RDS에 저장합니다.
```markdown
# S3 Select & Glacier Select
- 서버 사이드 필터링 SQL으로 적은 데이터 추출
- rows & columns 필터 가능
- 네트워크 전송비용 절감, 클라이언트 비용 절감
```

## Question 16:
규정 준수를 위해 여러분의 회사에는 데이터베이스 백업을 4년 동안 보관해야 한다는 정책이 있습니다. 그것들을 지울 수 없어야 합니다. 다음 중 무엇을 사용해야 할까요?
- (정답) 볼트 잠금 정책이 있는 Glacier 볼트
- 제한된 Linux 권한이 있는 EFS 네트워크 드라이브
- 버킷 정책이 있는 S3
```markdown
# Glacier Vault Lock
- WORM (Write Once Read Many) model
- 이후 변경에 대한 잠금 
- 규정 준수와 데이터 보존 목적으로 사용 가능

# S3 Object Lock
- 버전 관리 활성화 필요
- WORM (Write Once Read Many) model
- 객체 버전 삭제 차단 (일정 시간)
```

## Question 17:
여러분은 온프레미스에 저장된 대규모 데이터 세트가 있으며 S3 버킷에 업로드하려 합니다. 데이터 세트는 10GB 파일로 나뉩니다. 대역폭은 양호하지만 인터넷 연결이 안정적이지 않는 상황에서 이 데이터 세트를 S3에 업로드하고 프로세스가 빠르고 인터넷 연결 문제를 방지하는 가장 좋은 방법은 무엇일까요?
- (정답) S3 멀티파트 업로드 및 S3 Transfer Acceleration 사용
```markdown
# S3 Multi-Part upload
- recommended for files > 100MB
- must use for files > 5GB
- can help parallelize uploads (speed up transfers)

# S3 Transfer Acceleration
- increase transfer speed by transferring to edge location
- compatible with multi-part upload
```

## Question 18:
여러분은 CSV 형식으로 S3에 저장된 데이터 세트의 하위 집합을 검색하려 합니다, 컴퓨팅 및 네트워크 비용을 최소화하기 위해 한 달 동안의 데이터와 10개 열 중 3개 열만 검색하려고 합니다. 다음 중 어떤 것을 사용하시겠습니까?
- (정답) S3 Select
```markdown
# S3 Select & Glacier Select
- 서버 사이드 필터링 SQL으로 적은 데이터 추출
- rows & columns 필터 가능
- 네트워크 전송비용 절감, 클라이언트 비용 절감
```
