---
title: Menyamaratakan Tinggi Kolom Bootstrap
date: 2020-09-17 09:00:00 +0700
layout: post
categories: css, bootstrap
---

Secara *default* tinggi kolom pada **bootstrap** sama, tapi tidak dengan konten didalamnya. Hal itulah yang menyebabkan tinggi dari kolom bootstrap terlihat berbeda.

Untuk menyamaratakanya kita hanya perlu memberi sebuah atribut css pada kontent di dalam kolom.

Contohnya disini saya memiliki 4 buah kolom, yang masing-masing berisi sebuah `card`.

```html
<div class="row">
    <div class="col-md-3">
        <div class="card">
            <div class="card-body">
                Saya Suka Primata Pemberani
            </div>
        </div>
        <div>...</div>
    </div>
</div>
```

Setelah dibuka dapat dilihat tinggi masing-masing kolom berbeda. 

![Kolom Bootstrap]({{ site.url }}/img/tinggi-kolom-bootstrap.png)

Nah, untuk memperbaikinya, kita hanya perlu memberinya class `h-100` pada `card` agar tinggi card tersebut mengikuti kolomnya.

```html
<div class="row">
    <div class="col-md-3">
        <div class="card h-100">
            <div class="card-body">
                Aku Suka Primata Pemberani
            </div>
        </div>
        <div>...</div>
    </div>
</div>
```

Dan berikut hasilnya.

![Kolom Bootstrap Sama]({{ site.url }}/img/kolom-bootstrap-sama.png)

Silahkan Dicoba.
