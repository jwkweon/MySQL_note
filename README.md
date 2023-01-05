# MySQL_note

### 서브 쿼리

쿼리문 안에 또 쿼리문이 들어있는 것
| 서브쿼리의 결과가 둘 이상이 되면 에러!

```sql
SELECT *
FROM city
WHERE ContryCode = ( SELECT ContryCode
                     FROM city
                     WHERE Name = seoul );

```

### Order By

결과 출력 순서 조절 구문
`DESC`는 내림차순 정렬
`ASC`는 오름차순 정렬 (default이므로 생략 가능)


```sql
SELECT *
FROM city
ORDER BY Population DESC

```

### 중복 제거

SELECT 뒤에 DISTINCT를 쓰면 중복된 것들을 제거할 수 

```sql
SELECT DISTINCT last_name
FROM employees
ORDER BY last_name
```
