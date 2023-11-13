# Domain Name Service
[IP](IP.md) 주소는 인간이 기억하기 어려운데, 인간이 기억하기 쉽게 언어체계로 변환한 것

도메인 이름을 IP 주소로 변환해주며, **53번 포트**를 사용한다.

# Domain Name System
IP 주소와 도메인 주소를 이어주는 환경/시스템

이 안에서 동작하는 서버를 DNS 서버 -> 혼용 사용

## DNS 서버

DNS 서버는 호스팅 서버에 할당된 IP 주소와 도메인 네임이 같다는 것을 저장

### 구분
도메인 수는 엄청 많다. 그래서 종류가 계층화되어 단계적으로 관리가 된다.

[ISP](ISP) 서버에는 DNS 서버가 있고, 인터넷 사용자가 실제로 사용하는 DNS 서버임

ISP 서버에서 캐시 찾아보고 Root DNS, TLD DNS, Authoritative DNS를 거친다.

#### Root DNS 서버
[ICANN](ICANN)이 직접 관리
TLD DNS 서버의 IP들을 저장하고 안내함

#### TLD DNS 서버
Top Level Domain
도메인 등록 기관(.com, .net, .kr)이 관리
Authoritative DNS server IP를 저장하고 안내

#### Authoritative DNS 서버
실제 개인 도메인과 IP 주소의 관계가 기록/저장/변경
일반적으로 도메인/호스팅 업체의 '**네임서버**'라고 말하는 것

#### Recursive DNS 서버
위의 3가지 서버를 거치는데, 매번 거치면 비효율적이기 때문에, 캐시 느낌으로 저장
데이터를 일정기간([TTL](TTL)) 동안 캐시 형태로 저장