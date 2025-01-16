## previousElementSibling

```js
let mainSlideAll = document.querySelectorAll(".mainSlide");

mainSlideAll.forEach((i, z) => {
  if (i.classList.contains("active")) {
    i.previousElementSibling.classList.add("active");
    i.classList.remove("active");
  }
});
```

- i이전 요소의 active 추가

## nextElementSibling

```js
mainSlideAll.forEach((i, z) => {
  if (i.classList.contains("active")) {
    i.nextElementSibling.classList.add("active");
    i.classList.remove("active");
  }
});
```

- i다음 요소의 active 추가
