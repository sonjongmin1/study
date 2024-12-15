# `button`

```html
<h1>버튼 효과</h1>
<button class="btn">클릭</button>
```

```css
.btn {
  padding: 15px 25px;
  background-color: #10a44a;
  color: #f0bbc3;
  border-radius: 10px;
  cursor: pointer;
  box-shadow: 2px 5px darkblue;
}

/* 클릭했을때 */
.btn:active {
  box-shadow: 2px 2px darkblue;
  transform: translateY(4px);
}
```
