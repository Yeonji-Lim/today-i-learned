# Realm
사용자, 인증, 인가, 권한, 그룹을 관리하는 범위

하나의 Realm 내 Client들은 서로 SSO를 공유함

Realm은 독립적

Master Realm은 다른 Realm을 관리하는 데에 사용함

관리를 위한 Realm이고 다른 Realm이 상속받지는 않음

![](https://i.imgur.com/PTTLDe9.png)

이 그림에서 Application은 Client를 의미

User는 Client를 이용하는 사용자 -> Realm 단위로 되어있음

카카오 예시

카카오 마지막 페이지에 있는 선물하기, 쇼핑하기는 카카오톡 아이디로 바로 이용할 수 있음 : 같은 Realm

카카오 뱅크, 카카오 페이, 티스토리 이용할 때는 계정을 새로 가입해야 함 : 다른 Realm