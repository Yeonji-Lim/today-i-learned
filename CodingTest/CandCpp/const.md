# 변수

## const 비-멤버 변수

변할 수 없는 상수

```cpp
const int num = 1; // 일반적인 표현
int const num = 1; // 위와 같은 의미
 
num = 2;           // Compile Error
```

함수의 반환형, 매개 변수에 쓰일 때도 동일 의미

[매직 넘버](Magic_Number.md)를 사용하고자 할 때 const 변수를 사용하기도 함

## const 멤버 변수
선언시 초기화 해야함

```cpp
class Foo {
	const int num; // 메모리 할당이 아님
 
	Foo(void)
		: num(1) // const int num = 1;
	{
	}
};
 
class Bar {
	const int num;
 
	Bar(void) {
		num = 1; // Compile Error
		// const int num;
		// num = 1;
	}
};
```

## const 포인터 변수
#작성필요 https://easycoding91.tistory.com/entry/C-%EA%B0%95%EC%A2%8C-const-%EC%9C%84%EC%B9%98%EC%9D%98-%EC%9D%98%EB%AF%B8%EC%99%80-%EC%82%AC%EC%9A%A9-%EB%B0%A9%EB%B2%95