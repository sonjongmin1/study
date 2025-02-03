### canvas\_애니메이션

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
