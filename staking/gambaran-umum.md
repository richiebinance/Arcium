# Gambaran Umum

Staking merupakan komponen penting dalam Jaringan Arcium yang berfungsi untuk mengaktifkan Node Arx dan membuka akses terhadap sumber daya komputasinya. Tanpa jumlah stake yang memadai, node tidak memenuhi syarat untuk menjalankan pekerjaan, sehingga memastikan bahwa sumber daya komputasi dialokasikan secara aman kepada node yang tepercaya dan andal.

#### **Persyaratan Operasional dan Klaim Perangkat Keras Node**

Untuk mengaktifkan sebuah Node Arx, Operator Node harus memenuhi konstanta jaringan yang disebut **MINIMUM\_SELF\_DELEGATION\_PER\_1000\_CLUSTERS**, yang merepresentasikan jumlah minimum self-stake yang dibutuhkan agar node dapat bergabung hingga 1.000 klaster.

Selain itu, pada saat aktivasi, Operator Node juga membuat klaim terkait kapasitas beban komputasi maksimum yang dapat ditangani oleh node mereka, yang disebut sebagai **Node Hardware Claim**. Klaim ini harus didukung oleh jumlah stake terdelegasi yang sesuai agar perangkat keras node tersebut memenuhi syarat untuk digunakan dalam jaringan.

#### **Aktivasi Klaim Perangkat Keras Node**

Untuk mengukur dan menghitung aktivasi stake pada perangkat keras Node Arx, terdapat rasio konstan di seluruh jaringan yang menentukan jumlah stake (baik dari pihak ketiga maupun self-stake) yang diperlukan untuk membuktikan suatu klaim perangkat keras tertentu.

Rasio ini disebut **`REQUIRED_STAKE_PER_UNIT_OF_CU_LOAD_CAPACITY`**.

Rasio ini mengaitkan jumlah stake dengan spesifikasi perangkat keras node yang diklaim sendiri oleh operator.

Apabila total delegasi pada suatu node **tidak memenuhi** persyaratan ini, node tersebut hanya akan menerima penugasan komputasi secara proporsional dengan jumlah stake aktualnya, bukan berdasarkan kapasitas maksimum yang diklaim.

Sebaliknya, jika jumlah delegasi **melebihi** stake yang dibutuhkan, Operator Node wajib meningkatkan perangkat kerasnya untuk menjustifikasi kelebihan stake tersebut. Jika tidak, imbalan atas delegasi berlebih akan mengalami pengurangan secara sub-linear, guna mencegah over-delegation yang melampaui kemampuan perangkat keras node.

Pendekatan staking dalam Jaringan Arcium dirancang untuk mencegah sentralisasi dengan menciptakan hubungan yang hampir linear antara perangkat keras yang disediakan oleh Node Arx kepada jaringan dan jumlah stake yang diperlukan untuk mengaktifkannya.

#### **Alur Delegasi dan Imbalan**

Setelah diaktifkan, Node Arx dapat menerima delegasi stake tambahan, baik dari Operator Node maupun Delegator Pihak Ketiga. Setiap delegasi stake akan membuka kapasitas komputasi tambahan, sehingga node dapat menangani beban kerja yang lebih besar, hingga batas yang sesuai dengan Klaim Perangkat Keras.

#### **Mekanisme Delegasi**

Stake akan menjadi aktif pada awal epoch berikutnya setelah didelegasikan. Setelah aktif, node akan menerima bagian imbalan yang sama dari komputasi yang dieksekusi dalam klaster tempat node tersebut menjadi anggota. Sementara itu, Delegator akan memperoleh bagian imbalan secara proporsional dari imbalan yang diterima node yang menjadi tujuan delegasi, setelah dikurangi biaya persentase sebagai kompensasi bagi Operator Node atas pengoperasian infrastruktur.

Imbalan Delegator akan terakumulasi secara otomatis (auto-compounding), namun Delegator tetap dapat melakukan undelegasi kapan saja, yang akan membuka kembali stake tersebut pada awal epoch berikutnya.

#### **Imbalan Berbasis Epoch**

Imbalan dialokasikan pada akhir setiap epoch. Apabila Delegator memilih untuk menarik stake mereka atau memindahkan delegasi ke node lain (proses yang dikenal sebagai **redelegation**), maka akan berlaku periode cooldown selama satu epoch. Dalam periode ini, stake tetap terkunci sebelum dialokasikan ulang atau ditarik. Untuk detail lebih lanjut mengenai struktur biaya komputasi, silakan merujuk ke [Harga dan Insentif](../komputasi/harga-dan-insentif.md).

#### **Contoh Alur Kerja**

Untuk menggambarkan bagaimana proses delegasi berlangsung:

1. Operator Node melakukan self-delegation sebesar jumlah minimum yang disyaratkan untuk mengaktifkan Node Arx.
2. Delegator Pihak Ketiga menambahkan stake guna meningkatkan kapasitas komputasi node.
3. Setelah aktif, node mengeksekusi komputasi, dan imbalan yang diperoleh akan didistribusikan kepada para Delegator berdasarkan proporsi stake yang mereka delegasikan, setelah dikurangi biaya yang dikumpulkan oleh Operator Node.
4. Delegator dapat menarik imbalan mereka pada akhir epoch atau membiarkannya terakumulasi secara otomatis untuk imbalan di masa mendatang.

**Poin-Poin Utama:**

* Node dengan jumlah stake yang tidak mencukupi tidak memenuhi syarat untuk memproses komputasi.
* Delegasi yang melebihi proporsi stake terhadap klaim perangkat keras node tidak akan meningkatkan kapasitas, kecuali kapasitas komputasi (dan klaimnya) ditingkatkan.
* Hubungan stake terhadap kapasitas yang hampir linear mencegah over-delegation dan mendorong desentralisasi.
