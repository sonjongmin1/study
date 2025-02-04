# `canvas\_애니메이션`

## `활용 예제1`

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      body {
        margin: 0;
        padding: 0;
        overflow: hidden;
      }
    </style>
  </head>
  <body>
    <canvas></canvas>

    <script>
      const canvas = document.querySelector("canvas");
      const ctx = canvas.getContext("2d");

      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;

      const circle = {
        x: 100,
        y: 100,
        radius: 30,
        dx: 4,
        dy: 4,
        color: "gray",
      };

      function drawCircle() {
        ctx.beginPath();
        ctx.arc(circle.x, circle.y, circle.radius, 0, Math.PI * 2, false);
        ctx.fillStyle = circle.color;
        ctx.fill();
      }
      // drawCircle();

      function move() {
        ctx.clearRect(0, 0, canvas.width, canvas.height);
        drawCircle();
        circle.x += circle.dx;
        circle.y += circle.dy;
        if (
          circle.x + circle.radius > canvas.width ||
          circle.x - circle.radius < 0
        ) {
          circle.dx = -circle.dx;
        }

        requestAnimationFrame(move);
      }

      move();
    </script>
  </body>
</html>
```

## `활용 예제2`

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>캔버스 움직이는 원</title>
    <style>
      body {
        margin: 0;
        padding: 0;
        overflow: hidden;
        background-color: #000;
      }
    </style>
  </head>
  <body>
    <canvas></canvas>
    <script>
      const canvas = document.querySelector("canvas");
      const ctx = canvas.getContext("2d");

      // 테블릿 pc의 크기에 맞게 width, height 설정한다.
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;

      function pastelColor() {
        // 0부터 1사이의 난수(임의의 값을 가지는 수), Math.floor를 통해 정수를 받는다.
        let r = Math.floor(Math.random() * 105) + 150;
        let g = Math.floor(Math.random() * 105) + 150;
        let b = Math.floor(Math.random() * 105) + 150;
        return `rgba(${r},${g},${b},0.7)`;
      }

      // 클래스 만들기 (첫 글자는 대문자)
      class Bubble {
        // 공통적으로 쓰는 변수
        constructor() {
          this.radius = 80;
          // x,y는 원이나타나는 좌표,  2 * this.radius <- 공크기
          this.x = Math.random() * canvas.width - 2 * this.radius;
          this.y = Math.random() * canvas.height - 2 * this.radius;
          // 캔버스 속도 dx, dy
          this.dx = 1.5;
          this.dy = 1.5;
          this.color = pastelColor();
        }

        draw() {
          let centerX = this.x;
          let centerY = this.y;
          let radius = this.radius;

          // createRadialGradient(작은원 중심점의 x좌표, 작은원 중심점의 y좌표, 작은 원의 크기, 큰 원의 크기...)
          let grad = ctx.createRadialGradient(
            centerX - 20,
            centerY - 20,
            radius * 0.1,
            centerX,
            centerY,
            radius
          );

          grad.addColorStop(0, "white");
          grad.addColorStop(0.2, "rgba(255,255,255,0.8)");
          grad.addColorStop(0.8, this.color);
          grad.addColorStop(1, "rgba(255,255,255,0.2)");

          ctx.beginPath();
          // 원그리는 규칙
          ctx.arc(centerX, centerY, radius, 0, Math.PI * 2, false);
          ctx.fillStyle = grad;
          ctx.fill();
          ctx.lineWidth = 0.7;
          ctx.strokeStyle = "rgba(255,255,255, 0.5)";
          ctx.stroke();
          ctx.closePath();
        }

        move() {
          this.x += this.dx;
          this.y += this.dy;

          if (this.x + this.radius > canvas.width || this.x - this.radius < 0) {
            this.dx *= -1;
          }
          if (
            this.y + this.radius > canvas.height ||
            this.y - this.radius < 0
          ) {
            this.dy *= -1;
          }
        }
      }

      let bubbles = [];
      for (let i = 0; i < 10; i++) {
        bubbles.push(new Bubble());
      }

      function animate() {
        ctx.clearRect(0, 0, canvas.width, canvas.height);
        bubbles.forEach((bubble) => {
          bubble.move();
          bubble.draw();
        });
        requestAnimationFrame(animate);
      }

      animate();
    </script>
  </body>
</html>
```
