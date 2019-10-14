---
title: "Mysql dasar menggunakan cli"
date: 2018-12-14T10:04:51+07:00
draft: false
---

Disini saya memberikan beberapa catatan mengenai mysql menggunakan cli / command line interface di ubuntu atau biasa kita sebut dengan terminal.  

##### masuk ke mysql
{{< highlight bash >}}
$ mysql -u root -p  # tambah option -p apabila mysql kamu menggunakan password kalo tidak bisa di hilangkan -p nya
Enter password:     # baris ini akan muncul kalo mysql kamu menggunakan password
{{< /highlight >}}

Setelah kamu berhasil masuk ke mysql maka di terminal akan muncul tampilan seperti berikut.

{{< highlight bash >}}
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 248
Server version: 5.7.27-0ubuntu0.18.04.1 (Ubuntu)

Copyright (c) 2000, 2019, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> 
{{< /highlight >}}

##### menampilkan database
{{< highlight bash >}}
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
19 rows in set (0.72 sec)

mysql> 
{{< /highlight >}}

##### membuat database
disini saya membuat database dengan nama "belajar"
{{< highlight bash >}}
mysql> create database belajar;
Query OK, 1 row affected (0.16 sec)

mysql> 
{{< /highlight >}}

##### berpindah database
{{< highlight bash >}}
mysql> use belajar;
Database changed
mysql> 
{{< /highlight >}}

##### menampilkan tabel
{{< highlight bash >}}
mysql> show tables;
Empty set (0.00 sec)    # tabel masih kosong

mysql>
{{< /highlight >}}

##### membuat tabel
{{< highlight bash >}}
mysql> create table mahasiswa (
    -> id INT(3) NOT NULL AUTO_INCREMENT,
    -> nama VARCHAR(100) NOT NULL,
    -> nim VARCHAR(10) NOT NULL,
    -> alamat VARCHAR(200) NOT NULL,
    -> PRIMARY KEY (id)
    -> ) ENGINE = InnoDB;

Query OK, 0 rows affected (0.77 sec)

mysql>
{{< /highlight >}}

##### menampilkan skema tabel
{{< highlight bash >}}
mysql> describe mahasiswa;
+--------+--------------+------+-----+---------+----------------+
| Field  | Type         | Null | Key | Default | Extra          |
+--------+--------------+------+-----+---------+----------------+
| id     | int(3)       | NO   | PRI | NULL    | auto_increment |
| nama   | varchar(100) | NO   |     | NULL    |                |
| nim    | varchar(10)  | NO   |     | NULL    |                |
| alamat | varchar(200) | NO   |     | NULL    |                |
+--------+--------------+------+-----+---------+----------------+
4 rows in set (0.10 sec)

mysql>
{{< /highlight >}}

##### menampilkan data di tabel
{{< highlight bash >}}
mysql> select * from mahasiswa;
Empty set (0.00 sec)    # data masih kosong

mysql>
{{< /highlight >}}

##### menambahkan data pada tabel
{{< highlight bash >}}
mysql> insert into mahasiswa (nama,nim,alamat) values ("dede hermawan", "0001", "Bandung");
Query OK, 1 row affected (0.08 sec)

mysql>
{{< /highlight >}}
###### menambahkan data banyak sekaligus
{{< highlight bash >}}
mysql> insert into mahasiswa 
    -> (nama,nim,alamat) values 
    -> ("icha", "0002", "Bandung"),
    -> ("aliya", "0003", "Bandung"),
    -> ("azka", "0004", "Bandung");
Query OK, 3 rows affected (0.08 sec)
Records: 3  Duplicates: 0  Warnings: 0

mysql>
{{< /highlight >}}

setelah berhasil menambahkan data coba kembali untuk menampilkannya
{{< highlight bash >}}
mysql> select * from mahasiswa;
+----+---------------+------+---------+
| id | nama          | nim  | alamat  |
+----+---------------+------+---------+
|  1 | dede hermawan | 0001 | Bandung |
|  2 | icha          | 0002 | Bandung |
|  3 | aliya         | 0003 | Bandung |
|  4 | azka          | 0004 | Bandung |
+----+---------------+------+---------+

4 row in set (0.00 sec)

mysql>
{{< /highlight >}}

##### menampilkan data di tabel menggunakan kondisi where
{{< highlight bash >}}
mysql> select * from mahasiswa where id = 1;
+----+---------------+------+---------+
| id | nama          | nim  | alamat  |
+----+---------------+------+---------+
|  1 | dede hermawan | 0001 | Bandung |
+----+---------------+------+---------+
1 row in set (0.00 sec)

mysql>
{{< /highlight >}}

##### update data tabel
{{< highlight bash >}}
mysql> update mahasiswa set nama = 'dede' where id = 1;
Query OK, 1 row affected (0.07 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> select * from mahasiswa where id = 1;
+----+---------------+------+---------+
| id | nama          | nim  | alamat  |
+----+---------------+------+---------+
|  1 | dede          | 0001 | Bandung |
+----+---------------+------+---------+
1 row in set (0.00 sec)

mysql>
{{< /highlight >}}

##### hapus data tabel
{{< highlight bash >}}
mysql> delete from mahasiswa where id = 1;
Query OK, 1 row affected (0.07 sec)

mysql> select * from mahasiswa where id = 1;
Empty set (0.03 sec)

mysql>
{{< /highlight >}}

mungkin untuk pengenalan dasar mysql dengan command line sampai disini saja, kamu bisa mempelajari lebih dalam lagi terkait mysql / sintaks query, misalnya fungsi-fungsi dari sintaks limit, offset, join dsb.