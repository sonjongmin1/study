# 날씨API

https://openweathermap.org/guide

### 활용 1

```js
async function abcd() {
  try {
    let res = await fetch(
      `https://api.openweathermap.org/data/2.5/weather?lat={lat}&lon={lon}&appid=36c7e8662756cdc79406a17b81f4940b`
    );
    //   오류가 발생하면
    if (!res.ok) {
      throw new Error(
        `API를 가져오지 못했습니다. 오류코드는 ${res.status} 입니다.`
      );
    }
    // json은 자바스크립트에서 사용할 수 없으므로 객체로 바꾼다.
    let data = await res.json();
  } catch (error) {
    console.error(`실패했습니다.`, error);
  }
}
```

### 활용 2

```js
// 비동기식 사용하는 명령어, 자료가 완성이 될때까지 기다렸다가 자료를 보내주는 것
let abc = async () => {
  let res = await fetch(
    `https://api.openweathermap.org/data/2.5/weather?lat={lat}&lon={lon}&appid=36c7e8662756cdc79406a17b81f4940b`
  );

  // json은 자바스크립트에서 사용할 수 없으므로 객체로 바꾼다.
  let data = await res.json();

  return data;
};
```
