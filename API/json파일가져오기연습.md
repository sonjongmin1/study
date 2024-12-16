# html

```html
<h1>학생출력</h1>
<input type="file" id="fileIn" />
<div id="display"></div>
```

# js

```js
document.getElementById("fileIn").addEventListener("change", function (e) {
  let files = e.target.files[0];
  if (files) {
    let re = new FileReader();
    re.onload = function (e) {
      try {
        // let jsonData = e.target.result;
        let jsData = JSON.parse(e.target.result);
        let display = document.getElementById("display");

        jsData.forEach((item) => {
          let outBox = document.createElement("div");
          outBox.classList.add("outBox");

          let nameD = document.createElement("div");
          nameD.classList.add("outBox");
          nameD.textContent = item.이름;

          let junD = document.createElement("div");
          junD.classList.add("junD");
          junD.textContent = item.전공;

          let hakD = document.createElement("div");
          hakD.classList.add("hakD");
          hakD.textContent = item.학년;

          outBox.appendChild(nameD);
          outBox.appendChild(junD);
          outBox.appendChild(hakD);

          display.appendChild(outBox);
        });
      } catch (error) {
        document.write("읽기 실패", error.message);
      }
    };
    re.readAsText(files);
  }
});
```
