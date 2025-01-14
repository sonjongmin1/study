# `input`

- type : "text", "range", "checkbox", "date"

### 1. input 입력시 코드실행방법

#### Event Handler

- onChange : user가 값을 입력할때마다 실행 (입력이 완료된 후)
- onInput : onChange와 기능 같음, user가 값을 입력할때마다 실행 (입력할때마다 즉시)
- onMouseOver : 마우스를 가져다놯을때 실행
- onScroll : scroll bar를 조작할때 마다 코드 실행<br>
  Event Handler 모르면 찾아보기, 아래 내용은 반드시 숙지

#### 1. state 만드는 법 <br> 2. props 전송하는법 <br>3. 컴포넌트 만드는 법<br>4.UI만드는 step

### 2. \<input>에 입력한 값 가져오는 법

```js
<input onChange={(e)=>{console.log(e)}}>
// e : 발생하는 이벤트에 관련한 여러 기능이 담겨있음
<input onChange={(e)=>{console.log(e.target)}}>
// 이벤트 발생한 html태그
<input onChange={(e)=>{console.log(e.target.value)}}>
// 이벤트 발생한 html태그에 입력한 값
```

`e.stopPropagation() : 상위 html로 퍼지는 이벤트버블링 막기`

### 3. \<input>에 입력한 값 저장하기

```js
<input
  onChange={(e) => {
    setValue(e.target.value);
    console.log(value);
  }}
/>
```

- 보통 변수/state에 저장해둠
- state변경함수는 늦게처리됨(비동기처리)
- e.target.value 완료되기전에 다음줄 실행

# `select`

- dropdown 기능 사용가능

# `textarea`

- 사용자가 여러 줄의 텍스트를 입력할 수 있는 필드를 생성
  <br>

#### Q1. input 입력, 발행버튼누르면 블로그에 글이 하나 추가되는 기능 생성<br>

#### Q2. 글마다 옆에 삭제버튼 하나씩 만들어놓고 삭제버튼누르면 글이 사라지는 기능
