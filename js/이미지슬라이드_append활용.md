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
