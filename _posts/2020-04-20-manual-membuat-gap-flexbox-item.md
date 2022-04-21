---
layout: 'post'
title: 'Cara Manual Membuat Gap Pada Flexbox Item'
date: 2022-04-21 10:30:00 +0700
---

Flexbox item terkadang membutuhkan gap/jarak antar item.

Untuk membuatnya dapat dengan cara manual memanfaatkan properti `margin`.

Pada flexbox container-nya berikan negatif margin horizontal sebesar jarak gapnya.

Pada flexbox item-nya berikan padding horizontal sebesar jarak gapnya.

Untuk mengatasi overflow scroll tambahkan padding horizontal pada containernya sebesar jarak gapnya.

```css
.container {
  padding: 10px;
}
.row {
  display: flex;
  margin: 0 -10px;
}
.col {
  padding: 0 10px;
}
.box {
  border: 1px solid #ddd;
  padding: 10px;
}
```

```html
<div class="container">
  <div class="row">
    <div class="col">
      <div class="box">
        Col
      </div>
    </div>
    <div class="col">
      <div class="box">
        Col
      </div>
    </div>
    <div class="col">
      <div class="box">
        Col
      </div>
    </div>
    <div class="col">
      <div class="box">
        Col
      </div>
    </div>
  </div>
</div>
```