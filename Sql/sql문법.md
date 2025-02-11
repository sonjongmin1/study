# `SQL 문법`

### 테이블 생성 (행 row, 열 column)

```sql
create table 테이블이름(컬럼1 데이터타입 [제약조건],
    컬럼1 데이터타입 [제약조건]
);

-- 예시
create table ta(
    name varchar(50),
    city varchar(50)
);

```

### 데이터 타입

- 정수 int
- 실수 decimal(10,2) 소수포함 열자리 EX) 12345678.12
- 문자 varchar
- 날짜 date
- 날짜와 시간 timestamp

### 제약조건

- primary key : 기본키(식별자), 각 행을 유일하게 식별

### 식별

- not null : 반드시 값이 있어야한다.
- unique : 중복된 값이 없도록 보장
- default : 기본값
- auto_increment : 자동 증가

### 활용 예제1

```sql
create table testa(
	ID int auto_increment primary key,
	Name varchar(50) not null,
	Salary decimal(10,2) default 0.00,
	inDate date dafault "25-02-11"
);

select * from testa

```

### 활용 예제2

```sql
create table testb(
	pid int auto_increment primary key,
	pname varchar(100) unique not null,
	price decimal(8,2) default 0.00,
	dateat timestamp default CURRENT_TIMESTAMP
);

select * from testb
```

- 필드명에 at 붙으면 자동증가라고 보면 된다.
