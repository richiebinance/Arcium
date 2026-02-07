# Daftar Prioritas Node & Kriteria Seleksi Alternatif

### Daftar Prioritas Node (Node Priority List)

Selama proses pembuatan Klaster, node disusun dalam sebuah **daftar prioritas** yang menentukan urutan aktivasi **node cadangan** apabila node aktif menjadi tidak tersedia.

**Node Priority List bersifat tidak dapat diubah (immutable) setelah klaster** **dibuat.** Sifat ini menjamin keandalan dan kepercayaan terhadap properti Klaster yang telah ditetapkan, karena MXEs lain dapat bergantung pada properti tersebut agar dapat berfungsi dengan benar. Dengan mencegah perubahan setelah pembuatan, jaringan memastikan stabilitas dan konsistensi operasional.

Selain itu, Node Priority List juga berfungsi bersamaan dengan **Migrasi Klaster**. Dalam proses migrasi, daftar ini menjadi acuan untuk menentukan node mana yang akan dituju sebagai pengganti, sehingga tetap menjaga integritas operasional Klaster.

Dalam kondisi migrasi, daftar ini bertujuan untuk:

* Menggantikan node yang tidak tersedia secara mulus, sehingga gangguan pada operasi komputasi dapat diminimalkan.
* Mengoptimalkan alokasi sumber daya dengan memprioritaskan node yang memiliki kapasitas komputasi dan tingkat keandalan yang lebih tinggi.

### **Seleksi Alternatif Otomatis (Automatic Alternative Selection)**

**Automatic Alternative Selection** adalah mekanisme opsional untuk mencari **node alternatif** bagi sebuah klaster, yang dapat diaktifkan atau dinonaktifkan pada tingkat klaster saat proses pembuatan.

Jika diaktifkan, mekanisme ini akan berjalan ketika:\
a) Node Priority List telah habis, atau\
b) seluruh node dalam daftar tersebut tidak tersedia.

Proses seleksi dimulai dengan memfilter node berdasarkan kriteria tertentu:

1. Mengevaluasi persyaratan **Trusted Execution Environment (TEE)** untuk memastikan kesesuaian dengan kebutuhan keamanan klaster.
2. Menilai spesifikasi hardware, dengan mengecualikan node yang memiliki sumber daya tidak memadai.
3. Setelah proses penyaringan, node yang tersisa akan dirangking menggunakan **Trust Score**, yang mempertimbangkan faktor-faktor seperti durasi operasional node dan riwayat slashing, sehingga mendorong pemilihan node yang lebih andal dan terpercaya.

Selain itu, klaster juga dapat menyesuaikan kriteria pengecualian untuk memperhalus proses seleksi. Hal ini mencakup penggunaan **Node Blacklist** (offchain) untuk menghindari node tertentu, serta **Jurisdictional Blacklist** untuk mengecualikan node yang beroperasi di wilayah geografis tertentu.
