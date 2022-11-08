# AssertJ
많은 assertion을 제공하는 자바 라이브러리

에러 메시지와 테스트 코드의 가독성을 높여준다.

Junit에서 제공하는 assertEquals에 비해 가독성이 올라간다.

둘의 코드의 차이는 다음과 같다.

```java
//Junit
assertEquals(expected, actual); 

//AssertJ
assertThat(actual).isEqualTo(expected);
```

AssertJ가 조금더 가독성이 좋다는 것을 확인할 수 있다.

## Assertion description (Assertion 설명)
assertion이 수행될 때 상황을 설명할 수 있다. 

as라는 메서드로 지정할 수 있다.

주의할 점은 assertion이 수행되기 전에 작성되어야 한다는 것.

```java
// Bad: assertion 이후의 as는 작동하지 않는다.
assertThat(actual).isEqualTo(expected).as("description");

// Good: as를 assertion 이전에 넣는다.
assertThat(actual).as("description").isEqualTo(expected);
```

## Filtering assertions - iterables나 arrays에 적용되는 filtering

특정 필터를 자바 람다식을 이용하여 표현할 수 있다.
자바의 stream과 그 사용법이 거의 같다.

```java
@Test
void filter_test() {
	List<Post> list = new ArrayList<>();
	Post p1 = new Post("this is title", "this is content");
	Post p2 = new Post("Awesome Title", "Awesome content");
	Post p3 = new Psot("Notice", "This is board");
	
	list.add(p1);
	list.add(p2);
	list.add(p3);
	
	assertThat(list).filteredOn(post -> post.getContent().contains("is")).containsOnly(p1);
}
```
위의 예제는 Post.content에 "is"가 들어가는 객체들만 필터링한다음에 p1 객체가 있는지 검사한다. 

여기서 `containsOnly`는 원소의 순서, 중복 여부 관계 없이 값만 일치하는지 검증한다.

`contains`와 다른점은 원소의 갯수가지 정확히 일치해야 한다는 점이다.

그래서 위의 예시는 테스트를 실행시키면 실패하지만, `contains`를 사용하면 성공한다.

`containsExactly`도 있는데 이는 순서까지 모두 정확하게 일치해야한다. 

## BDD 스타일
BDD 스타일은 given, when, then으로 이루어진 스타일을 말한다.

## Exception 처리 test
