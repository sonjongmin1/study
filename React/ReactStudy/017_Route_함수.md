# react-router-dom에서 제공하는 함수

## `useNavigate`

- 페이지 이동도와주는 useNavigate(); 페이지 이동할수있는 함수 들어있음

```js
import { useNavigate } from "react-router-dom";

let navigate = useNavigate();

<div
  onClick={() => {
    navigate("/detail");
  }}
>
  Detail
</div>;
```

- \<Link>\</Link>태그 같은경우는 a태그와 같은 기능이지만
- useNavigate는 다양한 태그들에 적용하여 페이지 이동을 적용 할 수 있다.

```js
<div
  onClick={() => {
    navigate(1);
  }}
>
  Detail
</div>;

<div
  onClick={() => {
    navigate(-1);
  }}
>
  Detail
</div>;
```

- 1은 앞으로 한페이지 이동, 앞으로가기 버튼
- -1은 뒤로 한페이지 이동, 뒤로가기 버튼
- 2, -2적으면 앞으로 뒤로 2번 이동

## `404페이지 만들기`

```js
<Route path="*" element={<div>존재하지 않는 페이지</div>} />
```

- "\*"는 이외의 모든것을 뜻한다.

## `Nested Routes`, tag안에 tag

아래와 같이 작성해도 되나

```js
<Route path="/about/member" element={<About/>}/>
<Route path="/about/location" element={<About/>}/>
```

### Nested Routes를 사용하여 효율적으로 코드를 만들수 있다.

- 장점1. route 작성이 간단해진다.
- 장점2. \<Outlet>\</Outlet>(어디보여줄지 정하기)를 사용하면 아래와같이 nested route 접속시엔 element 2개가 보인다.
  - /about/member 접속시 \<About>&\<div>멤버\</div> 둘다 보인다.
- nested routes의 element 보여주는 곳은 \<Outlet>이다.

```js
<Route path="/about" element={<About />}>
  <Route path="member" element={<div>멤버</div>}></Route>
  <Route path="location" element={<About />}></Route>
</Route>
```

- /about 페이지를 만들고, /about/member, /about/location 페이지도 만들고 싶을때 사용

### Q. nested routes 언제쓰는지?

- 여러 페이지 필요할때
- 여러 유사한 페이지 필요할때
- 모달창기능, 탭기능 route로 만들 수 있다.

1. UI만들면 앞으로, 뒤로가기 버튼 이용가능
2. 페이지 이동이 쉬움 (UI 스위치 조작 쉬움)
