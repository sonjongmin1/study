# `focus, blur`

### JS

```js
$(document).ready(() => {
  $("input").focus((e) => {
    $(e.target).addClass("fo").removeClass("bl");
  });

  $("input").blur((e) => {
    $(e.target).removeClass("fo").addClass("bl");
  });
});
```

### Css

```css
.fo {
  background: yellowgreen;
}

.bl {
  background: blue;
}

input::placeholder {
  color: red;
  font-style: italic;
}
```

# `클릭시 img change`

```js
$(document).ready(() => {
  $("img").click(function () {
    if ($(this).hasClass("sn")) {
      $(this).attr({ src: "./img/snow.jpg", alt: "겨울눈" });
    }
  });
});
```

```css
#layout {
  max-width: 650px;
  margin: auto;
  border: 1px solid red;
}

img {
  display: block;
  width: 600px;
  height: 400px;
}
```

- img 여백은 display가 inline-block이여서, block으로 변경해주면 된다.
- 2개이상 속성을 바꿀때 $(this).attr({ src: "./img/snow.jpg", alt: "겨울눈" });

# `before_after`

### 제이쿼리 before() after() prepend() append() 메소드

```js
$(document).ready(() => {
  $("ul li").click(function () {
    $(this).before('<b style="color:blue;">&#9834; </b>');
  });
  $("ol li").click(function () {
    $(this).after('<b style="color:red;">&#10168; </b>');
  });
  $("button")
    .eq(0)
    .click(() => {
      $("p").prepend("<i style='color:brown'>&#9749; 티타임</i>");
    });
  $("button")
    .eq(1)
    .click(() => {
      $("dd").eq(0).prepend("<b style='color:yellowgreen'>&#9997; 손글씨</b>");
    });
  $("button")
    .eq(2)
    .click(() => {
      $("dd").eq(1).append("<b style='color:skyblue'>&#128591; 기도</b>");
    });
}); //.....All End.......
```

# `width`

### width

- content만 크기 측정

### innerWidth

- content와 padding까지 크기 측정

### outerWidth

- content, padding, border 크기까지 측정

```js
$(document).ready(() => {
  $("img")
    .eq(0)
    .click(function () {
      console.log($(this).width()); //넓이300
    });
  $("img")
    .eq(1)
    .click(function () {
      let x = $(this).height(); //높이 210.453
      x = Math.trunc(x); //소수점이하는 무시함
      console.log(x); //210
    });
  $("img")
    .eq(2)
    .click(function () {
      console.log($(this).innerHeight()); //높이( 20+200+20 )= 240
    });
  $("img")
    .eq(3)
    .click(function () {
      console.log($(this).innerWidth()); //넓이(20+300+20)
    });
  $("img")
    .eq(4)
    .click(function () {
      console.log($(this).outerWidth()); //넓이(6+20+300+20+6) =352
    });
  $("img")
    .eq(5)
    .click(function () {
      console.log($(this).outerHeight()); //높이(20+300+20)
    });
}); //.....All End.......
```

# `each 메서드`

### 실행문을 각각 실행

### Html

```html
<div id="layout">
  <h1>each() 메서드</h1>
  <button>콘텐츠 표시하기</button>
  <ul>
    <li>커피</li>
    <li>우유</li>
    <li>소다</li>
  </ul>
</div>
```

### JS

```js
$(document).ready(() => {
  $("button").click(() => {
    $("ul > li").each(function () {
      alert($(this).text());
    });
  });
});
```
