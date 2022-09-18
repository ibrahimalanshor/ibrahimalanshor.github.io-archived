---
layout: post
title: "Menghitung Relasi Terkait Pada Sequelize"
tags: [sequelize]
date: 2022-09-18 19:00:00 +0700
---

Misalnya disini ada tabel `articles` dan `categories`, `articles` berelasi dengan `categories` melalui kolom `categoryId`, berikut contoh kedua model sequelize-nya.

```js
const Article = sequelize.define(
  'article',
  {
    title: {
      type: DataTypes.STRING,
      allowNull: false,
    },
    content: {
      type: DataTypes.TEXT,
      allowNull: false,
    },
  },
  {
    tableName: 'articles',
  }
);

const Category = sequelize.define(
  'category',
  {
    name: {
      type: DataTypes.STRING,
      allowNull: false,
    }
  },
  {
    tableName: 'categories',
  }
);

Article.belongsTo(Category, {
  foreignKey: 'categoryId',
});

Category.hasMany(Article, {
  foreignKey: 'categoryId',
});
```

Saya ingin menampilkan semua `categories` beserta jumlah `articles`-nya. Berikut query SQL-nya.

```sql
SELECT 
    `categories`.*,
    COUNT(`articles`.`id`) AS `articleCount` 
FROM `categories` 
LEFT JOIN `articles`
ON 
  `articles`.`categoryId` = `categories`.`id`;
GROUP BY `categories`.`id`;
```

Berikut implementasinya pada query sequelize.

```js
Category.findAll({
  attributes: {
    include: [ [sequelize.fn('COUNT', sequelize.col('articles.id')), 'articleCount'] ]
  },
  include: [
    {
      model: Article,
      attributes: [],
      required: false
    }
  ],
  group: ['categories.id']
})
```