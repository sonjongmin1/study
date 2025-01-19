# `Fullpage`

### HTML

```html
<!DOCTYPE html>
<html>
  <head>
    <title>one page - wheel sliding move</title>
    <meta charset=utf-8">
    <meta name="viewport" content="width=device-width" />
    <!-- jQuery 라이브러리 로드 (버전 3.1.1) -->
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.1.1/jquery.min.js"></script>
    <!-- jQuery Fullpage 플러그인 로드 (스크롤 기반의 전체 페이지 슬라이드) -->
    <script src="https://cdn.jsdelivr.net/jquery.fullpage/2.9.4/jquery.fullpage.min.js"></script>
    <link
      rel="stylesheet"
      type="text/css"
      href="https://cdn.jsdelivr.net/jquery.fullpage/2.9.4/jquery.fullpage.min.css"
    />
    <link rel="stylesheet" href="./css/style.css" />
  </head>

  <body>
    <ul id="menu">
      <li class="act"><a href="#firstPage">0</a></li>
      <li><a href="#secondPage">1</a></li>
      <li><a href="#3rdPage">2</a></li>
      <li><a href="#4thpage">3</a></li>
    </ul>

    <div id="fullpage">
      <div class="section">00000</div>
      <div class="section">11111</div>
      <div class="section">22222</div>
      <div class="section">33333</div>
    </div>
    <script src="./js/main.js"></script>
  </body>
</html>
```

### CSS

```css
#fullpage > div {
  text-align: center;
}
#menu li {
  display: inline-block;
}
#menu li a {
  text-decoration: none;
  color: #000;
  padding: 41px 20px;
  display: block;
}
#menu {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  position: fixed;
  z-index: 1000;
  top: 0;
  right: 0;
  width: 100px;
  height: 100vh;
  padding: 0;
  margin: 0 auto;
  background: gray;
  text-align: center;
}

#menu > li {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 50px;
  height: 50px;
  border: 1px solid black;
  background-color: #fff;
  margin: 30px 0;
  border-radius: 100%;
}

#menu li:hover {
  background: rgba(255, 255, 255, 0.8);
}
#menu > .act {
  background: rgba(133, 15, 98, 0.7);
}
#menu > .act > a:hover {
  color: black;
}
#menu > .act > a {
  color: white;
}
```

### JS

```js
$(document).ready(function () {
  $("#fullpage").fullpage({
    sectionsColor: ["#daea99", "#bdeaf1", "#e8d4ef", "#f2ddc7"],
    anchors: ["firstPage", "secondPage", "3rdPage", "4thpage"],
    menu: "#menu",
    onLeave: function (index, nextIndex, direction) {
      // 메뉴 항목에 'act' 클래스 추가/제거
      $("#menu>li")
        .eq(nextIndex - 1)
        .addClass("act")
        .siblings()
        .removeClass("act");
      console.log(index);
      console.log("nextIndex" + nextIndex);
    },
  });

  $("#menu>li").click(function () {
    $(this).addClass("act").siblings().removeClass("act");
  });
});
```
