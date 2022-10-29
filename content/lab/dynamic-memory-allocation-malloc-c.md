---
title: 'Dynamic Memory Allocation Using Malloc C'
date: 2022-10-29 19:30:00 +0700
---

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
