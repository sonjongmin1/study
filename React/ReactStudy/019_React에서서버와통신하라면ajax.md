# `ajax`

### 서버에 GET, POST 요청을 할 때 새로고침 없이 데이터를 주고받을 수 있게 도와주는 간단한 브라우저 기능

설치

```js
npm install axios
```

```js
import axios from "axios";

<button
  onClick={() => {
    axios
      .get("https://codingapple1.github.io/shop/data2.json")
      .then((result) => {
        console.log(result);
        // 데이터만 보고싶을때
        // console.log(result.data);
      });
  }}
>
  버튼
</button>;
```

- ajax 이용한 GET요청은 axios.get("url")
- 요청결과는 axios.get("url").then()

Q. ajax 요청 실패할 경우

- 인터넷이 안되거나, 서버가 꺼졌을 경우, 요청하는 url이 잘못되어 있거나
- .catch()=>{console.log("실패하였습니다.")}

#### etc) 파라미터는 함수나 메서드가 호출될때 외부에서 전달되는 값이다.

# `post, fetch`

### 서버로 데이터전송 POST요청

```js
axios.post("/abcdef", { name: "kim" });
```

### 동시에 ajax 요청 여러개하려면

```js
Promise.all([axios.get("/url1"), axios.get("/url2")]).then(() => {});
```

### 원래는 서버와 문자만 주고받을 수 있다. 단, 따옴표가 있으면 array, object도 주고받기 가능하다. (JSON : array, object 자료)

### fetch()

- JS 기본문법으로도 GET요청 가능

```js
fetch("url")
  .then((result) => result.json())
  .then((data) => {});
```

- JSON -> array/object 변환과정 필요, axios를 쓰면 이과정이 필요없다.
