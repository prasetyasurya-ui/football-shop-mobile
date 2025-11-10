⚽ Wolverhampton Shop - Proyek Django

Selamat datang di repositori Wolverhampton Shop, sebuah aplikasi web e-commerce sederhana yang dibangun menggunakan framework Django. Proyek ini dikembangkan sebagai bagian dari tugas mata kuliah Pengembangan Berbasis Platform (PBP).

**[🔗 Tugas Individu 7](https://github.com/prasetyasurya-ui/football-shop-mobile/wiki/Tugas-Individu-7)**

## Tugas Individu 8

## Jelaskan perbedaan antara Navigator.push() dan Navigator.pushReplacement() pada Flutter. Dalam kasus apa sebaiknya masing-masing digunakan pada aplikasi Football Shop kamu?

Kedua Method ini digunakan untuk berpindah antar halaman dengan stack dan perbedaannya bagaimana cara mereka mengelola stack tersebut

- `Navigator.push()` menambahkan rute baru ke paling atas stack
- `Navigator.pushReplacement()` rute saat ini akan dihapus dari stack dan digantikan dengan rute baru

1. Untuk `Navigator.push()` cocok digunakan saat pengguna berada di halaman utama dan ingin ke halaman add product form dan ketika memencet kembali mereka akan ke halaman utama
2. Untuk `Navigator.pushReplacement()` cocok digunakan saat pengguna dari halaman add product misalnya akan ke page lihat products, mereka akan kembali ke halaman utama dan bukan halaman add product


## Bagaimana kamu memanfaatkan hierarchy widget seperti Scaffold, AppBar, dan Drawer untuk membangun struktur halaman yang konsisten di seluruh aplikasi?
Scaffold digunakan sebagai kerangka dasar struktur visual dari aplikasi. Appbar digunakan untuk menyajikan judul di paling atas layar secara konsisten letaknya. Drawer digunakan untuk menu navigasi yang dapat diakses secara cepat

##  Dalam konteks desain antarmuka, apa kelebihan menggunakan layout widget seperti Padding, SingleChildScrollView, dan ListView saat menampilkan elemen-elemen form? Berikan contoh penggunaannya dari aplikasi kamu.
- Padding, kelebihan dari padding adalah mencegah elemen menempel langsung ke tepi suatu elemen lain, akan memberikan jarak kosong (whitespace), digunakan untuk di form untuk bagian inputnya
- SingleChildScrollView, Memungkinkan konten di dalamnya untuk discroll ketika konten melebihi ukuran layar. Mencegah overflow. (digunakan untuk page form agar bisa discroll ketika input form banyak yang membuat menjadi panjang ke bawah)
- ListView, Untuk menampilkan daftar item yang dinamis. (digunakan pada drawer untuk menampilkan list item)

## Bagaimana kamu menyesuaikan warna tema agar aplikasi Football Shop memiliki identitas visual yang konsisten dengan brand toko?
Implementasi menggunakan primary color dan color secondary dengan menggunakan context agar semua widget dapat menggunakan warna warna tema yang telah ditentukan.