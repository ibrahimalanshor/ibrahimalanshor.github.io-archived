---
layout: post
title: "Cara Truncate Tabel Dengan Foreign Key Constraint MySQL"
tags: [js]
date: 2022-10-02 19:00:00 +0700
---

Statement `TRUNCATE` digunakan untuk menghapus semua data pada tabel.

`TRUNCATE` lebih efisien digunakan dibanding mengunakan `DELETE` statement tanpa klausa `WHERE`, karena `TRUNCATE` melakukan `DROP` tabel dan membuat ulang tabel tersebut, tidak menghapus data satu persatu baris.

Namun, jika ada foreign key constraint pada tabel yang akan di-`TRUNCATE`, operasi tersebut akan gagal.

```sql
TRUNCATE TABLE `users`;
-- ERROR 1701 (42000): Cannot truncate a table referenced in a foreign key constraint (`db`.`photos`, CONSTRAINT `photos_ibfk_1`)
```

Untuk mengatasinya anda dapat menontaktifkan pengecekan foreign key:

```sql
SET FOREIGN_KEY_CHECKS = 0; 
TRUNCATE table `users`; 
SET FOREIGN_KEY_CHECKS = 1;
```

Sumber: [https://stackoverflow.com/questions/5452760/how-to-truncate-a-foreign-key-constrained-table](https://stackoverflow.com/questions/5452760/how-to-truncate-a-foreign-key-constrained-table)