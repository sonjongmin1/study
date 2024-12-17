# JSON 활용

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <script>
        let obj = { name: "홍길동", age: 20, hobbies: ["운동", "등산"] };
        let jsonS = JSON.stringify(obj);
        console.log(jsonS);
        // {"name":"홍길동","age":20,"hobbies":["운동","등산"]}

        let obj2 = [1, "aaa", { key: "value" }];
        let json2 = JSON.stringify(obj2);
        console.log(json2);
        //   [1,"aaa",{"key":"value"}]

        let obj3 = { name: "홍길동", age: 20, city: "서울" };
        let jsonS3 = JSON.stringify(obj3, ["name", "city"]);
        console.log(jsonS3);
        // {"name":"홍길동","city":"서울"}

        let obj4 = { name: "홍길동", age: 20, city: "서울" };
        let jsonS4 = JSON.stringify(obj4, (key, value) => {
          if (key == "age") {
            return value + 5;
          }
          return value;
        });
        console.log(jsonS4);
        //   {"name":"홍길동","age":25,"city":"서울"}

        let jsonS5 = JSON.stringify(obj4, null, "  ");
        //   객체로 만들때 각각 두칸을 띄어서장식
        console.log(jsonS5);
      /*   {
            "name": "홍길동",
             "age": 20,
             "city": "서울"
            } /*
    </script>
  </body>
</html>

<!--
 JavaScript에서JSON.stringify()문서사용자어떤 모양 으로 나 **배배열 을 JSON 형식으로 변환 
 -->
```
