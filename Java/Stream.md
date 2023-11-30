> '데이터의 흐름'

# Stream API
다양한 데이터를 표준화된 방법으로 다루기 위한 라이브러리

[Java8](Java8.md)에 추가됨.

[람다](Lambda)를 활용할 수 있는 기술

```java
example.stream().filter(x -> x < 2).count
```

- stream() : 스트림 생성
- filter : 중간 연산(스트림 변환), 연속 수행 가능
- count : 최종 연산, 마지막에 단 한번 사용 가능

## 특징
- 데이터를 변경하지 않음
- 1회용
- 배열과 컬렉션을 함수형으로 처리할 수 있다.
- 지연 연산을 수행 (람다)
- 병렬 실행 가능 (람다)

## 종류
![](https://i.imgur.com/GcimZGv.png)

## 중간 연산(가공하기)
![](https://i.imgur.com/D6Hq5Om.png)

## 최종 연산(결과만들기)
![](https://i.imgur.com/c4tu9KJ.png)

![](https://i.imgur.com/kHTtj7S.png)

# 참고
https://khj93.tistory.com/entry/JAVA-%EB%9E%8C%EB%8B%A4%EC%8B%9DRambda%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B4%EA%B3%A0-%EC%82%AC%EC%9A%A9%EB%B2%95

https://futurecreator.github.io/2018/08/26/java-8-streams/