# canvas 이미지

![canvas](../img/canvas/canvasImg.png)

# HTML

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Canvas</title>
    <style>
      * {
        margin: 0;
        padding: 0;
      }
      canvas {
        border: 1px solid #000;
      }
    </style>
  </head>
  <body>
    <canvas width="300" height="300"></canvas>
    <!-- <img src="./img/apple.jpeg" alt="" /> -->
    <script>
      const canvas = document.querySelector("canvas");
      const ctx = canvas.getContext("2d");

      let img = new Image("");
      img.onload = function () {
        ctx.drawImage(img, 0, 0, canvas.width, canvas.he);
        // 위치를 정해주는 sx, sy
        // 정해준 위치를 자르는 sw, sh
        // 자른것에 대한 위치조정 sx, sy
        // 자른것에 대한 크기조정 dw, dh
        // 아래 명령어 앞에 부분은 생략해서 적어도 된다.
        // (img, sx, sy, sw, sh, dx, dy, dw, dh)
        ctx.drawImage(img, 300, 300, 1500, 1000, 0, 0, 1000, 500);
      };
      img.src = "./img/apple.jpeg";
      ctx.beginPath();
      ctx.arc(100, 150, 70, 0, Math.PI * 2, false);
      ctx.clip();
    </script>
  </body>
</html>
```
