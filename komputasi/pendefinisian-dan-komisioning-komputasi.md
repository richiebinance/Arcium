# Pendefinisian dan Komisioning Komputasi

Di Jaringan Arcium, untuk menjalankan komputasi, komputasi tersebut harus terlebih dahulu didefinisikan sebagai **Definisi Komputasi**, yang menyediakan kerangka kerja terstruktur untuk pelaksanaannya. Definisi Komputasi berfungsi sebagai cetak biru yang memastikan seluruh parameter, otoritas, dan logika ditentukan secara jelas sebelum komputasi diinstansiasi. Proses ini menjamin fleksibilitas, skalabilitas, serta eksekusi yang aman.

Setiap Definisi Komputasi terasosiasi dengan sebuah [**MXE**](../multi-party-execution-environments-mxes/gambaran-umum.md) (_MPC eXecution Environment_) dan terdiri atas komponen-komponen utama berikut:

1. **Spesifikasi Keluaran**: Setiap Definisi Komputasi memuat rincian mengenai keluaran yang diharapkan. Spesifikasi ini mendefinisikan struktur dan format data yang dihasilkan dari komputasi. Sejumlah data yang terbatas dapat dikembalikan melalui transaksi finalisasi _on-chain_ (karena keterbatasan bawaan ukuran transaksi Solana), namun data hasil tambahan dapat dikonfigurasikan untuk dikembalikan melalui permintaan _callback_ yang telah ditentukan sebelumnya.
2. **Pemberian Versi dan Peningkatan**: Setiap definisi mencakup bidang versi yang melacak pembaruan atau perubahan. Hal ini memastikan kompatibilitas ke belakang serta menjamin bahwa komputasi yang diinstansiasi dijalankan pada versi definisi yang benar. Mekanisme versi memungkinkan pengembang melakukan perbaikan tanpa mengganggu operasi yang sudah berjalan.
3. **Logika Eksekusi**: Logika komputasi didefinisikan sebagai sebuah **sirkuit** menggunakan [**kerangka kerja pengembang Arcis**](https://docs.arcium.com/developers/arcis), yang mengompilasi fungsi-fungsi yang ditandai dengan `#[instruction]` menjadi sirkuit-sirkuit individual.
4. **Otoritas Akses**: Definisi Komputasi menetapkan pihak-pihak yang berwenang untuk mengeksekusinya. Opsi otoritas meliputi:
   * **Tidak ada**: Tidak ada entitas yang diizinkan untuk mengeksekusi definisi ini.
   * **Privat**: Satu entitas tertentu memiliki hak eksekusi eksklusif.
   * **Terbatas**: Daftar entitas yang ditentukan memiliki hak eksekusi.
   * **Publik**: Setiap entitas di dalam jaringan dapat mengeksekusi komputasi tersebut.
5. **Parameter**: Setiap Definisi Komputasi dapat mencakup parameter yang menentukan masukan yang diperlukan saat eksekusi. Parameter ini terbagi ke dalam dua kategori:
   * **Teks biasa (plaintext)**: Masukan mentah yang tidak dienkripsi dan diberikan pada saat komisioning komputasi.
   * **Teks sandi (ciphertext)**: Masukan yang dienkripsi dengan sandi simetris dan disertakan pada saat komisioning komputasi.
6. **Biaya Eksekusi**: Metadata sirkuit merinci jumlah operasi aritmetika, masukan, dan keluaran yang diperlukan untuk eksekusi. Metadata ini memungkinkan perhitungan biaya yang presisi sehingga kebutuhan sumber daya dapat diketahui sejak awal.

### Pengomisionan Komputasi

Setelah sebuah Definisi Komputasi dibuat, langkah selanjutnya adalah mengomisionkannya untuk dieksekusi. Proses pengomisionan melibatkan persiapan komputasi agar dapat dijalankan di Jaringan Arcium, dengan menetapkan seluruh detail yang diperlukan.

Langkah-langkah utama dalam pengomisionan meliputi:

1. **Argumen**: Masukan untuk komputasi, yang sesuai dengan parameter yang telah didefinisikan sebelumnya, disertakan pada tahap ini.
2. **Waktu Eksekusi**: Pelanggan menentukan kapan komputasi harus dijalankan, termasuk opsi jendela validitas dengan penanda waktu (`valid after` dan `valid before`) untuk mendefinisikan rentang waktu eksekusinya.
3. **Biaya Prioritas**: Pelanggan menetapkan biaya prioritas untuk mendorong eksekusi yang lebih cepat, karena biaya yang lebih tinggi akan diprioritaskan di dalam _mempool_ jaringan.
4. **Callback**: Tindakan khusus yang dipicu setelah eksekusi didefinisikan sebagai:
   * **Instruksi Keberhasilan**: Tindakan _on-chain_ statis atau dinamis berdasarkan eksekusi yang berhasil, seperti menyimpan keluaran atau memicu komputasi lanjutan.
   * **Instruksi Kegagalan**: Tindakan _on-chain_ statis yang dijalankan apabila terjadi kegagalan.
5. **Penanganan Mempool**: Setelah sebuah komputasi dikomisionkan, komputasi tersebut akan ditempatkan di dalam _mempool_.

###
