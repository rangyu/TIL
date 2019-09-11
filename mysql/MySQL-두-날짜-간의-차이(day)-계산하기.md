# MySQL 두 날짜 간의 차이 계산하기 (DATEDIFF, TIMESTAMPDIFF)

그냥 (-)했더니 안되더라. 알고보니 날짜 계산할 때는 함수를 써야 했다.

## DATEDIFF
날짜간 일수 차이(day)를 계산할 때 사용한다.

```
DATEDIFF(날짜1, 날짜2);
```
위의 경우, 날짜1 - 날짜2 값이 계산된다.

## TIMESTAMPDIFF
원하는 단위를 지정해서 날짜간 차이 값을 구할 수 있다.

```
TIMESTAMPDIFF(단위, 날짜1, 날짜2);
```

### 단위
```
- SECOND : 초
- MINUTE : 분
- HOUR : 시
- DAY : 일
- WEEK : 주
- MONTH : 월
- QUARTER : 분기
- YEAR : 연
```

단위를 써서 사용하면 다음과 같다.

```
TIMESTAMPDIFF(SECOND, '2019-09-11, '2019-09-01');
```
