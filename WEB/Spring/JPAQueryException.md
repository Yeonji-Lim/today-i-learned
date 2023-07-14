Exception has occurred.: Expecting a SELECT query : `update Project p set p.title = :title where p.id = :id`

```
@Transactional  
@Modifying
@Query("update Project p set p.title = :title where p.id = :id")  
int updateTitle(@Param("id") Long id, @Param("title") String title);
```

이렇게 하면 해결