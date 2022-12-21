# Paging

사용자가 어떠한 데이터를 필요로 할 때, 전체 데이터 중의 일부를 보여주는 방식

게시판에서 글이 많으면 다음 페이지로 넘어가는 바로 그것
    
## Spring에서 Paging 처리
#추가공부필요

-   페이징을 담당할 PagingVO를 만든다 (util)
	-   보여지는 시작과 끝 페이지, 제일 마지막 페이지를 계산하는 메소드
	-   DB 쿼리에서 사용할 start, end 값 계산 메소드
-   게시판 Mapper에 페이징 처리하는 쿼리를 게시글 조회에 넣는다. BoardMapper.xml
-   해당 Mapper, Service, Controller에 메소드들을 생성해 연결

https://po9357.github.io/spring/2019-05-28-Board_Paging/
