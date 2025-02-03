# Canvas(캔버스) - Web API

### HTML

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Canvas</title>
    <style></style>
  </head>
  <body>
    <!-- 캔버스 요소 생성: width는 400px, height는 300px으로 설정 -->
    <canvas width="400" height="300"></canvas>
    <script>
      // canvas 요소를 DOM에서 선택
      const canvas = document.querySelector("canvas");

      // canvas의 2D 컨텍스트를 가져옴
      const ctx = canvas.getContext("2d");

      // 도형 내부를 채울 때 사용할 색상을 파란색으로 설정
      ctx.fillStyle = "blue";

      // 도형의 윤곽선을 그릴 때 사용할 색상을 빨간색으로 설정
      ctx.strokeStyle = "red";

      // 캔버스에 텍스트를 그리기 위한 폰트를 설정
      // italic: 텍스트를 기울임
      // 60px: 폰트 크기를 60px로 설정
      // serif: 세리프 폰트를 사용
      ctx.font = "italic 60px serif";

      // 캔버스에 채워진 텍스트를 그리기
      // "Javascript"라는 텍스트를 x: 100, y: 100 위치에 채움
      ctx.fillText("Javascript", 100, 100);

      // 캔버스에 텍스트의 윤곽선을 그리기
      // "Javascript"라는 텍스트를 x: 100, y: 100 위치에 스트로크
      ctx.strokeText("Javascript", 100, 100);

      // 다른 폰트 스타일로 변경
      // bold: 텍스트를 굵게 설정
      // 60px: 폰트 크기를 60px로 설정
      // sans-serif: 세리프가 없는 폰트 사용
      ctx.font = "bold 60px sans-serif";

      // 캔버스에 채워진 텍스트를 그리기
      // "Javascript"라는 텍스트를 x: 100, y: 200 위치에 채움
      ctx.fillText("Javascript", 100, 200);
    </script>
  </body>
</html>
```
