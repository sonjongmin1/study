# `자식이 부모의 state 가져다쓰고 싶을 때는 props`

<img src="../../img/reactStudy/img010_1.PNG" alt="img1" width="200" height="200">
<br>

- 부모컴포넌트에서 자식컴포넌트로 state를 전송해 줄 수 있다.
- 전송할때는 props라는 문법을 사용한다.

### 부모 → 자식 state 전송하는 법, props 문법 사용

1. <자식컴포넌트 작명={state이름}>
2. props 파라미터 등록 후 props.작명 사용
3. 단, 자식 → 부모로는 전송이 불가능하다.
