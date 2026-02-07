# Gambaran Umum Arsitektur

Arcium Network dirancang untuk komputasi rahasia (confidential computing) yang aman dan terdistribusi, mencakup berbagai jenis aplikasi mulai dari AI hingga keuangan terdesentralisasi (DeFi) dan seterusnya. Jaringan ini dibangun di atas teknik kriptografi tingkat lanjut, termasuk Multi-Party Computation (MPC), untuk memungkinkan komputasi yang trustless dan dapat diverifikasi tanpa memerlukan otoritas terpusat.

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

#### 1. MPC eXecution Environments (MXEs)

[**MXEs** ](../multi-party-execution-environments-mxes/gambaran-umum.md)adalah lingkungan khusus yang terkompartemenisasi, tempat komputasi didefinisikan dan dieksekusi secara aman. MXEs memungkinkan pemrosesan paralel (karena Klaster dapat melakukan komputasi secara bersamaan untuk berbagai MXEs), sehingga meningkatkan throughput dan keamanan.

MXEs bersifat sangat fleksibel dan dapat dikonfigurasi, memungkinkan **Pelanggan Komputasi** menentukan kebutuhan keamanan, skema enkripsi, serta parameter performa mereka sendiri. Meskipun setiap komputasi dijalankan di dalam Klaster Arx Nodes tertentu, satu MXE dapat terhubung dengan beberapa Klaster.

Pendekatan ini memastikan komputasi tetap dapat dieksekusi secara andal, bahkan jika beberapa Node dalam sebuah Klaster sedang offline atau mengalami beban tinggi. Dengan konfigurasi yang ditentukan di awal, pengguna dapat menyesuaikan lingkungan sesuai kebutuhan use case mereka dengan tingkat fleksibilitas yang tinggi.

#### 2. arxOS

**arxOS** adalah sistem operasi terenkripsi dan terdistribusi yang menjadi tulang punggung Arx Nodes dan Klaster, serta bertanggung jawab untuk mengoordinasikan dan mengeksekusi komputasi di dalam Arcium Network. Setiap node (seperti core pada sebuah komputer) menyumbangkan sumber daya komputasi untuk menjalankan komputasi yang didefinisikan oleh MXEs.

#### 3. Arcis (Framework Developer Arcium)

**Arcis** adalah framework developer berbasis Rust yang memungkinkan developer membangun di atas infrastruktur Arcium, dengan dukungan penuh terhadap seluruh protokol MPC milik Arcium. Arcis terdiri dari framework dan compiler berbasis Rust.

#### 4. Klaster Arx Nodes (menjalankan arxOS)

[**Klaster**](../klaster/gambaran-umum.md) menyediakan model kepercayaan (trust model) yang dapat dikustomisasi, mendukung protokol **dishonest majority** (awalannya [Cerberus](../multi-party-execution-environments-mxes/protokol-mpc.md)) serta protokol **“honest but curious”** (lihat [Manticore](../multi-party-execution-environments-mxes/protokol-mpc.md)). Protokol lainnya, termasuk **honest majority**, akan ditambahkan di masa depan untuk mendukung lebih banyak skenario use case.

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

### Penegakan di Level Blockchain (Chain-Level Enforcement)

Seluruh manajemen state dan orkestrasi komputasi dijalankan **secara onchain melalui Solana**, yang berfungsi sebagai lapisan konsensus untuk mengoordinasikan aksi para Arx Node. Hal ini memastikan distribusi reward yang adil, penegakan aturan jaringan, serta keselarasan antar Node terhadap state jaringan terkini.

Tugas-tugas komputasi diantrikan dalam arsitektur mempool terdesentralisasi, di mana komponen onchain membantu menentukan prioritas komputasi, mengidentifikasi perilaku menyimpang, dan mengatur urutan eksekusi. Penjelasan lebih lanjut mengenai arsitektur onchain dapat dibaca [di sini](../integrasi-solana-dan-koordinasi-multi-rantai/integrasi-solana-orkestrasi-dan-eksekusi.md).

Untuk memastikan kepatuhan terhadap aturan jaringan, Node diwajibkan melakukan **staking** sebagai jaminan. Jika terjadi pelanggaran atau penyimpangan dari protokol, mekanisme **slashing** akan diterapkan sebagai penalti untuk menjaga integritas jaringan. Untuk detail lebih lanjut mengenai staking dan slashing, silakan lihat bagian [Gambaran Umum Staking](../staking/gambaran-umum.md).

###
