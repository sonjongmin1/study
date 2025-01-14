# props를 응용한 상세페이지 만들기

### 중요

### state 만드는 곳은 state 사용하는 컴포넌트들 중 최상위컴포넌트(App.jsx)

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
  let [count, setCount] = useState(2);
  return (
    <>
      <h4 className={"title"}>{post}</h4>
      {title.map(function (a, i) {
        return (
          <div className="list">
            <h4>
              <span
                onClick={() => {
                  setCount(i);
                }}
              >
                {title[i]}
              </span>
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
        <Modal
          count={count}
          color="orange"
          title={title}
          titleChange={titleChange}
        />
      ) : null}
    </>
  );

  function Modal(props) {
    return (
      <div className="modal" style={{ backgroundColor: props.color }}>
        <h4>{props.title[props.count]}</h4>
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
