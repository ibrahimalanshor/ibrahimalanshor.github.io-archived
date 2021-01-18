---
layout: post
title: Cara Menampilkan Tanggal Dan Waktu Di Javascript
date: 2021-01-11 10:15:00 +0700
categories: javascript
---

Hehe nub

```javascript
const date = new Date()

const day = ['Sunday', 'Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday']
const today = day[date.getDay()]

let hours = date.getHours()
const period = (hours <= 12) ? "AM" : "PM" 
hours = (hours <= 12) ? hours : hours - 12

const minutes = date.getMinutes()
const second = date.getSeconds()

const time = `${hours} ${period} : ${minutes} : ${second}`

console.log("Today is", today)
console.log("Current Time is", time)
```

Sori nub malez mgodonf algoritma ini menertawaiku