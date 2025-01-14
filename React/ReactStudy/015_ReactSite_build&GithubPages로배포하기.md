# `리액트사이트 build & Github Pages로 배포하기`

### 웹브라우저는 HTML CSS JS 세개의 언어만 해석할 수 있다. 브라우저는 리액트의 state, JSX는 이해하지 못한다.<br> 따라서 리액트 프로젝트를 build라는걸 하면 브라우저 친화적인 HTML CSS JS 파일로 바꿔준다.

## 배포하기 전 체크사항

### 1.미리보기 띄워볼 때 콘솔창, 터미널에 에러만 안나면 된다.

warning 메세지는 사이트 구동에 별 영향이 없기 때문에 테스트해보실 땐 무시해도 된다.

### 2. 사이트를 배포할 때

http://jongmin.com/ 여기에 배포하는 경우엔 따로 설정이 필요없이 해도 되지만,<br>http://jongmin.com/blog/ 이런 하위 경로에 배포하고 싶으면 프로젝트에 설정이 따로 필요하다.
<br>
create-react-app을 사용해서 프로젝트를 만들었으면 프로젝트 파일 중 package.json 이라는 파일을 오픈해서

```js
"homepage": "/blog",
```

homepage라는 항목을 추가한 후 배포할 사이트 경로를 뒤에 추가하고 진행한다.

그리고 리액트 라우터가 설치되어있다면 라우터가 제공하는 basename="" 속성을 추가하는게 라우팅 잘될것이다.
<br>
vite create를 사용해서 프로젝트를 만들었으면<br>
프로젝트 파일 중 vite.config.js 파일을 오픈해서

```js
export default defineConfig({
  ...
  base : '/blog'
})
```

base : '/배포할사이트경로' 입력해주고 진행한다.<br>
그러면 css 파일들 사용시 /blog/css파일.css 이런 식으로 경로가 설정된다.<br>
base : './' 입력해주고 진행해도 된다.<br>
그러면 css 파일들 사용시 ./css파일.css 이런 식으로 경로가 설정된다.

## 1. 빌드작업

jsx같은 문법들은 브라우저가 해석 할 수 없어 html, css, js 문법으로 바꿔주는 작업이 필요 (컴파일 또는 build)

터미널

```js
npm run build
```

작업 프로젝트 폴더 내에 dist 또는 build 폴더가 생성되는데<br>
만들었던 코드를 전부 .html .css .js 파일로 변환해서 폴더에 담아준다.<br>
index.html이 메인페이지이다.

### 2. 무료 호스팅 github pages에 배포

HTML/CSS/JS 파일을 무료로 호스팅해주는 사이트<br>
github.com 로그인

1. New Repository

### Repository name 은 github pages로 발행하고 싶다면 <br>반드시 유저의 `깃허브아이디.github.io` 라고 입력해야한다. 그리고 README 파일 생성도 체크한 뒤에 생성해주면 된다.

### 3. Repository에 html 파일 올리기

Repository 생성이 끝나면 repository로 자동으로 들어가진다.<br>
dist 폴더 내의 파일을 전부 드래그 앤 드롭하면 된다.
드래그 앤 드롭하고 초록버튼까지 눌러주면 배포 끝.<br>
5분 정도 후에 https://내아이디.github.io 라고 주소창에 입력하면 유저의 사이트가 보인다.

### 주의사항

dist폴더를 드래그 앤 드롭하는게 아니라 dist 폴더 안의 내용물만 올린다.
