---
title: Membuat Pagination Pada Laravel
layout: post
date: 2020-09-20 17:00:00 +0700
categories: laravel
---

Untuk membuat pagination pada Laravel sangatlah mudah, hanya beberapa langkah.

Langsung saja.

## Controller

Disini saya menampilkan semua data dari tabel `Category` dan saya pecah menjadi 10 data per-halaman.

```php
public function index()
{
    $categories = Category::paginate(10);

    return view('category', ['categories' => $categories]);
}
```

## View

Untuk menampilkanya sama seperti menampilkan data biasa. Lalu kita tambahkan sebaris kode untuk menampilkan pagination-nya.

```php
<table>
    <thead>
    	<tr>
    	    <th>No</th>
    	    <th>Name</th>
    	</tr>
    </thead>
    <tbody>
        @foreach($categories as $category)
    	    <tr>
                <td>{% raw %}{{ $loop->iteration }}{% endraw %}</td>
                <td>{% raw %}{{ $category->name }}{% endraw %}</td>
            </tr>
        @endforeach
    </tbody>
</table>
{% raw %}{{ $categories->links() }}{% endraw %}
```

