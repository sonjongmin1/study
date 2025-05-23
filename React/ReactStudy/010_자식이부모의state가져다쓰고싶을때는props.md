# `자식이 부모의 state 가져다쓰고 싶을 때는 props`

<img src="../../img/reactStudy/img010_1.PNG" alt="img1" width="200" height="200">
<br>

- 부모컴포넌트에서 자식컴포넌트로 state를 전송해 줄 수 있다.
- 전송할때는 props라는 문법을 사용한다.

### 부모 → 자식 state 전송하는 법, props 문법 사용

1. <자식컴포넌트 작명={state이름}>
2. props 파라미터 등록 후 props.작명 사용
3. 단, 자식 → 부모로는 전송이 불가능하다.

```js
/* eslint-disable */

import "./App.css";
import { useState } from "react";

function App() {
  let post = "React Blog";
  let [title, titleChange] = useState(["가", "나", "다"]);
  let [content, contentChange] = useState([
    "추천내용1",
    "추천내용2",
    "추천내용3",
  ]);
  let [like, likeChange] = useState([0, 0, 0]);
  let [modal, setModal] = useState(false);
  return (
    <>
      <h4 className={"title"}>{post}</h4>
      {title.map(function (a, i) {
        return (
          <div className="list">
            <h4>
              <span>{title[i]}</span>
              <span
                onClick={() => {
                  let copy = [...like];
                  copy[i] = copy[i] + 1;
                  likeChange(copy);
                }}
              >
                👍{like[i]}
              </span>
            </h4>
            <p>{content[i]}</p>
          </div>
        );
      })}
      <button
        onClick={() => {
          setModal(!modal);
        }}
      >
        모달 버튼
      </button>
      {modal == true ? (
        <Modal color="orange" test={title} titleChange={titleChange} />
      ) : null}
    </>
  );

  function Modal(props) {
    return (
      <div className="modal" style={{ backgroundColor: props.color }}>
        <h4>{props.test[0]}</h4>
        <p>날짜</p>
        <p>상세내용</p>
        <button
          onClick={() => {
            props.titleChange(["파", "나", "다"]);
          }}
        >
          글수정
        </button>
        {/* 글수정 버튼누르면 첫 글제목이 "파"로 바뀜 */}
      </div>
    );
  }
}

export default App;
```
