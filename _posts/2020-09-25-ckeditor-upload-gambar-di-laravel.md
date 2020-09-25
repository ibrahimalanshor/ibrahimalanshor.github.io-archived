---
title: CKEditor Upload Gambar Di Laravel
date: 2020-09-25 19:10:00 +0700
layout: post
categories: laravel
---

![CKEditor]({{ site.url }}/img/ckeditor.png)

**CKEditor** adalah sebuah teks editor WYSIWYG yang digunakan untuk menulis konten di halaman web.

Selain menulis konten berupa teks, kita juga bisa menyisipkan gambar di tulisan kita.

Untuk itu saya akan membuat tutorial untuk membuat upload gambar di laravel.

## Mengatur Konfigurasi File Browser

Pertama kita akan mengatur konfigurasi file browser CKEditor.

```javascript
CKEDITOR.replace('content', {
    filebrowserUploadUrl: '{% raw %}{{ route("user.media.save", ["_token" => csrf_token()]) }}{% endraw %}',
    filebrowserUploadMethod: 'form'
})
```

## Membuat Method Upload Di Controller

Buat method untuk mengupload gambar CKEditor.

```php
// Save Image From CKEditor
public function save(Request $request)
{
    if ($request->hasFile('upload')) {
        $file = $request->upload;
        $fileName = pathinfo($file->getClientOriginalName(), PATHINFO_FILENAME);
        $fileName = $fileName.'_'.time().'.'.$file->getClientOriginalExtension();

        Storage::putFileAs('public/images', $file, $fileName);

        Media::create([
            'user_id' => $this->id(),
            'file' => $fileName
        ]);

        $ckeditor = $request->CKEditorFuncNum;
        $url = asset('storage/images/'.$fileName);
        $msg = 'Image uploaded successfully';

        $response = "<script>window.parent.CKEDITOR.tools.callFunction($ckeditor, '$url', '$msg')</script>";

        @header('Content-type: text/html; charset=utf-8');

        return $response;
    } else {
        abort(404);
    }
}
```

Silahkan dicoba.