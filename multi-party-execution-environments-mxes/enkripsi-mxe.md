# Enkripsi MXE

Enkripsi data dalam Arcium Network dikelola pada tingkat **MXE**.

Arcium Network menawarkan pendekatan enkripsi yang fleksibel, memungkinkan **Computation Customers** untuk menentukan protokol enkripsi secara individual untuk setiap MXE.

Setiap MXE beroperasi secara independen dan tidak berbagi state dengan MXEs lainnya. Meskipun solusi eksternal dapat digunakan untuk mempertahankan data terenkripsi di antara beberapa MXE, Arcium tidak menyediakan penyimpanan state di tingkat protokol. Pendekatan ini memastikan setiap komputasi tetap terisolasi, sehingga kerahasiaan dan keamanan data tetap terjaga.

Konsep **enkripsi yang dapat dikonfigurasi** pada Arcium memberikan fleksibilitas penuh kepada pengguna untuk menyesuaikan protokol enkripsi sesuai kebutuhan use case tertentu. Saat menyiapkan sebuah MXE, pengguna dapat memilih dari berbagai opsi enkripsi dengan menyeimbangkan antara performa dan tingkat keamanan.

Sebagai contoh:

* **Enkripsi ringan (lightweight encryption)** dapat dipilih untuk tugas yang mengutamakan kecepatan dan efisiensi.
* **Protokol enkripsi yang lebih kuat** tersedia untuk menangani data yang sangat sensitif dan membutuhkan perlindungan ekstra.

Fleksibilitas ini memastikan setiap MXE dapat dioptimalkan sesuai tujuan penggunaannya, dengan kombinasi keamanan dan performa yang tepat.

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

### Ketahanan terhadap Serangan Side-Channel

Beberapa platform eksekusi rahasia, seperti **Trusted Execution Environments (TEE)**, bergantung pada hardware untuk mengamankan data. Namun, pendekatan ini terbukti rentan terhadap berbagai **serangan side-channel** (misalnya [_sgx.fail_](https://sgx.fail/)), yang memungkinkan kebocoran data atau manipulasi, sehingga melemahkan jaminan privasi.

Sebaliknya, **protokol Cerberus milik Arcium** mengandalkan **keamanan komputasional dan keamanan berbasis teori informasi**, yang menjamin bahwa **bahkan jika mayoritas partisipan bertindak jahat, mereka tetap tidak dapat mengekstrak atau memalsukan informasi selama asumsi keamanan terpenuhi**.

Selain itu, beberapa implementasi MPC rentan terhadap **serangan timing**, di mana penyerang menyimpulkan informasi dari perbedaan kecil dalam waktu pemrosesan. Untuk mengatasi hal ini, solusi Arcium menggunakan **operasi dengan waktu konstan (constant-time operations)**, sehingga data tetap aman dan risiko kebocoran informasi berbasis timing dapat dihilangkan sepenuhnya.

###
