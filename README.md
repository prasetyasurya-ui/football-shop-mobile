⚽ Wolverhampton Shop - Proyek Django

Selamat datang di repositori Wolverhampton Shop, sebuah aplikasi web e-commerce mobile sederhana yang dibangun menggunakan framework flutter. Proyek ini dikembangkan sebagai bagian dari tugas mata kuliah Pengembangan Berbasis Platform (PBP).

**[🔗 Tugas Individu 8](https://github.com/prasetyasurya-ui/football-shop-mobile/wiki/Tugas-Individu-7)**

## Tugas Individu 9

## Step by Step
 
### Mengimplementasikan fitur registrasi akun pada proyek tugas Flutter.
Membuat register page dan menyambungkan ke endpoint register pada Django, Membuat API pada django untuk menghandle registrasi akun

### Membuat halaman login pada proyek tugas Flutter.
Membuat file `login.dart` yang merupakan apa yang akan dirender ke layar pada login page

### Mengintegrasikan sistem autentikasi Django dengan proyek tugas Flutter.
- Membuat modul baru di projek Django yaitu authentication
- Membuat logika dan endpoint API registrasi, login, dan logout di modul tersebut
- Dari flutter akan mengirim request ke server django untuk autentikasi

### Membuat model kustom sesuai dengan proyek aplikasi Django.
- Menggunakan website QuickType untuk konversi data JSON ke model Dart, data JSON di dapat dari mengakses view show_json

### Membuat halaman yang berisi daftar semua item yang terdapat pada endpoint JSON di Django yang telah kamu deploy. Tampilkan name, price, description, thumbnail, category, dan is_featured dari masing-masing item pada halaman ini (Dapat disesuaikan dengan field yang kalian buat sebelumnya).
- Membuat file `product_entry_card.dart` untuk card product
- Membuat file `product_entry_list.dart` untuk menampilkan list semua item
- Mengambil data JSON dari server Django yang sudah di deploy untuk dibuild sebagai card pada flutter dan di tampilkan ke layar

### Membuat halaman detail untuk setiap item yang terdapat pada halaman daftar Item.
- Membuat file `product_detail.dart` untuk menampilkan detail produk

### Melakukan filter pada halaman daftar item dengan hanya menampilkan item yang terasosiasi dengan pengguna yang login
- Membuat view `show_json_by_user` pada server Django dan tombol `My Products` akan fetch ke API Endpoint tersebut

## Jelaskan mengapa kita perlu membuat model Dart saat mengambil/mengirim data JSON? Apa konsekuensinya jika langsung memetakan `Map<String, dynamic>` tanpa model (terkait validasi tipe, null-safety, maintainability)?
Karena Dart adalah bahasa yang mengutamakan keamanan tipe, setiap field harus ada tipe data yang secara eksplisit didefinisikan sehingga kita mempunyai set of data yang konsisten. Selain itu, pada model terdapat property null safety (seperti String?).

Konsekuensi dari hanya menggunakan map adalah harus validasi setiap field saat diakses, ketika menggunakan tipe data yang salah dapat menyebabkan runtime error. Selain itu, harus selalu mengecek null manual karena tidak ada null safety seperti model. Untuk maintanability, apabila struktur JSON dari API berubah, logika akses dimana semua `Map<String, Dynamic>` digunakan harus diubah


## Apa fungsi package http dan CookieRequest dalam tugas ini? Jelaskan perbedaan peran http vs CookieRequest
1. Fungsi package http adalah package standard dart/flutter untuk melakukan HTTP request
2. Fungsi CookieRequest adalah sebagai hal yang mempertahankan cookie pada request yang berbeda

##  Jelaskan mengapa instance CookieRequest perlu untuk dibagikan ke semua komponen di aplikasi Flutter
1. Mempertahankan Sesi, memastikan bahwa satu sesi yang sama digunakan untuk semua request API
2. Efisiensi, tanpa mengirim cookie secara manual pada setiap panggilan

## Jelaskan konfigurasi konektivitas yang diperlukan agar Flutter dapat berkomunikasi dengan Django. Mengapa kita perlu menambahkan 10.0.2.2 pada ALLOWED_HOSTS, mengaktifkan CORS dan pengaturan SameSite/cookie, dan menambahkan izin akses internet di Android? Apa yang akan terjadi jika konfigurasi tersebut tidak dilakukan dengan benar?

1. `10.0.2.2` di `ALLOWED_HOSTS` (Django)
`10.0.2.2` adalah alamat IP Khusus yang digunakan oleh Android Emulator untuk merujuk ke host development machine. Django membatasi host yang dapat mengakses, jadi dengan menambahkan IP tersebut di `ALLOWED_HOSTS` akan memungkinkan request dari emulator diterima oleh server Django yang berjalan. Apabila tidak ditambahkan maka request emulator tidak akan di terima server django


2. Mengaktifkan `CORS`
`CORS (Cross-Origin Resource Sharing)` adalah mekanisme keamanan yang membatasi request HTTP lintas domain. Flutter yang berjalan di emulator akan dianggap sebagai domain yang berbeda dari Django, Mengaktifkan `CORS` akan memungkinkan request dari Flutter diizinkan oleh Django. Apabila tidak diaktifkan maka request dari flutter akan ditolak oleh Django

3. Pengaturan `SameSite` atau `Cookie`
Saat menggunakan autentikasi berbasis sesi, Django mengatur session cookie. Pengaturan CSRF_COOKIE_SAMESITE dan SESSION_COOKIE_SAMESITE harus diatur ke None atau Lax/Strict sesuai kebutuhan dan harus diikuti dengan pengaturan SESSION_COOKIE_SECURE = True jika menggunakan HTTPS. Tujuannya adalah memastikan browser dapat mengirim cookie sesi kembali ke server. Apabila tidak, terjadi Autentikasi gagal karena request selanjutnya tidak dianggap terautentikasi karena cookie tidak kembali ke server

4. Izin akses internet di Android
Aplikasi Android tidak memiliki akses jaringan secara default. Izin `<uses-permission android:name="android.permission.INTERNET"/>` harus ditambahkan ke file AndroidManifest.xml agar aplikasi Flutter dapat melakukan request HTTP/HTTPS. Apabila tidak, aplikasi tidak akan bisa mengakses internet dan tidak dapat mengirim request ke server django

## Jelaskan mekanisme pengiriman data mulai dari input hingga dapat ditampilkan pada Flutter.
1. Input Data (Flutter): User memasukkan data ke form dan menekan tombol save/kirim
2. Validasi Lokal: Flutter akan memvalidasi input
3. Membuat objek model dari data: Data input akan menjadi satu kesatuan yaitu model Dart
4. Membuat JSON: dari model Dart akan diubah menjadi string JSON
5. HTTP Request: Instance `CookieRequest` atau `http` akan digunakan untuk mengirim JSON String endpoint API Django
6. Validasi dan Deserialisasi: Data JSON divalidasi dan diubah menjadi objek python.
7. Logika & Penyimpanan: Data diproses dan disimpan ke databases
8. Response balik: Django akan mengirimkan respon JSON balik ke flutter tentang status request
9. Menerima Respon (Flutter): Flutter menerima respon JSON dan mengecek status requestnya (misalnya diterima atau ditolak)
10. Deserialiasi model: respon JSON diubah kembali menjadi objek model Dart
11. Pembaruan UI: StateManagement diperbarui dengan data baru, Widget yang mendengarkan perubahan state akan rebuild dan menampilkan data baru di layar

## Jelaskan mekanisme autentikasi dari login, register, hingga logout. Mulai dari input data akun pada Flutter ke Django hingga selesainya proses autentikasi oleh Django dan tampilnya menu pada Flutter.
- Register
1. Input: User memasukkan username dan password
2. Request: Data dikirimkan sebagai JSON ke endpoint register
3. Pembuatan Akun: View register akan menerima data, memvalidasi, lalu menggunakan Django untuk membuat akun baru dan menyimpannya di database
4. Respon (Django): Django merespon dengan status berhasil atau error tergantung di proses validasi
5. Feedback: Jika berhasil, pengguna akan diarahkan ke Login page oleh flutter dan notifikasi apabila gagal

- Login
1. Input: User memasukkan username dan password
2. Request: Data dikirimkan sebagai JSON ke endpoint login
3. Verifikasi: View login akan menerima data, memvalidasi dan apabila berhasil membuat session cookie baru
4. Pembaruan status: Flutter akan mencatat bahwa pengguna sekarang sudah login dan meredirect user ke halaman utama(menu)

- Logout
1. Input: User menekan tombol logout
2. Request: Data dikirimkan sebagai JSON ke endpoint logout
3. Verifikasi: View logout akan menerima data, memvalidasi dan apabila berhasil menginvalidasi sesi sekarang dan menghapus cookie
4. Pembaruan status: Flutter akan mencatat bahwa pengguna sekarang sudah logout dan meredirect user ke login page