사용자가 어떠한 데이터를 필요로 할 때, 전체 데이터 중의 일부를 보여주는 방식

```
게시판에서 글이 많으면 다음 페이지로 넘어가는 바로 그것

인스타 무한 스크롤
```

-   Spring에서 Paging 처리
	
	-   페이징을 담당할 PagingVO를 만든다 (util)
		-   보여지는 시작과 끝 페이지, 제일 마지막 페이지를 계산하는 메소드
		-   DB 쿼리에서 사용할 start, end 값 계산 메소드
	-   게시판 Mapper에 페이징 처리하는 쿼리를 게시글 조회에 넣는다. BoardMapper.xml
	-   해당 Mapper, Service, Controller에 메소드들을 생성해 연결

참고 링크

[[Spring] 스프링 게시판 만들기 - 페이징(Paging) 처리하기](https://po9357.github.io/spring/2019-05-28-Board_Paging/)

10개씩 끊고 싶을 때 쿼리

```sql
select * from [table] orders limit 10;
```

-   limit 구문
	
	숫자를 두 개 쓸 수 있다. offset, number
	
	```sql
select * from [table] orders limit 10 offset 0;
select * from [table] orders limit 10 offset 10;
	```
	
	차례로 1페이지, 2페이지 조회
	

**주의!** 그런데 그냥 이렇게 하면 새로운 게시글이 빨리올라오는 서비스의 경우

페이지를 넘겨도 계속 같은 글을 보게될 수 있다. 앞에서 계속 추가되기 때문
맨 처음 스크롤 했을 때 마지막 인덱스를 기준으로 다음 것을 보여주면 된다!