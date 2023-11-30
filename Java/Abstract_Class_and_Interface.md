추상 클래스는 클래스들 간에 공통된 구현을 가지며, 인터페이스는 클래스들이 특정 동작을 갖도록 규약을 정의합니다. 추상 클래스는 단일 상속을 지원하고 인스턴스화될 수 있지만, 인터페이스는 다중 상속을 지원하고 인스턴스화될 수 없습니다.

1. 추상 클래스는 일반 클래스와 마찬가지로 필드, 일반 메소드, 추상 메소드를 가질 수 있습니다. 반면에 인터페이스는 추상 메소드와 상수(constant)만을 가질 수 있습니다. 필드와 일반 메소드는 인터페이스에서 정의할 수 없습니다.
    
2. 클래스는 다중 상속이 불가능하지만, 인터페이스는 다중 상속이 가능합니다. 클래스는 하나의 클래스만 상속받을 수 있지만, 인터페이스는 여러 개를 구현할 수 있습니다. 이는 자바에서 다중 상속을 지원하지 않는 대신, 인터페이스를 통해 다중 상속의 장점을 활용할 수 있도록 합니다.
    
3. 추상 클래스는 일반적으로 공통된 동작을 가진 클래스들의 상위 클래스로 사용됩니다. 즉, 추상 클래스는 일부 구현을 가지며, 하위 클래스에서 나머지 구현을 완성해야 합니다. 반면에 인터페이스는 클래스들이 특정 동작을 갖도록 규약을 정의하는 역할을 합니다. 클래스는 인터페이스를 구현하여 해당 동작을 갖게 됩니다.
    
4. 추상 클래스는 인스턴스화될 수 있지만, 인터페이스는 인스턴스화될 수 없습니다. 추상 클래스는 자체적으로 객체를 생성할 수 있지만, 인터페이스는 단순히 동작을 정의하기 때문에 객체를 직접 생성할 수 없습니다.