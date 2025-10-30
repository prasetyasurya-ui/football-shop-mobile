⚽ Wolverhampton Shop - Proyek Django

Selamat datang di repositori Wolverhampton Shop, sebuah aplikasi web e-commerce sederhana yang dibangun menggunakan framework Django. Proyek ini dikembangkan sebagai bagian dari tugas mata kuliah Pengembangan Berbasis Platform (PBP).

**[🔗 Tugas Individu 6](https://github.com/prasetyasurya-ui/football_shop)**

## Tugas Individu 7

**[🔗 Kunjungi Aplikasi yang Sudah Deploy](https://prasetya-surya-footballshop.pbp.cs.ui.ac.id/)**

## Jelaskan apa itu widget tree pada Flutter dan bagaimana hubungan parent-child (induk-anak) bekerja antar widget.

Widget tree adalah tree yang nodenya dalah widget. Setiap widget dapat memiliki child dan parent dapat mengatur batasan untuk childnya seperti ukuran parent juga dapat mengatur letak posisi child di parent

## Sebutkan semua widget yang kamu gunakan dalam proyek ini dan jelaskan fungsinya.
- Stateless Widget
widget dasar yang tidak berubah konfigurasinya.
- Scaffold
kerangka utama halaman yang menyediakan slot untuk `appBar` (atas) dan `body` (tengah).
- Appbar
Widget yang muncul di atas layar, biasanya berisi judul.
- Text
Widget untuk menampilkan teks atau tulisan.
- Padding
Memberi jarak (padding) di sekeliling childnya
- SizedBox
Widget untuk membuat suatu kotak dengan ukuran tertentu.
- Center
Menempatkan posisi child di tengah
- GridView
Widget untuk menyusun child dalam bentuk grid
- Material
Widget yang memberi tampilan fisik
- InkWell
Membuat child nya bisa di klik dan ketika di klik ada efek visualnya
- Container
Widget yanb bisa digunakan untuk memberi padding, warna, atau ukuran.
- Icon
Menampilkan icon dari koleksi icon material design


##  Apa fungsi dari widget MaterialApp? Jelaskan mengapa widget ini sering digunakan sebagai widget root.
MaterialApp adalah widget wrapper level tertinggi. Sering digunakan karena dia otomatis menyediakan layanan inti seperti navigasi dan tema

## Jelaskan perbedaan antara StatelessWidget dan StatefulWidget. Kapan kamu memilih salah satunya?
1. Stateless widget tidak bisa berubah setelah dibuat. Gunakan ketika UInya hanya diam dan bergantung pada data yang dikirim parent
2. Stateful widget bisa merubah tampilannya sendiri saat runtime, gunakan ketika widget perlu mengingat sesuatu yang bisa berubah

## Apa itu BuildContext dan mengapa penting di Flutter? Bagaimana penggunaannya di metode build?
BuildContext adalah lokasi sebuah widget di dalam widget tree. Ini penting karena BuildContext digunakan untuk menemukan widget yang posisinya berada di atas widget saat ini di dalam tree. Contohnya ScaffoldMessenger.of(context) yang artinya buildContext tolong temukan ScaffoldMessanger terdekat yang ada di atas posisi widget ini

## Jelaskan konsep "hot reload" di Flutter dan bagaimana bedanya dengan "hot restart".
1. Hot Reload, injeksi kode yang baru ke VM yang sedang berjalan
2. Hot Restart, Menghancurkan dart VM yang lama lalu membuat yang baru

## Jelaskan bagaimana kamu menambahkan navigasi untuk berpindah antar layar di aplikasi Flutter.
Navigasi di flutter dikelola oleh widget `Navigator` yang bekerja seperti stack. contohnya pada onTap: () {
    Navigator.push(context, MaterialPageRoute(builder: (context) => DetailScreen()),)
}

- `Navigator.push()` akan mendorong layar baru ke stack Navigator
- `Navigator.pop()` akan kembali ke layar sebelumnya