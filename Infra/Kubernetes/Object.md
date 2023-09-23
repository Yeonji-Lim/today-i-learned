# Object

다음의 두가지로 이루어진다.
- **Basic Object** : 가장 기본적인 구성단위
	- 컨테이너화되어 배포되는 애플리케이션의 [워크로드](Workload)를 기술하는 오브젝트 : Pod, Service, Volume, Namespace
- **Controller** : 얘도 오브젝트. 기본 오브젝트를 생성하고 관리하는 추가 기능을 가진다.
- **Object Spec(설정 정보)**
- 메타 정보
- ...

## Object Spec
	오브젝트들은 오브젝트 스펙으로 정의가 된다.

커맨드 라인을 통해서 오브젝를 생성하면 인자로 전달하여 정의하거나 yaml또는 json 파일로 스펙을 정의할 수 있다.