# JSON 파일 가져오기

- json파일 형태 확장자는 .json : aa.json

### HTML

```html
<h1>json 파일 읽어오기</h1>
<input type="file" id="fileIn" />
<pre id="display"></pre>
```

### JS

```js
//json 파일 가져오기, 해석 : 인풋상자에 변화가 생기면 이벤트로 받고
document.getElementById("fileIn").addEventListener("change", function (e) {
  // 이벤트 파일의 0번째 가져오기
  let file = e.target.files[0];
  // 파일이 존재하면 파일을 읽어라
  if (file) {
    let reader = new FileReader();
    // 끝까지 다읽으면 할일을 해라
    reader.onload = function (e) {
      // 시도를해라
      try {
        let jsonData = e.target.result;
        let jsData = JSON.parse(jsonData);
        document.getElementById("display").textContent = `
                이름 : ${jsData.이름}
                취미 : ${jsData.취미.join(",")}
                나이 : ${jsData.나이}`;
      } catch (error) {
        // 읽어오지 못했을때는 아래와 같이 해라
        document.write("에러 발생", error.message);
      }
    };

    // text파일로 읽어주세요
    reader.readAsText(file);
  }
});
```
