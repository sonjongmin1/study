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

### 활용 예제1

```sql
select productname, productprice from exam3
where producttime > "2025-01-03"
order by  productprice asc limit 2
```

- limit 5, 10 로도 쓸수있다.
  - 5행까지 건너뛰고 6행부터 10행까지

### 활용 예제2

```sql
select employeename,employeepos,employdate,employmoney  from exam4
where employmoney >= 8000000
order by  employeepos asc
```

---

## `sql 함수`

### 합계 sum(필드명)

### 갯수 count(필드명)

### 평균 avg(필드명)

```sql
select avg(급여필드명) as 급여평균필드명 from 테이블명

-- 활용 예제
select sum(productprice) as productsum from exam3
```

- as 급여평균이라는 필드명 만들기

### Join

- 테이블 결합
- 모든 테이블을 조각 내서 사용하는 이유는 유저에게 데이터를 빠르게 제공하기 위함

```sql
select a.name, a.age, b.상품명, b.가격, c.부서 from tablea a
inner join tableb b on a.id = b.상품번호;
inner join tablec c on b.상품번호 = c.직원번호
-- a라는 테이블에 b라는 필드를 합침
-- on 뒤에는 조건
```

- 별명.가져올필드명 from 주축으로가져올필드 별명

### sql 순서 정리

```sql
select a.컬럼, b.컬럼1 avg(b.컬럼2) as 컬럼2평균 from tablea age
inner join tableb b on a.컬럼1 = b.컬럼1
where 조건
group by a.컬럼1 having 그룹조건
order by b.컬럼1 desc
limit 5
```

- 순서가 틀리면 에러 발생하므로 순서 주의하기

### group by

#### 활용예제

```sql
select product_name, sum(sales_amount) as totalsa from sales
group by product_name
having totalsa >= 820;
```
