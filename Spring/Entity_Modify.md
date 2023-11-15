#작성필요 

참고 : https://velog.io/@koo8624/Spring-%EB%B3%80%EA%B2%BD-%EA%B0%90%EC%A7%80%EB%A5%BC-%ED%99%9C%EC%9A%A9%ED%95%9C-Entity-%EC%88%98%EC%A0%95

영속 상태의 `Entity`는 `Dirty Check`로 수정이 가능하다. 

사용자가 폼 정보를 기반으로 새로운 `Entity` 객체를 생성하면 해당 객체는 준영속 상태에 해당하여 `Dirty Check`가 수행되지 않는다.

이럴 때는 `EntityManager`에서 `find()`나 `createQuery()`를 호출하여 영속 상태의 객체를 불러와 데이터를 수정하거나, 해당 `Entity`를 `merge`하여 영속 상태로 변경하여 `Dirty Check`가 작동하도록 해야한다.