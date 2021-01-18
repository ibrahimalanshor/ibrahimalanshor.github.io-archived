---
layout: post
title: Cara Membalikan Tulisan Di Javascript
date: 2020-11-15 20:10:00 +0700
categories: javascript
---

Cara 1: Looping

```javascript
let text = "w3resource"

const reverse = text => {
  const tlen = text.length - 1
  let change = ""

  for(let i = tlen; i >= 0; i--){
    change += text[i]
  }

  text = change

  return text
}

text = reverse(text)

console.log(text)
```

Cara 2: Array Join

```javascript
let text = "w3resource"

const reverse = text => {
  return text.split("").reverse().join("")
}

text = reverse(text)

console.log(text)
```