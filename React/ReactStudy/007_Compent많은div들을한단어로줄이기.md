# component

### 컴포넌트 만드는 법

- 1.function 만들기
- 2.return()안에 html 담기
- 3.<함수명></함수명> 쓰기

### App.jsx 컴포넌트 적용

```js
<Modal></Modal>
// 또는
<Modal/>
```

### JS

```js
function Modal() {
  return (
    <div className="modal">
      <h4>제목</h4>
      <p>날짜</p>
      <p>상세내용</p>
    </div>
  );
}
```

### return()안에 html 병렬기입하려면?

- 의미없는 \<div>대신 <></> (React Fragment 문법)사용가능
