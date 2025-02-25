# `Node`

- 자바스크립트만으로는 서버 연결을 못한다.
- `자바스크립트를 확장시켜 서버와 통신이 가능하게 해주는 환경이 Node.js이다.`

## `PHP(웹서버, 아파치, 워드프레스)`

- 워드프레스, 프론트부터 백엔드까지 한번에 지원해주는 시스템 (php만 지원)
  - 닷홈에서 빌릴 수 있다. (무료)
  - 지금은 Node가 대체하여 거의 사용하지않음

## `ASP(마이크로소프트 환경)`

- 지금은 Node가 대체하여 거의 사용하지않음

## `JSP(자바 서버 페이지) 자바(Tomcat, jBoss), 스프링부트`

- 자바언어로 서버를 연결시켜주는 기술이 JSP이다, Tomcat,jBoss가 쓰였지만 지금은 스프링부트가 자리잡았다.
- 자바는 금융기관, 대기업에서 주로 사용 (보안이 좋다), 나머지는 Node.js를 사용함
- 여러 회사중 톰켓을 이용하여 공부 예정, 톰켓은 프로그램 설치 실제로 움직이는 서버가 아님
- GCP는 톰캣 서버를 호스팅한다.
- 도커파일을 작성할 때 톰캣 이미지를 사용한다고 명시해야 한다.
  - `java + spring Boot + Oracle DB` (안정성 있는 DB 회사)
- Node.js : 대부분의 기업
  - `Node.js + Express.js(노드를 기반으로 노드를 쉽게 사용 할 수 있도록 도와주는 프로그램, 자바스크립트로 비유하면 제이쿼리) + DB(Mysql, PostgreSQL)`
- Python : AI / 머신러닝(기계에게 학습을 시켜 기계가 내가 원하는 답을 찾아줌)
  - `Python + Django`

# `Node 사용방법`

1. 노드설치
2. vscode > 폴더 > test01.js 파일 만들기

```js
// fs를 들고와달라고 require로 요청합니다.
const fs = require("fs");
// hello라는 utf8 방법으로 파일을 읽어주세요, err가 났을때 실제 data가 들어왔을때,  들고와주세요
fs.readFile("hello.js", "utf8", (err, data) => {
  if (err) {
    // 에러가 났을때, err은 실제 에러 출력
    console.error("파일을 읽지 못합니다.", err);
    // 리턴해서 나감
    return;
  }
  console.log(data);
});
```

### 터미널 명령어

```js
node test01.js
```

- 오류가 뜰텐데 hello.js 파일이 없기 때문이다.
- hello.js파일을 만들고 터미널 명령어를 입력하면 나온다.

```js
const fs = require("fs");
try {
  const data = fs.readFileSync("hello.txt", "utf8");
  console.log(data);
} catch (err) {
  console.error(err);
}
```

## 활용예제

```js
const { log } = require("console");
const fs = require("fs");
try {
  const data = fs.readFileSync("ko.txt", "utf8");
  const today = new Date();
  // 현재 표준시간형식으로 바꿈, 현재 날짜와 시간까지 같이 가져감
  // 날짜 나오고 T나오고 시간이 나옴
  const formatToday = today.toISOString().split("T")[0];
  console.log("현재날짜:", formatToday);
  console.log("애국가", data);
} catch (err) {
  console.error(err);
}
```

## express 설치

- node의 프레임워크이다.
- 노드를 사용하는 사람의 필수다.

### 터미널

```js
npm install express
```

- 주의사항

  - express는 반드시 한번더 실행시켜줘야 작동이 된다.

  ```js
  const express = require("express");
  const app = express();
  ```

- express를 최종적으로 실행시키는 명령어 app.listen(포트번호,()=>{})

```js
app.listen(3000, () => {
  console.log("서버가 http://localhost:3000 현재 실행중입니다.");
});
```

### 실행

```js
node test04.js
```

### curl 서버테스트가 잘 되었는지 실행하는 명령어

```js
node 파일명.js // 입력하여 먼저 실행
```

```js
curl -X get http://localhost:3000/users
```

- url 브라우저에 복붙해서 실행되는지 확인

### post방법

```js
curl -X POST http://localhost:3000/users -H "Content-Type: application/json" -d '{"name":"kim","age":25}'
```


