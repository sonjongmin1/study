# `선언문 기초`

- var
- let 변수
- const 상수
  <br>
  <br>

# `변수 선언 규칙`

- 첫글자 숫자X, 띄어쓰기X
- 카멜 표기법 다음 첫글자는 대문자 ex) let numBox
- 파스칼 표기법 첫글자 대문자, js는 내장함수의 첫글자가 대문자이므로 선호하지 않음. ex) let NumBox
- 언더스코어 표기법 ex) num_box
  <br>
  <br>

# `데이터 타입`

```js
// 숫자
let num1 = 10;
// 문자 ""
let num2 = "10";
// 참 거짓을 표현 하는 변수의 앞에 is를 넣는다.
let isTrue = true;
// 0이 아닌 모든것이 참
let temp = Boolean(num2);
// 출력 true
document.write(temp);
// 값의 타입을 묻는 함수, 데이터를 들고 올때 타입을 물을때가 많음
// 출력 number
document.write(typeof num1);
document.write("나는" + num1 + "입니다.");
// 템플릿리터럴, 백틱
document.write(`나는 ${num1}입니다.`);
let num3 = null;
document.write(`${num3}`);
```

  <br>
  <br>

# `연산자`

1. +, -, \*, /, % 산술연산자
2. 증감연산자
3. 비교연산자
4. 논리연산자

### 증감연산자

```js
let number = 10;
let number1 = 10;
// 증가 먼저
let result = ++number;
// 넘겨주는거 먼저
let result1 = number1++;
// 11, 11
document.write(number, result);
// 11, 10
document.write(number1, result1);
```

### 비교연산자

```js
let num1 = 10;
let num2 = "10";
// false
document.write(`${num1 > num2}<br>`);
// true
document.write(`${num1 >= num2}<br>`);
// false === 값을 타입까지 고려해서 비교
document.write(`${num1 === num2}<br>`);
// true
document.write(`${num1 !== num2}<br>`);
// 비교연산자는 왼쪽부터 운선순위를 가진다.
```

### 논리연산자

```js
let a = 2 < 3; // true
let b = 30 > 50; // false
let c = 20 < 30; // true
// && and
document.write(a && b); // false, 두 값 모두 true 이어야 true
document.write(a && b && c); // false, a와 b가 false c는 true이므로 false
document.write(!(a && b) && c); // true, a와 b가 true c는 true이므로 true
// || or
document.write(a || b); // true, 둘 중 하나만 true 이어야 true
```

<br>
<br>

### 제어문이란 프로그램에서 결과값을 도출하기 위해 순서를 제어하거나, 반복

### 제어문의 종류 조건문(if,switch), 반복문, 중단(break), 건너뛰기(continue)

### 반복문 (for, while, do-while)

<br>
<br>

# `조건문`

#### if, switch, 삼항연산자

<br>
<br>

# `반복문`

### for, while, do-while

while 문<br>
while (조건식){<br>
실행문;<br>
증가감식;<br>
}

# `while, do-while`

```js
let num1 = 10;
let num2 = 10;
let sum = 0;
let sum1 = 0;

while (num1 < 20) {
  num1++;
  sum += num1;
}

//무한루프 break로 탈출 while은 조건이 false일때 탈출
while(){
    if(num1 == 10){
        break;
    }
}

//무한루프 break로 탈출
while(true){
    if(num1 == 10){
        break;
    }
}

// 한번은 무조건 실행
do {
  num2++;
} while (num1 < 9);

document.write(num2);
```

<br>
<br>

# `for문`

```js
let i;
for (let i = 0; i < 5; i++) {
  let str = "";
  for (let j = 1; j < i; j++) {
    str += "*";
  }
}
```

# 별찍기

```js
document.write(".");
for (let i = 0; i < 10; i++) {
  document.write(i);
}

document.write("<br>");
for (let i = 0; i < 10; i++) {
  document.write(i);
  for (let j = 0; j < 10; j++) {
    if (i + j == 9) {
      document.write("*");
    } else {
      document.write("-");
    }
  }
  document.write("<br>");
}
```

# `배열`

```js
let arr = ["a", "b", "c", "d"];
// 뒤 push
arr.push("d");
// 앞 unshift
arr.unshift("a");
// pop 뒤에서 빼기
arr.pop();
// shift 앞에서 빼기
arr.shift();

// 자르기
let arr2 = arr.slice(0, 1);
// splice(인덱스번호, 제거갯수, 추가할데이터)
// sort() 오름차순 정렬, reverse() 내림차순, 정렬 유니코드가 가지고 있는 숫자의 순서대로 오름차순 정렬 특수문자 > 숫자 > 대문자 > 소문자
// includes("") 배열에 포함되어 있는지 확인
```

```js
let arr = ["apple", "banana", "orange"];
// 배열을 복사 할 때는 ... 스프레드 연산자(전개 연산자:안에 있는 배열을 펼쳐 놓는다.)를 사용한다.
let arr2 = [...arr];
arr2.push("grape");
document.write(arr2);
```
