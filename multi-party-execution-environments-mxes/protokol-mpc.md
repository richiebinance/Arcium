# Protokol MPC

### Protokol MPC

Protokol MPC berbeda-beda tergantung pada model keamanannya, asumsi kriptografi yang digunakan, serta tingkat efisiensinya. Dari sisi **model keamanan**, terdapat beberapa pendekatan berikut:

1. **Honest but Curious (Jujur tapi Penasaran):**\
   Semua partisipan mengikuti protokol dengan benar, namun berusaha memperoleh sebanyak mungkin informasi dari data yang dipertukarkan.
2. **Honest Majority (Mayoritas Jujur):**\
   Mengharuskan setidaknya N/2 partisipan bersikap jujur untuk menjamin privasi dan integritas data.
3. **Dishonest Majority (Mayoritas Tidak Jujur):**\
   Mampu bertahan meskipun hingga N−1 partisipan bertindak jahat, dan tetap menjamin privasi serta kebenaran hasil selama masih ada setidaknya satu partisipan yang jujur.

Protokol MPC juga dapat diklasifikasikan berdasarkan **asumsi kriptografi** yang digunakan:

* **Keamanan Komputasional:**\
  Bergantung pada sulitnya masalah matematika tertentu (misalnya faktorisasi bilangan besar). Sistem ini umumnya aman saat ini, tetapi berpotensi rentan di masa depan, terutama dengan hadirnya komputasi kuantum.
* **Keamanan Teoretis Informasi:**\
  Menjamin keamanan berdasarkan prinsip teori informasi tanpa bergantung pada kesulitan komputasi (misalnya _Additive Secret Sharing_). Pendekatan ini lebih kuat secara teoritis, namun biasanya kurang efisien.

Protokol MPC mutakhir, termasuk yang digunakan di Arcium Network, umumnya menerapkan **model preprocessing**, di mana operasi kriptografi paling mahal dilakukan terlebih dahulu pada fase _offline_. Fase _online_ kemudian mengeksekusi komputasi aktual secara efisien dengan memanfaatkan nilai yang telah dipraproses.

Kedua pendekatan ini bergantung pada **secret sharing**, yaitu memecah sebuah nilai menjadi beberapa bagian (share) dan membagikannya ke setiap partisipan. Properti dari share ini memungkinkan penjumlahan dua nilai atau perkalian dengan konstanta dilakukan secara lokal oleh masing-masing peer. Namun, perkalian antar share memerlukan komunikasi antar peer.

Untuk memverifikasi keabsahan nilai yang dikirim dari satu peer ke peer lainnya, skema ini menggunakan **MAC (Message-Associated Codes)** yang tidak dapat dipalsukan oleh peer. MAC ini memastikan tidak terjadi kecurangan; jika pemalsuan terdeteksi, peer dapat secara sepihak menghentikan protokol.

1. **Protokol berbasis Oblivious Transfer (OT):**\
   OT adalah primitif kriptografi yang memungkinkan pengirim mengirim dua pesan (A dan B) kepada penerima, di mana penerima hanya dapat mengetahui salah satu pesan tanpa memberi tahu pengirim pesan mana yang dipilih. Protokol ini relatif efisien secara komputasi, tetapi membutuhkan overhead komunikasi yang besar. Namun, kemajuan terbaru seperti _silent OT_ membuat pendekatan ini jauh lebih kompetitif.
2. **Metode berbasis Fully Homomorphic Encryption (FHE) dan Zero-Knowledge Proof (ZKP):**\
   Protokol ini menggabungkan FHE dan ZKP untuk mengirim pesan antar peer dalam bentuk terenkripsi dan melakukan komputasi di atasnya guna menghasilkan nilai preprocessing yang valid. ZKP digunakan untuk memverifikasi kebenaran ciphertext FHE, sehingga peer tidak dapat menyimpang secara jahat tanpa terdeteksi. Pendekatan ini efisien dari sisi komunikasi, namun komputasi FHE masih tergolong berat meskipun telah banyak kemajuan.

### MPC vs Teknik Enkripsi Lainnya

Komputasi terenkripsi sangat penting untuk menghadirkan privasi dalam berbagai ekosistem digital, termasuk aplikasi yang terintegrasi dengan blockchain.

Meskipun terdapat berbagai solusi, tidak semuanya cocok untuk kebutuhan aplikasi terdesentralisasi maupun hybrid onchain/offchain.

Berikut perbandingan beberapa teknik utama:

#### **Fully Homomorphic Encryption (FHE)**

FHE memungkinkan komputasi dilakukan langsung pada data terenkripsi tanpa perlu dekripsi, sehingga privasi data tetap terjaga sepanjang proses. Meskipun sering dianggap sebagai metode enkripsi masa depan, FHE memiliki biaya komputasi yang sangat tinggi. Saat ini, throughput transaksinya masih terbatas (sekitar 5 TPS), sehingga sulit diterapkan secara praktis dalam skala blockchain besar. Selain itu, proses dekripsi tertentu berpotensi menjadi titik lemah jika tidak dikelola dengan aman.

#### **Trusted Execution Environments (TEEs)**

TEE memungkinkan komputasi privat dengan menjalankan proses di area hardware yang terisolasi dan aman. Teknologi ini sudah digunakan di lingkungan produksi dan menawarkan performa tinggi. Namun, TEE rentan terhadap _side-channel attacks_, di mana penyerang mengekstrak informasi rahasia melalui perilaku hardware. Ketergantungan pada penyedia hardware tepercaya juga menjadi risiko tersendiri, karena kompromi pada hardware dapat berdampak pada seluruh sistem. Sebaliknya, solusi kriptografi seperti MPC tidak memerlukan kepercayaan pada hardware tertentu.

#### **Zero-Knowledge Proofs (ZKPs)**

ZKP memungkinkan satu pihak membuktikan kebenaran suatu pernyataan tanpa mengungkap data dasarnya. Ini sangat efektif untuk memverifikasi komputasi offchain. Namun, ZKP kurang cocok untuk sistem _shared state_ seperti blockchain, di mana banyak pihak perlu berinteraksi secara bersamaan dengan data terenkripsi yang sama. ZKP lebih tepat digunakan untuk kasus khusus seperti _selective disclosure_.

#### **Secure Multi-Party Computation (MPC): Solusi Optimal**

MPC muncul sebagai metode paling fleksibel dan skalabel untuk menjaga kerahasiaan dalam sistem terdesentralisasi. MPC memungkinkan banyak pihak menghitung sebuah fungsi secara kolaboratif tanpa mengungkap data masing-masing pihak.

Dibandingkan FHE, MPC lebih cepat dan lebih hemat biaya, sehingga cocok untuk aplikasi real-time. TEEs memang menawarkan eksekusi lebih cepat, tetapi bergantung pada hardware tepercaya dan tidak sepenuhnya _trustless_. MPC juga memberikan jaminan keamanan yang kuat: hasil komputasi tetap benar meskipun sebagian partisipan bertindak jahat.

Keunggulan utama MPC:

* **Keamanan Tinggi:** Mendukung eksekusi terdesentralisasi tanpa kepercayaan pada hardware atau perantara tertentu.
* **Fleksibilitas:** Cocok untuk berbagai use case Web3, mulai dari AI hingga DeFi.
* **Efisiensi Biaya dan Kecepatan:** Lebih unggul dibanding teknik lain seperti FHE. Dengan inovasi dari platform seperti Arcium, MPC kini dapat diterapkan dalam skala besar untuk membuka berbagai aplikasi onchain bernilai tinggi.

<figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption><p>MPC bekerja dengan cara berbagai pihak menambahkan angka rahasia ke informasi mereka, meneruskannya, melakukan perhitungan akhir, dan kemudian menghapus jumlah angka rahasia tersebut. Untuk gambaran sederhana, baca posting blog kami di sini: https://www.arcium.com/articles/eli5-mpc</p></figcaption></figure>

### MPC di Arcium

Tim engineer Arcium sedang mengembangkan dua backend MPC yang diberi nama **Cerberus** dan **Manticore**. Keduanya memiliki trade-off yang berbeda dan memungkinkan cakupan aplikasi yang lebih luas.

* **Cerberus** adalah backend utama untuk komputasi MPC. Setiap share diautentikasi menggunakan MAC, sehingga node yang jujur dapat mendeteksi perilaku jahat dan menghentikan komputasi. Dengan asumsi setidaknya ada satu node yang jujur, hasil komputasi dijamin benar. Cerberus memberikan jaminan keamanan paling kuat.
* **Manticore** beroperasi dalam model _honest but curious_. Backend ini bergantung pada **Trusted Dealer**, yaitu node yang menghasilkan data preprocessing untuk fase online lalu keluar dari sistem. Pendekatan ini menghasilkan waktu eksekusi yang lebih cepat dan memungkinkan operasi kompleks seperti machine learning dan AI. Namun, jaminan keamanannya lebih lemah dibanding Cerberus. Manticore ditujukan untuk lingkungan dengan operator node yang dipercaya dan memiliki insentif untuk bersikap jujur.

**Contoh penggunaan:**\
Pelatihan model machine learning dapat dilakukan menggunakan Manticore karena kebutuhan komputasinya yang tinggi. Setelah model terlatih, Cerberus dapat digunakan untuk melakukan prediksi dengan tingkat keamanan yang lebih kuat.
