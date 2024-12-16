# html

```html
<h1>도서 목록</h1>
<input type="file" id="fileIn" />
<div id="display"></div>
```

# Css

```css
.bookD {
  color: blue;
}

.outBox {
  margin-top: 20px;
}

.inBox {
  display: flex;
}

.inBox > div:nth-child(2) {
  margin-left: 5px;
}

.outBox > div:not(:first-child) {
  padding: 0 10px;
}
```

# js

```js
document.getElementById("fileIn").addEventListener("change", function (e) {
  let files = e.target.files[0];
  if (files) {
    let reader = new FileReader();
    reader.onload = function (e) {
      try {
        let jsData = JSON.parse(e.target.result);
        let display = document.getElementById("display");

        jsData.forEach((item) => {
          let outBox = document.createElement("div");
          outBox.classList.add("outBox");
          let inBox = document.createElement("div");
          inBox.classList.add("inBox");

          let bookD = document.createElement("div");
          bookD.classList.add("bookD");
          bookD.textContent = item.교재;

          let nameD = document.createElement("div");
          nameD.classList.add("nameD");
          nameD.textContent = `저자 : ${item.저자},`;

          let yearD = document.createElement("div");
          yearD.classList.add("yearD");
          yearD.textContent = `출판년도 : ${item.출판년도}`;

          outBox.appendChild(bookD);
          outBox.appendChild(inBox);
          inBox.appendChild(nameD);
          inBox.appendChild(yearD);

          display.appendChild(outBox);
        });
      } catch (error) {
        document.write("에러발생", error.message);
      }
    };

    reader.readAsText(files);
  }
});
```

# json
