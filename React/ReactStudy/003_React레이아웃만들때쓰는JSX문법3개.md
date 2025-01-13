# `JSX문법`

## 1. class 넣을 땐 className

## 2. 변수

### 데이터바인딩 : {} 중괄호를 이용하여 변수를 집어넣을 수 있다.

```js
import "./App.css";

function App() {
  let post = "강남 우동 맛집";
  return (
    <div className="App">
      <h4 id={post}>{post}</h4>
    </div>
  );
}

export default App;
```

## 3. Style

### style 넣을 땐 style = {{스타일명:"값"}}

- 주의사항 "-" 하이픈 사용 X 붙여쓰고 카멜케이스로 표기(첫 알파벳 대문자), Ex) font-size -> fontSize

```js
function App() {
  let post = "강남 우동 맛집";
  return (
    <div className="App">
      <h4 style={{ color: "red", fontSize: "16px" }} id={post}>
        {post}
      </h4>
    </div>
  );
}

export default App;
```
