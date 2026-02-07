# Harga dan Insentif

Struktur harga dan insentif Jaringan Arcium dirancang untuk memastikan kompensasi yang adil bagi node Arx, sekaligus memungkinkan Pelanggan Komputasi mengoptimalkan biaya, kecepatan, dan prioritas.

Dengan mengombinasikan harga dasar tetap dan pasar biaya prioritas yang dinamis, sistem ini memastikan biaya yang dapat diprediksi sekaligus fleksibilitas untuk komputasi yang bersifat mendesak.

Biaya Prioritas dan Biaya Dasar dibagi berdasarkan jumlah [CUs](tugas-komputasi.md) yang digunakan, sehingga penggabungan beberapa komputasi tidak memengaruhi total biaya.

<figure><img src="../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

### Harga Dasar

Arcium menggunakan harga dasar yang menjamin tingkat kelayakan ekonomi minimum bagi tugas-tugas komputasi, bahkan pada periode dengan permintaan rendah.

Harga dasar ditetapkan pada **tingkat minimum yang layak secara ekonomi** untuk menutupi biaya operasional Operator Node, termasuk pemeliharaan perangkat keras, konsumsi energi, dan infrastruktur.

### Unit Komputasi

Sebagai pengingat, biaya eksekusi sebuah komputasi diukur dalam **Unit Komputasi (Computation Units/CUs)**, yaitu metrik terstandarisasi yang merepresentasikan sejumlah tetap pekerjaan komputasi.

Biaya per CU ditentukan pada setiap _epoch_ melalui proses pemungutan suara. Operator Node memberikan **suara berbobot stake** untuk menentukan harga CU pada _epoch_ berikutnya. Tidak ikut memberikan suara dianggap sebagai suara untuk mempertahankan harga saat ini.

Untuk mencegah manipulasi, hanya stake yang didelegasikan sendiri (_self-delegated stake_) oleh Operator Node yang dapat berpartisipasi dalam proses pemungutan suara.

Selain itu:

* **Stake Delegasi Berlebih**: Jika stake yang didelegasikan sendiri oleh Operator Node melebihi jumlah yang diperlukan untuk mengaktifkan seluruh perangkat kerasnya, hanya porsi stake yang berada di bawah ambang batas tersebut yang diperhitungkan.
* **Pendelegasi Pihak Ketiga**: Pendelegasi tidak dapat memberikan suara, karena insentif mereka dapat berbeda dengan Operator Node. Sebagai contoh, pendelegasi mungkin memprioritaskan keuntungan jangka pendek, sementara Operator Node memiliki kepentingan langsung terhadap biaya infrastruktur dan kesehatan jaringan dalam jangka panjang.

Node didorong untuk memberikan suara ketika mereka menilai bahwa penyesuaian harga dasar diperlukan demi menjaga kelayakan ekonomi. Tidak memberikan suara dianggap wajar dalam kondisi pasar yang stabil, ketika harga dasar yang berlaku sudah efektif.

Pengoperasian infrastruktur fisik secara inheren mengikat Operator Node pada keterlibatan jangka panjang, karena mereka menanggung biaya berkelanjutan untuk pemeliharaan perangkat keras, konsumsi energi, dan sumber daya terkait. Periode penguncian (_lock-up_) stake berfungsi sebagai mekanisme sekunder, dan secara bersama-sama langkah-langkah ini menjaga keandalan serta keberlanjutan jaringan hingga harga dasar disesuaikan pada _epoch_ berikutnya.

Harga dasar menetapkan **batas bawah kompensasi**, namun pelanggan tetap dapat membayar **biaya prioritas** tambahan untuk mempercepat komputasi (dijelaskan di bawah). Model harga berlapis ini memastikan keberlangsungan operasional sekaligus fleksibilitas bagi pelanggan dengan kebutuhan yang sensitif terhadap waktu.

### Prioritas Biaya Pasar

Sementara harga dasar menyediakan biaya acuan untuk komputasi, **biaya prioritas** memungkinkan Pelanggan Komputasi mempercepat tugas mereka dengan berpartisipasi dalam pasar biaya yang dinamis. Pasar ini memberikan insentif kepada node untuk memprioritaskan komputasi dengan bayaran lebih tinggi, sehingga tugas yang sensitif terhadap waktu dapat diproses lebih dahulu ketika permintaan jaringan tinggi.

Biaya prioritas beroperasi dalam **pasar spesifik Klaster** atau **serikat Klaster**, yaitu kelompok Klaster yang saling terhubung dan berbagi node yang sama. Setiap Klaster (atau serikat Klaster) membentuk pasar biaya tersendiri, di mana komputasi hanya bersaing dengan tugas lain yang menggunakan node yang sama. Segmentasi ini memastikan efisiensi dan mencegah tugas yang tidak berkaitan saling mengganggu alokasi sumber daya.

Untuk komputasi yang sangat mendesak, pelanggan dapat menawarkan biaya prioritas yang cukup tinggi untuk memonopoli sementara sumber daya sebuah Klaster. Hal ini memungkinkan mereka melewati tugas-tugas lain yang bersaing di dalam Klaster atau serikat Klaster, sehingga sangat menguntungkan bagi komputasi berskala besar atau kritis terhadap waktu. Dengan menyeimbangkan penawaran dan permintaan, pasar biaya prioritas menciptakan sistem eksekusi tugas yang fleksibel dan efisien, melengkapi stabilitas harga dasar.

<figure><img src="../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

### **Insentif Ekonomi bagi Node Arx**

Node Arx memperoleh pendapatan dari harga dasar dan biaya prioritas, sehingga memastikan operasional yang berkelanjutan sekaligus mendorong kinerja yang tinggi.

**Pendapatan dari harga dasar** memberikan pemasukan yang konsisten untuk menutupi biaya operasional, terlepas dari tingkat permintaan jaringan, sehingga menjamin stabilitas jangka panjang bagi Operator Node. Sementara itu, **pendapatan dari biaya prioritas** memberikan imbalan kepada Klaster Node yang memproses komputasi berprioritas tinggi. Hal ini mendorong pemanfaatan sumber daya yang efisien dan memotivasi node untuk tetap kompetitif di pasar.

Meskipun periode penguncian bagi Operator Node mendorong pola pikir jangka panjang dan stabilitas, penalti _slashing_ atas ketidakberpartisipasian dan perilaku menyimpang berfungsi untuk mencegah eksploitasi jangka pendek.

### **Persaingan pada Tingkat Klaster**

Sistem harga Arcium menyeimbangkan fleksibilitas pelanggan dan kelayakan ekonomi node dengan memanfaatkan mekanisme dinamis berbasis pasar di dalam Klaster yang digunakan bersama.

Klaster dinamis memastikan bahwa pasar biaya terbentuk secara alami ketika komputasi bersaing atas sumber daya Klaster yang sama. Ketika permintaan meningkat, biaya prioritas akan naik secara dinamis, mengarahkan sumber daya komputasi yang terbatas ke tugas-tugas yang paling mendesak dan bernilai tinggi. Sistem adaptif ini mengalokasikan sumber daya secara efisien, sehingga jaringan dapat memenuhi kebutuhan pelanggan yang beragam tanpa membebani node secara berlebihan.

Keadilan antar-node dijaga dengan mendistribusikan biaya prioritas secara merata kepada setiap node yang berpartisipasi dalam sebuah Klaster. Pendekatan ini memberikan imbalan yang setara berdasarkan beban kerja dan memastikan kompensasi yang adil, selaras dengan insentif node dan efisiensi operasional jaringan.

Melalui kombinasi persaingan dinamis dan distribusi imbalan yang adil ini, Arcium membangun ekosistem yang kuat dan fleksibel, mampu beradaptasi terhadap perubahan permintaan sambil tetap menjaga keadilan dan keandalan.

### Cara Pelanggan Mengoptimalkan Biaya

**Total biaya yang dibayarkan oleh Pelanggan Komputasi merupakan penjumlahan dari biaya dasar dan biaya prioritas yang dipilih.**

Baik biaya prioritas maupun biaya dasar dibagi berdasarkan jumlah [**CUs**](tugas-komputasi.md) yang digunakan. Hal ini memastikan harga disesuaikan dengan ukuran komputasi dan memungkinkan perbandingan yang adil antarberbagai beban kerja. Dengan menormalkan biaya pada tingkat per unit, jaringan memastikan bahwa **harga dasar dan biaya prioritas** dapat dievaluasi secara independen dari ukuran komputasi. Artinya, baik komputasi besar maupun kecil, **biaya per CU** tetap menjadi metrik utama dalam penentuan harga eksekusi.

Pelanggan Komputasi dapat mengoptimalkan biaya dengan mengelola parameter eksekusi secara cermat:

1. **Menetapkan Jendela Eksekusi**: Menghindari biaya tinggi pada saat permintaan puncak dengan menjadwalkan komputasi di luar jam sibuk.
2. **Menyesuaikan Biaya Prioritas**: Menggunakan biaya prioritas secara strategis untuk menyeimbangkan biaya dan urgensi. Biaya rendah cocok untuk komputasi yang tidak mendesak, sementara biaya lebih tinggi memastikan eksekusi segera.
