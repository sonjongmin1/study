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
