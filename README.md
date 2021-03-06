# LabWeb 11
## Nama        : Wayis Al Qorni TS
## Nim         : 312010169
## Kelas       : TI.20.A.1
## Mata Kuliah : Pemrograman web

### Langkah-langkah Praktikum 
#### Persiapan 
Sebelum memulai menggunakan Framework Codeigniter, perlu dilakukan konfigurasi pada webserver. Beberapa ekstensi PHP perlu diaktifkan untuk kebutuhan pengembangan Codeigniter 4. 
Berikut beberapa ekstensi yang perlu diaktifkan: • php-json ekstension untuk bekerja dengan JSON; • php-mysqlnd native driver untuk MySQL; • php-xml ekstension untuk bekerja dengan XML; • php-intl ekstensi untuk membuat aplikasi multibahasa; • libcurl (opsional), jika ingin pakai Curl. 
 
Untuk mengaktifkan ekstentsi tersebut, melalu XAMPP Control Panel, pada bagian Apache klik Config -> PHP.ini 

![gamabar1](s/1.PNG)

Pada bagian extention, hilangkan tanda ; (titik koma) pada ekstensi yang akan diaktifkan. Kemudian simpan kembali filenya dan restart Apache web server. 

![gambar2](s/2.PNG)

### Instalasi Codeigniter 4 
Untuk melakukan instalasi Codeigniter 4 dapat dilakukan dengan dua cara, yaitu cara manual dan menggunakan composer. Pada praktikum ini kita menggunakan cara manual.

* Unduh Codeigniter dari website https://codeigniter.com/download  
* Extrak file zip Codeigniter ke direktori htdocs/lab11_ci. 
* Ubah nama direktory framework-4.x.xx menjadi ci4. 
* Buka browser dengan alamat http://localhost/lab11_ci/ci4/public/  
 
 ![gambar3](s/3.PNG)

 ### Menjalankan CLI (Command Line Interface) 
 Codeigniter 4 menyediakan CLI untuk mempermudah proses development. Untuk mengakses CLI buka terminal/command prompt.  

 ![gambar4](s/4.PNG)

 Arahkan lokasi direktori sesuai dengan direktori kerja project dibuat (xampp/htdocs/lab11_ci/ci4/)  
Perintah yang dapat dijalankan untuk memanggil CLI Codeigniter adalah:

`php spark`

![gambar5](s/5.PNG)

### Mengaktifkan Mode Debugging 
Codeigniter 4 menyediakan fitur debugging untuk memudahkan developer untuk mengetahui pesan error apabila terjadi kesalahan dalam membuat kode program. 
Secara default fitur ini belum aktif. Ketika terjadi error pada aplikasi akan ditampilkan pesan kesalahan seperti berikut. 

![gambar6](s/6.PNG)

Semua jenis error akan ditampilkan sama. Untuk memudahkan mengetahui jenis errornya, maka perlu diaktifkan mode debugging dengan mengubah nilai konfigurasi pada environment variable CI_ENVIRINMENT menjadi development. 

![gambar7](s/7.PNG)

Ubah nama file env menjadi .env kemudian buka file tersebut dan ubah nilai variable CI_ENVIRINMENT menjadi development. 

![gambar8](s/8.PNG)

Contoh error yang terjadi. Untuk mencoba error tersebut, ubah kode pada file app/Controller/Home.php hilangkan titik koma pada akhir kode. 
 
 ![gambar9](s/9.PNG)

 ### Struktur Direktori 
 Untuk lebih memahami Framework Codeigniter 4 perlu mengetahui struktur direktori dan file yang ada. Buka pada Windows Explorer atau dari Visual Studio Code -> Open Folder. 

Terdapat beberapa direktori dan file yang perlu dipahami fungsi dan kegunaannya. 
• .github folder ini kita butuhkan untuk konfigurasi repo github, seperti konfigurasi untuk build dengan github action; 
• app folder ini akan berisi kode dari aplikasi yang kita kembangkan; 
• public folder ini berisi file yang bisa diakses oleh publik, seperti file index.php, robots.txt, favicon.ico, ads.txt, dll; 
• tests folder ini berisi kode untuk melakukan testing dengna PHPunit; 
• vendor folder ini berisi library yang dibutuhkan oleh aplikasi, isinya juga termasuk kode core dari system CI. 
• writable folder ini berisi file yang ditulis oleh aplikasi. Nantinya, kita bisa pakai untuk menyimpan file 

yang di-upload, logs, session, dll. 
Sedangkan file-file yang berada pada root direktori CI sebagai berikut. 
• .env adalah file yang berisi variabel environment yang dibutuhkan oleh aplikasi. 
• .gitignore adalah file yang berisi daftar nama file dan folder yang akan diabaikan oleh Git. 
• build adalah script untuk mengubah versi codeigniter yang digunakan. Ada versi release (stabil) dan development (labil). 
• composer.json adalah file JSON yang berisi informasi tentang proyek dan daftar library yang dibutuhkannya. File ini digunakan oleh Composer sebagai acuan. 
• composer.lock adalah file yang berisi informasi versi dari libraray yang digunakan aplikasi.
• license.txt adalah file yang berisi penjelasan tentang lisensi Codeigniter; 
• phpunit.xml.dist adalah file XML yang berisi konfigurasi untuk PHPunit. 
• README.md adalah file keterangan tentang codebase CI. Ini biasanya akan dibutuhkan pada repo github atau gitlab. 
• spark adalah program atau script yang berfungsi untuk menjalankan server, generate kode, dll. 

![gambar10](s/10.PNG)

Fokus kita pada folder app, dimana folder tersebut adalah area kerja kita untuk membuat aplikasi. Dan folder public untuk menyimpan aset web seperti css, gambar, javascript, dll. 

### Memahami Konsep MVC 
Codeigniter menggunakan konsep MVC. MVC meripakan singkatan dari Model-View-Controller. MVC merupakan konsep arsitektur yang umum digunakan dalam pengembangan aplikasi. Konsep MVC adalah memisahkan kode program berdasarkan logic proses, data, dan tampilan. Untuk logic proses diletakkan pada direktori Contoller, Objek data diletakkan pada direktori Model, dan desain tampilan diletakkan pada direktori View.

Codeigniter menggunakan konsep pemrograman berorientasi objek dalam mengimplementasikan konsep MVC.

Model merupakan kode program yang berisi pemodelan data. Data dapat berupa database ataupun sumber lainnya.

View merupakan kode program yang berisi bagian yang menangani terkait tampilan user interface sebuah aplikasi. didalam aplikasi web biasanya pasti akan berhubungan dengan html dan css.

Controller merupakaan kode program yang berkaitan dengan logic proses yang menghubungkan antara view dan model. Controller berfungsi untuk menerima request dan data dari user kemudian diproses dengan menghubungkan bagian model dan view.

Routing dan Controller Routing merupakan proses yang mengatur arah atau rute dari request untuk menentukan fungsi/bagian mana yang akan memproses request tersebut. Pada framework CI4, routing bertujuan untuk menentukan Controller mana yang harus merespon sebuah request. Controller adalah class atau script yang bertanggung jawab merespon sebuah request.

Pada Codeigniter, request yang diterima oleh file index.php akan diarahkan ke Router untuk meudian oleh router tesebut diarahkan ke Controller. 

Router terletak pada file app/config/Routes.php 

![gambar11](s/11.PNG)

Pada file tersebut kita dapat mendefinisikan route untuk aplikasi yang kita buat. 
Contoh: 

`$routes->get('/', 'Home::index');` 
 
Kode tersebut akan mengarahkan rute untuk halaman home.  
Membuat Route Baru. Tambahkan kode berikut di dalam Routes.php 
```html
$routes->get('/about', 'Page::about'); 
$routes->get('/contact', 'Page::contact'); 
$routes->get('/faqs', 'Page::faqs'); 
 ```
Untuk mengetahui route yang ditambahkan sudah benar, buka CLI dan jalankan perintah berikut.

`php spark routes`

![gambar12](s/12.PNG)

Selanjutnya coba akses route yang telah dibuat dengan mengakses alamat url http://localhost:8080/about  

![gambar13](s/13.PNG)

Ketika diakses akan mucul tampilan error 404 file not found, itu artinya file/page tersebut tidak ada. Untuk dapat mengakses halaman tersebut, harus dibuat terlebih dahulu Contoller yang sesuai dengan routing yang dibuat yaitu Contoller Page. 

### Membuat Controller 
Selanjutnya adalah membuat Controller Page. Buat file baru dengan nama page.php pada direktori Controller kemudian isi kodenya seperti berikut. 
```html
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

Selanjutnya refresh Kembali browser, maka akan ditampilkan hasilnya yaotu halaman sudah dapat diakses. 

![gambar14](s/14.PNG)

### Auto Routing 
Secara default fitur autoroute pada Codeiginiter sudah aktif. Untuk mengubah status autoroute dapat mengubah nilai variabelnya. Untuk menonaktifkan ubah nilai true menjadi false. 

`$routes->setAutoRoute(true);` 
 
Tambahkan method baru pada Controller Page seperti berikut. 
```html
public function tos() 
{     
    echo "ini halaman Term of Services"; 
} 
```
Method ini belum ada pada routing, sehingga cara mengaksesnya dengan menggunakan alamat: http://localhost:8080/page/tos  
 
 ![gambar15](s/15.PNG)

### Membuat View 
 Selanjutnya adalam membuat view untuk tampilan web agar lebih menarik. Buat file baru dengan nama about.php pada direktori view (app/view/about.php) kemudian isi kodenya seperti berikut. 
```html
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
```html
 public function about() 
 {     
     return view('about', [         
         'title' => 'Halaman Abot',         
         'content' => 'Ini adalah halaman abaut yang menjelaskan tentang isi halaman ini.'     
         ]); 
} 
```

![gambar16](s/16.PNG)

### Membuat Layout Web dengan CSS 
Pada dasarnya layout web dengan css dapat diimplamentasikan dengan mudah pada codeigniter. Yang perlu diketahui adalah, pada Codeigniter 4 file yang menyimpan asset css dan javascript terletak pada direktori public.

Buat file css pada direktori public dengan nama style.css (copy file dari praktikum lab4_layout. Kita akan gunakan layout yang pernah dibuat pada praktikum 4. 

![gambar17](s/17.PNG)

Kemudian buat folder template pada direktori view kemudian buat file header.php dan footer.php 

File app/view/template/header.php 
```html
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

File app/view/template/footer.php 
```html
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
                <p>Vestibulum lorem elit, iaculis in nisl volutpat, malesuada tincidunt arcu. Proin in leo fringilla, vestibulum mi porta, faucibus felis. Integer pharetra est nunc, nec pretium nunc pretium ac.</p>             
            </div>         
        </aside>     
    </section>     
    <footer>         
        <p>&copy; 2021 - Universitas Pelita Bangsa</p>     
    </footer>     
</div> 
</body> 
</html> 
```

Kemudian ubah file app/view/about.php seperti berikut. 
```html
<?= $this->include('template/header'); ?> 
 
<h1><?= $title; ?></h1> 
<hr> 
<p><?= $content; ?></p> 
 
<?= $this->include('template/footer'); ?> 
```

Selanjutnya refresh tampilan pada alamat http://localhost:8080/about 

![gambar18](s/18.PNG)

### Pratikum 12

## 1. Database
- Jalankan ``Apache, MySql`` pada Xampp, Buat database dengan nama ``lab_ci4`` di http://localhost/phpmyadmin.
- Buat tabel dengan nama ``artikel``.
    ```sql
    CREATE TABLE artikel (
        id INT(11) auto_increment,
        judul VARCHAR(200) NOT NULL,
        isi TEXT,
        gambar VARCHAR(200),
        status TINYINT(1) DEFAULT 0,
        slug VARCHAR(200),
        PRIMARY KEY(id)
    );
    ```
![Foto](foto/labci4.png)
<br>

## 2. Konfigurasi Koneksi Database
- Terletak di folder ``ci4``, file `.env`, Hapus tanda `#`.
![Foto](foto/env.png)
<br>

## 3. Membuat Model 
- Terletak di folder `app/Models`, buat file `ArtikelModel.php`.
![Foto](foto/model.png)
<br>

## 4. Membuat Controller 
- Terletak di folder `app/Controllers`, buat file `Artikel.php`.
![Foto](foto/artikel.png)
<br>

## 5. Membuat View pada artikel 
- Terletak di folder `app/Views/artikel`, buat file `index.php`.
![Foto](foto/index.png)
<br>

- Buka browser, ketik http://localhost:8080/artikel 

![Foto](foto/index2.png)
<br>

- Masukkan data ke tabel artikel,
    ```sql
    INSERT INTO artikel (judul, isi, slug) VALUE
    ('Artikel pertama', 'Lorem Ipsum adalah contoh teks atau dummy dalam industri 
    percetakan dan penataan huruf atau typesetting. Lorem Ipsum telah menjadi 
    standar contoh teks sejak tahun 1500an, saat seorang tukang cetak yang tidak 
    dikenal mengambil sebuah kumpulan teks dan mengacaknya untuk menjadi sebuah 
    buku contoh huruf.', 'artikel-pertama'), 
    ('Artikel kedua', 'Tidak seperti anggapan banyak orang, Lorem Ipsum bukanlah 
    teks-teks yang diacak. Ia berakar dari sebuah naskah sastra latin klasik dari 
    era 45 sebelum masehi, hingga bisa dipastikan usianya telah mencapai lebih 
    dari 2000 tahun.', 'artikel-kedua');
    ``` 
<br>

- Refresh kembali browser.
![Foto](foto/artikel2.png)
<br>

## 6. Membuat Tampilan detail Artikel
- Terletak di folder `app/Controllers`, edit file `Artikel.php`. Tambah method ``view()``.
![Foto](foto/artikel1.png)
<br>

## 7. Membuat View pada Detail
- Terletak di folder `app/Views/artikel`, buat file `detail.php`.
![Foto](foto/detail.png)
<br>

## 8. Membuat Routing untuk artikel detail
- Terletak di folder `app/Config`, edit file `Routes.php`.
![Foto](foto/routes.png)
<br>

- Klik `Artikel Kedua` pada http://localhost:8080/artikel, untuk pindah ke detailnya.
![Foto](foto/artikel22.png)
<br>

## 9. Membuat Menu admin
- Terletak di folder `app/Controller`, edit file `Artikel.php`. Tambah method `admin_index()`.
![Foto](foto/index11.png)
<br>

- Selanjutnya, akses kembali folder `app/Views/artikel`, buat file `admin_index.php`.
    ```php
    <?= $this->include('template/admin_header'); ?>
    <table class="table table-bordered table-hover">
        <thead>
            <tr class="table-primary">
                <th scope="col">ID</th>
                <th scope="col">Judul</th>
                <th scope="col">Status</th>
                <th scope="col">Aksi</th>
            </tr>
        </thead>
        <tbody>
            <?php if($artikel): foreach($artikel as $row): ?>
            <tr>
                <td><?= $row['id']; ?></td>
                <td>
                    <b><?= $row['judul']; ?></b>
                    <p><small><?= substr($row['isi'], 0, 50); ?></small></p>
                </td>
                <td><?= $row['status']; ?></td>
                <td>
                    <a class="btn btn-primary p-1" href="<?= base_url('/admin/artikel/edit/' . 
                    $row['id']);?>">Ubah</a>
                    <a class="btn btn-danger p-1" onclick="return confirm('Yakin menghapus data?');" href="<?= base_url('/admin/artikel/delete/' . 
                    $row['id']);?>">Hapus</a>
                </td>
            </tr>
            <?php endforeach; else: ?>
            <tr>
                <td colspan="4">Belum ada data.</td>
            </tr>
            <?php endif; ?>
        </tbody>
        <tfoot>
            <tr class="table-primary">
                <th scope="col">ID</th>
                <th scope="col">Judul</th>
                <th scope="col">Status</th>
                <th scope="col">Aksi</th>
            </tr>
        </tfoot>
    </table>
    <?= $this->include('template/admin_footer'); ?>
    ```
<br>

- Buka folder yang ada di ``app/Views/artikel/template``, kemudian buat:
- ``admin_header.php``,
![Foto](foto/1212.png)
<br>

- ``admin_footer.php``
![Foto](foto/1111.png)
<br>

## 10. Membuat Routing untuk menu admin
- Terletak di folder `app/Config`, edit file `Routes.php`.
![Foto](foto/routes1.png)
<br>

- Akses browser dengan http://localhost:8080/admin/artikel.
![Foto](foto/ending12.png)
<br>

## 11. Menambah data untuk Artikel
- Terletak di folder `app/Controller`, edit file `Artikel.php`. Tambah method `add()`.
![Foto](foto/artikelphp.png)
<br>

- Akses kembali folder `app/Views/artikel`, buat file `form_add.php`.
![Foto](foto/formphp.png)
<br>

- Akses browser dengan http://localhost:8080/admin/artikel/add.
![Foto](foto/admin.png)
<br>

## 12. Mengubah data pada Artikel
- Terletak di folder `app/Controller`, edit file `Artikel.php`. Tambah method `edit()`.
![Foto](foto/artikel11.png)
<br>

- Akses kembali folder `app/Views/artikel`, buat file `form_edit.php`.
![Foto](foto/formedit.png)
<br>

- Akses browser dengan http://localhost:8080/admin/artikel/edit/1 untuk Mengubah artikel pertama.
![Foto](foto/formedit.png)
<br>

## 13. Menghapus data pada Artikel
- Terletak di folder `app/Controller`, edit file `Artikel.php`. Tambah method `delete()`.
![Foto](foto/data.png)
<br>

- Akses browser dengan http://localhost:8080/admin/artikel/add untuk membuat artikel ketiga, lalu `kirim`.
![Foto](foto/web12.png)
<br>

- Untuk mengeceknya ketik di url, http://localhost:8080/artikel kemudian enter.
![Foto](foto/lab12.png)
<br>

- Pergi ke menu admin untuk menghapusnya, http://localhost:8080/admin/artikel, kemudian pilih `hapus`.
![Foto](foto/delet.png)
<br>

- Artikel berhasil dihapus.
![Foto](foto/kelar.png)
<br>
</div>

### LINK LANJUTANNYA PERTEMUAN 13
https://github.com/RiskyHariAdi/lab13_web 