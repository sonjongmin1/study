# `Node.js_MySQL2 연결 설정`

```js
// 터미널 명령어로 설치
// 순서1. npm install express
// 순서2. npm install mysql2  (mysql2는 db동할수있는 node지원 프로그램)
const express = require("express");
const app = express();

const mysql = require("mysql2");

app.use(express.json());

// 연결 설정, 데이터베이스 환경 설정
const db = mysql.createConnection({
  // 공개 ip 주소
  host: "공개아이피주소",
  user: "root(설정한 유저 이름)",
  password: "비밀번호",
  database: "root(설정한 데이터베이스 이름)",
});

// 실제로 연결 시키는것 노드에서 지원, 모든 환경설정은 db가 가지고있다.
// err 연결 시켰을때 에러나면 에러처리
db.connect((err) => {
  if (err) {
    console.error("mysql 연결 실패", err);
    return;
  }
  console.log("mysql 연결 성공");
});

// 터미널 명령어 node test01.js 입력
// 대부분의 테스트 번호는 3000, <- 에러 발생하면 4000 또는 5000 으로 사용
// express는 app이라는 친구가 가지고 있음
// app.listen <- app에서 실행을 시키기, 포트번호 3000번에 연결시키기

// 요청과 응답, get 보여주는 역할, get은 sql문에서 select만 사용 할 수 있다.
app.get("/users", (req, res) => {
  // 데이터베이스 명령어 통칭, 쿼리라고한다.
  // 큰수를 제일 위로 desc(내림차순), ex) 방명록
  const sql = "select * from userinfo order by id desc";
  // db.query(sql명령문,(err,results)=>{})
  db.query(sql, (err, results) => {
    if (err) {
      console.err("데이터 조회중(셀렉트중) 에러가 났습니다.");
    }
    res.json(results);
  });
});

app.listen(3000, () => {
  console.log("서버가 연결되었습니다. http://localhost:3000");
});
```
