# Praktikum 9 - PHP Modular - Pemrograman Web
```
Maulana Hasanudin
312010106
TI.20.D.1
Universitas Pelita Bangsa
```
# LANGKAH 1
## Jalankan XAMPP dan akses http://localhost/phpmyadmin/ untuk membuat database.
![1](https://user-images.githubusercontent.com/101716660/171666831-b0bddbbf-72c6-48cc-b987-c85cab3fcf5a.png)


# LANGKAH 2
## Buat file lab9_php_modular pada root directory web server (d:\xampp\htdocs)
![2](https://user-images.githubusercontent.com/101716660/171667026-903ebdc9-9e16-441b-8a2b-3dd39cbf7d99.png)


# LANGKAH 3
## Buat file baru dengan nama header.php pada folder (d:\xampp\htdocs\lab9_php_modular)
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Contoh Modularisasi</title>
    <link href="style.css" rel="stylesheet" type="text/stylesheet" media="screen" />
</head>
<body>
    <div class="container">
        <header>
            <h1>Modularisasi Menggunakan Require</h1>
        </header>
        <nav>
        <a href="home.php">Home</a>
        <a href="about.php">Tentang</a>
        <a href="kontak.php">Kontak</a>
        </nav>
 ```
# LANGKAH 4
## Buat file baru dengan nama footer.php pada folder (d:\xampp\htdocs\lab9_php_modular)
 ```  
   <footer>
            <p>&copy; 2021, Informatika, Universitas Pelita Bangsa</p>
        </footer>
    </div>
</body>
</html>
```
![3](https://user-images.githubusercontent.com/101716660/171667280-3a6c9bf2-a43f-4b34-863b-df9ff7ddd2cf.png)


# LANGKAH 5
## Buat file baru dengan nama home.php pada folder (d:\xampp\htdocs\lab9_php_modular)
```
<?php require('header.php'); ?>

<div class="content">
    <h2>Ini Halaman Home</h2>
    <p>Ini adalah bagian content dari halaman.</p>
</div>

<?php require('footer.php'); ?>
```
![4](https://user-images.githubusercontent.com/101716660/171667487-4cc246f6-9811-438d-b407-c6401e797508.png)


# LANGKAH 6
## Buat file baru dengan nama about.php pada folder (d:\xampp\htdocs\lab9_php_modular)
```
<?php require('header.php'); ?>

<div class="content">
    <h2>Ini Halaman About</h2>
    <p>Ini adalah bagian content dari halaman.</p>
</div>

<?php require('footer.php'); ?>
```
![5](https://user-images.githubusercontent.com/101716660/171667580-91306ba7-c687-4371-a3ef-1d275d6947cc.png)


# HASIL
## Home 
![6](https://user-images.githubusercontent.com/101716660/171667774-e3c45fd3-d17d-4f08-b098-4c7773805101.png)
## About
![7](https://user-images.githubusercontent.com/101716660/171667908-62bc7d26-cc0d-445b-8117-11d3fe824608.png)



# TUGAS
## Implementasikan konsep modularisasi pada kode program praktikum 8 tentang database, sehingga setiap halamannya memiliki template tampilan yang sama.
# LANGKAH 1
## Buat file lab9_tugas pada root directory web server (d:\xampp\htdocs)
![8](https://user-images.githubusercontent.com/101716660/171668024-263c4e2c-3eea-469a-8dd6-534b23c59638.png)


# LANGKAH 2
## Buat file baru dengan nama koneksi.php pada folder (d:\xampp\htdocs\lab9_tugas)
```
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
![9](https://user-images.githubusercontent.com/101716660/171668304-ca07f1f2-de37-44c4-a1c4-7f1725287a64.png)


# LANGKAH 3
## Buat file baru dengan nama header.php pada folder (d:\xampp\htdocs\lab9_tugas)
```
<?php
include("koneksi.php");

// query untuk menampilkan data
$sql = 'SELECT * FROM data_barang';
$result = mysqli_query($conn, $sql);
?>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Contoh Modularisasi</title>
    <link href="style.css" rel="stylesheet" type="text/css" />
</head>
<body>
    <div id="container">
        <header>
            <h1>Database</h1>
        </header>
        <nav>
            <a href="home.php">Home</a>
            <a href="tambah.php">Tambah Barang</a>
        </nav>
```
![10](https://user-images.githubusercontent.com/101716660/171668489-4182e3e2-b2e0-4d10-92a9-fb531237479e.png)


# LANGKAH 4
## Buat file baru dengan nama footer.php pada folder (d:\xampp\htdocs\lab9_tugas)
```
<footer>
            <p>&copy; 2022, Maulana hasanudin, 312010106, TI.20.D.1</p>
        </footer>
    </div>
</body>
</html>
```



# LANGKAH 5
## Buat file baru dengan nama home.php pada folder (d:\xampp\htdocs\lab9_tugas)
```
<?php require('header.php'); ?>

<div class="content">
    <h1>Data Barang</h1>
    <div class="main">
        <table>
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
            <td><img src="gambar/<?= $row['gambar'];?>" alt="<?=$row['nama'];?>"></td>
            <td><?= $row['nama'];?></td>
            <td><?= $row['kategori'];?></td>
            <td><?= $row['harga_jual'];?></td>
            <td><?= $row['harga_beli'];?></td>
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

<?php require('footer.php'); ?>
```
![12](https://user-images.githubusercontent.com/101716660/171669352-4fd513c3-17d4-4da1-96b6-15cbe317f394.png)
 ![13](https://user-images.githubusercontent.com/101716660/171669416-46fbabc6-3033-4f46-aafe-c2b4b6b431c5.png)
![14](https://user-images.githubusercontent.com/101716660/171669549-75ef09eb-245c-4385-b280-4bc48c02bc82.png)


# LANGKAH 6
## Buat file baru dengan nama tambah.php pada folder (d:\xampp\htdocs\lab9_tugas)
```
<?php
error_reporting(E_ALL);
include_once 'koneksi.php';

if (isset($_POST['submit']))
{
    $nama = $_POST['nama'];
    $kategori = $_POST['kategori'];
    $harga_jual = $_POST['harga_jual'];
    $harga_beli = $_POST['harga_beli'];
    $stok = $_POST['stok'];
    $file_gambar = $_FILES['file_gambar'];
    $gambar = null;

    if ($file_gambar['error'] == 0)
    {
        $filename = str_replace(' ', '_',$file_gambar['name']);
        $destination = dirname(__FILE__) .'/gambar/' . $filename;
        if(move_uploaded_file($file_gambar['tmp_name'], $destination))
        {
            $gambar = 'gambar/' . $filename;;
        }
    }
    
    $sql = 'INSERT INTO data_barang (nama, kategori, harga_jual, harga_beli, stok, gambar) ';
    $sql .= "VALUE ('{$nama}', '{$kategori}','{$harga_jual}','{$harga_beli}', '{$stok}', '{$gambar}')";
    $result = mysqli_query($conn, $sql);
    header('location: home.php');
}
?>

<?php require('header.php'); ?>

<div class="content">
    <h1>Tambah Barang</h1>
    <div class="main">
        <form method="post" action="tambah.php" enctype="multipart/form-data">
            <div class="input">
                <label>Nama Barang</label>
                <input type="text" name="nama" style="margin-left: 20px;" />
            </div>
            <div class="input">
                <label>Kategori</label>
                <select name="kategori" style="margin-left: 58px;" >
                    <option value="Komputer">Komputer</option>
                    <option value="Elektronik">Elektronik</option>
                    <option value="Hand Phone">Hand Phone</option>
                </select>
            </div>
            <div class="input">
                <label>Harga Jual</label>
                <input type="text" name="harga_jual" style="margin-left: 40px;" />
            </div>
            <div class="input">
                <label>Harga Beli</label>
                <input type="text" name="harga_beli" style="margin-left: 43px;" />
            </div>
            <div class="input">
                <label>Stok</label>
                <input type="text" name="stok" style="margin-left: 85px;" />
            </div>
            <div class="input">
                <label>File Gambar</label>
                <input type="file" name="file_gambar" />
            </div>
            <div class="submit">
                <input type="submit" name="submit" value="Simpan" />
            </div>
        </form>
    </div>
</div>

<?php require('footer.php'); ?>
```
![15](https://user-images.githubusercontent.com/101716660/171669868-56774372-89bc-49f4-a9f2-1e292c710e02.png)
 ![16](https://user-images.githubusercontent.com/101716660/171669931-01da0e54-2356-4156-ab7c-79bb33b48deb.png)
 ![17](https://user-images.githubusercontent.com/101716660/171669994-df86bee3-cebc-41c7-abd5-006c244284c8.png)

# LANGKAH 7
## Buat file baru dengan nama ubah.php pada folder (d:\xampp\htdocs\lab9_tugas)
```
<?php
error_reporting(E_ALL);
include_once 'koneksi.php';

if (isset($_POST['submit']))
{
    $id = $_POST['id'];
    $nama = $_POST['nama'];
    $kategori = $_POST['kategori'];
    $harga_jual = $_POST['harga_jual'];
    $harga_beli = $_POST['harga_beli'];
    $stok = $_POST['stok'];
    $file_gambar = $_FILES['file_gambar'];
    $gambar = null;

    if ($file_gambar['error'] == 0)
    {
        $filename = str_replace(' ', '_', $file_gambar['name']);
        $destination = dirname(__FILE__) . '/gambar/' . $filename;
        if (move_uploaded_file($file_gambar['tmp_name'], $destination))
        {
            $gambar = 'gambar/' . $filename;;
        }
    }

    $sql = 'UPDATE data_barang SET ';
    $sql .= "nama = '{$nama}', kategori = '{$kategori}', ";
    $sql .= "harga_jual = '{$harga_jual}', harga_beli = '{$harga_beli}', stok = '{$stok}' ";
    if (!empty($gambar))
        $sql .= ", gambar = '{$gambar}' ";
    $sql .= "WHERE id_barang = '{$id}'";
    $result = mysqli_query($conn, $sql);

    header('location: home.php');
    }

    $id = $_GET['id'];
    $sql = "SELECT * FROM data_barang WHERE id_barang = '{$id}'";
    $result = mysqli_query($conn, $sql);
    if (!$result) die('Error: Data tidak tersedia');
    $data = mysqli_fetch_array($result);

    function is_select($var, $val) {
        if ($var == $val) return 'selected="selected"';
        return false;
}
?>

<?php require('header.php'); ?>

<div class="content">
    <h1>Ubah Barang</h1>
    <div class="main">
        <form method="post" action="ubah.php" enctype="multipart/form-data">
            <div class="input">
                <label>Nama Barang</label>
                <input type="text" name="nama" value="<?php echo $data['nama'];?>" style="margin-left: 20px;"/>
            </div>
            <div class="input">
                <label>Kategori</label>
                <select name="kategori" style="margin-left: 58px;">
                    <option <?php echo is_select ('Komputer', $data['kategori']);?> value="Komputer">Komputer</option>
                    <option <?php echo is_select ('Komputer', $data['kategori']);?> value="Elektronik">Elektronik</option>
                    <option <?php echo is_select ('Komputer', $data['kategori']);?> value="Hand Phone">Hand Phone</option>
                </select>
            </div>
            <div class="input">
                <label>Harga Jual</label>
                <input type="text" name="harga_jual" value="<?php echo $data['harga_jual'];?>" style="margin-left: 40px;"/>
            </div>
            <div class="input">
                <label>Harga Beli</label>
                <input type="text" name="harga_beli" value="<?php echo $data['harga_beli'];?>" style="margin-left: 43px;"/>
            </div>
            <div class="input">
                <label>Stok</label>
                <input type="text" name="stok" value="<?php echo $data['stok'];?>" style="margin-left: 85px;"/>
            </div>
            <div class="input">
                <label>File Gambar</label>
                <input type="file" name="file_gambar" />
            </div>
            <div class="submit">
                <input type="hidden" name="id" value="<?php echo $data['id_barang'];?>" />
                    <input type="submit" name="submit" value="Simpan" />
            </div>
        </form>
    </div>
</div>

<?php require('footer.php'); ?>
```
![18](https://user-images.githubusercontent.com/101716660/171670186-9ffaaba2-c700-4227-add1-030884a97229.png)
 ![19](https://user-images.githubusercontent.com/101716660/171670243-5d138d03-334a-4b4a-985d-1db2a239ad28.png)
 ![20](https://user-images.githubusercontent.com/101716660/171670311-ca23af42-d23a-4076-a4cd-18fc000557f1.png)


# LANGKAH 8
## Buat file baru dengan nama hapus.php pada folder (d:\xampp\htdocs\lab9_tugas)
```
<?php
include_once 'koneksi.php';
$id = $_GET['id'];
$sql = "DELETE FROM data_barang WHERE id_barang = '{$id}'";
$result = mysqli_query($conn, $sql);
header('location: home.php');
?>
```
![21](https://user-images.githubusercontent.com/101716660/171670460-43379701-cdb4-478a-b172-86485b70a232.png)

# LANGKAH 9
## Buat file baru dengan nama style.css pada folder (d:\xampp\htdocs\lab9_tugas) untuk mempercantikan tampilan
```
/* import google font */
@import
url('https://fonts.googleapis.com/css2?family=Open+Sans:ital,wght@0,300;0,400;0,600;0,700;0,800;1,300;1,400;1,600;1,700;1,800&display=swap');
@import
url('https://fonts.googleapis.com/css2?family=Open+Sans+Condensed:ital,wght@0,300;0,700;1,300&display=swap');

/* Reset CSS */
* {
    margin: 0;
    padding: 0;
}
body {
    line-height:1;
    font-size:100%;
    font-family:'Open Sans', sans-serif;
    color:#5a5a5a;
}
#container {
    width: 980px;
    margin: 0 auto;
    box-shadow: 0 0 1em #cccccc;
}

/* header */
header {
    padding: 20px;
}
header h1 {
    margin: 20px 10px;
    color: #b5b5b5;
}

/* navigasi */
nav {
    display: block;
    background-color: #1f5faa;
}
nav a {
    padding: 15px 30px;
    display: inline-block;
    color: #ffffff;
    font-size: 14px;
    text-decoration: none;
    font-weight: bold;
}
nav a.active,
nav a:hover {
    background-color: #2b83ea;
}

/* Content Panel */
.content {
    background-color: #e4e4e5;
    padding: 50px 20px;
    margin-bottom: 20px;
}
.content h1 {
    margin-bottom: 20px;
    font-size: 35px;
}
.content p {
    margin-bottom: 20px;
    font-size: 18px;
    line-height: 25px;
}

/* footer */
footer {
    clear:both;
    background-color:#1d1d1d;
    padding:20px;
    color:#eee;
}

/* tabel */
body{
    font-family: sans-serif;
}
table{
    border-collapse: collapse;
}
th, td{
    border: 1px solid black;
    font-size: 16px;
    padding: 7px 9px;
}
table th {
    background:#1f5faa;
    color:#DCDCDC;
    font-weight:bold;
    font-size:14px;
}
table tr:nth-child(even) {
    background:#F0F8FF;
}

/* Tambah Barang */
.input{
    padding: 5px;
}
```
![22](https://user-images.githubusercontent.com/101716660/171670752-eb419f1f-0ec5-4def-8117-7fa2e52c9c03.png)
 ![23](https://user-images.githubusercontent.com/101716660/171670804-8e2a6149-3231-4993-b59e-8bd1f2648440.png)
 ![24](https://user-images.githubusercontent.com/101716660/171670895-a74aae9a-c573-4d94-b614-6c6038d4e45a.png)



Hasil
Tampilan Home
![25](https://user-images.githubusercontent.com/101716660/171671512-4e67f9f1-9740-4699-b0a5-ea0ed15c4fd1.png)


Tampilan Tambah Barang
![26](https://user-images.githubusercontent.com/101716660/171671589-0c7ea41d-9fe0-4679-8f28-a172c59c0284.png)


Tampilan Ubah Barang
![27](https://user-images.githubusercontent.com/101716660/171671659-e7ab821f-5a9e-453d-bd27-0c8bbf9b35c1.png)
