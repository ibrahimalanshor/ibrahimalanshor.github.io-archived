---
layout: post
title: "Cara Membedakan Style tag &lt;code&gt; yang diluar tag &lt;pre&gt;"
tags: [css]
date: 2022-07-12 21:00:00 +0700
---

```css
pre > code {
  color: red;
}
:not(pre) > code {
  color: blue;
}
```

```html
<pre>
  <code>var a  = 12</code>
  <code>var b  = 10</code>
</pre>

<code>console.log</code>
```

Tag `<code>` yang didalam tag `<pre>` akan berwarna merah, dan yang diluar berwarna biru.