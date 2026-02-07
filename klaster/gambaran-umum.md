# Gambaran Umum

**Klaster** merujuk pada **kelompok Arx node yang berkolaborasi untuk mengeksekusi komputasi rahasia** di dalam Arcium Network.

Klaster dibuat oleh **Computation Customers** dengan menentukan sekumpulan Arx node berdasarkan persyaratan tertentu, seperti kapasitas komputasi, fitur keamanan, serta reputasi node-node tersebut.

Selama proses pembuatan, pelanggan menentukan beberapa atribut utama, antara lain:

* **Kapasitas Beban Komputasi (Computational Load Capacity):**\
  Volume komputasi maksimum yang harus ditangani oleh sebuah Klaster pada satu waktu. Karena setiap komputasi memiliki ukuran yang berbeda, satu komputasi besar dapat membutuhkan sumber daya yang jauh lebih besar dibandingkan beberapa komputasi kecil sekaligus.
* **Persyaratan Node Aktif (Active Node Requirements):**\
  Menentukan jumlah minimum node aktif yang harus tersedia di dalam Klaster untuk menjamin kapasitas komputasi yang konsisten. Ini mencakup **Node Priority List**, yang mengatur urutan aktivasi node. Sebagian besar properti Klaster seperti Node Priority List bersifat tidak dapat diubah setelah Klaster dibuat, namun batas kapasitas komputasi masih dapat ditingkatkan apabila didukung oleh seluruh node yang berpartisipasi.
* **Persyaratan Keamanan (Security Requirements):**\
  Menjabarkan standar dan protokol keamanan yang harus dipatuhi oleh Klaster.

Dan atribut lainnya.

Pelanggan juga dapat menggunakan kembali Klaster yang sudah ada dan sesuai dengan kebutuhan mereka, sehingga mengurangi biaya setup dan meningkatkan efisiensi penggunaan sumber daya. Sebagai contoh, sebuah proyek dapat memanfaatkan Klaster berkapasitas tinggi yang sudah ada untuk algoritma perdagangan privat, daripada membuat Klaster baru dari nol.

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

### **Partisipasi & Penerimaan MXE**

Setelah sebuah Klaster dibuat, Arx node di dalamnya harus menyetujui partisipasi mereka.

Proses persetujuan ini memungkinkan setiap node mempertimbangkan berbagai faktor, seperti beban kerja internal, tingkat kepercayaan terhadap node lain, serta yurisdiksi geografis. Klaster juga dapat dikonfigurasi untuk menyertakan node acak yang dipilih oleh mekanisme **sybil-resistance** jaringan, sehingga meningkatkan keamanan dengan mengurangi risiko kolusi atau kontrol terpusat.

**Selain persyaratan persetujuan node untuk bergabung dalam** Klaste&#x72;**, setiap Klaster juga harus menerima MXEs**, yaitu lingkungan yang berisi definisi komputasi. MXE berfungsi sebagai wadah eksekusi komputasi dan menentukan jenis tugas apa saja yang dapat diproses. Mekanisme penerimaan MXE ini sepenuhnya terpisah dari sistem undangan Klaster.

Proses penerimaan MXE dikelola melalui perilaku yang dapat dikonfigurasi:\
beberapa Klaster mungkin mengharuskan persetujuan bulat dari seluruh node untuk MXE baru, sementara Klaster lain menggunakan proses yang lebih sederhana dan otomatis. Jika satu Arx node saja menolak penerimaan MXE ke dalam Klaster mereka, maka MXE tersebut akan gagal diterima.

Fleksibilitas ini memastikan **Computation Customers** dapat dengan cepat menemukan Klaster yang sesuai dengan kebutuhan mereka, sambil tetap menyeimbangkan antara kecepatan dan keamanan.

### **Paralelisasi dan Skalabilitas**

Klaster dalam Arcium Network dirancang untuk mengoptimalkan efisiensi komputasi dengan mendistribusikan tugas ke berbagai node dan Klaster, sehingga memungkinkan performa tinggi dan skalabilitas.

Alih alih memparalelkan satu komputasi ke banyak node dalam satu Klaster, Arcium berfokus pada pemrosesan **berbagai komputasi secara bersamaan di seluruh jaringan**, demi memastikan keandalan dan ketersediaan tinggi. Untuk detail mengenai orkestrasi dan antrean komputasi, lihat dokumentasi[ Integrasi Solana: Orkestrasi dan Eksekusi](../integrasi-solana-dan-koordinasi-multi-rantai/integrasi-solana-orkestrasi-dan-eksekusi.md).
