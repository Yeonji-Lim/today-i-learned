Controller가 직접적으로 API 와 맞닿아 있다. 로직은 Service에서 구현

# Repository

`JpaRepository<Entity, Long>` 을 상속 받으면 기본적인 CRUD가 생성된다. 

## JPA 처리를 담당하는 Repository 종류

1) Repository<T, ID>  
2) CrudRepository<T, ID>  
3) PagingAndSortingRepository<T, ID>  
4) JpaRepository<T, ID>

T : Entity의 타입클래스, ID : P.K 값의 Type

