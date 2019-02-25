---
title: "Membuat Blog Dengan Hugo"
date: 2018-08-24T19:49:00+07:00
draft: false
---

Sekarang saya mencoba memberikan penjelasan bagaimana caranya membuat blog dengan menggunakan **Hugo**, Hugo adalah framework untuk membuat website dengan konsep SSG (*Static Site Generator*), dimana SSG ini dalam pembuatan webnya tidak memerlukan database sehingga performa web nya bisa lebih cepat di bandingkan web berplatform CMS (*Content Management System*) karena CMS biasanya menggunakan database untuk menyimpan postingan baik berupa artikel, gambar, dan yang lainnya.  

Karena nantinya blog yang kita buat ini akan kita deploy ke github pages, maka kita harus install git terlebih dahulu di sistem kita, setelah git terpasang selanjutnya kita install Hugo.  

### 1. Install Git dan Hugo

Disini saya menggunakan sistem operasi ubuntu yang merupakan salah satu distribusi Linux  
Ketikan perintah dibawah untuk menginstall Git di Linux  
{{< highlight bash >}}
$ apt install git
{{< /highlight >}}
Untuk memeriksa git apakah sudah terpasang di sistem kita sekaligus untuk melihat versi berapa, gunakan perintah di berikut ini
{{< highlight bash >}}
$ git --version
{{< /highlight >}}
Setelah git terpasang sekarang waktunya kita **Install Hugo**, untuk melihat berbagai versi Hugo silakan lihat di [repositori Hugo](https://github.com/goHugoio/Hugo/releases).  
{{< highlight bash >}}
$ wget https://github.com/gohugoio/hugo/releases/download/v0.53/hugo_0.53_Linux-64bit.deb
{{< /highlight >}}
setelah source selesai di download, kita install dengan perintah:  
{{< highlight bash >}}
$ sudo dpkg -i hugo_0.53_Linux-64bit.deb
{{< /highlight >}}
Untuk mengecek berhasil atau tidaknya kita menginstall hugo, ketikan perintah berikut:
{{< highlight bash >}}
$ hugo version
{{< /highlight >}}
Apabila muncul tampilan seperti dibawah ini berarti proses menginstall hugo nya sudah berhasil.

![Example image](/img/membuat-blog-dengan-hugo/hugo-version.png)

### 2. Membuat blog baru dengan hugo

Untuk membuat blog baru hugo menggunakan perintah di bawah ini:
{{< highlight bash >}}
hugo new site [nama-blog]
{{< /highlight >}}
Sebagai contoh saya akan membuat blog bernama **blogku**
![Example image](/img/membuat-blog-dengan-hugo/create_new_site.png)
Maka hugo akan membuatkan direktori baru beserta strukturnya. Serta akan memberikan keterangan di terminal mengenai langkah selanjutnya yang harus di lakukan supaya blogku bisa di jalankan atau di akses via browser

### 3. Menambahkan tema
Berdasarkan keterangan pada saat kita membuat blog baru, kita di anjurkan menambahkan tema pada blog hugo kita, di hugo sendiri ada banyak tema dari banyak kontributor dan disebarkan secara gratis, silakan cari tema yang kamu sukai di [sini](https://themes.gohugo.io/).

Setelah menemukan tema yang sesuai dengan apa yang kamu inginkan, untuk memasang temanya terlebih dahulu baca dokumentasi dari tema tersebut karena disana ada konfigurasi yang harus diikuti agar temanya bisa digunakan.
Untuk mengistall tema tersebut masuklah ke direktori **themes**, lalu ketikan perintah dibawah ini untuk mendownload / clone sumber temanya dari github
{{< highlight bash >}}
$ git clone [URL_TEMANYA]
{{< /highlight >}}
Sebagai contoh saya akan memasang tema yang bernama [hugo-journal](https://themes.gohugo.io/hugo-journal/)
{{< highlight bash >}}
$ git clone https://github.com/damiencaselli/hugo-journal.git
{{< /highlight >}}
Setelah tema berhasil terpasang, kembali pindah ke direktori *root* blognya dan jalankan server hugo.
{{< highlight bash >}}
$ cd ..
$ hugo server
{{< /highlight >}}
Maka hugo akan menjalankan server pada alamat default [http://localhost:1313](http://localhost:1313)
![Example image](/img/membuat-blog-dengan-hugo/hugo_server.png)
![Example image](/img/membuat-blog-dengan-hugo/view_post.png)
Setelah berhasil menambahkan tema sekarang kita lanjut menambahkan artikel/konten pada blog.
### 4. Menulis artikel di blog hugo
Untuk membuat artikel ketikkan perintah di bawah ini di root direktori blognya
{{< highlight bash >}}
$ hugo new post/[nama-file-konten].md
{{< /highlight >}}
Sebagai contoh:
{{< highlight bash >}}
$ hugo new post/membuat-blog-dengan-hugo.md
{{< /highlight >}}
Maka file baru akan terbuat pada direktori **content/post/** dengan nama **membuat-blog-dengan-hugo.md**
![Example image](/img/membuat-blog-dengan-hugo/new_post.png)
Jangan lupa mengubah nilai *draft* pada *Front Matter* menjadi **false**.

Setelah itu simpan, lalu jalankan servernya dan coba lihat perubahannya
![Example image](/img/membuat-blog-dengan-hugo/view_post_2.png)
Mungkin untuk artikel mengenai pembuatan blog nya cukup sampai sini saja, selanjutnya kita akan membahas bagaimana caranya **deploy blog hugo ini ke server** di post yang selanjutnya
