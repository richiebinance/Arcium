# Siklus Hidup Komputasi Arcium

**Siklus Hidup Komputasi** di Jaringan Arcium mengatur bagaimana sebuah komputasi bertransisi dari tahap pendefinisian hingga eksekusi dan penyelesaian. Proses yang terstruktur ini memastikan koordinasi yang mulus, optimalisasi sumber daya, serta penanganan linimasa eksekusi yang presisi.

### Ikhtisar Siklus Hidup

Siklus hidup sebuah komputasi di Jaringan Arcium mengikuti tahapan yang jelas dan berurutan. Tahapan ini memastikan komputasi didefinisikan secara aman, dikomisionkan secara efisien, dan dieksekusi dengan akurat.

Berikut lima tahap utamanya:

1. **Pendefinisian**: Komputasi didefinisikan dalam konteks sebuah MXE, yang berfungsi sebagai cetak biru untuk eksekusinya (lihat bagian [Pendefinisian dan Pengomisionan Komputasi](pendefinisian-dan-komisioning-komputasi.md) untuk detail). Tahap ini mencakup penetapan masukan, keluaran, logika, pemberian versi, serta izin akses.
2. **Pengomisionan**: Komputasi yang telah didefinisikan diinstansiasi dengan menetapkan argumen, jendela eksekusi, serta parameter lain yang diperlukan untuk pelaksanaan.
3. **Penempatan di Mempool**: Komputasi yang telah dikomisionkan dimasukkan ke dalam antrean mempool.
4. **Eksekusi**: Node-node mengeksekusi komputasi secara aman dengan memastikan privasi dan keakuratan.
5. **Callback Pascapengeksekusian**: Setelah eksekusi, tindakan yang telah ditentukan untuk kondisi keberhasilan maupun kegagalan dijalankan guna memastikan integrasi alur kerja yang mulus.

### **Jendela Validitas Eksekusi**

Setiap komputasi dapat menentukan **jendela eksekusi** opsional yang terdiri atas:

* **Stempel Waktu Valid After**: Waktu paling awal komputasi dapat dieksekusi.
* **Stempel Waktu Valid Before**: Waktu paling akhir komputasi dapat dieksekusi.

Stempel waktu ini memastikan komputasi diproses pada waktu yang tepat. Apabila stempel waktu _valid after_ berada di masa depan, komputasi akan tetap berada di dalam mempool hingga waktu tersebut tercapai. Sebaliknya, apabila stempel waktu _valid before_ berada di masa lalu, komputasi tersebut tidak lagi valid dan tidak dapat dieksekusi.

Secara bawaan:

* **Valid After**: Diatur ke nol (tanpa penundaan).
* **Valid Before**: Diatur ke tak hingga (tanpa kedaluwarsa).

Namun, pengaturan bawaan ini akan digantikan apabila stempel waktu eksplisit ditentukan pada saat pengomisionan.

### **Callback Pascapengeksekusian**

Setelah sebuah komputasi dieksekusi, sistem akan memicu _callback_ berdasarkan hasilnya:

* **Callback Keberhasilan**: Menangani tindakan untuk komputasi yang berhasil dieksekusi. Tindakan ini dapat mencakup:
  * **Tindakan On-Chain Dinamis**: Memicu proses _on-chain_ berdasarkan hasil komputasi.
  * **Tindakan On-Chain Statis**: Proses _on-chain_ tetap untuk menangani skenario keberhasilan.
* **Callback Kegagalan**: Mengelola tindakan ketika komputasi gagal. Callback ini selalu bersifat statis dan mencakup:
  * **Tindakan On-Chain Statis**: Proses _on-chain_ tetap untuk menangani skenario kegagalan.

Mekanisme _callback_ memastikan sistem tetap fleksibel dan responsif, bahkan ketika terjadi hasil yang tidak terduga.
