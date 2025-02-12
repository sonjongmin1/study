# `SQL 문법`

## Create 테이블 생성 (행 row, 열 column)

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
	inDate date default "25-02-11"
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

select * from testb;
```

- 필드명에 at 붙으면 자동증가라고 보면 된다.

## INSERT

```sql
insert into testa(Name,Salary, inDate) values
("lee",5000.00, "2023-1-11");
```

- 자료 insert

```sql
insert into testa(Name,Salary, inDate) values
("son1",6000.00, default),("son2",6000.00, default);
```

- 자료 한번에 insert

### 활용예제3

```sql
insert into testb(pname, price, dateat) values
("tablet", 500.00, default);

insert into testb(pname, price, dateat) values
("monitor", 3000.00, default);

insert into testb(pname, price) values
("keyboard", 2000.00),("mouse", 1000.00);

select * from testb;
```

## Delete

```sql
delete from 테이블명 where 조건;

-- 예시
delete from testb where (price >= 5000);
```

## Delete, Where 활용

```sql
delete from testa where (Name like "k%");
```

- Name 컬럼명에서 첫글자가 k인 행들 모두 삭제

### Alter

```sql
alter table 테이블명 drop column 컬럼이름;
```

- 특정 컬럼을 테이블에서 삭제합니다.

### Drop

```sql
drop table 테이블명;
```

- 테이블그자체를 삭제
- delete는 테이블 구조는 유지하고 데이터를 삭제

### Order by 정렬방식, limit (5줄만 나오도록 제한)

#### desc 내림차순 <br>asc 오름차순

```sql
Order by desc limit 2
-- 내림 차순으로 두번째가지만 나타나라
```

- 주의사항 : 명령어 정해진 위치를 준수해야한다.
