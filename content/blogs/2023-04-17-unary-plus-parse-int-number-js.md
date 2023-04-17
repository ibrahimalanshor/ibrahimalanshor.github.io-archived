---
title: Unary Plus Vs parseInt vs Number Javascript
date: 2023-04-17 05:30:00 +0700
images: ['/images/blogs/unary-parse-number-js/thumbnail.jpg']
---

Unary Plus operator, parseInt function, dan Number constructor dapat digunakan untuk mengubah/mengonversi suatu nilai kedalam bentuk `Number` pada javascript.

```js
const nums = [123, '12345']

for (num of nums) {
    console.log(`parseInt(${num}) = `, parseInt(num))
    console.log(`+${num} = `, +num)
    console.log(`Number(${num})`, Number(num))
}

// parseInt(123) =  123
// +123 =  123
// Number(123) 123
// parseInt(12345) =  12345
// +12345 =  12345
// Number(12345) 12345
```

Dari ketiga metode diatas, ketiganya menghasilkan output yang sama. Namun pada beberapa contoh lain, ketiganya akan menghasilkan output yang berbeda.

`parseInt` akan mengavaluasi string dari kiri ke kanan ke dalam bentuk `Number` sampai bertemu dengan `non-numeric` value. Sedangkan `parseInt` dan `Number` akan mengembalikan `NaN` jika seluruh karakter string yang dikirimkan tidak dapat dievaluasi ke dalam bentuk `Number`.

```js
const nums = ['123edd', '1a', '999bob', 'bob']

for (num of nums) {
    console.log(`parseInt(${num}) = `, parseInt(num))
    console.log(`+${num} = `, +num)
    console.log(`Number(${num})`, Number(num))
}

// parseInt(123edd) =  123
// +123edd =  NaN
// Number(123edd) NaN
// parseInt(1a) =  1
// +1a =  NaN
// Number(1a) NaN
// parseInt(999bob) =  999
// +999bob =  NaN
// Number(999bob) NaN
// parseInt(bob) =  NaN
// +bob =  NaN
// Number(bob) NaN
```

> Dapat dilihat, walaupun string `123edd`, `1a`, dan `999bob` terdapat karakter non-numeric, `parseInt` tetap mengevaluasi beberapa karakter numeric sampai ditemukan karakter non-numeric. Sehingga hasilnya menjadi `123`, `1` dan `999`. Namun jika langsung ditemukan karakter non numerik, `parseint` langsung mengembalikan `NaN` pada string `bob`.

Untuk `null`, `true`, `false`, dsb, pada `Number` dan `unary plus` akan mengembalikan `0` atau `1`, sedangkan `parseInt` akan mengembalikan `NaN`.

```js
const nums = [null, true, false, []]

for (num of nums) {
    console.log(`parseInt(${num}) = `, parseInt(num))
    console.log(`+${num} = `, +num)
    console.log(`Number(${num})`, Number(num))
}

// parseInt(null) =  NaN
// +null =  0
// Number(null) 0
// parseInt(true) =  NaN
// +true =  1
// Number(true) 1
// parseInt(false) =  NaN
// +false =  0
// Number(false) 0
// parseInt() =  NaN
// + =  0
// Number() 0
```

Ketika string/value berupa bilangan float, mengggunakan `parseInt` akan menghilangkan angka dibelakang koma, sedangkan `Number` dan `unary plus` tetap memertahankannya.

```js
const nums = ['123.5', 144.5, '115.205']

for (num of nums) {
    console.log(`parseInt(${num}) = `, parseInt(num))
    console.log(`+${num} = `, +num)
    console.log(`Number(${num})`, Number(num))
}

// parseInt(123.5) =  123
// +123.5 =  123.5
// Number(123.5) 123.5
// parseInt(144.5) =  144
// +144.5 =  144.5
// Number(144.5) 144.5
// parseInt(115.205) =  115
// +115.205 =  115.205
// Number(115.205) 115.205
```

Saya biasanya menggunakan `parseInt` untuk mengambil karakter numerik pada string, yang mungkin terdapat karakter `non-numerik` juga seperti dari input user, sedangkan `Number` dan `unary plus` biasanya untuk mengonversi string yang numerik ke dalam bentuk `Number` dari string yang sudah pasti numerik seperti dari database atau sumber lain.

Sumber:

- [Unary plus (+) - JavaScript | MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Unary_plus)
- [parseInt() - JavaScript | MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/parseInt)
- [Number() constructor - JavaScript | MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/Number)