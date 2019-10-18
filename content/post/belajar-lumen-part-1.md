---
title: "Belajar Lumen Part 1"
date: 2019-10-17T22:47:15+07:00
draft: false
---

### Pengenalan Lumen
Supaya tidak mudah lupa disini saya akan mencatat tahapan saya belajar **lumen**, bagi yang tidak tahu lumen itu apaan sih? hhe. Oke jadi [Lumen](https://lumen.laravel.com/) itu adalah sebuah micro framework PHP yang dibuat oleh pengembang **laravel**, dan kenapa disebut micro framework itu karena si lumen ini memang di rancang untuk membuat proyek dengan skala yang lebih kecil agar lebih ringan. Berbeda dengan laravel yang banyak sekali library terpasang pada saat penginstalan yang mungkin bagi kita library itu tidak semuanya kita pakai yang mengakibatkan file proyek kita cukup besar, di lumen sendiri banyak library-library pada laravel yang di hilangkan atau tidak ada pada saat pemasangan sehingga ukuran file dari proyek lumen ini relatif kecil.  

Lumen ini biasanya dipakai untuk membuat **webservice REST API**, tetapi lumen ini juga bisa dipakai untuk membuat aplikasi web pada umumnya, misalnya membuat sistem informasi, akan tetapi kalau untuk membuat aplikasi web library nya kurang begitu lengkap sehingga membutuhkan pekerjaan tambahan untuk memasang library-library yang dibutuhkan.  

### Penginstalan Lumen
Untuk menginstall lumen salah satu caranya kamu bisa menggunakan **composer**, dengan perintah seperti di bawah ini :
{{< highlight bash >}}
$ composer create-project --prefer-dist laravel/lumen belajarLumen
{{< /highlight >}}
Perintah di atas menandakan kamu membuat sebuah projek lumen dengan nama projek **belajarLumen**. Tunggu beberapa saat sampai proses penginstalan lumen selesai, oh iya proses penginstalan ini membutuhkan koneksi internet ya.

### Menjalankan Lumen
Setelah proses penginstalan selesai sekarang kita coba untuk mengakses projek lumen tersebut, silakan kamu pindah ke direktori root projek lumen kamu dimana disini saya kasih nama belajarLumen lalu ketikkan perintah seperti dibawah ini
{{< highlight bash >}}
$ cd belajarLumen   # berpindah ke root projek lumen
$ php -S localhost:8000 -t public   # menjalankan projek lumen
PHP 7.2.19-0ubuntu0.18.04.2 Development Server started at Thu Oct 17 23:21:56 2019
Listening on http://localhost:8000
Document root is /home/aliya-azka/Code/belajarLumen/public
Press Ctrl-C to quit.
{{< /highlight >}}
Sekarang coba kamu akses url  http://localhost:8000 dengan menggunakan browser, apabila browsernya menampilkan tampilan seperti berikut :
![Example image](/img/belajar-lumen/show.png)   

Itu berarti kamu berhasil memasang projek lumen, sesuai dengan gambar di atas saya memasang lumen dengan versi 6.1.0 dan laravel component versi 6.0.  

Pada postingan selanjutnya kita akan membahas bagaimana cara membuat sample crud RESTAPI dengan lumen.


