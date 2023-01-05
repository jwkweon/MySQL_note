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
