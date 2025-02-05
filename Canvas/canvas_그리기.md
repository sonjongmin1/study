# `canvas_그리기`

### HTML

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>캔버스 그리기</title>
    <link rel="stylesheet" href="./css/style.css" />
  </head>
  <body>
    <div id="outBox">
      <div id="toolBar">
        <div>
          <!-- 색상을 고를 수 있는 단추 -->
          <label for="co">색상</label>
          <input id="co" type="color" />
          <label for="1width">선 굵기</label>
          <input type="text" />
          <input id="1width" type="number" min="1" max="50" value="2" />
        </div>
        <button id="reset">지우기</button>
      </div>
      <canvas></canvas>
    </div>
    <script src="./js/main.js"></script>
  </body>
</html>
```

### CSS

```css
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  width: 100vw;
  height: 100vh;
  overflow: hidden;
}

#toolBar {
  display: flex;
  justify-content: space-between;
  padding: 20px;
  background-color: gray;
}

canvas {
  width: 100%;
  height: 100%;
}
```

### JS

```js
const canvas = document.querySelector("canvas");
const toolBar = document.querySelector("#toolBar");

canvas.width = window.innerWidth;
canvas.height = window.innerHeight - toolBar.offsetHeight;

let canvasX = canvas.offsetLeft;
let canvasY = canvas.offsetTop;

const ctx = canvas.getContext("2d");

let flag = false;
let startX = 0;
let startY = 0;

toolBar.addEventListener("change", (e) => {
  if (e.target.id == "co") {
    ctx.strokeStyle = e.target.value;
  }
  if (e.target.id == "1width") {
    ctx.lineWidth = e.target.value;
  }
});

canvas.addEventListener("mousedown", (e) => {
  flag = true;
  startX = e.clientX;
  startY = e.clientY - toolBar.offsetHeight; // canvasOffsetY
});

canvas.addEventListener("mousemove", (e) => {
  if (!flag) return;
  ctx.lineCap = "round";
  ctx.lineTo(e.clientX, e.clientY - toolBar.offsetHeight);
  ctx.stroke();
});

canvas.addEventListener("mouseup", (e) => {
  flag = false;
  ctx.beginPath();
});

toolBar.addEventListener("click", (e) => {
  if (e.target.id == "reset") {
    ctx.clearRect(0, 0, canvas.width, canvas.height);
  }
});
```
