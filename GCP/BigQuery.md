# 빅쿼리

## 함수 및 연산자

### 비교

- 정렬을 위해서 NULL, NaN은 유효한 숫자(-inf 포함)보다 작은 값으로 평가됨
- NaN > NULL로 평가되지만, NaN과의 비교는 false를 반환, NULL과의 비교는 NULL을 반환함.

### 형변환

- 명시적 타입 변환(캐스팅) : 명시적으로 데이터 타입 변환. CAST() 함수를 사용해 형변환
    - 캐스팅이 실패하면 오류를 반환하는데, SAFE_CAST를 사용하면 오류 대신 NULL을 반환함

```sql
SELECT CAST("true" AS bool), SAFE_CAST("invalid" AS bool)
```

- 타입 강제(coercion): 암시적 형변환.
    - 사용하는 데이터타입과 필요한 데이터 타입이 다르면 자동으로 타입 강제가 이뤄짐.
    - 예를 들어 FLOAT64가 필요한데 INT64를 사용하면 정수가 강제로 float로 변환됨.
    - 빅쿼리에서는 INT64 → FLOAT64 / NUMERIC, NUMERIC → FLOAT64 형변환만 강제로 이뤄지며 다른 변환은 모두 명시적 변환을 해줘야 함.

```sql
with example as (
	select 'John' as employee, 'Paternity Leave' as hours_worked
	union all select 'Janaki', '35'
	union all select 'Jian' , 'Vacation'
	union all select 'Jose' , '40'
)
select sum(safe_cast(hours_worked as int64)) from example
;
```

## 문자열 함수

- 주요 함수

```sql
with example as (
	select * from unnest([ 'Seattle', 'New York', 'Singapore']) as city
)
select city
	, length(city) as len -- 문자열 크기
	, lower(city) as lower -- 소문자화
	, strpos(city, 'or') as orpos -- 쿼리 문자열의 위치 반환
from example
;
```

- substr : 위치를 기준으로 문자열 추출
- concat : 문자열 연결

```sql
with example as (
	select 'armin@abc.com' as email, 'Anapolis, MD' as city
	union all select 'boyan@bca.com', 'Boulder, CO'
	union all select 'carri@cab.com', 'Chicago, IL'
)
select 
	concat(
		substr(email, 1, strpos(email, '@') -1), --username
		' from ', city) as callers
from example
;
```

### 로컬에서 데이터 업로드하기

- 데이터셋 생성하기

```bash
bq mk ch04 
```

- 데이터 로드하기

```bash
bq load -null_marker=NULL --source_format=CSV --autodetect ch04.college_scorecard/college_scorecard.csv.gz
```

- 테이블 스키마 확인하기

```bash
bq show --format prettyjson --schema ch04.college_scorecard
```

- 테이블 삭제하기

```bash
bq rm ch04.college_scorecard
bq rm -r -f ch04 <- 재귀적으로(-r) 경고없이(-f) 테이블 제거
```

- SQL로도 테이블 삭제 가능

```bash
DROP TABLE IF EXISTS ch04.college_scorecard_gcs
```

- 테이블 복제

```bash
bq cp ch04.college_scorecard someds.college_scorecard_copy
```