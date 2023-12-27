# Lab8-web

<h1 align="center"><b>Praktikum 8</b></h1> 

**Nama: Rini Ariza**

**NIM: 312210337**

**Kelas: TI.22.A3**

---

## Instruksi Praktikum
1. Persiapkan text editor misalnya VSCode.
2. Buat folder baru dengan nama lab8_php_database pada docroot webserver (htdocs)
3. Ikuti langkah-langkah praktikum yang akan dijelaskan berikutnya.
   
### Langkah-langkah Praktikum
### Persiapan
#### Untuk memulai membuat aplikasi CRUD sederhana, yang perlu disiapkan adalah database server menggunakan MySQL. Pastikan MySQL Server sudah dapat dijalankan melalui XAMPP.
#### Menjalankan MySQL Server Untuk menjalankan MySQL Server dari menu XAMPP Contol.

## Menjalankan MySQL Server
### Untuk menjalankan MySQL Server dari menu XAMPP Contol.

![Screenshot (502)](https://github.com/rniarzz/Lab8web/assets/115542704/96f742d7-8b8e-4a59-a28a-7382ea1329f5)

## Mengakses MySQL Client menggunakan PHP MyAdmin

## Pastikan webserver Apache dan MySQL server sudah dijalankan. Kemudian buka melalui browser: http://localhost/phpmyadmin/

## Membuat Database: Studi Kasus Data Barang

![image](https://github.com/rniarzz/Lab8web/assets/115542704/d6e74f09-2069-4870-94cf-88a5856e70ea)

## Membuat Database

```php
CREATE DATABASE latihan1;
```

## Membuat Tabel

```php
CREATE TABLE data_barang (
    id_barang int(10) auto_increment Primary Key,
    kategori varchar(30),
    nama varchar(30),
    gambar varchar(100),
    harga_beli decimal(10,0),
    harga_jual decimal(10,0),
    stok int(4)
);
```

![Screenshot (505)](https://github.com/rniarzz/Lab8web/assets/115542704/bb0a5dc3-74af-4ac3-825b-37ab10810446)

## Menambahkan Data

```php
INSERT INTO data_barang (kategori, nama, gambar, harga_beli, harga_jual, stok)
VALUES ('Elektronik', 'HP Samsung Android', 'hp_samsung.jpg', 2000000, 2400000, 5),
('Elektronik', 'HP Xiaomi Android', 'hp_xiaomi.jpg', 1000000, 1400000, 5),
('Elektronik', 'HP OPPO Android', 'hp_oppo.jpg', 1800000, 2300000, 5);
```

![lab4](https://github.com/rniarzz/Lab8web/assets/115542704/4eac4ae1-8b0f-4a1c-b4f3-6efd55b0e451)

## Membuat Program CRUD
### Buat folder lab8_php_database pada root directory web server (c:\xampp\htdocs)

![Screenshot (504)](https://github.com/rniarzz/Lab8web/assets/115542704/481928db-131a-41ef-8b12-d6aef12dc421)

## Kemudian untuk mengakses direktory tersebut pada web server dengan mengakses URL: http://localhost/lab8_php_database/

![Screenshot (467)](https://github.com/rniarzz/Lab8web/assets/115542704/94fb42cc-f5db-4d58-b54c-68e555880cda)
