# array/object 다룰 때 원본은 보존하는게 좋음

```js
/* eslint-disable */

import "./App.css";
import { useState } from "react";

function App() {
  let post = "React Blog";
  let [글제목, 글제목변경] = useState([
    "남자코트추천",
    "강남우동맛집",
    "파이썬독학",
  ]);
  let [시간, c] = useState(["2월 17일 발행", "2월 18일 발행", "2월 19일 발행"]);
  let [좋아요, 좋아요변경] = useState(0);

  return (
    <div className="App">
      <div className="black-nav">
        <h4>{post}</h4>
      </div>
      <div className="list">
        <h3>
          <span
            onClick={() => {
              let copy = [...글제목];
              copy[0] = "여자코트 추천";
              copy.sort();
              글제목변경(copy);
            }}
          >
            {글제목[0]}
          </span>
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

### state변경함수 특징

- 기존 state == 신규 state의 경우 변경안해줌

### array/object의 특징

- array/object 담은 변수엔 화살표만 저장됨

```js
let arr = [1, 2, 3];
// [1,2,3]이 어딨는지 알려주는 화살표만 들어있음
// 변수1 & 변수2 화살표가 같으면 변수1 == 변수2 비교해도 true 나옴
// Ex)
let copy = 글제목;
copy[0] = "여자코트 추천";
console.log(copy == 글제목);
글제목변경(copy);
```

## 결론

### state가 array/object면 독릭접 카피본을 만들어서 수정해야함
