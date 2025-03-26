# `이미지슬라이드_append활용`

# .append

### 이동된 첫 번째 이미지를 맨 뒤로 옮긴다.

# .prepend

### 마지막 이미지를 맨 앞으로 옮긴다.

```js
// 눈속임을 위함
const slide = document.getElementById("slide");
const callback = () => {
  slide.style.transition = "none";
  // left를 0으로 초기화
  slide.style.left = 0;
  // 첫 번째 이미지를 맨 뒤로 옮긴다.
  slide.append(slide.firstElementChild);
};

// 슬라이드 구현
const toLeftMove = () => {
  slide.style.transition = "left 1s";
  slide.style.left = "-1100px";
  // 1초뒤 콜백 함수 실행
  setTimeout(callback, 1000);
};

// 2.5초 간격으로 toLeftMove함수 실행
setInterval(toLeftMove, 2500);
```

# `활용 예제 .clientWidth`

```js
let slide = document.getElementById("slide");
let slideImg = document.querySelector("#slide > img");
let slideImgWidth = slideImg.clientWidth;
console.log(slideImgWidth);
let callback = () => {
  slide.style.transition = "none";
  slide.style.left = 0;
  slide.append(slide.firstElementChild);
};

let toLeft = () => {
  slide.style.transition = "left 1s";
  slide.style.left = `-${slideImgWidth}px`;
  setTimeout(callback, 1000);
};

// setInterval(toLeft, 2900);
```

- clientWidth는 웹 개발에서 요소의 너비를 계산할 때 사용되는 JavaScript 속성이다. HTML 요소의 내부 너비를 픽셀 단위로 반환한다. 이 속성은 CSS로 스타일링된 너비와 실제 콘텐츠가 표시될 수 있는 영역을 반영하므로, 정확한 요소의 크기를 계산할 때 유용하다.

### 전체코드

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>slide</title>
    <style>
      * {
        box-sizing: border-box;
        margin: 0;
        padding: 0;
      }

      body {
        width: 100vw;
        height: 100vh;
      }

      section {
        position: relative;
        width: 100%;
        height: 350px;
        background-color: skyblue;
        /* overflow-x: hidden; */
      }

      .slide {
        display: flex;
        position: absolute;
        width: 300%;
        height: 350px;
        background-color: yellow;
        left: 0;
      }

      .slide > img {
        width: 100%;
        height: 350px;
        background-size: cover;
        background-repeat: no-repeat;
        background-position: center;
      }

      .img1 {
        background-color: red;
      }
      .img2 {
        background-color: orange;
      }
      .img3 {
        background-color: yellow;
      }
    </style>
  </head>
  <body>
    <section>
      <div class="slide">
        <img class="img1" src="#" alt="이미지1" />
        <img class="img2" src="#" alt="이미지2" />
        <img class="img3" src="#" alt="이미지3" />
      </div>
    </section>
    <script>
      let slide = document.querySelector(".slide");
      let slideImgWidth = document.querySelector(".slide > img").clientWidth;

      let callback = () => {
        slide.style.transition = "none";
        slide.style.left = 0;
        slide.append(slide.firstElementChild);
      };

      let moveLeft = () => {
        slide.style.transition = "left 1s";
        slide.style.left = `-${slideImgWidth}px`;
        setTimeout(callback, 1000);
      };

      setInterval(moveLeft, 2900);
    </script>
  </body>
</html>
```

### 직접 만든 코드

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      * {
        box-sizing: border-box;
        margin: 0;
        padding: 0;
      }

      body {
        width: 100vw;
        height: 50vh;
      }

      section {
        position: relative;
        width: 100%;
        height: 50vh;
        /* overflow-x: hidden; */
      }

      .slide {
        display: flex;
        position: absolute;
        width: 300%;
        height: 50vh;
        left: 0;
      }

      .slide img {
        width: 100%;
        background-repeat: no-repeat;
        background-size: cover;
        background-position: center;
      }
      .prev {
        width: 100px;
        height: 100px;
        background-color: blue;
      }
      .next {
        width: 100px;
        height: 100px;
        background-color: yellow;
      }
    </style>
  </head>
  <body>
    <section>
      <div class="slide">
        <img src="./img/soop.jpg" alt="이미지1" />
        <img src="./img/nike.jpg" alt="이미지2" />
        <img src="./img/hyungielite.jpg" alt="이미지3" />
      </div>
    </section>
    <div class="prev">왼쪽</div>
    <div class="next">오른쪽</div>
    <script>
      let slide = document.querySelector(".slide");
      let slideImg = document.querySelector(".slide > img").clientWidth;
      let prev = document.querySelector(".prev");
      let next = document.querySelector(".next");
      let isMoving = false;

      slide.style.left = `-${slideImg}px`;

      prev.addEventListener("click", function () {
        if (!isMoving) {
          isMoving = true; // 이동 중 상태로 설정
          moveLeft();
          setTimeout(() => {
            isMoving = false; // 1초 후 이동 가능 상태로 설정
          }, 1000);
        }
      });
      next.addEventListener("click", function () {
        if (!isMoving) {
          isMoving = true;
          moveRight();
          setTimeout(() => {
            isMoving = false;
          }, 1000);
        }
      });

      let callbackL = () => {
        slide.style.transition = "none";
        slide.style.left = `-${slideImg}px`;
        slide.append(slide.firstElementChild);
      };

      let moveLeft = () => {
        slide.style.transition = "left 1s";
        slide.style.left = `-${slideImg * 2}px`;
        setTimeout(callbackL, 1000);
      };

      let callbackR = () => {
        slide.style.transition = "none";
        slide.style.left = `-${slideImg}px`;
        slide.prepend(slide.lastElementChild);
      };

      let moveRight = () => {
        slide.style.transition = "left 1s";
        slide.style.left = 0;
        setTimeout(callbackR, 1000);
      };

      //   setInterval(moveRight, 2900);
    </script>
  </body>
</html>
```
