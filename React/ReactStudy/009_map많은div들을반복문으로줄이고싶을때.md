# `반복문으로 같은 html 반복생성하는 법`

### map()사용법

1. array 자료 갯수만큼 함수안의 코드 실행

```js
[1, 2, 3].map(function () {
  console.log(1);
});
```

### 결과

111

2. 함수의 파라미터는 array안에 있던 자료

```js
[1, 2, 3].map(function (a) {
  console.log(a);
});
```

#### 결과

123

3. return에 뭐 적으면 array로 담아줌

```js
[1, 2, 3].map(function (a) {
  return "12345";
});
```

#### 결과

["12345","12345","12345"]

### 활용예시

```js
{
  글제목.map(function (a, i) {
    return (
      <div className="list">
        <h4>{글제목[1]}</h4>
        <p>2월 17일 발행</p>
      </div>
    );
  });
}
```

- i는 반복문 돌 때 마다 0부터 1씩 증가하는 정수

### 결론

#### 비슷한 html 반복생성하려면 map()쓰면 된다.
