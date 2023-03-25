# 함수 종속성 Functional Dependency
어떤 속성 A의 값을 알면 다른 속성 B의 값이 유일하게 정해지는 관계

## 표기
`A -> B` 
A는 B의 결정자 (Determinant)
A는 B를 결정한다.(Determine)
B는 A에 종속한다.(Dependent)

## FD Diagram

릴레이션의 속성은 직사각형으로 표현하고
화살표로 속성간의 함수 종속성을 표현하며,
복합속성의 경우 직사각형으로 묶는다.

![](https://i.imgur.com/TCR1IJj.png)

학생 번호는 학생이름, 학과, 주소를 결정한다.
학생 번호와 강좌 이름은 성적을 결정한다.