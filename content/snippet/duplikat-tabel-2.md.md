---
title: 'Duplikat Tabel MYSQL #2'
date: 2022-09-18 20:00:00 +0700
---

```sql
CREATE TABLE new_table LIKE source_table;
INSERT INTO new_table FROM SELECT * FROM source_table;
```