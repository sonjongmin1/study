# `리액트queryselector사용방법`

### useEffect 사용

## 활용예시

### detail.js

```js
import { useEffect } from "react";

const useCustomEffect = () => {
  useEffect(() => {
    let detailMain = document.querySelectorAll(".detailMain > div");

    detailMain.forEach((i) => {
      i.addEventListener("click", function () {
        i.style.backgroundColor = "red";
      });
    });
  }, []);
};
```

### detail.jsx

```js
// 가져올경로
import useCustomEffect from "../detail.js";

// 함수 호출
useCustomEffect();
```
