# MySQL 만약 키 값이 있으면 UPDATE 없으면 INSERT 하기

만약 키 값이 있으면 UPDATE문을 수정하고 없으면 INSERT문을 수행하길 원한다면 `INSERT ON DUPLICATE KEY UPDATE` 쿼리를 사용하면 된다. 

```sql
INSERT INTO `tablename` (`column1`, `column2`, `column3`) 
VALUES ('value1', 'value2', 'value3')  
ON DUPLICATE KEY UPDATE `column1`='value1', `column2`='value2', `column3`='value3';
```

위 쿼리를 사용하면 중복된 키 값이 있을 경우 UPDATE문을 없으면 INSERT문을 수행한다.

(이때 꼭 칼럼들 중 하나는 유니크한 키 값을 지니고 있어야 한다)
