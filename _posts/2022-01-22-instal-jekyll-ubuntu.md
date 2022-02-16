---
layout: "post"
title: "Cara Instal Jekyll Pada Ubuntu"
date: 2022-01-22 09:00:00 +0700
---

Jekyll adalah _static site generator_ yang dibuat dengan menggunakan bahasa pemrograman Ruby.

Untuk menginstall jekyll, pastikan komputer anda sudah terinstal beberapa paket berikut.

* Ruby (versi 2.5.0 keatas), cek dengan perintah `ruby -v`
* RubyGems, cek dengan perintah `gem -v`
* GCC dan Make, cek dengan perintah `gcc -v`, `g++ -v`, dan `make -v`

Jika belum terinstal berikut adalah cara instalasinya.

## Instal Ruby dan RubyGems

Update daftar paket.

```bash
sudo apt update
```

Instal Ruby dan RubyGems.

```bash
sudo apt-get install ruby-full build-essential zlib1g-dev
```

Atur `PATH` untuk RubyGems.

```bash
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

Cek instalasi.

```bash
ruby -v
gem -v
```

## Instal GCC, G++ dan Make

Update daftar paket.

```bash
sudo apt update
```

Instal paket.

```bash
sudo apt install build-essential
```

Cek instalasi.

```bash
gcc -v
g++ -v
make -v
```

## Instal Jekyll

Install jekyll dan bundler melalui gem.

```bash
gem install jekyll bundler
```

Buat sebuah situs jekyll baru.

```bash
jekyll new myblog
```

Masuk ke situs jekyll yang sudah dibuat.

```bash
cd myblog
```

Jalankan jekyll.

```bash
jekyll serve
```

Atau

```bash
bundle exec jekyll serve
```

Buka situs jekyll pada alamat `http://localhost:400`.