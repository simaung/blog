---
title: "Belajar Python: Virtual Environtment"
date: 2019-01-04T20:04:07+07:00
draft: false
---
Apasih *virtual environment* (venv) itu? jadi begini jika kamu seorang *programmer* pasti pernah melakukan update versi dari bahasa pemrograman yang kamu pakai ke versi yang terbaru, nah ketika versi bahasa tersebut berhasil kamu update ternyata ada beberapa project kamu yang menggunakan versi lama menjadi *error* karena ada beberapa *method* yang tidak sesuai dengan versi yang baru tersebut, jadi di python untuk menangani permasalahan tersebut digunakanlah venv.  

Intinya dengan venv kamu bisa menggunakan versi python yang berbeda untuk setiap projectnya sesuai dengan yang kamu inisialisasikan pada saat pembuatan venv pertama kali. Jadi untuk setiap project akan memiliki *dependencies* nya sendiri tanpa ada keterkaitan dengan project yang lainnya.

Jika kamu menggunakan python 3, venv sudah tersedia sebagai module standar pada saat penginstallan, jadi jika kamu ingin membuat venv kamu bisa langsung mengetikkan perintah berikut
```bash
# venv dengan python versi 3.7
$ python3 -m venv env
```
Dengan menjalankan perintah diatas python akan membuatkan direktori dengan nama **env**, dimana akan memiliki struktur direktori seperti berikut:
```bash
env
├── bin
│   ├── activate
│   ├── activate.csh
│   ├── activate.fish
│   ├── easy_install
│   ├── easy_install-3.7
│   ├── pip
│   ├── pip3
│   ├── pip3.7
│   ├── python -> python3
│   └── python3 -> /usr/local/bin/python3
├── include
├── lib
│   └── python3.7
├── lib64 -> lib
└── pyvenv.cfg
```
Untuk masuk ke venv kamu tinggal ketikkan perintah di bawah ini:
```bash
$ source env/bin/activate
(env) $
```
Kamu bisa lihat pada baris kedua ada **(env)** itu menandakan kamu sudah masuk kedalam mode *virtual environment*, sekarang untuk mengecek nya masih di dalam mode venv silakan install flask
```bash
(env) $ pip install flask
```
tunggu beberapa saat sampai proses instalasi flask selesai, apabila sudah selesai proses instalasi flask nya sekarang coba kamu cek flask tersebut apakah ada atau tidak
```bash
(env) $ flask --version
Flask 1.0.2
Python 3.7.2 (default, Jan  4 2019, 11:20:11) 
[GCC 7.3.0]
```
Apabila tampilannya seperti di atas itu berarti flask sudah terinstall, sekarang coba kamu keluar dulu dari mode venv dengan perintah *deactivate* lalu cek kembali apakah flask nya ada atau tidak
```bash
(env) $ deactivate
$ flask --version
Traceback (most recent call last):
  File "/home/user/.local/bin/flask", line 7, in <module>
    from flask.cli import main
ModuleNotFoundError: No module named 'flask'
```
Seteleh di cek ternyata flask tidak dikenal, itu di karenakan flask tidak terinstall di lingkungan OS (global)

Oke mungkin untuk sementara sampai disini dulu pembahasan mengenai *Virtual Environment*, nanti kalo ada yang perlu di tambahin saya coba update post ini.
