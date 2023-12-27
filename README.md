# Lab8-web

<h1 align="center"><b>Praktikum 8</b></h1> 

**Nama: Aan Fadillah Putra**

**NIM: 312210327**

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

![Aan 1 png](https://github.com/aanfadillah/Lab8-web/assets/115763475/bb2d7c7f-b571-41db-9583-9ddb421f5aac)


## Mengakses MySQL Client menggunakan PHP MyAdmin

## Pastikan webserver Apache dan MySQL server sudah dijalankan. Kemudian buka melalui browser: http://localhost/phpmyadmin/

## Membuat Database: Studi Kasus Data Barang

![aan2](https://github.com/aanfadillah/Lab8-web/assets/115763475/fa96882a-077b-4923-8661-e6c2057c3f30)


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

![aan3 png](https://github.com/aanfadillah/Lab8-web/assets/115763475/6013c468-da6a-4b44-8b69-5e0352b72b88)


## Menambahkan Data

```php
INSERT INTO data_barang (kategori, nama, gambar, harga_beli, harga_jual, stok)
VALUES ('Elektronik', 'HP Samsung Android', 'hp_samsung.jpg', 2000000, 2400000, 5),
('Elektronik', 'HP Xiaomi Android', 'hp_xiaomi.jpg', 1000000, 1400000, 5),
('Elektronik', 'HP OPPO Android', 'hp_oppo.jpg', 1800000, 2300000, 5);
```

![aan4 png](https://github.com/aanfadillah/Lab8-web/assets/115763475/f2e2c3d9-4884-440f-a52b-232f7705a6b8)


## Membuat Program CRUD
### Buat folder lab8_php_database pada root directory web server (c:\xampp\htdocs)

![aan5 png](https://github.com/aanfadillah/Lab8-web/assets/115763475/2d5ad9d6-f9d6-4bf3-9608-5a7ccffb0607)


## Kemudian untuk mengakses direktory tersebut pada web server dengan mengakses URL: http://localhost/lab8_php_database/

![aan6 png](https://github.com/aanfadillah/Lab8-web/assets/115763475/71a3dcd6-efff-4369-847b-f368b50f9e4b)


## Membuat file koneksi database
### Buat file baru dengan nama ```koneksi.php```

```php
<?php
$host = "localhost";
$user = "root";
$pass = "";
$db = "latihan1";
$conn = mysqli_connect($host, $user, $pass, $db);
if ($conn == false)
{
  echo "Koneksi ke server gagal.";
  die();
} #else echo "Koneksi berhasil";
?>
```
### Buka melalui browser untuk menguji koneksi database untuk menyampilkan pesan koneksi berhasil, uncomment pada perintah ```echo “koneksi berhasil”;```

![aan7 png](https://github.com/aanfadillah/Lab8-web/assets/115763475/ba6783aa-ec28-4110-ae50-0e4e1839f555)


## Membuat file index untuk menampilkan data (Read)
### Buat file baru dengan nama ```index.php```

```php
<?php
include("koneksi.php");
$sql = 'SELECT * FROM data_barang';
$result = mysqli_query($conn, $sql);
?>
<DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <link href="style.css" rel="stylesheet" type="text/css" />
    <title>Data Barang</title>
</head>
<body>
    <div class="container">
        <h1>Data Barang</h1>
        <tr>
            <a href="tambah.php?id=">Tambah Barang</a>
        </tr>

        <div class="main">
            <table border="1" cellpadding="5" cellspacing="0">
            <tr>
                <th>Gambar</th>
                <th>Nama Barang</th>
                <th>Katagori</th>
                <th>Harga Jual</th>
                <th>Harga Beli</th>
                <th>Stok</th>
                <th>Aksi</th>
            </tr>
            <?php if($result): ?>
            <?php while($row = mysqli_fetch_array($result)): ?>
            <tr>
                <td><?= $row['nama'];?></td>
                <td><?= $row['nama'];?></td>
                <td><?= $row['kategori'];?></td>
                <td><?= $row['harga_beli'];?></td>
                <td><?= $row['harga_jual'];?></td>
                <td><?= $row['stok'];?></td>
                <td>
                    <a href="ubah.php?id=<?= $row['id_barang'];?>">Ubah</a>
                    <a href="hapus.php?id=<?= $row['id_barang'];?>">Hapus</a>
                </td>
            </tr>
            <?php endwhile; else: ?>
            <tr>
                <td colspan="7">Belum ada data</td>
            </tr>
            <?php endif; ?>
            </table>
        </div>
    </div>
</body>
</html>
```
## Menambah Data (Create)
### Buat file baru dengan nama ```tambah.php```

```php
<?php
include("koneksi.php");

$sql = 'SELECT * FROM data_barang';
$result = mysqli_query($conn, $sql);

?>
<DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <link href="style.css" rel="stylesheet" type="text/css" />
    <title>Data Barang</title>
</head>
<body>
    <div class="container">
        <h1>Data Barang</h1>
        <tr>
            <a href="tambah.php?id=">Tambah Barang</a>
        </tr>

        <div class="main">
            <table border="1" cellpadding="5" cellspacing="0">
            <tr>
                <th>Gambar</th>
                <th>Nama Barang</th>
                <th>Katagori</th>
                <th>Harga Jual</th>
                <th>Harga Beli</th>
                <th>Stok</th>
                <th>Aksi</th>
            </tr>
            <?php if($result): ?>
            <?php while($row = mysqli_fetch_array($result)): ?>
            <tr>
                <td><?= $row['nama'];?></td>
                <td><?= $row['nama'];?></td>
                <td><?= $row['kategori'];?></td>
                <td><?= $row['harga_beli'];?></td>
                <td><?= $row['harga_jual'];?></td>
                <td><?= $row['stok'];?></td>
                <td>
                    <a href="ubah.php?id=<?= $row['id_barang'];?>">Ubah</a>
                    <a href="hapus.php?id=<?= $row['id_barang'];?>">Hapus</a>
                </td>
            </tr>
            <?php endwhile; else: ?>
            <tr>
                <td colspan="7">Belum ada data</td>
            </tr>
            <?php endif; ?>
            </table>
        </div>
    </div>
</body>
</html>
```
![aan8 png](https://github.com/aanfadillah/Lab8-web/assets/115763475/dae699c9-9f51-40b7-8e05-d191f978c51f)


/>
			</div>
		</form>
	</div>
</div>
</body>
</html>
```
![aan9 png](https://github.com/aanfadillah/Lab8-web/assets/115763475/5b0aac81-a621-4794-a3f4-508fb5e5257e)


## Menghapus Data (Delete)
### Buat file baru dengan nama ```hapus.php```

```php
<?php
include_once 'koneksi.php';
$id = $_GET['id'];
$sql = "DELETE FROM data_barang WHERE id_barang = '{$id}'";
$result = mysqli_query($conn, $sql);
header('location: index.php');
?>
```
## Laporan Praktikum
1. Buatlah repository baru dengan nama Lab8Web.
2. Kerjakan semua latihan yang diberikan sesuai urutannya.
3. Screenshot setiap perubahannya.
4. Buatlah file README.md dan tuliskan penjelasan dari setiap langkah praktikum beserta screenshotnya.
5. Commit hasilnya pada repository masing-masing.
6. Kirim URL repository pada e-learning ecampus

<h1 <p align="center"><b>======== Sekian Terima Kasih ==========</b></p></h1>
