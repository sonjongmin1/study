## Lifecycle과 useEffect

- 컴포넌트가 사람처럼 죽고 태어나고
- 컴포넌트가 보이는 순간, 페이지에 장착 (mount)
- 컴포넌트안에서 state를 조작하면, 업데이트 (update)
- 필요없으면 제거 (unmount)

#### 장착될때, 업데이트(재랜더링) 될때, 제거 될때, 중간중간 코드실행이 가능하다.

## useEffect

```js
import { useEffect } from "react";
function Detail(props) {
  useEffect(() => {
    console.log("Hello");
  });
}
```

- useEffect는 Detail 컴포넌트가 처음 장착이 될때, 업데이트 될때 실행이 된다.
- Detail 페이지 들어가면 Hello가 두번 출력됨, React에서 개발을 할때 useEffect안에 있는 코드는 디버깅을 위해 두번정도 실행 될 수 있으나, 실제 사이트에서는 한번 동작, 두번째 동작하는 것을 지우려면 index.js파일에서 React.StrictMode 제거하기

## useEffect 사용 이유

- useEffect 안에 있는 코드는 html 렌더링 후에 동작한다.
- useEffect 안에 적는 코드들은, 어려운 연산
- 서버에서 데이터가져오는 작업
- 타이머 장착하기

```js
// 1. 재렌더링마다 코드실행하고 싶으면 사용
useEffect(() => {});
// 2. mount시 1회 코드실행하고 싶으면
useEffect(() => {}, []);
// 3. unmount시 1회 코드실행하고 싶으면
useEffect(() => {
  return () => {};
}, []);
// 4. useEffect 실행 전에 뭔가 실행하려면 언제나 return()=>{}
```

Q. Effect인 이유?
A. Side Effect : 함수의 핵심기능과 상관없는 부가기능에서 나온 함수명이다.
useEffect에 들어갈 것들을 함수의 핵심기능 html 랜더링기능이 아닌 그외의 것들을 보통 집넣기 때문에 Side Effect같다해서 useEffect라고 이름을 지음.
