# Integrasi Solana: Orkestrasi dan Eksekusi

Jaringan Arcium memanfaatkan Solana untuk mengorkestrasi dan mengelola alur kerja komputasi secara efisien. Throughput tinggi dan latensi rendah milik Solana memungkinkan proses inti Arcium—seperti orkestrasi komputasi, manajemen node, dan sistem pembayaran berjalan secara mulus di onchain.

#### Koordinasi Onchain

Jaringan Arcium menggunakan program berbasis Solana untuk mengoordinasikan proses-proses utama berikut:

* **Manajemen Node**: Registrasi, konfigurasi, dan penjadwalan node Arx guna memastikan kesiapan mereka dalam memproses tugas secara aman.
* **Orkestrasi Komputasi**: Mengumpulkan komputasi ke dalam mempool, menetapkan tugas ke klaster node Arx, serta memproses hasil eksekusi.
* **Ekonomi Jaringan**: Mengelola pembayaran, imbalan, staking, dan mekanisme slashing untuk memastikan keandalan node Arx sekaligus memberikan insentif terhadap keamanan jaringan.

Node Arx berperan sebagai pekerja komputasi terdesentralisasi offchain, sementara Solana berfungsi sebagai pusat utama untuk antrean, penugasan, dan validasi tugas. Komputasi dimasukkan ke dalam **mempool onchain** dan dieksekusi oleh klaster node Arx yang telah ditentukan, dengan hasil yang tersedia bagi penerima yang berhak.

#### Arsitektur Mempool

Untuk mengelola komputasi secara efisien, **Arcium menggunakan satu mempool tunggal**, tempat seluruh **komputasi yang telah dikomisikan** diantrikan dan diprioritaskan untuk dieksekusi. Meskipun hanya terdapat satu mempool global, pasar biaya prioritas beroperasi di dalam [pasar spesifik klaster atau gabungan klaster](../komputasi/harga-dan-insentif.md), sehingga setiap komputasi hanya bersaing memperebutkan sumber daya dengan komputasi lain yang menggunakan node yang sama.

Setelah sebuah komputasi masuk ke dalam mempool:

* Komputasi akan menunggu eksekusi oleh node Arx yang memenuhi syarat, dengan prioritas berdasarkan biaya prioritas dan kondisi jaringan.
* Jendela validitas (stempel waktu “valid setelah” dan “valid sebelum”) menentukan kelayakan eksekusi.
* Tugas ditetapkan secara dinamis ke klaster node yang tersedia untuk memastikan distribusi beban kerja yang efisien.

Model eksekusi berbasis prioritas ini memastikan seluruh komputasi diproses secara adil, tanpa bergantung pada dependensi atau pemrosesan multi-tahap.

#### Eksekusi Alur Kerja yang Mulus

Setelah diantrikan, komputasi akan melalui tahapan berikut:

1. **Dikumpulkan** di dalam mempool.
2. **Ditugaskan** ke klaster node Arx untuk dieksekusi.
3. **Divalidasi**, dengan keluaran yang diproses secara aman dan disediakan bagi penerima yang sesuai.

Melalui proses yang terintegrasi ini, Arcium memastikan koordinasi tugas yang presisi, optimalisasi sumber daya, serta toleransi terhadap kegagalan, bahkan pada kondisi beban komputasi yang tinggi.
