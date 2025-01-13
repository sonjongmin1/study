### return()안에는 병렬로 태그 2개 이상 기입금지

```js
import "./App.css";

function App() {
  let post = "강남 우동 맛집";
  return <div className="App"></div>;
}

export default App;
```

# `state`

### state : 중요한 자료를 잠깐 저장할 때 쓰는 변수

- 1.import{useState}
- 2.useState(보관할 자료)
- 3.let[작명, 작명]

### Destructuring 문법

- let num = [1,2,3]; array자료 : 여러 자료들을 한곳에 보관하고 싶을때 사용
- 1과 2를 따로 변수로 빼고 싶을때 Destructuring 문법을 사용한다.
- Destructuring 문법은 array자료들을 각각 변수로 빼주는 문법이다.
- let a = num[0];
- let b = num[1];
- let [a, c] = [1, 2]; // Destructuring 문법 편리하게 사용 방법

### 핵심

### let [글제목, b] = useState("남자 코트 추천");

- useState를 쓰면 그 자리에 ["남자 코트 추천",함수] array자료가 남는다.
- let [글제목, b] useState 이것을 각각 변수로 빼서 쓰겠다라는 뜻

# `변수 문법이 따로 있는데 state문법을 쓰는 이유?`

- 변수와 state문법의 차이점 : 일반 변수는 갑자기 변경되면 html에 자동으로 반영안됨
- state는 갑자기 변경되면 state쓰던 html은 자동 재렌더링됨
- 모든것을 state로 쓰지말고 변경이 자주 안되는 logo같은 것들, 자주 변경되는 것들에 사용한다.

```js
import "./App.css";
import { useState } from "react";

function App() {
  let post = "강남 우동 맛집";
  let [글제목, b] = useState("남자 코드 추천");
  // b는 state변경 도와주는 함수

  return (
    <div className="App">
      <h4>{글제목}</h4> // state에 보관했던 자료 나옴
    </div>
  );
}

export default App;
```

### WARNING 메세지 없애는 방법

```js
/* eslint-disable */
```
