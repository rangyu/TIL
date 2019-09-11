# MySQL 델타값(변동량) 구하기 쿼리

INNER JOIN을 사용해서 델타값을 구했다.

다음은 wdate(작성일) 기준으로 매일의 count 변동량(diff)을 구하는 쿼리이다.


```sql
SELECT *, o.`count` - p.`p_count` as diff FROM `tablename` as o 
INNER JOIN (SELECT `count` as p_count, `wdate` as p_wdate FROM `tablename`) as p 
ON DATE(DATE_SUB(o.`wdate`, INTERVAL 1 DAY)) = DATE(p.`p_wdate`) 
ORDER BY `wdate` desc
```

