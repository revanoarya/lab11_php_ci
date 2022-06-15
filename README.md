## Nama     : Revano Arya Saputra
## NIM      : 312010461
## Kelas    : TI.20.A.1
## Matkul   : Pemograman Web

### Praktikum 11 pertemuan 12 PHP Frame Work (Codeigniter) <b>

  # Langkah - langkah Praktikum

## 1. Mengaktifkan ekstentsi tersebut, melalu XAMPP Control Panel, pada bagian Apache klik Config -> PHP.ini <b>

![1](https://user-images.githubusercontent.com/101621068/172889853-12fbddf3-1698-4aad-8d8c-94fb250e6afd.png)

## 2. Pada bagian extention, hilangkan tanda ; (titik koma) pada ekstensi yang akan diaktifkan. Kemudian simpan kembali filenya dan restart Apache web server. <b>

![2](https://user-images.githubusercontent.com/101621068/172890499-57a15c86-7ad6-4ee1-8570-29d40c2b7abe.png)

## 3. Instalasi Codeigniter 4 <b>

Untuk melakukan instalasi Codeigniter 4 dapat dilakukan dengan dua cara, yaitu cara
manual dan menggunakan composer. Pada praktikum ini kita menggunakan cara
manual.
http://localhost/Lab11Web/lab11_php_ci/ci4/public/

![3](https://user-images.githubusercontent.com/101621068/172891573-5c9aeb0d-ddf4-4da5-828d-48dac7bef8de.png)

## 4. Menjalankan CLI (Command Line Interface) <b>

Menjalankan CLI (Command Line Interface) Codeigniter 4 menyediakan CLI untuk mempermudah proses development. Untuk mengakses CLI buka terminal/command prompt.

![4](https://user-images.githubusercontent.com/101621068/172891895-57fa9228-7e29-4731-93cf-b04c675ec72e.png)

Arahkan lokasi direktori sesuai dengan direktori kerja project dibuat (xampp/htdocs/lab11_ci/ci4/)

```php
PHP Spark
```

![5](https://user-images.githubusercontent.com/101621068/172892233-d40c354f-9650-4988-af5e-10f942c4bd65.png)

## 5. Mengaktifkan Mode Debugging <b>

Codeigniter 4 menyediakan fitur debugging untuk memudahkan developer untuk mengetahui pesan error apabila terjadi kesalahan dalam membuat kode program. Secara default fitur ini belum aktif. Ketika terjadi error pada aplikasi akan ditampilkan
pesan kesalahan seperti berikut.

![6](https://user-images.githubusercontent.com/101621068/172892678-3d4a9f64-f09b-4d42-a5f6-0628095e0751.png)

Semua jenis error akan ditampilkan sama. Untuk memudahkan mengetahui jenis errornya, maka perlu diaktifkan mode debugging dengan mengubah nilai konfigurasi pada environment variable CI_ENVIRONMENT menjadi development.

![7](https://user-images.githubusercontent.com/101621068/172892808-da99b0d3-0a66-4095-9755-40a0e1641e7b.png)

Ubah nama file env menjadi .env kemudian buka file tersebut dan ubah nilai variable CI_ENVIRONMENT menjadi development.

![8](https://user-images.githubusercontent.com/101621068/172892962-97f427bc-bcbd-49f4-ab60-54c2b5c4e1a1.png)

Contoh error yang terjadi. Untuk mencoba error tersebut, ubah kode pada file app/Controller/Home.php hilangkan titik koma pada akhir kode.

![9](https://user-images.githubusercontent.com/101621068/172893080-0c067576-18b4-40aa-8c6d-fbed7588ad81.png)

## 6. Membuat Routes Baru <b>

Tambahkan code pada routes.php

```php
$routes->get('/about', 'Page::about');
$routes->get('/contact', 'Page::contact');
$routes->get('/faqs', 'Page::faqs');
```

![10](https://user-images.githubusercontent.com/101621068/172893564-33bfc7f8-9688-4282-97d8-ba351276a017.png)

Untuk mengetahui route yang ditambahkan sudah benar, buka CLI dan jalankan perintah berikut.

```php
PHP Spark Routes
```

![11](https://user-images.githubusercontent.com/101621068/172893964-e02ca907-51e0-421c-a5f3-8fef855fabcb.png)

Selanjutnya coba akses route yang telah dibuat dengan mengakses alamat url 
http://localhost:8080/about

![12](https://user-images.githubusercontent.com/101621068/172894112-dffc0a21-5202-4f36-aab6-318e876ada4c.png)

Ketika diakses akan mucul tampilan error 404 file not found, itu artinya file/page tersebut tidak ada. Untuk dapat mengakses halaman tersebut, harus dibuat terlebih dahulu Contoller yang sesuai dengan routing yang dibuat yaitu Contoller Page.

## 7. Membuat Controller <b>

Selanjutnya adalah membuat Controller Page. Buat file baru dengan nama page.php pada direktori Controller kemudian isi kodenya seperti berikut.

```php
<?php

namespace App\Controllers;

class Page extends BaseController
{
    public function about()
    {
        echo "Ini halaman About";
    }
    public function contact()
    {
        echo "Ini halaman Contact";
    }
    public function faqs()
    {
        echo "Ini halaman FAQ";
    }
}
```

Berikut hasil nya

![13](https://user-images.githubusercontent.com/101621068/172894574-5c23e907-b3e6-4974-a08a-869b5c81d08a.png)

## 8. Auto Routing <b>

Secara default fitur autoroute pada Codeiginiter sudah aktif. Untuk mengubah status autoroute dapat mengubah nilai variabelnya. Untuk menonaktifkan ubah nilai true menjadi false.

```php
$routes->setAutoRoute(true);
```

Tambahkan method baru pada Controller Page seperti berikut.

```php
  public function tos()
    {
        echo "ini halaman Term of Services";
    }
```

Method ini belum ada pada routing, sehingga cara mengaksesnya dengan menggunakan alamat:
http://localhost:8080/page/tos

![14](https://user-images.githubusercontent.com/101621068/172894988-bf9189f6-e9c6-4b6b-ac02-bb565e801108.png)

## 9. Membuat View <b>

Selanjutnya adalam membuat view untuk tampilan web agar lebih menarik. Buat file baru dengan nama about php pada direktori view (app/view/about.php) kemudian isi kodenya seperti berikut.

```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title><?= $title; ?></title>
</head>
<body>
    <h1><?= $title; ?></h1>
    <hr>
    <p><?= $content; ?></p>
</body>
</html>
```

Ubah method about pada class Controller Page menjadi seperti berikut:

```php
public function about()
    {
        return view('about', [
            'title' => 'Halaman About',
            'content' => 'Ini adalah halaman about yang menjelaskan tentang isi halaman ini.'
        ]);
    }
```

Lalu refresh halaman tersebut

![15](https://user-images.githubusercontent.com/101621068/172895350-5877486d-b30a-4515-9f4e-bcff4700c208.png)

## 10. Membuat Layout Web dengan CSS <b>

Pada dasarnya layout web dengan css dapat diimplamentasikan dengan mudah pada codeigniter. Yang perlu diketahui adalah, pada Codeigniter 4 file yang menyimpan asset css dan javascript terletak pada direktori public.

Buat file css pada direktori public dengan nama style.css (copy file dari praktikum lab4_layout. Kita akan gunakan layout yang pernah dibuat pada praktikum 4.

![16](https://user-images.githubusercontent.com/101621068/172895529-3fdd8508-ffc6-4ee7-8766-2fb79487e154.png)

Kemudian buat folder template pada direktori view kemudian buat file header.php dan footer.php

File app/views/template/header.php

```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title><?= $title; ?></title>
    <link rel="stylesheet" href="<?= base_url('/style.css');?>">
</head>
<body>
    <div id="container">
    <header>
        <h1>Layout Sederhana</h1>
    </header>
    <nav>
        <a href="<?= base_url('/');?>" class="active">Home</a>
        <a href="<?= base_url('/artikel');?>">Artikel</a>
        <a href="<?= base_url('/about');?>">About</a>
        <a href="<?= base_url('/contact');?>">Kontak</a>
    </nav>
<section id="wrapper">
    <section id="main">
```

File app/views/template/footer.php

```php
    </section>
    <aside id="sidebar">
        <div class="widget-box">
            <h3 class="title">Widget Header</h3>
            <ul>
                <li><a href="#">Widget Link</a></li>
                <li><a href="#">Widget Link</a></li>
            </ul>
        </div>
        <div class="widget-box">
            <h3 class="title">Widget Text</h3>
            <p>Vestibulum lorem elit, iaculis in nisl volutpat, malesuada
tincidunt arcu. Proin in leo fringilla, vestibulum mi porta, faucibus felis.
Integer pharetra est nunc, nec pretium nunc pretium ac.</p>
        </div>
    </aside>
</section>
<footer>
    <p>&copy; 2022 - Universitas Pelita Bangsa</p>
</footer>
</div>
</body>
</html>
```

Kemudian ubah file app/view/about.php seperti berikut.

```php
<?= $this->include('template/header'); ?>

<h1><?= $title; ?></h1>
<hr>
<p><?= $content; ?></p>

<?= $this->include('template/footer'); ?>
```

Lalu refresh halaman tersebut

![17](https://user-images.githubusercontent.com/101621068/172895934-a5c34709-043f-4024-953a-c7e04bbea443.png)

# PERTANYAAN DAN TUGAS

Lengkapi kode program untuk menu lainnya yang ada pada Controller Page, sehingga semua link pada navigasi header dapat menampilkan tampilan dengan layout yang sama.
