# Gambaran Umum

MXEs adalah unit operasional inti dalam Arcium Network, yang berfungsi sebagai lingkungan yang dapat dikustomisasi tempat tugas komputasi dijalankan secara aman. MXEs dibuat oleh [**Pelanggan Komputasi**](../memulai/pemangku-kepentingan-jaringan.md#pelanggan-komputasi)\
dan bersifat fleksibel, memungkinkan pengguna menyesuaikan penyediaan data, protokol enkripsi, serta parameter lainnya sesuai dengan kebutuhan aplikasi tertentu.

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

MXE dapat berupa:

1. **Sekali Pakai (Single-Use):**\
   Dirancang untuk komputasi satu kali yang tidak berbagi state dengan tugas lain dan tidak perlu diulang. Contohnya adalah tugas analisis data terisolasi yang dieksekusi sekali lalu selesai.
2. **Berulang (Recurring):**\
   Dikonfigurasikan untuk menangani komputasi berulang dengan input data baru, namun tanpa menyimpan state yang persisten. Tipe ini ideal untuk operasi berkelanjutan di mana data segar diproses pada setiap siklus komputasi.

Arcium Network bersifat **stateless**, yang berarti setiap komputasi harus diselesaikan dalam satu epoch dan tidak dapat berlanjut ke tugas berikutnya pada level protokol. Namun, Pelanggan Komputasi dapat menggunakan mekanisme eksternal untuk mengelola persistensi data antar komputasi di luar protokol Arcium.

MXEs dapat dikaitkan dengan beberapa **Klaster**, yang bertanggung jawab untuk mengeksekusi komputasi. Keterkaitan ini meningkatkan keandalan dan ketersediaan MXEs, sehingga tetap dapat berfungsi meskipun beberapa node di Klaster utama tidak tersedia. Untuk detail lebih lanjut tentang distribusi komputasi di jaringan, lihat [**Gambaran Umum Klaster**](../klaster/gambaran-umum.md).

### Alur Eksekusi

Menjalankan komputasi di MXEs Arcium memerlukan beberapa prasyarat berikut:

1. **Pemeriksaan Kesiapan Klaster:**\
   Peer dalam Klaster menilai kapasitas mereka untuk tugas yang akan dijalankan dengan memverifikasi ketersediaan nilai preprocessing. Jika tidak mencukupi, node akan secara otomatis menghasilkan nilai baru untuk menjaga kesiapan. Perangkat lunak node menjadwalkan ronde preprocessing lebih awal untuk mengoptimalkan penggunaan sumber daya dengan memanfaatkan kapasitas komputasi dan penyimpanan yang tersedia.
2. **Pengambilan Komputasi:**\
   Komputasi dipilih dari **satu mempool terdesentralisasi**, dengan input yang relevan diambil dan dimuat ke dalam circuit untuk diproses. Node Arx bekerja sama untuk menangani gate secara paralel, sehingga efisiensi eksekusi dapat dimaksimalkan.
3. **Pengiriman Hasil:**\
   Setelah selesai, hasil akhir diverifikasi secara kolektif, ditandatangani, dan dikirim ke blockchain. Karena seluruh komputasi harus diselesaikan dalam satu epoch, tugas yang belum selesai saat epoch berakhir akan dihentikan. Pelanggan Komputasi dapat menggunakan mekanisme eksternal untuk merangkai hasil komputasi menjadi komputasi baru di luar protokol Arcium.

###
