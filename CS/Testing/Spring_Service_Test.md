# Service 테스트 방법
실제 로직을 처리하는 Service는 다양한 테스트 기법이 필요하다.

## Verify
의존하고 있는 Mock이 해당되는 동작을 수행했는지 확인하는 검증

```java
verify(accountRepository, times(1)).save(any<Account>());
verify(accountRepository, times(0)).findById(anyLong());
```

## ArgumentCaptor
의존하고 있는 Mock에 전달된 데이터가 내가 의도하는 데이터가 맞는지 검증

```java
ArgumentCaptor<Account> captor = ArgumentCaptor.forClass(Account.class);
verify(accountRepository, times(1)).save(captor.capture());
assertEquals("1234", captor.getValue().getAccountNumber());
```

## assertions
assert가 붙는 방법들

```java
assertEquals("1234", captor.getValue().getAccountNumber());
assertNotEquals("1234", captor.getValue().getAccountNumber());
assertNull(result);
assertNotNull(result);

assertTrue(resut.getBoolean());
assertFalse(resut.getBoolean());
assertAll(

    () -> assertTrue(resut.getBoolean()),

    () -> assertFalse(resut.getBoolean())
);
```

## assertThrows
예외를 던지는 로직을 테스트
```java
AccountException exception =
                assertThrows(AccountException.class, () ->

                    accountService.getAccount(123L));
assertEquals(ACCOUNT_NOT_FOUND, exception.getErrorCode());
```