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

### Limit 출력 제한

`LIMIT num`을 통해서 출력 수를 제한할 수 있음

```sql
SELECT *
FROM employees
LIMIT 100
```

sql workbench 자체적으로 limit이 걸려있음

### GROUP BY

같은 CountryCode를 가진 애들 중 Population이 가장 큰 것을 보여줌
이때 AS는 별칭을 바꾸는 역할

```sql
SELECT CountryCode, MAX(Population) AS 'max'
FROM city
GROUP BY CountryCode
```

`MAX()` 외에도 많은 집계함수 (Aggregate Function)들이 있음

```
AVG() : 평균
MIN() : 최소값
MAX() : 최대값
COUNT() : 행의 개수
COUNT(DISTINCT) : 중복 제외된 행의 개수
STDEV() : 표준편차
VARIANCE() : 분산
```

### DATE_FORMAT

날짜 입력에 대해서 형식을 지정해줌
```sql
SELECT data_format(date, '%Y-%m-%d')
```

```sql
SELECT data_format(date, 'YYYY-mm-dddd')
```

주의점 

```sql
SELECT data_format(date, '%Y-%M-%D')
```
이때 `%M`은 영어로 3월은 March와 같이 영어로 출력됨
`%D`는 뒤에 st, rd, th같은 기수로 출력됨

### CASE WHEN

```sql
CASE
  WHEN 조건1 THEN 조건1이 참일시 수행
  WHEN 조건2 THEN 조건2가 참일시 수행
  ELSE 나머지 
END
```

### 그외 프로그래머스 풀면서 느낀 TIPS

1. SELECT에 숫자가 들어간 문자열을 쓰는 경우 `'5123어쩌구'`로 처리했는데 틀린 경우가 있음
  이 경우에는 ``5123어쩌구``로 하면 통과됨
2. 문제 조건에 ORDER가 주어졌고 답안도 순서대로 나오지만 틀린 경우
  ORDER BY로 따로 써줘야 정답처리 되는 경우가 있었음
3. ~

