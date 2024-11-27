# Html

```html
<div id="container">
  <ul id="fadeImg">
    <li class="on"><img src="../img/modal1.png" alt="" /></li>
    <li><img src="../img/modal2.png" alt="" /></li>
    <li><img src="../img/modal3.png" alt="" /></li>
  </ul>
  <ul id="bar">
    <li class="on"></li>
    <li></li>
    <li></li>
  </ul>
</div>
```

# Css

```css
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

ul {
  list-style: none;
}

a {
  text-decoration: none;
}

body {
  width: 100vw;
}

#container {
  position: relative;
  width: 100%;
  height: 200px;
  background-color: skyblue;
}

#fadeImg {
  position: relative;
  width: 100%;
  height: 100%;
}

#fadeImg > li {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  opacity: 0;
  transition: 0.5s;
}

#fadeImg > li.on {
  opacity: 1;
}

#fadeImg > li > img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

#bar {
  position: absolute;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  top: 170px;
  left: 50%;
  transform: translateX(-50%);
  width: 15%;
  height: 30px;
  background-color: yellow;
}

#bar > li {
  width: 20px;
  height: 20px;
  background-color: white;
  border-radius: 30px;
}

#bar > li.on {
  background-color: blue;
}
```

# Js

```js
let imgs = document.querySelectorAll("#fadeImg > li");
let bars = document.querySelectorAll("#bar > li");
let tot = imgs.length;
let count = 0;
let playTime = "";

function showImg(index) {
  imgs.forEach((list) => {
    list.classList.remove("on");
  });

  imgs[index].classList.add("on");

  bars.forEach((bar) => {
    bar.classList.remove("on");
  });

  bars[index].classList.add("on");
}

function autoPlay() {
  playTime = setInterval(() => {
    count++;
    if (count >= tot) {
      count = 0;
    }
    showImg(count);
  }, 3000);
}

autoPlay();

function stopPlay() {
  clearInterval(playTime);
}

bars.forEach((item, index) => {
  item.addEventListener("click", function () {
    stopPlay();
    count = index;
    showImg(count);
    setTimeout(autoPlay, 3000);
  });
});
autoPlay();
```
