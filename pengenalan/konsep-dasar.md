# Konsep Dasar

Pada halaman ini, kami memberikan gambaran umum mengenai konsep-konsep inti dalam Arcium, termasuk:

1. **MPC eXecution Environments (MXEs):** Lingkungan virtual terenkripsi untuk mengeksekusi komputasi terenkripsi, yang memungkinkan developer menyesuaikan protokol, asumsi kepercayaan, perangkat keras, dan lainnya.
2. **arxOS:** Sistem operasi terenkripsi dan terdistribusi yang menjadi fondasi Arcium, memudahkan siapa pun untuk menjalankan komputasi terenkripsi. arxOS bergantung pada konsep inti Arcium lainnya yang dijelaskan di bawah, termasuk **Arx Nodes** dan **Klaster**.
3. **Arcis:** Framework pemrograman intuitif milik Arcium untuk membangun aplikasi apa pun agar bersifat privat dan terenkripsi.

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

### Memahami Superkomputer Terenkripsi

Untuk merangkum kapabilitas dan fungsi Arcium, jaringan ini digambarkan sebagai sebuah **“superkomputer terenkripsi.”** Mirip dengan arsitektur komputasi tradisional, setiap node bertindak sebagai satu prosesor yang berkontribusi pada satu superkomputer terenkripsi. Melalui penggabungan dan penyatuan seluruh prosesor inilah superkomputer tersebut terwujud dengan fitur-fitur uniknya&#x20;

arxOS adalah sistem operasi terenkripsi dan terdistribusi (jaringan Node Arcium) yang bertanggung jawab menjalankan komputasi.\
[MXEs](../multi-party-execution-environments-mxes/gambaran-umum.md) (MPC eXecution Environments) berperan sebagai mesin virtual superkomputer, lingkungan yang sangat fleksibel tempat komputasi didefinisikan dan dieksekusi secara aman.\
Sementara itu, **Arcis** adalah framework developer berbasis Rust milik Arcium.

### Arcium dan Arx Nodes

Arcium Network terdiri dari **Arx Nodes** yang terdesentralisasi dan bertugas melakukan komputasi atas data terenkripsi. Nama _Arx_ berasal dari bahasa Latin yang berarti “benteng,” mencerminkan bahwa setiap Arx Node adalah titik aman dalam jaringan. Namun, kekuatan sebenarnya dari Arx Nodes terletak pada kolaborasi mereka di dalam jaringan terdesentralisasi.

* **Staking dan Slashing:**\
  Untuk menjaga integritas jaringan, Arx Nodes diwajibkan melakukan staking sebagai jaminan. Perilaku tidak jujur atau penyimpangan dari protokol akan dikenai penalti, seperti slashing terhadap token yang di-stake. Mekanisme ini mendorong node untuk beroperasi secara jujur dan menjaga keamanan jaringan.

### Multi-Party Computation (MPC)

Multi-Party Computation (MPC) adalah fondasi kriptografi dari Arcium. MPC memungkinkan banyak pihak untuk menghitung suatu fungsi secara bersama-sama sambil tetap menjaga kerahasiaan input masing-masing pihak, sehingga privasi data terjaga sepanjang proses.

* **Secret Sharing** adalah metode kriptografi utama dalam MPC, yang digunakan untuk membagi data menjadi beberapa fragmen dan mendistribusikannya ke berbagai Arx Node. Tidak ada satu node pun yang memiliki akses ke keseluruhan data.
* **Threshold Encryption** memastikan bahwa proses dekripsi hanya dapat dilakukan jika sejumlah minimum pihak yang berwenang bekerja sama. Di Arcium, metode ini menjaga data sensitif tetap terlindungi dengan mensyaratkan ambang batas jumlah node tertentu untuk melakukan dekripsi selama komputasi. Hal ini meningkatkan keamanan dalam komputasi kolaboratif.

### Eksekusi Trustless

Di dalam Arcium Network, komputasi dijalankan secara **trustless**, artinya tidak diperlukan otoritas terpusat untuk memverifikasi integritas pemrosesan data. Sebagai gantinya, mekanisme kriptografi seperti MPC menjamin bahwa komputasi dilakukan dengan benar. Node diwajibkan melakukan staking untuk dapat berpartisipasi, dan setiap penyimpangan dari protokol akan dikenai penalti (misalnya slashing). Sistem trustless ini memastikan data tetap rahasia dan hasil komputasi akurat.

### Cluster dan MXEs (MPC eXecution Environments)

**Cluster** dalam Arcium Network adalah kumpulan Arx Nodes yang bekerja sama untuk mengeksekusi tugas MPC. Setiap komputasi dikelola di dalam sebuah **MPC eXecution Environment (MXEs)**, yang menentukan parameter tugas, termasuk pengelolaan data, protokol keamanan, serta Cluster yang ditunjuk untuk memprosesnya.

Umumnya, satu Klaster dapat mendukung beberapa MXEs secara bersamaan, sehingga penggunaan sumber daya dan distribusi beban kerja menjadi lebih efisien. Selain itu, MXEs dapat dikonfigurasi untuk menggunakan beberapa Klaster, memungkinkan perpindahan secara mulus jika satu Kklaster sedang sibuk atau tidak tersedia sementara. Hal ini menjamin ketersediaan tinggi (high availability) dan fleksibilitas jaringan.

### Byzantine Fault Tolerance

Arcium Network dirancang dengan **Byzantine Fault Tolerance (BFT)**, yang memungkinkannya tetap berfungsi dengan benar meskipun terdapat node yang berperilaku jahat atau mengalami kegagalan. BFT memastikan jaringan tetap aman dan andal walaupun sebagian node bertindak tidak terduga, sehingga operasi dapat terus berjalan secara stabil dalam lingkungan terdesentralisasi.

### Epoch

Pengaturan waktu di Arcium Network dibagi ke dalam periode berdurasi tetap yang disebut **Epoch**. Epoch berfungsi sebagai kerangka kerja untuk penjadwalan komputasi, distribusi reward, serta pengelolaan penguncian token. Mekanisme waktu yang konsisten ini memastikan eksekusi tugas yang efisien dan adil di seluruh jaringan.

<br>
