# Html

```html
<input type="checkbox" id="chkbox" /> <label for="chkbox"></label>
```

# Css

```css
input[id="chkbox"] {
  display: none;
}

label {
  display: inline-block;
  width: 25px;
  height: 25px;
  background-color: skyblue;
}

input[type="checkbox"]:checked + label {
  background-color: yellow;
}

input[type="checkbox"]:checked + label::before {
  content: "V"; /* V 표시 */
}

input[type="checkbox"]:not(:checked) + label::before {
  content: ""; /* V를 숨김 */
}
```
