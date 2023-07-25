# IP 주소 지정

## IPv4
- 4개의 파트
- 각 파트는 8비트 -> 2진수 표기: 0 ~ 255 : 약 43억개

## IPv6
- 8개의 파트
- 각 파트는 128비트로 구성 -> 16진수 표기

## CIDR
인터넷 상의 데이터 라우팅 효율성을 향상시키는 IP 주소 할당 방법
특정 네트워크 구간 표시

# VPC
Virtual Private : 가상 + 격리

## Amazon VPC
- 사용자의 AWS 계정 전용 격리된 가상 네트워크
- 단일 리전 소속, 모든 가용 영역을 포함

## Subnet
- 네트워크를 효율적으로 사용하는 용도
- VPC IP 주소 범위
- 단일 가용 영역내에서만 존재
- 주소 범위 중에 IP 5개는 AWS에서 관리 용도로 사용한다.
	- 서브넷을 너무 작게 잡지 말자
- 예약 IP
	- ﻿﻿10.0.0.0: 네트워크 주소입니다.
	- ﻿﻿10.0.0.1: AWS에서 VPC 라우터용으로 예약됩니다.
	- ﻿﻿10.0.0.2: AWS에서 예약됩니다. ONS 서버의 IP 주소는 항상 vPC 네트워크 범위의 기본 IP 주소에 2를 더한 값입니다.
	- ﻿﻿10.0.0.3: 차후 사용을 위해 AWS에서 예약됩니다.
	- ﻿﻿10.0.0.255: 네트워크 브로드캐스트 주소입니다. VPC에서는 브로드캐스트가 지원되지 않으므로 이 주소가 예약됩니다.

## Internet Gateway
- VPC와 인터넷 간에 통신을 위해 존재하는 컴퍼넌트
- 생성 후에 VPC에 attach

## Route table
- 네트워크 트래픽이 전달되는 위치 지정 하는데 사용되는 규칙세트(경로)를 포함

## Elastic IP Address(EIP, 탄력적 IP 주소) 
- 정적 IPv4 주소 → Public IP 고정 
- 기본적으로 리전당 5개까지 생성 가능
- EC2 instance 및 [ENI](ENI) 에 붙였다가 뗐다가 할 수 있다.

## NAT gateway
Private Subnet 내 Resource의 Outbound Intenet 접속을 위함.(EIP 필요)

NAT: (Network Address Translation, 네트워크 주소 변환)

## Elastic network interface 
- 가상 네트워크 카드를 나타내는 논리적 네트워킹 구성 요소 
- 고유한 private IP 보유, EIP 연동 가능, MAC Address 보유

# VPC 트래픽 보안

## Network ACL(NACL)
- 서브넷 수준에서 특정 인바운드 또는 아웃바운드 트래픽을 허용하거나 거부합니다. 
- 특성: 상태 비저장 
- 설정: 허용/거부 
- 규칙: 낮은 번호의 규칙부터 순서대로 평가

## Security group(보안그룹) 
- 보안 그룹은 연결된 리소스에 도달하고 나갈 수 있는 트래픽을 제어합니다. 
- 특성: 상태 저장 
- 설정: 허용 
- 규칙: 여러 보안 그룹을 리소스와 연결하면 각 보안 그룹의 규칙이 집계되어 액세스 허용 여부를 결정 
- * Security Group Chaining