# Gambaran Umum

Saat meluncurkan sebuah node Arx, detail metadata tertentu tentang node tersebut harus disediakan, termasuk keterkaitannya dengan seorang _Operator Node_.

**Operator Node** adalah entitas metadata yang merepresentasikan pihak yang mengoperasikan node Arx, dan dapat mewakili lebih dari satu node Arx.

<figure><img src="../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

### Operator Node

Operator Node memiliki hubungan satu-ke-banyak dengan node Arx, yang berarti satu Operator Node dapat menjalankan beberapa node. Metadata berikut terkait dengan seorang Operator Node:

* **Yurisdiksi**: Mengikuti standar kode ISO 3166-1 alfa-2 untuk yurisdiksi (misalnya DE untuk Jerman, FR untuk Prancis, dan seterusnya).
* **URL**: Tautan ke halaman web yang merepresentasikan Operator Node (misalnya media sosial atau halaman web yang menjelaskan layanan dan reputasi operator).

Karena bidang metadata ini dideklarasikan sendiri, lokasi perangkat keras sebenarnya relatif terhadap yurisdiksi yang diberikan tidak diverifikasi oleh Jaringan Arcium. Namun, klaim lokasi akan dievaluasi secara independen oleh komunitas Jaringan Arcium (bersama dengan penilaian terhadap tim operator, pendekatan keamanan, transparansi, reputasi lintas jaringan, dan aspek lainnya).

### Metadata

Metadata sebuah node Arx bersifat unik untuk node tersebut dan dapat berbeda dari metadata Operator Node yang terkait, karena satu operator dapat menjalankan beberapa node, misalnya di yurisdiksi yang berbeda.

Metadata khusus node ini terdiri dari bidang-bidang berikut:

* **IP & Port**: Bidang ini secara langsung berkaitan dengan penerapan node, dengan menetapkan detail akses RPC ke node Arx.
* **Yurisdiksi**: Mengikuti standar kode ISO 3166-1 alfa-2 yang sama seperti yang digunakan oleh Operator Node.

Sebagaimana pada bidang yurisdiksi Operator Node, bidang yurisdiksi pada node Arx tidak diverifikasi dan oleh karena itu juga akan dievaluasi secara independen oleh komunitas Jaringan Arcium.
