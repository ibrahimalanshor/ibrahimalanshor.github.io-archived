---
layout: post
title: "Cara Membuat Infinite Scroll Up Seperti Aplikasi Chat Dengan Javascript"
---

Jika anda perhatikan pada aplikasi chat misalnya WhatsApp, ia menerapkan infinite scroll up atau scroll tak terbatas ke atas.

Jadi ketika pengguna melakukan scroll ke atas, pesan sebelumnya akan diambil beberapa, sampai pesan yang pertama.

Kebetulan beberapa hari yang lalu saya sedang mencoba [socket.io](https://socket.io/) untuk membuat aplikasi chating sederhana.

Yang saya inginkan ketika awal membuka aplikasi, pesan yang ditampilkan tidak semuanya, hanya 30 saja.

Dan ketika pengguna melakukan scroll hingga batas tertentu, baru pesan yang terdahulu diambil lagi.

Kendala yang saya hadapi adalah ketika pesan yang terdahulu diambil, posisi scroll tiba-tiba berada pada posisi pesan yang pertama.

Kalau di aplikasi chat pada umumnya ketika pesan terdahulu diambil, posisi scroll tetap, namun scrollnya jadi panjang.

Kode awalnya seperti ini.

```javascript
document.getElementById('chat').addEventListener('scroll', async function () {
  if (this.scrollTop === 0 && size.value <= chats.value.total) {
    size.value += 25

    await getChats()
  }
})
```

Setelah cukup lama mencari jawaban, akhirnya saya menemukan solusinya pada link berikut:

[How to infinite-scroll with distance from top instead of bottom (good for chat scroll history)](https://forum.ionicframework.com/t/how-to-infinite-scroll-with-distance-from-top-instead-of-bottom-good-for-chat-scroll-history/7054/8)

Masalahnya sama seperti yang saya alami, dan disitu ada yang memberikan jawaban.

Kemudian saya coba dan berhasil.

```javascript
const scroll = pos => {
  const chatEL = document.getElementById('chat')

  chatEL.scrollTop = pos
}

document.getElementById('chat').addEventListener('scroll', async function () {
  if (this.scrollTop === 0 && size.value <= chats.value.total) {
    size.value += 25

    const lastPos = this.scrollHeight

    await getChats()

    scroll(this.scrollHeight - lastPos)
  }
})
```

Intinya ketika pesan terdahulu hendak diambil, simpan dulu posisi scroll pada saat itu, kemudian ketika pesannya sudah diambil lakukan scroll ke posisi terakhir yang tadi sudah disimpan.