## 다른 파일에 있던 변수 가져오기

### 1. export

### JS

```js
let a = 10;
export default a;
```

```js
export { 변수1, 변수2 };
```

### 2. import

### App.js

```js
import 작명 from "./data.js";
```

---

### export 여러개 하려면

### JS

```js
let a = 10;
let b = 100;

export default { a, b };
```

### App.js

```js
import { 변수1, 변수2 } from "경로";
```

## object

```js
let a = { name: "kim", age: 20 };
console.log(a.name);
```
