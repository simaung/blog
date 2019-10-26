---
title: "Belajar Lumen #2"
date: 2019-10-20T08:32:22+07:00
draft: false
---

### Persiapan schema database
Tujuan dari pelajaran lumen ini yaitu kita dapat membuat simple CRUD dengan menggunakan lumen, nah sebelum kita masuk ke proses CRUD tersebut sekarang kita buat sample schema database terlebih dahulu untuk di pergunakan proses CRUD kedepannya.

#### Setting awal database
silakan kamu ubah settingan database terlebih dahulu, settingan ini terdapat pada file .env dan ubah pada variabel berikut
{{< highlight bash >}}
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=nama_database_kamu
DB_USERNAME=username_database_kamu
DB_PASSWORD=password_database_kamu
{{< /highlight >}}

#### Membuat database
Oke pertama kali kita buat dulu database dengan nama **belajar_lumen**, cara membuat database sudah pernah saya bahas pada postingan sebelumnya yang berjudul [mysql dasar menggunakan cli](../mysql-dasar-menggunakan-cli/), tapi ingat kamu hanya sampai pada tahapan membuat database aja untuk pembahasan ini karena untuk membuat tabel, kolom dan yang lainnya akan kita gunakan keajaiban dari laravel hhe.

Oke lanjut kita membuat file migration, dimana file migration ini berfungsi untuk menggenerate pembuatan tabel sekaligus fieldnya
{{< highlight bash >}}
$ php artisan make:migration create_posts_table
{{< /highlight >}}
Lalu buka file migration tersebut (**database/migrations/prefix_create_posts_table**) dan ubah di bagian **method up**  menjadi seperti berikut
{{< highlight php >}}
 public function up()
    {
        Schema::create('posts', function (Blueprint $table) {
            $table->bigIncrements('id');
            $table->string('title');
            $table->string('body');
            $table->timestamps();
        });
    }
{{< /highlight >}}
Pengertian dari sintaks file migration itu adalah kita akan membuat sebuah tabel di database dengan nama **posts** dan menambahkan kolom **title** dan **body** pada tabel tersebut, setelah itu sekarang kita lakukan migrate untuk menjalankan atau mengeksekusi file migration ke database
{{< highlight bash >}}
$ php artisan migrate
{{< /highlight >}}
sekarang coba kamu cek apakah tabel posts ini sudah ada di database.
![Example image](/img/belajar-lumen/tabel_hasil_migrate.png)
Berdasarkan tampilan diatas saya menamai database sy dengan nama belajar_lumen disana dapat kita lihat ada dua buah tabel dengan masing-masing bernama migrations dan posts, untuk sekarang kita abaikan aja tabel dengan nama migrations tersebut karena itu merupakan history dari migration dan di generate otomatis pada saat kita melakukan migrate, dan kita lihat tabel **posts** nah itu merupakan tabel hasil generate skrip file migrations yang kita tambahkan sebelumnya

#### membuat seeder posts dengan Faker
Setelah tabel posts nya terbuat sekarang kita akan mencoba menambahkan data pada tabel tersebut dengan menggunakan bantuan *seeder* dan *faker* pada laravel
{{< highlight bash >}}
$ php artisan make:seeder PostsTableSeeder
{{< /highlight >}}
Lalu ubah file **database/seed/PostsTableSeeder** menjadi seperti berikut:
{{< highlight php >}}
public function run()
{
    $faker = Faker::create('id_ID');

    foreach(range(1,11) as $i){
        DB::table('posts')->insert([
            'title' => $faker->sentence(10),
            'body' => $faker->sentence(50),
        ]);
    }
}
{{< /highlight >}}
Dan jalankan seeder dengan sintaks
{{< highlight bash >}}
$ php artisan db:seed --class=PostsTableSeeder
{{< /highlight >}}
