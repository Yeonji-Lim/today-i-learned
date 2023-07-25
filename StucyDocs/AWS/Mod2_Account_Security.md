# 보안 주체 및 자격 증명

## IAM(Identity and Access Management)
AWS 리소스에 대한 액세스를 안전하게 제어(인증, 권한 부여)하는데 사용하는 서비스

## 보안 주체
AWS 리소스에 대한 작업을 요청할 수 있는 엔터티(사람, AWS 서비스)
페더레이션 사용자, 수임된 역할, [IdP](IdP.md)일 수 있다.

- 페더레이션 사용자 : IAM을 통해 직접 관리되지 않는 외부 자격 증명

## Account root 사용자
- AWS 서비스 및 리소스에 대한 전체 액세스 권한을 지님
- 엑세스 : 이메일 주소, 암호
- [MFA](MFA) 설정으로 사용자 보안 인증을 보호하고 일상적인 업무에는 사용하지 않는 것 을 강력히 권고

## 액세스 방법에 따른 자격 증명

### 프로그래밍 방식 엑세스
AWS CLI 설정시 aws configure로 설정

## IAM 주요 구성요소

### User
AWS와의 상호 작용에 IAM User를 사용하는 인간 사용자 또는 서비스
- 이름, 자격 증명으로 구성

### User Group
IAM User의 집합
- Group은 Group을 포함할 수 없다. -> 중첩 불가! 수평관계만 가능
- IAM User는 여러 그룹에 속하기 가능

### Policy
정책, 권한을 담은 문서

### Role
역할, 권한을 부여하는 방법

#### 부여 대상
- IAM 사용자(동일 계정, 다른 계정) 
- AWS 서비스 
- AWS 계정 
- 웹 자격 증명: Amazon Login, Amazon Cognito, Facebook, Google, Custom(SAML, OpenID Connect) 
- SAML 2.0(AD, LDAP) 
- 사용자 지정 신뢰 정책
- 외부 인증
	- On-Premise(AD, LDAP)
	- Web([IdP](IdP.md))

#### 역할 수임(Assumming a role)
지속시간: default 1HH, min 15MM, max 12HH

1. API 호출을 통해 해당 역할을 수임 하도록 요청
2. AWS STS(Security Token Service) 는 임시 보안인증 정보를 반환(temporary security credential)
3. 임시 보안 인증 정보를 사용해 리소스를 핸들링

Policy와 Role이 같이 적용되면 임시인 Role이 우선순위가 높다. 병합되는 것이 아니다!

# 보안 정책

## 정책 유형

### 자격 증명 기반 정책(Identity-based policies)

#### 관리형
- AWS 관리형
	- AWS가 생성한 정책 -> 수정, 삭제 불가
	- 직무, 서비스 액세스
- 고객 관리형 
	- 고객이 맞춤형으로 생성
#### 인라인
단일 사용자, 그룹 또는 역할에 직접 추가 (비권장)

### 리소스 기반 정책(Resource-based policies)
권한 대상을 포함

## 정책 요소
- Effect(필수): Allow, Deny 
- Principal: 대상 계정, 사용자, 역할 또는 페더레이션 사용자(리소스 정책만 사용) 
- Action(필수): 정책이 허용하거나 거부하는 작업 목록 
- Resource(필수): 작업이 적용되는 리소스 목록 
- Condition: 정책이 권한을 부여하는 상황을 지정

## 정책 평가
거부우선, 교집합

# 다중 계정 관리

## IAM
- 대상: User 
- 그룹관리: Group(Group 은 Group을 포함할 수 없다)
- 권한제어: Policy

## Organization
- 여러 AWS 계정을 조직에 통합하고 중앙에서 관리할 수 있는 계정 관리 서비스 
- 대상: Account → Account 내 모든 사용자에 영향미침(Root 포함) 
- 그룹관리: OU(Organization Unit) 
	- 계정을 그룹으로 만들어 단일 유닛으로 관리할 수 있습니다. 
	- OU는 다른 OU를 포함할 수 있다 
- 권한제어 
	- SCP(Service control policy) → SCP 는 IAM Policy 에 우선한다.