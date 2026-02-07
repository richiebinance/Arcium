# Ketahanan terhadap Sensor & Penanganan Kegagalan

Jaringan Arcium dirancang untuk memastikan ketahanan yang kuat terhadap sensor serta toleransi terhadap kegagalan, sehingga integritas komputasi tetap terjaga meskipun terjadi kegagalan node atau perilaku jahat.

Pada bagian ini akan dibahas **a) strategi ketahanan terhadap sensor, b) penanganan kegagalan,** dan **c) mekanisme slashing.**

### Ketahanan terhadap Sensor

Ketahanan terhadap sensor sangat penting untuk menjaga kepercayaan dalam sistem terdesentralisasi. Di Jaringan Arcium, node tidak dapat secara selektif memblokir atau mengganggu komputasi tanpa menghadapi konsekuensi.

Arsitektur jaringan menegakkan hal ini melalui beberapa mekanisme berikut:

1. **Deteksi Kriptografis terhadap Perilaku Menyimpang:**\
   Node yang mencoba mengganggu komputasi dengan mengirimkan data yang salah, membatalkan tugas, atau secara keliru mengklaim bahwa node lain berperilaku menyimpang dapat dideteksi secara kriptografis, misalnya dengan Cerberus ([Protokol MPC](../multi-party-execution-environments-mxes/protokol-mpc.md) bawaan Arcium). Setiap penyimpangan dari protokol yang telah disepakati akan memicu proses otomatis untuk mengidentifikasi node yang bersalah.
2. **Slashing sebagai Efek Jera:**\
   Perilaku menyimpang akan berujung pada penalti slashing yang mengurangi jumlah stake milik node pelanggar. Meskipun transaksi berbahaya sudah dapat dideteksi, mekanisme ini berfungsi sebagai hukuman tambahan sekaligus kompensasi atas biaya deteksi.

### Penanganan Kegagalan

Toleransi terhadap kegagalan merupakan elemen penting untuk memastikan jaringan tetap beroperasi dengan lancar, meskipun node mengalami kegagalan akibat masalah teknis atau niat jahat.

Jaringan Arcium menangani kegagalan melalui strategi berikut:

1. **Deteksi Ketidakikutsertaan:**\
   Ketidakikutsertaan terjadi ketika sebuah node gagal menjalankan tugas yang ditetapkan. Jaringan mendeteksi hal ini melalui sinyal komunikasi di dalam klaster. Jika sebuah node tidak memberikan respons, node tersebut akan ditandai untuk ditinjau. Tugas dapat dialihkan ke kumpulan node yang lebih luas (di luar klaster terkait) apabila konsensus tidak dapat dicapai di dalam klaster.
2. **Deteksi Kecurangan:**\
   Kecurangan terjadi ketika sebuah node memberikan hasil komputasi yang tidak benar. Jaringan Arcium menggunakan teknik kriptografis untuk mengidentifikasi keluaran yang tidak valid. Hal ini memastikan bahwa setiap upaya manipulasi hasil dapat segera terdeteksi dan dikenai sanksi.

Selain itu, sebagai bagian dari mekanisme penyelesaian sengketa, ketika kegagalan terdeteksi, komputasi akan dijalankan ulang secara redundan oleh node lain untuk memastikan hasil yang andal. Redundansi ini menjamin ketahanan jaringan, bahkan dalam skenario berisiko tinggi.

### Mekanisme Slashing

Jaringan Arcium menerapkan penalti slashing untuk menegakkan akuntabilitas.

Terdapat dua jenis slashing utama:

1. **Ketidakikutsertaan:**\
   Node yang gagal berpartisipasi dalam komputasi akan dikenai penalti yang lebih tinggi karena kebutuhan sumber daya yang lebih besar untuk mendeteksi dan mengonfirmasi ketidakikutsertaan tersebut.
2. **Kecurangan:**\
   Node yang memberikan hasil yang tidak benar akan dikenai penalti berdasarkan besarnya beban komputasi yang telah mereka ganggu.
