### WARNING 메세지 없애는 방법

```js
/* eslint-disable */
```

### App.jsx

```js
/* eslint-disable */

import "./App.css";
import { useState } from "react";

function App() {
  let post = "React Blog";
  let [글제목, b] = useState(["남자코트추천", "강남우동맛집", "파이썬독학"]);
  let [시간, c] = useState(["2월 17일 발행", "2월 18일 발행", "2월 19일 발행"]);
  let [좋아요, 좋아요변경] = useState(0);

  return (
    <div className="App">
      <div className="black-nav">
        <h4>{post}</h4>
      </div>
      <div className="list">
        <h3>
          {글제목[0]}
          <span
            onClick={() => {
              좋아요변경(좋아요 + 1);
            }}
          >
            👍
          </span> {좋아요}
        </h3>
        <p>{시간[0]}</p>
      </div>
      <div className="list">
        <h3>{글제목[1]}</h3>
        <p>{시간[1]}</p>
      </div>
      <div className="list">
        <h3>{글제목[2]}</h3>
        <p>{시간[2]}</p>
      </div>
      <div />
    </div>
  );
}

export default App;
```

### 핵심

- state 변경하는 법, 등호로 변경금지
- state 변경용 함수, 변경용 함수를써야 html 재렌더링도 잘됨 
- 항상 state 변경함수 쓰기
