# gird

### 1.1 display : grid

: flex와 유사하게 자식들의 요를 그리드 배치한다.

### 1.2 grid-template-columns, grid-template-rows

: 그리드의 행과 열의 크기를 설정

```css
.container {
  grid-template-columns: 100px 200px 100px;
  grid-template-rows: 150px auto 150px;
}

grid-template-columns: repeat(3, 1fr);
grid-template-columns: 1fr 2fr;
```

### 1.3 grid-gap, column-gap, row-gap

: grid-gap 행과 열간의 간격을 동일하게 설정<br>
: column-gap 열간의 간격만 설정<br>
: row-gap 행 간의 간격만 설정

### 1.4 grid-template-areas

: grid 레이아웃을 시각적으로 정의

```css
.wrap {
  display: grid;
  grid-template-areas:
    'header header header header'
    'sidemenu content1 content1 content1'
    'footer footer footer footer';
}

.grid1 {
  grid-area: header;
  background-color: skyblue;
}
```

### 1.5 grid-column과 grid-row

```css
.grid1 {
  grid-column: 1 / 3;
  grid-row: 1 / 3;
  background-color: skyblue;
}
```

### 1.6 justify-items, justify-content

: justify-items : 아이템기준 start, end, center, stretch<br>
: justify-content : 컨테이너기준
