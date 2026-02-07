# Tugas Komputasi

**Unit Komputasi (Computation Unit atau CU)** adalah konstanta di seluruh jaringan yang merepresentasikan sejumlah tetap pekerjaan komputasi.

CU merupakan unit komputasi terkecil di Jaringan Arcium, dan seluruh jenis operasi aritmetika di Jaringan Arcium (yang membentuk komputasi) diukur menggunakan CU.

Secara khusus, penetapan harga dasar komputasi menggunakan CU sebagai acuan dasar untuk kompensasi node Arx.

### Jenis Tugas Komputasi

Di Jaringan Arcium, komputasi terbagi ke dalam dua kategori utama:

**1) Komputasi Sistem**, dan\
**2) Komputasi Pelanggan**.

Kedua jenis tugas ini memiliki tujuan yang berbeda di dalam jaringan, di mana yang pertama berkaitan dengan operasi internal jaringan, sedangkan yang kedua menangani permintaan dari pelanggan eksternal.

### Komputasi Sistem

Komputasi Sistem merupakan proses kritis yang dihasilkan secara otomatis oleh jaringan untuk menjaga kesehatan dan operasionalnya. Proses ini meliputi:

* **Komputasi Distributed Key Generation (DKG)**: Setiap node Arx di dalam sebuah Klaster menerima fragmen dari keseluruhan kunci kriptografi yang dikenal sebagai _key share_. _Key share_ ini secara kolektif membentuk kunci untuk _MPC eXecution Environment (MXE)_ pada Klaster tersebut, sehingga memungkinkan pelaksanaan tugas komputasi bersama secara aman tanpa mengungkapkan masukan individual.
* **Komputasi Migrasi**: Mengelola migrasi Klaster yang direncanakan maupun yang dipaksakan (lihat [**Migrasi Klaster**](../klaster/forking-and-migrasi-klaster.md)). Komputasi ini memastikan sistem dapat beradaptasi secara dinamis terhadap perubahan atau kegagalan. Biaya prioritas untuk komputasi migrasi dikontribusikan secara kolektif oleh node-node dalam Klaster yang bermigrasi, dengan besaran yang bervariasi tergantung preferensi masing-masing node dan tingkat urgensi migrasi.
* **Komputasi Deteksi Ketidakberpartisipasian**: Dipicu ketika terdeteksi ketidakberpartisipasian di dalam sebuah Klaster. Komputasi ini meningkatkan proses penyelesaian sengketa dengan melibatkan node tambahan untuk menangani permasalahan, sehingga memastikan akuntabilitas dan stabilitas jaringan. Apabila terjadi _slashing_ akibat ketidakberpartisipasian atau bentuk pelanggaran lainnya, biaya prioritas yang terkait dengan komputasi ini akan dikembalikan kepada node-node yang berpartisipasi, guna melindungi kepentingan mereka dan menjaga integritas operasional.

### Komputasi Pelanggan

Komputasi Pelanggan adalah tugas yang diajukan oleh **Pelanggan Komputasi** untuk menjalankan operasi yang bersifat privat dan rahasia. Tugas-tugas ini sangat dapat dikonfigurasi untuk memenuhi beragam kebutuhan pengembang dan pelaku bisnis.
