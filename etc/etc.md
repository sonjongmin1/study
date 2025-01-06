### position, offset

- 두 메서드는 속성이 필수이다. (position().top, offset().top)
- position은 부모위치가 기준, offset은 윈도우가 기준이다.

### append();

- 해당 선택자 내부 오른쪽 끝에 추가한다.

### prepend();

- 해당 선택자 내부 왼쪽 끝에 추가한다.

### siblings();

- siblings()는 selector는 제외한다라는 전제하에 모든 형제요소들이라는 의미이다. (나를 뺀 나머지 형제들)

### e.preventDefault()

- 맨 위로 스크롤되는 기본 동작 방지

### .keydown()

- 키를 누를때 발생

활용 예시 (Jquery)

```js
$(document).keydown((e) => {
  if (e.key === "Escape") {
    $(선택자).fadeOut();
  }
});
```

### click 과 mouseup 차이점?

- click() : 클릭을 시작하는 순간과 떼는 순간이 일치해야만 동작한다
- mouseup() : 달라도 된다
