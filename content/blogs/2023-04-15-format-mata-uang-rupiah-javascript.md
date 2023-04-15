---
title: Format Mata Uang Rupiah Dengan Javascript
date: 2023-04-15 11:00:00 +0700
images: ['/images/blogs/format-rupiah/thumbnail.jpg']
---

Javascript menyediakan objek `Intl.NumberFormat` untuk memudahkan proses internationalization salah satunya memformat string/angka ke mata uang tertentu.

Untuk membuat objek `Intl.NumberFormat` anda dapat menggunakan `Intl.NumberFormat` constructor.

Contoh.

```js
const formatter = new Intl.NumberFormat()
```

Untuk menggunakannya agar dapat memformat string/angka ke mata uang rupiah, anda perlu mengirimkan `locale`-nya dan opsi `formatting`-nya pada constructor argument.

Untuk `locale` isi dengan kode negara Indonesia yaitu `id-ID`.

Untuk opsi `formatting`-nya dalam bentuk objek, dengan dua properti, `style` dan `currency`. Style digunakan untuk menentukan bentuk formatnya, contohnya `currency`, dan `currency` digunakan untuk menentukan mata uangnya, contohnya `IDR`.

```js
const formatter = new Intl.NumberFormat('id-Id', {
    style: 'currency',
    currency: 'IDR'
})
```

Setelah itu tinggal dipanggil, method `format` dari objek formatter yang sudah dibuat dengan mengirimkan string/angka yang akan diformat ke mata uang rupiah.

```js
const formatter = new Intl.NumberFormat('id-Id', {
    style: 'currency',
    currency: 'IDR'
})

console.log( formatter.format('12000') ) // Rp 12.000,00
console.log( formatter.format('99999') ) // Rp 99.999,00
console.log( formatter.format('145000') ) // Rp 145.000,00
console.log( formatter.format(450000 ) ) // Rp 450.000,00
console.log( formatter.format(18341234) ) // Rp 18.341.234,00
```