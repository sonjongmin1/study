### vue 설치 명령어() / cli방식

### 확장 프로그램 vue official 설치

```js
npm install -g @vue/cli
```

### 프로젝트 폴더 만들기

```js
vue create test03
```

### vue3 버전 선택

### vue 실행 방법

```js
npm run serve
```

### `Vue`

### template

- 태그들이 들어가는 공간

### script

- 명령어가 들어가는 공간

### vue의 onclick 사용 방법

```html
<template>
  <div>
    <h1>현재 카운트 : {{count}}</h1>
    <button @click="addcount">증가</button>
  </div>
</template>
<script setup>
  // vue 3에서 지원하는 setup 방식
  import { ref } from "vue";
  const count = ref(0);
  const addcount = () => {
    count.value++;
  };

  <!-- setup 사용 안하면 복잡함-->
</script>
```

### 파일 생성방법 component파일 > 파일생성 파일이름.vue

- v-bind, v-if, v-for

```html
<template>
  <div>
    <h1 v-if="isOn">이 텍스트는 토글됩니다.</h1>
    <button @click="toggleText">보이기/숨기기</button>
  </div>
</template>
<script setup>
  import { ref } from "vue";
  const isOn = ref(true);
  const toggleText = () => {
    isOn.value = !isOn.value;
  };
</script>
```

# vue의 router

```js
npm install vue-router@4
```