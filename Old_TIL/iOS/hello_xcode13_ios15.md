## Hello Xcode13, ios15

structure 형식으로 바뀐 다음에는 처음 들어가보는 xcode 13의 ios 파트..

간단한 앱을 하나 만들어보자 싶어서 한번 튜토리얼 부터 차근히 해보려한다.

ios app을 생성하고 나면 

{프로젝트이름}App.swift라는 파일이 자동으로 생기는데 난 튜토리얼 그대로 따라가려고 Landmarks로 이름을 설정함

~~~
import SwiftUI

@main
struct LandmarksApp: App {
    var body: some Scene {
        WindowGroup {
            ContentView()
        }
    }
}
~~~

이렇게 생김. 이렇게 SwitftUI 앱 라이프 사이클을 사용하는 앱이라면 App 프로토콜을 준수하는 구조를 가지고 있다. 

여기서 

body : 하나 이상의 스크린을 반환

@main : 여기가 entry point임을 명시

ContentView.swift로 가보자

~~~
import SwiftUI

struct ContentView: View {
    var body: some View {
        Text("Hello, world!")
            .padding()
    }
}

struct ContentView_Previews: PreviewProvider {
    static var previews: some View {
        ContentView()
    }
}
~~~

두개의 struct가 있는 데,

첫번째는 View 프로토콜을 따르고 View의 내용과 레이아웃을 설정

두번째는 말그대로 preview, 위의 ContentView를 미리보기 할 수 있게 한다.

코드로 변경할 수도 있지만 command + 클릭 > SwiftUI Inspector

해당하는 객체의 내용이나 레이아웃을 변경할 수 있다. 

Stack이라는 구조에 포함하려고 할 때도 간단히 코드에서 command + 클릭 > Embeded in VStack(또는 HStack)

오른쪽 상단의 + 버튼으로 객체를 포함시킬 수 있다.

이걸 이니셜라이저 initializer라고 한다.

HStack에서 전체 너비를 사용하고자 하면 spacer라는 것을 그 안의 오브젝트들 사이에 추가하면 됨

.padding이라는 modifier를 통해 화면의 양 끝에 딱 붙는 것을 방지할 수 있다.

~~~
struct ContentView: View {
    var body: some View {
        VStack(alignment: .leading) {
            Text("Turtle Rock")
                .font(.title)
            HStack {
                Text("Joshua Tree National Park")
                    .font(.subheadline)
                Spacer()
                Text("California")
                    .font(.subheadline)
            }
        }
        .padding()
    }
}
~~~

그림 위에 같은 모양의 도형을 overlay하는 것으로 테두리를 추가할 수 있음

원하는 Kit을 가져올 때는 import로 가져옴

State 속성으로 한 개 이상의 View에서 수정할 수 있는 앱 데이터에 대한 정보 소스를 설정한다

SwiftUI는 기본 저장소를 관리하고 값에 의존하는 뷰를 자동으로 업데이트해준다고 함

state 변수에 $를 붙이면 그 변수의 기본값을 참조하겠다는 뜻임

여기서는 지도를 사용했는데 사용자가 지도와 상호작용할 때, 

Map이 알아서 UI에 표시된 지도 부분과 일치하도록 지역값을 업데이트함

~~~
import SwiftUI
import MapKit

struct MapView: View {
    
    @State private var region = MKCoordinateRegion(
        center: CLLocationCoordinate2D(latitude: 34.011_286, longitude: -116.166_868),
        span: MKCoordinateSpan(latitudeDelta: 0.2, longitudeDelta: 0.2)
    )
    
    var body: some View {
        Map(coordinateRegion: $region)
    }
}

struct MapView_Previews: PreviewProvider {
    static var previews: some View {
        MapView()
    }
}
~~~

이때 구현된 Map을 보고 싶다면 미리보기를 정적모드가 아닌 라이브모드로 전환해야 함

Swrift에서 List는 identifiable한 데이터를 다뤄야 한다.

데이터를 그렇게 만드는 방법으로는 두가지가 있는데,

각 요소를 고유하게 식별하는 속성에 대한 키 경로를 데이터와 함께 전달하거나,

데이터 유형이 identifiable 프로토콜을 준수하도록 하면 된다.

후자의 경우 따로 List안에서 id를 명시하지 않아도 된다.

## 슬로우쿼리(slowquery)

예상시간보다 실행이 오래걸리는 쿼리.. 거의 말그대로의 의미였다.

## KVO

Key value Observing

특정 위치에 있는 값(value)를 observing, 감시한다.

그래서 해당 값이 바뀌면 observer가 값이 바뀌었다고 알려준다.

서버와 통신한다고 했을 때, 서버를 통해서 갔다오는 것이 시간이 걸리게 된다.

그래서 서버로 요청한 다음에 결과를 받는 변수에게 observer를 걸어두면 서버에서 결과값이 value에 채워질때 observer의 알림으로 알게 되는 것!

## KVC

Key Value Coding

특정 키에 맞추어서 키의 값을 가져오는 것을 말한다.

딕셔너리!
