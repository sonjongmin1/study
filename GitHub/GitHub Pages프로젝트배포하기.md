## `GitHub Pages에 프로젝트 배포하기: Vite와 gh-pages 설정 가이드`

- 깃허브 리파지토리 만들기

```js
git init
git add .
git commit -m "add"
git remote ~~~ // 깃허브 홈페이지에서 복사
git remote set-url ~~~ // remote안돼면 강제로 밀어넣기
git branch -M main
git push -u origin main
```

### gh-pages 설치, --save-dev 필요한 옵션 들고오기

```js
npm install gh-pages --save-dev
```

- 깃허브 페이지 > settings > 브렌치 메인으로 바꾸기, 원래 페이지로 내 계정주소를 만들어야 된다.
- 내 주소 복사 ex) https://sonjongmin1.github.io/test7777/

### package.json

- 아무데나 공간 만들기, json에게 내 홈페이지 주소를 알리기 위함 (필수)
- script 안에 아무대나, 마지막

### 입력

```js
"homepage":"내주소",
```

### 입력

```js
"scripts":{
    "predeploy": "npm run build",
    "deploy": "gh-pages -d build"
}
```

- 주의사항 : vite로 설치한거면 deploy": "gh-pages -d dist로 바꿔야한다.

### 터미널 입력

```js
npm run deploy
```

- vite로 설치한 리액트는
- vite.config.js에 아래 내용 추가
- base 경로 추가 예시

### Ex

```js
import { defineConfig } from "vite";
import react from "@vitejs/plugin-react";

// https://vite.dev/config/
export default defineConfig({
  plugins: [react()],
  base: "/test7777/",
});
```

```js
git add .
git commit -m "add"
git push origin main
npm run build
npm run deploy
```
