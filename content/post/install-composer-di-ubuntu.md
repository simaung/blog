---
title: "Install Composer Di Ubuntu 18.04"
date: 2018-12-25T21:29:42+07:00
draft: false
---

[Composer](https://getcomposer.org) merupakan perangkat lunak package manager untuk PHP. Fungsinya mirip dengan package manager di distro Linux atau Ubuntu, butuh script tertentu, dependensi, dan update cukup menggunakan Composer. Composer akan mengunduh script yang dibutuhkan.  

Sebelumnya persiapkan dependecy untuk menginstall dan menjalankan composer
{{< highlight bash >}}
$ sudo apt update
$ sudo apt install curl php-cli php-mbstring git unzip
{{< /highlight >}}

Pastikan kamu berada di home direktori, lalu download source composer menggunakan *curl* :
{{< highlight bash >}}
$ cd ~
$ curl -sS https://getcomposer.org/installer -o composer-setup.ph
{{< /highlight >}}

Selanjutnya verifikasi installer cocok dengan hash SHA-384 dengan hash installer terbaru yang ditemukan di halaman Kunci / [signature publik](https://composer.github.io/pubkeys.html) Composer. Copy hash dari halaman tersebut dan simpan di variabel shell dengan nama HASH
{{< highlight bash >}}
$ HASH=a5c698ffe4b8e849a443b120cd5ba38043260d5c4023dbf93e1558871f1f07f58274fc6f4c93bcfd858c6bd0775cd8d1
{{< /highlight >}}
Sekarang jalankan skrip php berikut untuk memverifikasi bahwa skrip instalasi aman untuk dijalankan
{{< highlight bash >}}
$ php -r "if (hash_file('SHA384', 'composer-setup.php') === '$HASH') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
{{< /highlight >}}
Kamu akan melihat tampilan seperti berikut jika hash yang kamu masukan cocok
{{< highlight bash >}}
$ Installer verified
{{< /highlight >}}
Jika kamu melihat **Installer corrupt**, maka kamu harus mengulang lagi download script instalasi dan mengecek kembali kamu menggunakan hash yang cocok. Lalu jalankan sintak untuk memverifikasi penginstall lagi, apabila berhasil di verifikasi kamu dapat melanjutkan ke tahapan selanjutnya
Untuk menginstall **composer** secara global di sistem kamu, gunakan perintah berikut yang akan mengunduh dan menginstal composer sebagai perintah seluruh sistem bernama composer, di bawah /usr/local/bin:
{{< highlight bash >}}
$ sudo php composer-setup.php --install-dir=/usr/local/bin --filename=composer
{{< /highlight >}}
Kamu akan melihat tampilan
{{< highlight bash >}}
Output
All settings correct for using Composer
Downloading...

Composer (version 1.6.5) successfully installed to: /usr/local/bin/composer
Use it: php /usr/local/bin/composer
{{< /highlight >}}
Untuk menguji instalasi kamu berhasil atau tidak, coba jalankan perintah berikut
{{< highlight bash >}}
$ composer
{{< /highlight >}}
Perintah di atas, akan mencetak versi, perintah dan argumen Composer, yang menandakan instalasi composer kamu berhasil
{{< highlight bash >}}
    _____
  / ____/___  ____ ___  ____  ____  ________  _____
 / /   / __ \/ __ `__ \/ __ \/ __ \/ ___/ _ \/ ___/
/ /___/ /_/ / / / / / / /_/ / /_/ (__  )  __/ /
\____/\____/_/ /_/ /_/ .___/\____/____/\___/_/
                    /_/
Composer version 1.8.4 2018-02-11 10:52:10

Usage:
  command [options] [arguments]
{{< /highlight >}}
