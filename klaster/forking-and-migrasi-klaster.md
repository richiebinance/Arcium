# Forking & Migrasi Klaster

Sebagai pengingat, **Klaster** dalam Arcium Network adalah sekumpulan node Arx yang digabungkan untuk secara kolektif mengeksekusi operasi **Multi-Party Computation (MPC)**.

Untuk **Klaster non-Permissioned**, sebelum klaster diaktifkan, satu node Arx acak dari Network akan dimasukkan ke dalam kumpulan node klaster. Node acak ini tidak ditentukan secara eksplisit oleh **Computation Customer**, melainkan dipilih secara independen melalui mekanisme [**Pemilihan Node Alternatif Otomatis**](daftar-prioritas-node-and-kriteria-seleksi-alternatif.md#daftar-prioritas-node-node-priority-list) (lihat bagian [Sybil Resistance](ketahanan-terhadap-serangan-sybil-sybil-resistance.md#id-1.-ketahanan-sybil-intra-klaster) untuk penjelasan lebih lanjut).

klaster akan aktif dan dapat digunakan setelah **seluruh node Arx** yang ditugaskan menyetujui penugasan tersebut, termasuk node yang dipilih secara acak. Jika persetujuan tidak bersifat bulat, **Computation Customer** yaitu entitas yang memulai dan mengomisi perhitungan dalam jaringan dapat membatalkan proses pembentukan klaster setelah minimal satu epoch penuh berlalu. Apabila satu saja node Arx yang ditugaskan ke klaster menolak penugasan, maka proses pembuatan klaster akan gagal.

klaster dalam Arcium Network dirancang agar adaptif terhadap berbagai situasi. Namun, terdapat kondisi tertentu di mana perubahan komposisi Klaster menjadi diperlukan.

Dua mekanisme utama yang memungkinkan adaptabilitas ini adalah:

1. **Klaster Forking**: Proses di mana node-node dalam sebuah Klaster memutuskan untuk mengeluarkan (eject) sebuah MXE, sehingga terbentuk Klaster baru yang secara independen mendukung MXE tersebut.
2. **Klaster Migration**: Pemindahan tugas atau node dari satu Klaster ke Klaster lain, baik karena pengunduran diri yang direncanakan maupun kondisi terpaksa seperti downtime, penurunan stake, atau akibat **Klaster Forking**.

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

### Percabangan Klaster

Percabangan Klaster terjadi ketika satu atau lebih node Arx dalam sebuah Klaster memutuskan untuk mengeluarkan MXE tertentu dari kelompok mereka. Hal ini dapat terjadi jika node-node tersebut menilai bahwa MXE terlibat dalam aktivitas yang tidak diinginkan (misalnya aktivitas ilegal) atau muncul masalah operasional lainnya. Berikut alur prosesnya:

1. **Inisiasi Fork**\
   Jika sebuah node Arx dalam Klaster ingin mengeluarkan MXE, node tersebut akan memberi sinyal atas niat tersebut. Node-node lain dalam Klaster memiliki waktu hingga awal epoch berikutnya untuk memutuskan apakah akan ikut mengeluarkan MXE atau tetap mendukungnya. Pada awal epoch baru, fork hanya akan terjadi jika setidaknya satu node memilih untuk tetap mendukung MXE yang dikeluarkan. Jika semua node sepakat untuk mengeluarkan MXE, maka fork tidak terjadi.
2. **Pembentukan Klaster Baru**\
   Node-node yang memilih untuk mengeluarkan MXE akan tetap berada di Klasterasli, sementara node-node yang memilih untuk terus mendukung MXE akan membentuk Klaster baru. Namun, node yang mendukung MXE yang dikeluarkan juga tetap menjadi bagian dari Klaster asli, sehingga secara efektif berpartisipasi dalam Klaster lama dan Klaster baru sekaligus. Biaya pembentukan Klaster baru dan migrasi MXE ke Klaster tersebut akan dibagi di antara node-node yang memulai proses pengeluaran MXE.
3. **Menjaga Keberlanjutan Layanan**\
   Klaster asli dapat terus beroperasi tanpa gangguan, memberikan dukungan komputasi kepada MXE lain. Sementara itu, Klaster baru memungkinkan MXE yang dikeluarkan untuk tetap melanjutkan operasinya, terisolasi dari node-node yang tidak lagi ingin terlibat.

### **Migrasi Klaster**

Migrasi adalah proses pemindahan tugas dari satu Klaster node Arx ke Klaster node Arx lainnya.

Terdapat dua jenis utama migrasi:

1. **Migrasi Paksa (Forced Migration)**\
   Penugasan ulang tugas node Arx secara otomatis ke node pengganti ketika node tersebut gagal memenuhi kriteria yang disyaratkan, seperti penurunan stake atau downtime berkepanjangan. Mekanisme ini memastikan keberlanjutan operasional Klaster. Sebagai contoh, pelanggaran protokol (misalnya kecurangan berulang atau downtime lama) dapat memicu migrasi paksa, di mana tanggung jawab node yang bermasalah dialihkan ke node lain yang tersedia.
2. **Migrasi Terencana (Planned Migration)**\
   Transisi yang telah direncanakan sebelumnya, di mana operator node Arx secara sukarela mundur dari jaringan dan memastikan tugas-tugasnya dialihkan ke node pengganti tanpa penalti tambahan selain biaya migrasi standar, selama pemberitahuan yang memadai diberikan. Sebagai contoh, operator node Arx yang berencana keluar dari jaringan dapat memulai migrasi satu epoch sebelumnya, sehingga beban kerjanya dapat dialihkan ke node-node aktif lainnya.

### Biaya Migrasi

Dalam migrasi paksa, biaya akan dibagi secara proporsional di antara seluruh pemangku kepentingan dari node Arx yang bermigrasi yaitu node yang dikeluarkan dari Cluster asalnya. Namun, biaya ini umumnya relatif kecil dan tercermin sebagai pengurangan kecil pada reward yang didistribusikan. Meski demikian, karena migrasi paksa selalu merupakan akibat dari pelanggaran yang dapat dikenai slashing, dampak finansial sebenarnya jauh lebih besar. Operator node dan para pemangku kepentingannya juga akan menerima penalti tambahan akibat slashing, sehingga migrasi paksa menjadi jauh lebih mahal dibandingkan pengunduran diri yang direncanakan.

Sebaliknya, migrasi terencana mengharuskan node Arx yang bermigrasi menanggung biaya migrasi dari self-delegation miliknya. Hal ini memastikan bahwa biaya pengalokasian ulang tugas node ke node-node baru dalam jaringan dapat ditanggung dengan baik, sehingga mencegah potensi gangguan layanan. Cluster baru akan dibentuk berdasarkan konfigurasi yang ada, dengan memprioritaskan node-node yang tersedia dari  Cluster asal atau dari [**Daftar Prioritas Node dengan menggunakan mekanisme seleksi alternatif.**](daftar-prioritas-node-and-kriteria-seleksi-alternatif.md#daftar-prioritas-node-node-priority-list)
