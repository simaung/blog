---
title: "Deploy Blog Hugo Ke Github"
date: 2018-08-31T21:42:53+07:00
draft: false
---
Oke setelah [sebelumnya ](../membuat-blog-dengan-hugo/) kita membahas bagaimana caranya membuat blog *SSG* (Static Static Generator) menggunakan hugo, sekarang saya akan membahas caranya mendeploy blog hugo ini ke github.  

Disini saya mendeploy hugo ke github sebagai situs personal/organisasi, sebelumnya dipastikan disistem kita sudah terpasang **git** selanjutnya pastikan juga kamu sudah punya akun di [github](https://github.com).  
### Langkah-langkahnya
Sebelumnya kita buat dulu dua buah repositori yang kegunaannya masing-masing untuk menyimpan konten dan source dari blog nya, sementara satu lagi untuk menyimpan hasil render dari blog tersebut.
Buat dua repo di Github dengan nama sebagai berikut:  
1. blog (opsional) digunakan untuk menyimpan file dan source blog hugo  
2. username.github.io (username di ganti sesuai username atau organisasi kalian ya) digunakan untuk menyimpan hasil render blognya

Masuk ke direktori blog hugo kita, lalu kita inisialisasi git 
{{< highlight bash >}}
$ cd blogku
$ git init
{{< /highlight >}}
Setelah itu kita hapus folder public nya
{{< highlight bash >}}
$ rm -rf public
{{< /highlight >}}
setelah itu silakan kalian kaitkan repo lokal ini ke repo *remote*(github) lalu kita push blog kita ke repo *remote* tersebut, caranya:
{{< highlight bash >}}
$ git remote add origin https://github.com/{username}/{nama-repo}.git
$ git add .
$ git commit -m "first commit"
$ git push -u origin master
{{< /highlight >}}
Kita sudah selesai mengupload file blog kita ke repo *remote* akan tetapi kita belum bisa mengakses blog kita di website dikarenakan blog hugo ini akan bisa di akses melalui alamat url **https://username.github.io** apabila kita mencoba mengakses url tersebut maka akan muncul keterangan **Error 404 Not Found** itu karena repo tersebut masih kosong, nah sebagai isinya kita akan membuatkan *submodule* dari repo intinya yaitu repo **blog**.

Pastikan kamu berada di repo **blog**, lalu ketikkan perintah berikut untuk menambahkan *submodule*
{{< highlight bash >}}
$ git submodule add -b master https://github.com/{username}/{username}.github.io.git public
{{< /highlight >}}
Perintah tersebut akan melakukan clone repo **username.github.io** ke dalam direktori **public**.
Sekarang kita mulai mempublikasikan blognya, silakan kamu ketik perintah berikut:
{{< highlight bash >}}
# generate static web
hugo

# push ke repository
cd public
git add .
git commit -m "tes Deploy hugo"
git push -u origin master
{{< /highlight >}}
Perintah diatas di pergunakan setiap kali kita mau update konten, lumayan ribet kalo harus terus-terusan ngetik perintah tersebut setiap kali update maka dari itu kita buatkan skrip .sh nya aja biar hanya dengan satu baris perintah kita bisa update blognya
{{< highlight bash >}}
#!/bin/bash

echo -e "\033[0;32mDeploying updates to GitHub...\033[0m"

# Genterate file statis
hugo # if using a theme, replace by `hugo -t <yourtheme>`

# pindah ke direktori publik
cd public
# tambahkan perubahan ke Git
git add -A

# Buat sebuah commit baru
msg="rebuilding site `date`"
if [ $# -eq 1 ]
  then msg="$1"
fi
git commit -m "$msg"

# Push atau puload ke Github
git push origin master

# Balik ke direktori sebelumnya
cd ..
{{< /highlight >}}
Kita simpan file tersebut dengan nama **deploy.sh** aja lalu berikan hak akses eksekusi untuk skrip ini
{{< highlight bash >}}
$ chmod +x deploy.sh
{{< /highlight >}}
Jadi klo kita mau update konten kita tinggal jalankan skrip d**deploy.sh** nya aja
{{< highlight bash >}}
$ ./deploy.sh

# bisa ditambah pesan commitnya
$ ./deploy.sh "tes deploy web hugo ke github"
{{< /highlight >}}
Sekarang coba kamu akses url **username.github.io** kalau proses deploy kamu sukses kamu akan bisa melihat blog hugo kamu disana
