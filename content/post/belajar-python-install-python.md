---
title: "Belajar Python: Install dan Update Python"
date: 2019-01-01T17:08:16+07:00
draft: false
---
Apabila kamu pengguna linux, python sebenarnya tidak perlu diinstall karena  sebagian besar distro linux sudah menyediakannya secara default.  

Untuk mengeceknya silakan ketikkan perintah di bawah ini
{{< highlight bash >}}
$ python --version
Python 2.7.1
{{< /highlight >}}
Seperti yang dapat kamu lihat diatas python yang terpasang adalah versi 2.7.1, sebenarnya python ini ada dua versi yang beredar yaitu versi 2 dan versi 3.

Untuk mengecek masing-masing versi silakan kamu ketikkan perintah berikut
{{< highlight bash >}}
# untuk mengecek versi 2
$ python --version
Python 2.7.1

# untuk mengecek versi 3
$ python3 --version
Python 3.6.7
{{< /highlight >}}
Versi default python yang terpasang di ubuntu tidak selalu versi yang terbaru, sehingga apabila kamu ingin mengupdate python ke versi yang terbaru caranya kamu bisa ikuti langkah seperti yang saya lakukan berikut ini:  

### Update python ke versi terbaru
untuk mengupdate versi python ke versi terbaru kamu bisa ketikkan perintah berikut:
{{< highlight bash >}}
$ sudo apt upgrade python3
{{< /highlight >}}
Tapi bagaimanapun apabila kamu lebih suka dan ingin menginstall secara manual kamu bisa langsung ke sumber datanya [disini](https://www.python.org/downloads/source/), berikut caranya:

Download dulu *source* nya dengan perintah di bawah ini.
{{< highlight bash >}}
$ https://www.python.org/ftp/python/3.7.2/Python-3.7.2.tgz
{{< /highlight >}}
Setelah selesai di download, *exctract* hasil download tersebut dengan perintah
{{< highlight bash >}}
$ -xvf Python-3.7.2.tgz
{{< /highlight >}}
Lalu pindah ke direktori hasil *extract* tadi
{{< highlight bash >}}
$ cd Python-3.7.2
{{< /highlight >}}
Terus jalankan perintah di bawah ini untuk mulai menginstall python nya
{{< highlight bash >}}
$ ./configure
$ sudo make
$ sudo make install
{{< /highlight >}}
Apabila proses intalasi selesai dan berhasil, selanjutnya kita akan membuat Python3.7.2 sebagai default python3, langkahnya adalah tambahkan perintah alias pada .zshrc / .bashrc 
{{< highlight bash >}}
alias python3=python3.7
{{< /highlight >}}
### Hapus python
Untuk menguninstall python dari sistem ubuntu kamu, ketikkan perintah berikut:
{{< highlight bash >}}
$ sudo apt remove python3.7
{{< /highlight >}}
Jika kamu menginstall python dari sumber data dan ingin mengupdatenya ke versi terbaru, maka kamu harus menghapus file-file hasil penginstallan sebelumnya lalu ulangi proses instalasi seperti yang sudah saya jelaskan diatas. Biasanya semua file yang berkaitan dengan proses instalasi python tersebut tersimpan di path **/usr/local/bin** jadi kamu harus hapus file-file tersebut dengan cara:
{{< highlight bash >}}
$ sudo rm /usr/local/bin/py*
$ sudo rm /usr/local/bin/pip*
$ sudo rm /usr/local/bin/idle*
$ sudo rm /usr/local/bin/2to3*
$ sudo rm /usr/local/bin/easy_install-3.7
{{< /highlight >}}
Mungkin cukup sekian dulu ya penjelasan mengenai cara install dan update python nya, di lain kesempatan kita akan membahas mengenai python secara lebih jauh.
