# `날씨 API`

https://openweathermap.org/guide

### 활용 1

```js
async function abcd() {
  try {
    let res = await fetch(
      `https://api.openweathermap.org/data/2.5/weather?lat={lat}&lon={lon}&appid={APIKEY}`
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
    `https://api.openweathermap.org/data/2.5/weather?lat={lat}&lon={lon}&appid={APIKEY}`
  );

  // json은 자바스크립트에서 사용할 수 없으므로 객체로 바꾼다.
  let data = await res.json();

  return data;
};
```

### 활용 3

```js
let temp = document.querySelector("#temp");
let wind = document.querySelector("#wind");
let position = document.querySelector("#position");
let intro = document.querySelector("#intro");

// 나의 API KEY
let API_key = "";
let cityName = "ansan";

let weather = async () => {
  let res = await fetch(
    `https://api.openweathermap.org/data/2.5/weather?q=${cityName}&appid=${API_key}&units=metric&lang=kr`
  );
  let data = await res.json();

  console.log(data);
  temp.textContent = data.main.temp;
  wind.textContent = data.wind.speed;
  position.textContent = data.name;
  intro.textContent = data.weather[0].description;
};

weather();
```

# `날씨 API 아이콘 가져오기`

```js
let temp = document.querySelector("#temp");
let wind = document.querySelector("#wind");
let position = document.querySelector("#position");
let des = document.querySelector("#des");
let weatherImg = document.querySelector("#weatherImg");
let iconUrl = "https://openweathermap.org/img/wn/10d@2x.png";

// 나의 API KEY
let API_key = "36c7e8662756cdc79406a17b81f4940b";
let cityName = "ansan";

let weather = async () => {
  let res = await fetch(
    `https://api.openweathermap.org/data/2.5/weather?q=${cityName}&appid=${API_key}&units=metric&lang=kr`
  );
  let data = await res.json();

  console.log(data);
  temp.textContent = data.main.temp;
  wind.textContent = data.wind.speed;
  position.textContent = data.name;
  des.textContent = data.weather[0].description;

  if (data.weather[0].icon == "04d") {
    weatherImg.style.backgroundImage = `url(${iconUrl})`;
  }
};

weather();
```
