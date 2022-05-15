# Quiz 21: AWS 보안 및 암호화 퀴즈

## Question 6:
AWS KMST는 대칭 및 비대칭 KMS 키 모두를 지원합니다.
- (정답) 맞습니다.
```markdown
- 문제 내 오타: KMST (X) -> KMS (O)
KMS키는 대칭일 수도, 비대칭일 수도 있습니다. 대칭 KMS 키는 암호화와 복호화에 사용되는 256비트 키를 나타냅니다. 비대칭 KMS 키는 암호화 및 복호화, 혹은 서명과 검증에 사용되는 RSA 키 쌍을 나타내지만, 둘 다에 사용되지는 않습니다. 혹은 서명 및 검증에 사용되는 타원 곡선(ECC) 키 쌍을 나타냅니다.

# KMS Customer Master Key (CMK) 종류
- Customer Master Key는 사용자가 생성하는 것이 아닌 AWS에서 만들어 주는 것
- Client Side Encryption(사용자가 직접 키를 사용하여 암/복호화 하는 것)과 다름 
## 대칭 (Symmetric, AES-256 keys)
• First offering of KMS, single encryption key that is used to Encrypt and Decrypt
• AWS services that are integrated with KMS use Symmetric CMKs
• Necessary for envelope encryption
• You never get access to the Key unencrypted (must call KMS API to use)
• KMS API를 사용할 수 있을 때 사용 
## 비대칭 (Asymmetric, RSA & ECC key pairs)
• Public (Encrypt) and Private Key (Decrypt) pair
• Used for Encrypt/Decrypt, or Sign/Verify operations
• The public key is downloadable, but you can’t access the Private Key unencrypted
• Use case: encryption outside of AWS by users who can’t call the KMS API
• KMS API를 사용할 수 없을 때 사용

# (참고) envelope encryption
- key를 이용하여 암호화 시킨 데이터와 함께 key 또한 암호화 하고, 이것을 암호화된 데이터와 함께 동봉하여 보관하는 방식
```

## Question 8:
KMS CMK를 사용해 암호화된 EBS 스냅샷이 있는 AMI가 있습니다. 이 AMI를 다른 AWS 계정과 공유하려 합니다. AMI를 원하는 AWS 계정과 공유했으나, 다른 AWS 계정에서는 여전히 이를 사용할 수 없는 상태입니다. 이 경우, 어떻게 문제를 해결해야 할까요?
- 다른 AWS 계정이 로그아웃 후 다시 로그인해 자격 증명을 새로고침해야 함
- (정답) AMI를 암호화하는 데에 사용된 KMS CMK를 다른 AWS 계정과 공유해야 함
- 암호화된 EBS 스냅샷을 가진 AMI는 공유할 수 없음
```markdown
해설: 다른 계정에서는 암호화하는 데에 사용한 KMS API를 호출할 수 없기 때문에 키(CMK)를 계정 간(cross-account) 공유해야 함

# KMS Key Policies
## Default KMS Key Policy:
• Created if you don’t provide a specific KMS Key Policy
• Complete access to the key to the root user = entire AWS account
• Gives access to the IAM policies to the KMS key
• 기본키는 IAM 정책으로만 접근제어를 하기 때문에 계정 간 공유가 불가
## Custom KMS Key Policy:
• Define users, roles that can access the KMS key
• Define who can administer the key
• Useful for cross-account access of your KMS ke
• 커스텀 키는 IAM 정책 외에 직접 공유할 수 있기 때문에 계정 간 공유 가능 

# Copying Snapshots across accounts
1. Create a Snapshot, encrypted with your own CMK
2. Attach a KMS Key Policy to authorize cross-account access
3. Share the encrypted snapshot
4. (in target) Create a copy of the Snapshot, encrypt it with a KMS Key in your account
5. Create a volume from the snapshot
```

## Question 9:
S3 버킷과 EBS 스냅샷 모두를 암호화하는 데에 사용한 고객 관리형 CMK를 KMS에서 생성했습니다. 기업 정책에 따라 암호화 키를 매 3개월마다 교체해야 합니다. 어떻게 해야 할까요?
- KMS CMK를 다시 구성해 자동 교체를 활성화하고, ‘Period(기간)’를 3개월로 선택
- AWS에 의해 3개월 마다 자동으로 교체되는 AWS 관리 키를 사용
- (정답) KMS CMK를 수동으로 교체. KMS CMK를 생성하고 키 별칭을 사용해 새로운 KMS CMK를 참조. 오래된 데이터의 복호화를 위해 기존의 KMS CMK는 유지
```markdown
# 해설
- 3개월 -> 수동 키 순환을 사용해야 함
- (참고) 수동 키 순환은 CMK ID가 동일하기 때문에 alias(별칭)을 사용하여 변경사항을 숨기는 것이 좋음 

# KMS Automatic Key Rotation vs. KMS Manual Key Rotation
## 자동 키 순환
• For Customer-managed CMK (not AWS managed CMK)
• If enabled: automatic key rotation happens every 1 year
• Previous key is kept active so you can decrypt old data
• New Key has the same CMK ID (only the backing key is changed)
• 1년 주기로

## 수동 키 순환
• When you want to rotate key every 90 days, 180 days, etc...
• New Key has a different CMK ID
• Keep the previous key active so you can decrypt old data
• Better to use aliases in this case (to hide the change of key for the application)
• Good solution to rotate CMK that are not eligible for automatic rotation (like asymmetric CMK)
• 1년 이내의 주기로 순환이 필요할 때, 자동 키 순환이 불가한 비대칭 CMK를 사용할 때
```