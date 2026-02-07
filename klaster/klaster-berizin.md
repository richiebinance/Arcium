# Klaster Berizin

**Klaster Berizin** memungkinkan organisasi untuk mengontrol bagaimana tugas komputasi dijalankan melalui berbagai konfigurasi yang dapat disesuaikan. Dengan ini, organisasi dapat menerapkan pengaturan yang selaras dengan kebutuhan spesifik mereka terkait keamanan, kepatuhan, dan performa.

Terdapat tiga konfigurasi utama:

1. **Fully-Permissioned**\
   Dikonfigurasikan untuk organisasi yang sepenuhnya mengoperasikan infrastrukturnya sendiri, hanya menggunakan Arx node internal guna memastikan privasi dan kontrol data secara penuh.
2. **Partially-Permissioned**\
   Model hibrida yang menggabungkan node internal organisasi dengan sejumlah node eksternal terpilih untuk meningkatkan kapasitas komputasi, sambil tetap mempertahankan tingkat pengawasan tertentu.
3. **Public / Non-Permissioned**\
   Terbuka untuk seluruh node terverifikasi di Arcium Network, menyediakan pengaturan terdesentralisasi yang ideal untuk tugas-tugas yang tidak memerlukan kontrol node yang ketat.

Kategori-kategori ini menawarkan tingkat desentralisasi yang berbeda-beda, sehingga memungkinkan kolaborasi dalam komputasi bersama lintas struktur organisasi termasuk analisis data dan pelatihan model AI tanpa mengorbankan privasi dataset masing-masing pihak. Berbagai use case lain juga dimungkinkan, seperti riset kolaboratif antar kompetitor atau berbagi data rahasia antar divisi dalam satu perusahaan.

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

#### **Fully-Permissioned Klaster**

Organisasi atau institusi dapat memilih untuk menjalankan Klaster yang sepenuhnya dikendalikan, dengan hanya menggunakan Arx node yang mereka operasikan sendiri. Konfigurasi ini memberikan kontrol penuh atas infrastruktur, sehingga hanya node yang dipercaya yang dapat mengeksekusi tugas komputasi.

Model ini sangat cocok bagi perusahaan dengan persyaratan keamanan data yang ketat, kewajiban regulasi, atau yang menangani komputasi dengan sensitivitas tinggi. Sebagai contoh, institusi keuangan yang memproses data nasabah yang bersifat rahasia dapat menggunakan fully-permissioned Klaster untuk memastikan hanya Arx node internal yang sangat terpercaya yang memproses transaksi sensitif tersebut.

Selain itu, regulasi tertentu seperti [GDPR](https://gdpr-info.eu/) atau standar kepatuhan industri lainnya dapat mewajibkan kontrol ketat atas lokasi dan cara pemrosesan data, sehingga permissioned Klaster menjadi kebutuhan penting dalam skenario tersebut.

Meskipun bersifat terisolasi, fully-permissioned Klaster tetap dapat memanfaatkan mekanisme konsensus Arcium Network untuk fungsi-fungsi seperti penyelesaian sengketa, penentuan harga dasar (base pricing), dan pemrosesan data yang aman. Dengan demikian, organisasi tetap memperoleh manfaat fitur jaringan secara luas tanpa mengorbankan kerahasiaan.

#### **Partially-Permissioned Klaster**

Ini adalah model hibrida di mana sebuah organisasi mengoperasikan sebagian node dalam Klaster, sekaligus mengikutsertakan beberapa node eksternal.

Partially-permissioned Klaster ideal untuk use case yang membutuhkan keberadaan node eksternal (non-internal) sebagai mekanisme pengawasan terhadap setup yang pada dasarnya bersifat tertutup.

Sebagai contoh, organisasi dapat melatih model AI menggunakan node internal mereka, sembari memvalidasi hasilnya melalui node eksternal untuk memastikan transparansi dan akurasi.

#### **Public / Non-Permissioned Klaster**

Klaster jenis ini terbuka bagi jaringan Arx node yang lebih luas dan memungkinkan node tepercaya mana pun untuk bergabung dan berpartisipasi. Meskipun kriteria tertentu dapat ditetapkan seperti pembatasan geografis atau persyaratan teknis khusus konfigurasi default tetap menjamin aksesibilitas yang luas.

Perlu dicatat bahwa hanya Public / Non-Permissioned Klaster yang menggunakan mekanisme pemilihan node acak seperti yang dijelaskan pada halaman Overview, yang berfungsi untuk memastikan [**Sybil resistance**](ketahanan-terhadap-serangan-sybil-sybil-resistance.md) dan mendorong desentralisasi.

Konfigurasi ini sangat bermanfaat bagi proyek yang menginginkan tingkat desentralisasi yang lebih tinggi, karena memungkinkan partisipasi yang lebih luas di seluruh jaringan serta mengurangi risiko kolusi atau kontrol terpusat.
