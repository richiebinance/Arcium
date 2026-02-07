# Pemangku Kepentingan Jaringan

Arcium Network terdiri dari tiga pemangku kepentingan jaringan yang berinteraksi secara ekonomi dengan jaringan, baik untuk **menggunakan** maupun **menyediakan** layanan.

Mereka meliputi:

* **Pelanggan Komputasi**: Pihak yang membeli layanan komputasi rahasia dengan membuat environment komputasi ([**MXEs**](../multi-party-execution-environments-mxes/gambaran-umum.md)) dan membayar biaya untuk menjalankan komputasi yang aman dan privat.
* **Arx Operators**: Pihak yang menyediakan sumber daya komputasi ke jaringan dengan menjalankan Arx Nodes, serta memperoleh reward dari penyelesaian tugas terenkripsi.
* **Pihak Ketiga yang Menunjuk**: Pihak yang mendelegasikan stake mereka ke [**Arx Node**](../arx-nodes/gambaran-umum.md), berbagi reward dari komputasi yang dijalankan node tersebut, sekaligus menanggung risiko yang terkait.

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

### **Pelanggan Komputasi**

Sebagai pihak **buy-side**, **Computation Customers** membeli layanan komputasi rahasia dari Arcium Network. Untuk mengakses layanan ini, mereka mengikuti langkah-langkah berikut:

* **Membuat Computation Environment (MXE)**\
  Menentukan objek data persisten yang berfungsi sebagai penyimpanan data untuk komputasi di dalam MXEs, serta memilih Klaster yang akan menjalankan environment tersebut. Karena Arcium bersifat stateless, pengelolaan persistensi data dilakukan oleh pelanggan secara eksternal.
* **Mengonfigurasi Detail Komputasi**\
  Menentukan kode Arcis dan tugas komputasi yang akan dijalankan, termasuk input data persisten maupun sekali pakai, serta memecah pekerjaan besar menjadi tugas-tugas kecil yang lebih mudah dikelola bila diperlukan.
* **Memesan Eksekusi Komputasi**\
  Membayar biaya dasar yang ditentukan jaringan, ditambah biaya prioritas (priority fee) untuk mendahulukan komputasi yang bersifat mendesak. Pada tahap awal, biaya prioritas ini mungkin bersifat opsional; namun seiring meningkatnya volume aktivitas di Arcium Network, penetapan priority fee yang kompetitif akan menjadi penting agar komputasi dapat diproses dalam waktu yang wajar.

**Contoh**:\
Seorang pelanggan dapat memesan komputasi berkelanjutan untuk algoritma trading DeFi, dengan memastikan operasi besar dan berkesinambungan dipecah menjadi tugas-tugas berurutan yang lebih kecil. Setiap komputasi diproses secara aman menggunakan infrastruktur Arcium.

### Operator ARX

**Operator ARX** menyediakan sumber daya komputasi bagi Arcium Network dengan menjalankan **Arx MPC Nodes** pada infrastruktur perangkat keras mereka. Mereka mendapatkan kompensasi berdasarkan komputasi yang berhasil diselesaikan, serta memiliki tanggung jawab utama berikut:

* **Deklarasi Sumber Daya**\
  Operator menyatakan kapasitas komputasi yang disediakan oleh node mereka, yang menentukan jumlah collateral yang harus di-stake agar node dapat berpartisipasi dalam jaringan.
* **Reputasi**\
  Operator dipilih oleh Pelanggan Komputasi melalui Klaster, berdasarkan reputasi yang dipengaruhi oleh riwayat slashing, performa komputasi, dan tingkat keandalan.
* **Kapabilitas TEE**\
  Operator dapat memilih untuk melengkapi Arx Node mereka dengan **Trusted Execution Environment (TEE)** untuk menangani tugas yang membutuhkan tingkat keamanan tambahan.

#### Sumber Pendapatan

1. **Reward dari self-delegation**\
   Operator Arx melakukan staking menggunakan collateral milik mereka sendiri untuk mengaktifkan perangkat keras, biasanya melebihi batas minimum yang diwajibkan. Batas minimum ini berfungsi sebagai mekanisme pengaman untuk biaya migrasi Klaster jika node tiba-tiba offline. Reward diperoleh berdasarkan total self-stake.
2. **Biaya delegasi pihak ketiga**\
   Operator memperoleh fee dari third-party delegators yang melakukan staking ke node mereka. Collateral eksternal ini membuka kapasitas komputasi tambahan, sehingga node dapat menangani beban kerja yang lebih besar.

**Contoh**:\
Seorang Arx Operator dapat mengkhususkan diri pada node berperforma tinggi yang dioptimalkan untuk komputasi skala besar, sehingga diminati oleh pelanggan yang membutuhkan keamanan data tinggi dan pemrosesan efisien, misalnya untuk pelatihan model AI atau transaksi DeFi rahasia. Dengan menyediakan sumber daya komputasi yang andal dan skalabel, operator ini dapat menarik pelanggan dengan kebutuhan privasi dan performa yang tinggi.

### Third-Party Delegators

**Third-Party Delegators** menyumbangkan stake mereka ke sebuah Arx Node dengan imbalan bagian dari reward yang dihasilkan node tersebut dari penyelesaian komputasi. Delegator memiliki peran penting dalam jaringan dengan meningkatkan kapasitas komputasi node, namun juga menanggung **risiko collateral**.

Risiko ini muncul karena jika Arx Node tempat mereka mendelegasikan stake dikenai penalti akibat perilaku menyimpang (misalnya pelanggaran protokol), stake delegator juga akan terkena **slashing** secara proporsional.

Selain mendukung daya komputasi, **third-party delegators juga berfungsi sebagai indikator keandalan dan tingkat kepercayaan node**. Dengan melakukan due diligence sebelum memilih node, delegator membantu menyoroti node-node dengan reputasi baik, sehingga memudahkan pemangku kepentingan lain dalam mengidentifikasi node yang dianggap dapat diandalkan.

Delegator menerima bagian reward secara proporsional (pro-rata), setelah Arx Operator memotong fee berbasis persentase untuk pengelolaan infrastruktur fisik.

**Contoh**:\
Seorang delegator yang ingin memperoleh pendapatan pasif dari asetnya dapat mendelegasikan stake ke Arx Operator dengan reputasi baik dan riwayat node yang andal, sehingga dapat berbagi reward komputasi sambil menerima risiko slashing.

**Delegasi Opsional**:\
Arx Operator dapat memilih untuk menonaktifkan delegasi pihak ketiga, dan hanya mengandalkan stake milik mereka sendiri untuk menjalankan komputasi.
