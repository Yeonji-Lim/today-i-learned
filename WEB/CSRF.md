# Cross Site Request Forgery

사용자의 의도와 관계 없이 행해지는 공격 기법

ex : 사용자는 그저 버튼을 눌렀을 뿐인데 해커가 버튼에 심어놓은 스크립트에 의해 의도와 관계없이 공격이 행해짐

## 막는 방법

### [Referer Check](Referer_Check)

### [CSRF Token](CSRF_Token)

Spring Security에서는 공식적으로 이 CSRF 공격에 대한 방어 기능을 제공해주고 있다.