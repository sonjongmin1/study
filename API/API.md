# `API (Application Programming Interface)`

- 웹과 서버사이에서 서로 주고 받는 인터페이스
- API는 클라이언트가 네트워크를 통해 서버에 요청을 보내고, 서버는 네트워크를 통해 클라이언트에게 JSON 형식(또는 다른 데이터 형식)으로 응답을 돌려준다.

# API종류

- 웹 api (REST API, SOAP API, graphQL API)
- 운영체제 api
- 프레임워크 api

# REST API (Representational State Transfer)

- 대중적인 API
- REST 네트워크 클라이언트, 서버 통신방식(웹 기반)
- HTTP 기반으로 데이터를 교환
- REST API에서 서버를 보내줄때 JSON이 기반이여서 JSON을 알아야한다.

### JSON, XML(태그), CSV(쉼표), TEXT

- JSON은 데이터가 가볍다.
- 데이터를 교환할때 서버가 보내주는 방식

#### JSON 예시

```json
{
  "name": "Alice",
  "age": 25,
  "courses": ["Math", "Science", "History"],
  "address": {
    "street": "123 Main St",
    "city": "Wonderland"
  }
}
```

#### XML(태그) 예시

```xml
 <책제목>홍길동전</책제목>
 <저자>허군</저자>
```

#### CSV 예시

```csv
name,age,courses
Alice,25,"Math, Science, History"
```

### 공공 API (주로 REST API 사용)

- 서울시 공공 데이터 API: 대중교통, 날씨, 관광지 정보<br> https://data.seoul.go.kr/

- 공공 데이터 포털: 대한민국 공공정보<br> https://www.data.go.kr/

- OpenWeatherMap API : 글로벌 날씨 정보 <br>https://openweathermap.org/api

- Google Maps API: : 지도, 길찾기 정보 <br> https://developers.google.com/maps

# `Json 파싱`

- json 문자열 -> javascript 객체 변환
- json.parse(파싱데이터)
- json 데이터는 반드시 제목 내용 " " 쌍따옴표 사용 (템플릿 홑따옴표 사용 불가)

```js
let jsonData = `{"이름" :"홍길동","나이":20, "취미":["독서", "등산","코딩"]}`;
// 객체로 변환
let jsData = JSON.parse(jsonData);
console.log(jsonData);
console.log(jsData);
document.write(jsData.이름);
document.write(jsData.취미[1]);
document.write(jsonData.이름);

//  이중 삼중으로 겹칠수 있다.
let jsonData2 = `{"학생":{"이름":"홍길동"},"성적":{"수학":80, "영어":90}}`;
let jsData2 = JSON.parse(jsonData2);
console.log(jsonData2);
console.log(jsData2);
document.write(jsData2.학생.이름);
document.write(jsData2.성적.영어);
document.write(jsData2.성적.수학);
```

결과<br>
홍길동등산undefined홍길동9080
