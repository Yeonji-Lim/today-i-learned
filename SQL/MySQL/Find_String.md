# 문자열이 포함되는지 여부 확인

## LOCATE

```SQL
LOCATE(substr, str)
```

str에 substr이 포함되어있는 위치를 반환한다.
인덱스가 0 초과이면 포함하고 있는 것

## INSTR
LOCATE와 인자 위치가 반대!

```SQL
INSTR(str, substr)
```

str에 substr이 포함되어있는 위치를 반환한다.
인덱스가 0 초과이면 포함하고 있는 것

## LIKE

```SQL
COLUMN_NAME LIKE substr
```

% 없이 사용하면 substr와 완전히 같은 행을 찾음

```SQL
COLUMN_NAME LIKE '단어' # '단어'와 일치하는 행을 찾음
COLUMN_NAME LIKE '단어%' # '단어'로 시작하는 행을 찾음
COLUMN_NAME LIKE '%단어' # '단어'로 끝나는 행을 찾음
COLUMN_NAME LIKE '%단어%' # '단어'를 포함하는 행을 찾음
```