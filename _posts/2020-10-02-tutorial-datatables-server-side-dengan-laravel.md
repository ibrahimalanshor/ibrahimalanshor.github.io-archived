---
title: Tutorial Datatables Server Side Dengan Laravel
date: 2020-10-02 20:00:00 +0700
categories: datatables, laravel
layout: post
---

**Datatables** merupakan salah satu plugin jquery yang cukup populer dan juga sangat berguna untuk kebutuhan sebuah sitem aplikasi.

Datatables adalah plugin jquery yang berguna untuk menampilkan data dalam bentuk tabel, dan memiliki fitur tambahan seperti, pencarian, pengurutan, *pagination*, dll.

Dalam menampilkan data, datatables memiliki dua cara yang bisa dilakukan, yaitu *Client Side* dan *Server Side*.

Kali ini saya akan membahas mengenai *Server Side*, yang artinya data yang akan diambil diproses di sisi server kemudian dikembalikan ke client untuk diproses dengan datatables.

Dan tentunya laravel sudah menyediakan paket khusus untuk memudahkan kita bekerja dengan datatables, yaitu *Yajra Datatables*.

## Instalasi

Install paket **Yajra Datatables** dengan composer.

```bash
composer require yajra/laravel-datatables-oracle:"~9.0"
```

## Penggunaan

Untuk penggunaanya kita bisa mengkombinasikanya dengan Eloquent maupun dengan Query Builder.

Disini saya akan menggunakan Eloquent, dan saya akan menampilkan data user.

Berikut controller-nya.

```php
public function index(Request $request)
{
    if ($request->ajax()) {
        $users = User::all();
        return Datatables::of($users)->make(true);
    }
    return view('user.index');
}
```

Berikut blade-nya.

```html
<div class="table-responsive">
    <table class="table table-striped table-bordered">
        <thead>
            <tr>
                <th>Name</th>
                <th>Email</th>
            </tr>
        </thead>
    </table>
</div>

<script>
    let ajax_url = "{% raw %}{{ route('user.index') }}{% endraw %}"
</script>
```

Berikut javascript-nya.

```javascript
const table = $('table').DataTable({
    serverSide: true,
    ajax: ajax_url,
    columns: [
        { data: 'name' },
        { data: 'email' },
    ],
})
```

Silahkan dicoba.