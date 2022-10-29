---
layout: post
title: "Alokasi Memori Dinamis Menggunakan malloc() pada C"
tags: [c]
date: 2022-10-29 18:30:00 +0700
---

`malloc` adalah built in function yang terdapat pada file header `<stdlib.h>`.

`malloc` adalah singkatan dari __memory allocation__, yang digunakan untuk mengalokasikan sebuah blok memori secara dinamis berdasarkan ukuran yang ditentukan.

Syntax:

```c
ptr = (cast_type*) malloc(size);
```

Jika berhasil, `malloc` mengembalikan `void` pointer yang bisa di-_cast_ ke bentuk lainnya, jika tidak `malloc` mengembalikan `NULL`.

Contoh Program.

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int i, n;

    printf("Enter number of elements: ");
    scanf("%d", &n);

    int *ptr = (int *) malloc(n * sizeof(int));

    if (ptr == NULL) {
        printf("Memory not available");
        exit(1);
    }

    for (i = 0; i < n; i++) {
        printf("Enter element: ");
        scanf("%d", ptr + i);
    }

    for (i = 0; i < n; i++) {
        printf("%d ", *(ptr + i));
    }

    free(ptr);

    return 0;
}
```

Sumber: [https://www.youtube.com/watch?v=Vch7_YeGKH4](https://www.youtube.com/watch?v=Vch7_YeGKH4)
