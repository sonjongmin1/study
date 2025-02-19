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
	inDate date default "25-02-11",

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

### 활용예제2

```sql
CREATE TABLE 고객A (
    고객ID INT AUTO_INCREMENT PRIMARY KEY,
    고객이름 VARCHAR(50) NOT NULL,
    연락처 VARCHAR(20),
    이메일 VARCHAR(50) NOT NULL,
    가입일 TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
INSERT INTO 고객A (고객이름, 연락처, 이메일) VALUES
('홍길동', '010-1111-2222', 'hong@example.com'),
('이순신', '010-3333-4444', 'lee@example.com'),
('장보고', '010-5555-6666', 'jang@example.com'),
('김유신', '010-7777-8888', 'kim@example.com'),
('유재석', '010-9999-0000', 'you@example.com');

CREATE TABLE 제품B (
    제품번호 INT AUTO_INCREMENT PRIMARY KEY,
    제품명 VARCHAR(50) NOT NULL,
    단가 DECIMAL(10,2) NOT NULL,
    출시일 DATE NOT NULL
);
INSERT INTO 제품B (제품명, 단가, 출시일) VALUES
('노트북', 1500000.00, '2023-01-15'),
('스마트폰', 800000.00, '2023-02-20'),
('태블릿', 600000.00, '2023-03-10'),
('헤드폰', 120000.00, '2023-04-05'),
('스마트워치', 250000.00, '2023-05-01');
CREATE TABLE 주문C (
    주문번호 INT AUTO_INCREMENT PRIMARY KEY,
    고객ID INT NOT NULL,
    제품번호 INT NOT NULL,
    주문일 DATE NOT NULL,
    수량 INT NOT NULL,
    총금액 DECIMAL(10,2) NOT NULL,
    FOREIGN KEY (고객ID) REFERENCES 고객A(고객ID),
    FOREIGN KEY (제품번호) REFERENCES 제품B(제품번호)
);

INSERT INTO 주문C (고객ID, 제품번호, 주문일, 수량, 총금액) VALUES
(1, 1, '2023-06-01', 1, 1500000.00),
(2, 2, '2023-06-02', 2, 1600000.00),
(3, 3, '2023-06-03', 1, 600000.00),
(4, 4, '2023-06-04', 3, 360000.00),
(5, 5, '2023-06-05', 2, 500000.00);
```

### 활용예제2 답

```sql
select a.고객이름, a.가입일, b.제품명, b.단가 as 평균단가, c.주문일
from 고객A a
inner join 제품B b on a.고객ID = b.제품번호
inner join 주문C c on b.제품번호 = c.주문번호
where b.출시일 > "2023-01-15"
order by b.제품명 desc
limit 4;
```

### 활용예제3 답

```sql
select a.고객이름, a.이메일, b.제품명, max(b.단가) as 최대단가, c.주문일
from 고객A a
inner join 제품B b on a.고객ID = b.제품번호
inner join 주문C c on b.제품번호 = c.주문번호
where a.이메일 like "%example.com"
group by a.고객이름, a.이메일, b.제품명, c.주문번호
having 최대단가 >= 500000
order by a.고객이름 asc
limit 5
```

### update 테이블명 set 수정내용 where 조건

#### 활용예제1

```sql
update 고객A set 연락처 = "010-9999-9999" where 고객이름 = "유재석";
```

#### 활용예제2

```sql
update 제품B set 단가 = 단가 - 단가*0.05  where 단가 >= 500000;
```

### case when 조건 then 조건참 수정값 else 조건 거짓수정 end;

```sql
update 제품B set 단가 = case
when 출시일 < "2023-04-01" then 단가*0.95
else 단가 * 1.05
end
```

### set autocommit = 0;

### start transaction;

### commit;

### rollback;

### 뷰(view) : 가상테이블

- 자주쓰는 셀렉트를 하나의 이름으로 지어줘서 사용하는게 뷰이다.

```sql
 create view 뷰이름 as
 select 열1, 열2 from 테이블이름
 where 조건
--
 select * from 뷰이름;
 create view 고객상세뷰 as
 select 고객.이름, 제품.제품명, 주문.수량
 from 고객
 join 제품 on 고객.고객ID = 제품.제품번호
 join 주문 on 고객.고객ID = 주문.고객ID
```

#### 활용예제

```sql
create view 월별주 as
select
	date_format(주문일, "%y-%m") as 주문월,
	count(*) as 주문건수,
	sum(총금액) as 월총금액
	from 주문
	group by 주문월

select * from 월별주
```

### date_format(필드명(날짜), "%m - %d") as 날짜다

---

# `연습예제`

```sql
CREATE TABLE 고객 (
    고객ID INT AUTO_INCREMENT PRIMARY KEY,
    고객이름 VARCHAR(50),
    연락처 VARCHAR(20),
    가입일 DATE
);

CREATE TABLE 제품 (
    제품번호 INT AUTO_INCREMENT PRIMARY KEY,
    제품명 VARCHAR(100),
    단가 DECIMAL(10,2),
    출시일 DATE
);

CREATE TABLE 주문 (
    주문ID INT AUTO_INCREMENT PRIMARY KEY,
    고객ID INT,
    제품번호 INT,
    주문일 DATE,
    수량 INT,
    총금액 DECIMAL(10,2)
);
```

```sql
INSERT INTO 고객 (고객이름, 연락처, 가입일) VALUES
('김철수', '010-1111-1111', '2023-01-10'),
('이영희', '010-2222-2222', '2023-02-15'),
('유재석', '010-3333-3333', '2023-03-20'),
('박명수', '010-4444-4444', '2023-04-25'),
('홍길동', '010-5555-5555', '2023-05-30'),
('강호동', '010-6666-6666', '2023-06-05'),
('신동엽', '010-7777-7777', '2023-07-10'),
('정형돈', '010-8888-8888', '2023-08-15'),
('하하',    '010-9999-9999', '2023-09-20'),
('조세호', '010-1010-1010', '2023-10-25');
```

### concat

```sql
update 고객
set 고객이름 = concat(고객이름, "_vip")
where 연락처 like "010-7777%"
```

```sql
INSERT INTO 제품 (제품명, 단가, 출시일) VALUES
('제품A', 100.00, '2023-03-01'),
('제품B', 200.00, '2023-04-15'),
('제품C', 300.00, '2023-02-20'),
('제품D', 400.00, '2023-05-05'),
('제품E', 500.00, '2023-01-10'),
('제품F', 600.00, '2023-06-15'),
('제품G', 700.00, '2023-03-30'),
('제품H', 800.00, '2023-07-20'),
('제품I', 900.00, '2023-02-05'),
('제품J', 1000.00, '2023-08-25');
```

```sql
INSERT INTO 주문 (고객ID, 제품번호, 주문일, 수량, 총금액) VALUES
(1, 1, '2023-03-05', 2, 0),
(2, 2, '2023-04-20', 5, 0),
(3, 3, '2023-03-25', 6, 0),
(4, 4, '2023-05-10', 3, 0),
(5, 5, '2023-06-15', 7, 0),
(6, 6, '2023-07-20', 1, 0),
(7, 7, '2023-04-10', 8, 0),
(8, 8, '2023-08-05', 4, 0),
(9, 9, '2023-02-15', 9, 0),
(10, 10, '2023-09-10', 2, 0);
```

### 예제1.

- 예제 1: 고객 테이블의 연락처 업데이트
- 고객이름이 '유재석'인 고객의 연락처를 '010-1234-5678'로 변경

### 예제2.

- 예제 2: 제품 테이블의 단가 업데이트 (특정 고객 주문 관련)
- 고객ID가 5번인 고객이 주문한 제품의 단가를 5% 할인 적용

### 예제3.

- 예제 3: 주문 테이블의 총금액 업데이트 (특정 주문일 범위 할인)
- 주문일이 2023년 4월인 주문에 대해, 총금액을 제품의 단가 _ 수량 _ 0.9 (10% 할인)로 계산

### 예제4.

- 예제 4: 고객 테이블의 가입일 업데이트 (주문일 조건)
- 고객이 한 주문 중 최소 주문일이 2023-03-01 이전인 경우, 가입일을 '2023-03-01'로 수정

### 예제5.

- 예제 5: 주문 테이블의 수량 업데이트 (CASE 문 사용)
- 주문 수량이 3 미만이면 수량을 1 증가, 3 이상이면 1 감소

### 예제6.

- 예제 6: 유재석 고객의 모든 주문 수량 2증가

### 예제7.

- 예제 7: 제품 테이블의 단가 업데이트 (출시일 조건)
- 출시일이 '2023-04-01' 이전인 제품은 단가에 5% 추가 할인 적용

### 예제8.

- 예제 8: 제품 테이블의 단가에 고정 금액 추가
- 출시일이 '2023-06-01' 이후인 제품의 단가에 50원 추가

### 예제9.

- 예제 9: 고객 테이블의 고객이름 업데이트 (특정 연락처 조건)
- 연락처가 '010-5555'로 시작하는 고객의 이름 뒤에 '\_VIP' 접미어 추가
