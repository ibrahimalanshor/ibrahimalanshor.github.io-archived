---
title: 'MySQL - ERROR 1701 (42000): Cannot truncate a table referenced in a foreign key constraint'
date: 2022-10-02 19:00:00 +0700
---

```sql
SET FOREIGN_KEY_CHECKS = 0; 
TRUNCATE table `users`; 
SET FOREIGN_KEY_CHECKS = 1;
```