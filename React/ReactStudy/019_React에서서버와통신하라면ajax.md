# `ajax`

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
