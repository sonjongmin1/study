# `날씨 api`

### Home.jsx

```jsx
import React from "react";
import { useState, useEffect } from "react";

const Home = () => {
  const [weather, setWeather] = useState(null);
  const [dateTime, setDateTime] = useState(new Date());

  const API_KEY = "36c7e8662756cdc79406a17b81f4940b";
  const city = "ansan";
  const weatherAPI = `https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${API_KEY}&units=metric`;

  useEffect(() => {
    fetch(weatherAPI)
      .then((response) => response.json())
      .then((data) => {
        setWeather(data);
        console.log(weatherAPI); // URL 확인
        console.log(data);
      })
      .catch((error) => console.error("오류났다", error));

    const timer = setInterval(() => {
      setDateTime(new Date());
    }, 1000);
    return () => {
      clearInterval(timer);
    };
  }, [weatherAPI]); // 고정된 경우 빈 배열 사용

  return (
    <div className="page home">
      <h1>홈</h1>
      <p>오늘의 날짜: {dateTime.toLocaleDateString()}</p>
      <p>오늘의 시간: {dateTime.toLocaleTimeString()}</p>
      {weather ? (
        <>
          <p>도시 : {weather.name}</p>
          <p>온도 : {weather.main.temp}</p>
          <p>습도 : {weather.main.humidity}</p>
        </>
      ) : (
        <p>날씨 정보를 불러오는 중입니다...</p>
      )}
    </div>
  );
};

export default Home;
```
