# ORDER BY

```sql
SELECT college, region, seed FROM tournament
ORDER BY region, seed;

SELECT college, region AS r, seed AS s FROM tournament
ORDER BY r, s;
```

컬럼 이름과 alias를 사용하여 ORDER BY와 GROUP BY절을 작성할 수 있다.

역방향으로 정렬하기 위해서는 정렬하려는 ORDER BY 절 안의 컬럼 이름을 위한 _DESC 키워드_ 를 추가해야 한다.
_기본 값을 ascending 순서_ 이며 ASC 키워드를 사용하여 명시적으로 지정할 수 있다.
