# `emmet`

### HTML 작성 시 편리하게 작성할 수 있도록 도와주는 자동완성 기능의 플러그인<br>VS Code에는 기본적으로 emmet이 내장되어 있으므로 바로 사용이 가능하다.

#### 자식(childe) : >

- div > ul > li

```html
<div>
  <ul>
    <li></li>
  </ul>
</div>
```

#### 형제자매(sibling) : +

- div + p + bq

```html
<div></div>
<p></p>
<blockquote></blockquote>
```

#### 등반(climb-up):^

- div+div>p>span^bq

```html
<div></div>
<div>
  <p><span></span></p>
  <blockquote></blockquote>
</div>
```

- div+div>p>span^^^bq

```html
<div></div>
<div>
  <p><span></span></p>
</div>
<blockquote></blockquote>
```

#### 곱셈(multiplication) : \*

```html
<ul>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
</ul>
```

#### 그룹화(grouping) : ()

- div>(header>ul>li\*2>a)+footer>p

```html
<div>
  <header>
    <ul>
      <li><a href=""></a></li>
      <li><a href=""></a></li>
    </ul>
  </header>
  <footer>
    <p></p>
  </footer>
</div>
```

#### 속성 연산자(attribute operators)

- ID : #
- Class : .(dot)
- div#header+div.page+div#footer.class1.class2.class3

```html
<div id="header"></div>
<div class="page"></div>
<div id="footer" class="class1 class2 class3"></div>
```

#### 사용자 정의 속성(custom attributes) : [attr]

- td[title="Hello world!" colspan=3]

```html
<td title="Hello world!" colspan="3"></td>
```

#### 항목 번호 매기기(item numbering) : $

- ul>li.item$$$\*5

```html
<ul>
  <li class="item001"></li>
  <li class="item002"></li>
  <li class="item003"></li>
  <li class="item004"></li>
  <li class="item005"></li>
</ul>
```

#### 번호 매기기 기준 및 방향 변경(changing numbering base and direction) : \$@, \$@-

- ul>li.item$@3\*5

```html
<ul>
  <li class="item3"></li>
  <li class="item4"></li>
  <li class="item5"></li>
  <li class="item6"></li>
  <li class="item7"></li>
</ul>
```
