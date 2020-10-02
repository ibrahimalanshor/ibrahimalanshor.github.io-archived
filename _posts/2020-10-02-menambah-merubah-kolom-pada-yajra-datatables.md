---
title: Menambah dan Merubah Kolom Pada Yajra Datatables
layout: post
categories: laravel, datatables
date: 2020-10-02 20:20:00 +0700
---

Setelah memasang datatables pada postingan sebelumnya, kali ini saya akan memberikan cara untuk menambah dan merubah kolom pada **Yajra Datatables**.

## Menambah Kolom Index

Untuk menambah kolom index atau kolom nomer pada tabel, kita bisa menambahkan method `addIndexColumn`.

```php
Datatables::of($users)
    ->addIndexColumn()
    ->make(true);
```

Untuk menampilkanya, kita tinggal menambah kolomnya di javascript.

```javascript
const table = $('table').DataTable({
    serverSide: true,
    ajax: ajax_url,
    columns: [
        { data: 'DT_RowIndex' },
        { data: 'name' },
        { data: 'email' }
    ]
})
```

## Menambah Kolom Baru

Untuk menambah kolom baru, kita bisa menggunakan method `addColumn`.

Contoh, disini saya akan menambah kolom status yang berisi Pelajar.

```php
Datatables::of($users)
    ->addIndexColumn()
    ->addColumn('status', 'Pelajar')
    ->make(true);
```

Untuk menampilkanya, kita tinggal menambah kolomnya di javascript.

```javascript
const table = $('table').DataTable({
    serverSide: true,
    ajax: ajax_url,
    columns: [
        { data: 'DT_RowIndex' },
        { data: 'name' },
        { data: 'email' },
        { data: 'status' }
    ]
})
```

## Merubah Kolom

Untuk merubah kolom, kita bisa menggunakan method `editColumn`.

Contoh, disini saya akan merubah kolom name.

```php
Datatables::of($users)
    ->addIndexColumn()
    ->addColumn('status', 'Pelajar')
    ->editColumn('name', 'Hai {% raw %} {{ $name }} {% endraw %}')
    ->make(true);
```

Sekian, silahkan dicoba.