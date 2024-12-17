# `JSON 활용`

### 활용예제 1

- JSON.stringify()는 JavaScript에서 객체 또는 값을 JSON 문자열로 변환하는 함수이다.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <script>
        let obj = { name: "홍길동", age: 20, hobbies: ["운동", "등산"] };
        let jsonS = JSON.stringify(obj);
        console.log(jsonS);
        // {"name":"홍길동","age":20,"hobbies":["운동","등산"]}

        let obj2 = [1, "aaa", { key: "value" }];
        let json2 = JSON.stringify(obj2);
        console.log(json2);
        //   [1,"aaa",{"key":"value"}]

        let obj3 = { name: "홍길동", age: 20, city: "서울" };
        let jsonS3 = JSON.stringify(obj3, ["name", "city"]);
        console.log(jsonS3);
        // {"name":"홍길동","city":"서울"}

        let obj4 = { name: "홍길동", age: 20, city: "서울" };
        let jsonS4 = JSON.stringify(obj4, (key, value) => {
          if (key == "age") {
            return value + 5;
          }
          return value;
        });
        console.log(jsonS4);
        //   {"name":"홍길동","age":25,"city":"서울"}

        let jsonS5 = JSON.stringify(obj4, null, "  ");
        //   객체로 만들때 각각 두칸을 띄어서장식
        console.log(jsonS5);
      /*   {
            "name": "홍길동",
             "age": 20,
             "city": "서울"
            } /*
    </script>
  </body>
</html>
```

### 활용 예제2

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <h1>json 생성</h1>
    <div id="jsonOut">
      <h2>데이터</h2>
      <pre id="jsonDis"></pre>
    </div>
    <button id="jsonDbtn">파일 다운로드</button>
    <script>
      let jsData = {
        name: "홍길동",
        age: 20,
        hobbies: ["등산", "운동", "수영", "독서"],
        add: { city: "서울", country: "한국" },
      };

      let jsonDis = document.getElementById("jsonDis");

      // jsData객체를 JSON 형식의 문자열로 변환, null 모든 속성이 변환 대상, " " 들여쓰기
      jsonDis.textContent = JSON.stringify(jsData, null, "  ");

      document
        .getElementById("jsonDbtn")
        .addEventListener("click", function () {
          let jsonData = JSON.stringify(jsData, null, "  ");
          // json파일을 가상메모리로 띄우기 Blob 규칙은 배열먼저 선포 이후 값을 지정
          let blob = new Blob([jsonData], { type: "application/json" });
          let alink = document.createElement("a");
          // URL을 만들어서 연결시킴
          alink.href = URL.createObjectURL(blob);
          alink.download = "data.json";
          alink.click();
          // 가상 메모리제거, 사용한 URL을 더 이상 필요하지 않게 되었을때 자원을 효율적으로 관리
          URL.revokeObjectURL(alink.href);
        });
    </script>
  </body>
</html>
```

### 활용 예제3

- toISOString()은 JavaScript의 Date 객체에서 사용할 수 있는 메서드로, 날짜와 시간을 국제 표준으로 변환하여 문자열로 반환한다.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <button id="btn">json 다운로드</button>
    <script>
      document.getElementById("btn").addEventListener("click", function () {
        let jsData = {
          today: new Date().toISOString(),
          random: Math.random(),
          message: "실시간 동적데이터 생성완료",
        };

        let jsonData = JSON.stringify(jsData, null, "  ");
        //  가상메모리 띄우기
        let blob = new Blob([jsonData], { type: "application/json" });
        let alink = document.createElement("a");
        // 가상메모리의 내용을 URL로 만듬
        alink.href = URL.createObjectURL(blob);
        alink.download = "aa.json";
        alink.click();

        // 가상 메모리제거, 사용한 URL을 더 이상 필요하지 않게 되었을때 자원을 효율적으로 관리
        URL.revokeObjectURL(alink.href);
      });
    </script>
  </body>
</html>
```

### 활용 예제4 체크리스트

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <h1>취미를 선택하세요</h1>
    <label> <input type="checkbox" value="독서" />독서 </label>
    <label> <input type="checkbox" value="운동" />운동 </label>
    <label> <input type="checkbox" value="코딩" />코딩 </label>
    <button id="saveBtn">json파일로 저장</button>
    <!-- checkbox의 value 값을 가져오기 -->
    <script>
      document.getElementById("saveBtn").addEventListener("click", function () {
        let inCheck = document.querySelectorAll("input[type=checkbox]:checked");
        let jsData = [];
        inCheck.forEach((item) => {
          jsData.push(item.value);
        });
        // 객체로 변신시키는 방법
        jsData = { hobbies: jsData };
        let jsonData = JSON.stringify(jsData, null, "  ");
        let blob = new Blob([jsonData], { type: "application/json" });
        let alink = document.createElement("a");
        alink.href = URL.createObjectURL(blob);
        alink.download = "aa.json";
        alink.click();

        URL.revokeObjectURL(alink.href);
      });
    </script>
  </body>
</html>
```

### 활용 예제 5

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <h1>데이터 입력</h1>
    <input type="text" id="nameIn" placeholder="이름입력" />
    <input type="number" id="ageIn" placeholder="나이입력" />
    <button id="addBtn">데이터 추가</button>
    <button id="saveBtn">json저장</button>
    <h2>추가된 데이터</h2>
    <ul id="addData"></ul>
    <script>
      let dataArr = [];
      document.getElementById("addBtn").addEventListener("click", function () {
        let nameIn = document.getElementById("nameIn").value || "값이없음";
        let ageIn = document.getElementById("ageIn").value || "값이없음";
        dataArr.push({ nameIn, ageIn });

        let li = document.createElement("li");
        li.textContent = `이름 : ${nameIn}, 나이: ${ageIn}`;

        document.getElementById("nameIn").value = "";
        document.getElementById("ageIn").value = "";
        document.getElementById("addData").appendChild(li);
        console.log(dataArr);
      });

      document.getElementById("saveBtn").addEventListener("click", function () {
        let jsData = JSON.stringify(dataArr, null, " ");
        let blob = new Blob([jsData], { type: "application/json" });

        let alink = document.createElement("a");
        alink.href = URL.createObjectURL(blob);
        alink.download = "aa.json";
        alink.click();

        URL.revokeObjectURL(alink.href);
      });
    </script>
  </body>
</html>
```

### 활용예제 버튼 활성화 비활성화

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <script src="jquery-3.7.1.min.js"></script>
    <script src="https://code.jquery.com/jquery-3.7.1.js"></script>
    <style>
      /* 활성화 */
      #btn {
        background-color: orange;
      }

      /* 비활성화 */
      #btn.on {
        background-color: gray;
      }
    </style>
  </head>
  <body>
    <button id="btn">활성화</button>
    <script>
      $(document).ready(function () {
        $("#btn").click(function () {
          $(this).toggleClass("on");
          $(this).text($(this).hasClass("on") ? "비활성화" : "활성화");
        });
      });
    </script>
  </body>
</html>
```
