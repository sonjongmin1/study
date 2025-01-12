# `React 개발환경 셋팅`

### 1. 구글 Node.js검색, 다운로드

### 2. Visual Studio Code 다운로드

### 터미널 실행

```js
npm create vite@latest
y
React
Javascript
프로젝트이름
cd 프로젝트이름
npm install // 리액트에 필요한 라이브러리들
/*
라이브러리란? 재사용 가능한 코드의 집합
 */

/*
코드 실행 안될시
- Get-ExecutionPolicy
- Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
- npm create vite@latest
실행 정책 변경 Restricted 정책을 RemoteSigned로 변경하면 문제가 해결
- window 사용자 이름이 한글일 경우 오류발생, 영어로 바꿔주기, 참조 window사용자이름바꾸기
*/
```

### 미리보기 실행

```js
npm run dev
/*
오류 발생시 node.js 버전이 17미만일 경우 발생
node.js 최신으로 다운로드
버전확인 명령어 node -v
*/
local host // cmd + click 페이지 열기
//미리보기 중지 ctrl + c

```

### js (JavaScript)

- 정의: 일반적인 JavaScript 코드를 의미하며, 웹 브라우저나 Node.js에서 실행된다.
- 자바스크립트는 브라우저 안에서만 실행된다.

### jsx (JavaScript XML)

- JavaScript와 XML(HTML과 유사한 문법)을 결합한 확장 문법으로, React에서 주로 사용된다.
- node.js는 자바스크립트를 내 컴퓨터 어디에서나 실행 될 수 있도록 해주는 실행 엔진같은것, 내컴퓨터 아무데서나 코드를짜도 자바스크립트 실행이 가능함
- node.js를 설치하면 npm도 같이 설치됨
- npm은 package manger 같은 것인데 자바스크립트 라이브러리들을 설치하고 삭제 하는것을 쉽게 도와주는 간단한 프로그램이다.
- vite(빌드/번들링 툴)라는 라이브러리 도움을 받으면 리액트, 뷰, 스벨트 등 프로젝트 생성을 도와준다.
- vite(빌드/번들링 툴) 장점

  - 소스코드 사이즈 압축 가능
  - 자바스크립트로 개발할때 리액트 문법, 뷰 문법 등을 자바스크립트로 컴파일 가능
  - 빠른 미리보기

# `React Foundation`

- App.jsx안의 내용을 > main.jsx(main.js, index.js main.jsx와 같은 용도의 파일)안에 넣고 > index.html안에 넣게 코드 짜임
- public 폴더는 이미지파일이나, 데이터파일 보관하는 곳
- package.json 파일은 설치한 라이브러리들을 기록해주는 용도의 파일, npm 명령어 설정도 가능
- node_modules는 설치한 라이브러리들을 보관해주는 곳

### 1. 시작시 App.css, index.css 지우기

```css
body {
  margin: 0;
}
div {
  box-sizing: border-box;
}
```

### 2. App.jsx 파일도 비우고 시작, \<div>\</div>만 남기고 시작

```js
import "./App.css";

function App() {
  return <div></div>;
}
export default App;
```
