### HTML

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <script src="./main.js"></script>
  </body>
</html>
```

### Javascript

```js
let canvas;
let ctx;

//canvas 만들기
canvas = document.createElement("canvas");
//canvas에서 2d를 만들것이다.
ctx = canvas.getContext("2d");
//canvas 사이즈 정해주기
canvas.width = 400;
canvas.height = 700;
//canvas 세팅, canvas 태그 HTML에 적용하기
document.body.appendChild(canvas);
//이미지 가져오기
let astronautImg, endImg, spaceBgImg, bulletImg;
//우주인 좌표 따로 빼기, 우주인이 움직일려면 좌표가 계속 바뀐다.
let astronautX = canvas.width / 2 - 25;
let astronautY = canvas.height - 50;

// 총알을 담을 리스트
let bulletList = [];
function Bullet() {
  // Bullet에 대한 x, y값
  this.x = 0;
  this.y = 0;
  // init 함수를 초기화
  this.init = function () {
    this.x = astronautX - 6;
    this.y = astronautY - 40;

    //  this안에는 x,y,init이 있다.
    bulletList.push(this);
  };
  this.update = function () {
    this.y -= 7;
  };
}

function loadImage() {
  spaceBgImg = new Image();
  spaceBgImg.src = "img/spaceBg.jpg";

  astronautImg = new Image();
  astronautImg.src = "img/astronaut.png";

  endImg = new Image();
  endImg.src = "img/end.jpg";

  bulletImg = new Image();
  bulletImg.src = "img/bullet.png";
}
// 누른키들을 저장할 변수 생성
let keysDown = {};

// 키 누를때
function setupKeyboardListener() {
  document.addEventListener("keydown", function (event) {
    // keycode라는 이름에서 key라는 이름으로 바뀜, 쓰는데에는 지장 없지만 되도록 key사용
    console.log("무슨 키가 눌렸는지 확인", event.key);
    keysDown[event.key] = true;
    console.log("키다운 객체에 들어간 값은?", keysDown);
  });
  // 키 땔때 저장한 keysDown 객체 초기화
  document.addEventListener("keyup", function (event) {
    delete keysDown[event.key];
    console.log("버튼 클릭후", keysDown);

    //스페이스바 키값 " "
    if (event.key == " ") {
      // 총알생성 함수
      createBullet();
    }
  });
}

// 하나의 함수에는 하나의 역할만 있어야 하는게 맞다. 개발자 입장에서도 가독성이 좋고 코드를 이해하기 좋음.
function createBullet() {
  console.log("총알생성");
  // new 라는 것은 정의해둔 Bullet function을 하나 더 만듦, b에 저장
  let b = new Bullet();
  b.init();
  console.log("새로운 총알 리스트", bulletList);
}

// 좌, 우 움직이는 구현
function update() {
  if ("ArrowRight" in keysDown) {
    astronautX += 5;
  }
  if ("ArrowLeft" in keysDown) {
    astronautX -= 5;
  }

  // 우주인의 좌표값이 무한대로 업데이트가 되는게 아닌, 경기장안에 있을려면
  if (astronautX <= 0) {
    astronautX = 0;
  }
  if (astronautX >= canvas.width - 50) {
    astronautX = canvas.width - 50;
  }

  // 총알의 y좌표 업데이트하는 함수 호출
  for (let i = 0; i < bulletList.length; i++) {
    bulletList[i].update();
  }
}

//이미지 canvas에 그려주기, render은 그리다.
function render() {
  update();
  ctx.drawImage(spaceBgImg, 0, 0, canvas.width, canvas.height);
  ctx.drawImage(astronautImg, astronautX, astronautY);
  for (let i = 0; i < bulletList.length; i++) {
    ctx.drawImage(bulletImg, bulletList[i].x, bulletList[i].y);
  }
}
//canvas 계속 호출하기
function main() {
  render();
  //Test   console.log("animation calls main function");
  // 애니메이션 처럼 프레임을 여러번 호출하는 함수, 무한 호출
  requestAnimationFrame(main);
}

loadImage();
setupKeyboardListener();
main();

/*
총알 만들기
1. 스페이스바를 누르면 총알 발사
2. 총알이 발사 = 총알의 y값이 --, 총알의 x값은 스페이스를 누른 순간의 우주인 x좌표
3. 발사된 총알들은 총알 배열에 저장
4. 총알들은 x,y 좌표값이 있어야 한다.
5. 총알 배열을 가지고 render 그려준다.
*/
```
