# Ketahanan terhadap Serangan Sybil (Sybil Resistance)

Serangan Sybil terjadi ketika satu entitas membuat banyak identitas palsu untuk memberikan pengaruh yang tidak proporsional terhadap jaringan. Untuk mengatasi hal ini, Arcium Network menggunakan konsensus **Proof of Stake**, yang mengharuskan setiap node melakukan staking dalam jumlah minimum agar dapat beroperasi.

Dalam Arcium Network, ketahanan terhadap Sybil sangat penting untuk menjaga integritas dan keamanan sistem. Untuk menghadapi potensi serangan Sybil, Arcium menerapkan strategi pada dua tingkat:

* **Ketahanan Sybil Intra-Klaster**: Mencegah kolusi antar node di dalam Klaster yang sama. Dengan mewajibkan setidaknya satu node yang dipilih secara acak di semua Klaster non-permissioned, jaringan memastikan bahwa meskipun beberapa node mencoba berkolusi, keberadaan node independen tersebut berfungsi sebagai penyeimbang, sehingga secara signifikan mengurangi risiko serangan Sybil di dalam cluster.
* **Ketahanan Sybil Tingkat Jaringan (Network-Wide)**: Untuk melindungi seluruh jaringan dari serangan Sybil, Arcium meningkatkan ukuran node-set dalam Klaster dan menyertakan satu node acak di setiap Klaster non-permissioned. Selain itu, para partisipan jaringan menggunakan sistem reputasi operator node untuk mendorong keterlibatan komunitas dalam memantau dan melaporkan aktivitas mencurigakan; jaringan juga menerapkan hukuman slashing yang lebih berat untuk downtime node yang terjadi secara bersamaan.

### 1. Ketahanan Sybil Intra-Klaster

Ketahanan Sybil intra-Klaster bertujuan mengurangi risiko kolusi antar node dalam Klaster yang sama, yang dapat membahayakan kerahasiaan secret yang dibagikan. Meskipun jaringan secara keseluruhan memiliki kumpulan node yang beragam, Klaster publik individual dengan node-set yang kecil dan terpusat tetap berpotensi rentan.

Untuk mengatasi hal ini, **Arcium Network memastikan penyertaan setidaknya satu node yang dipilih secara acak di semua Klaster non-permissioned**. Node ini, yang dipilih dari jaringan yang lebih luas, bertindak sebagai penyeimbang independen dan mengurangi kemungkinan terjadinya serangan Sybil intra-klaster. Selama terdapat setidaknya satu node yang jujur dalam sebuah Klaster, integritas Klaster tersebut tetap terjaga. Langkah-langkah ini secara kolektif menjaga keamanan dan kerahasiaan operasional Klaster.

### 2. Ketahanan Sybil Tingkat Jaringan (Network-Wide)

Serangan Sybil pada tingkat jaringan bertujuan untuk mengganggu mekanisme konsensus protokol secara menyeluruh, seperti **Base Price Voting** dan sistem **Non-Participation Detection**. Untuk melindungi diri dari serangan semacam ini, Arcium Network menerapkan beberapa strategi berlapis:

1. **Penyertaan Node Acak**\
   Seperti dijelaskan sebelumnya, Klaster non-permissioned menyertakan setidaknya satu node yang dipilih secara acak untuk memastikan keberagaman dan netralitas.
2. **Skalabilitas Node-Set Klaster**\
   Meningkatkan ukuran dan keberagaman node-set dalam Klaster akan memperkuat keamanan jaringan secara keseluruhan.
3. **Trusted Execution Environments (TEE)**\
   Node dalamKlaster dapat secara opsional menyediakan TEE untuk semakin memperkuat kerahasiaan dan tingkat kepercayaan.
4. **Sistem Reputasi Operator Node**\
   Sistem reputasi offchain memungkinkan operator node membangun kepercayaan berdasarkan kinerja sebelumnya, keterlibatan komunitas, serta pengalaman dalam layanan validasi jaringan (dari chain dan protokol lain).
5. **Pemantauan oleh Komunitas**\
   Keterlibatan aktif komunitas menyediakan lapisan pertahanan sosial, dengan mendorong partisipan untuk memantau dan melaporkan aktivitas yang mencurigakan.
6. **Penalti Strategis**\
   Hukuman slashing yang lebih berat diterapkan untuk downtime node yang terjadi secara bersamaan. Hal ini mencegah pengoperasian banyak node dengan konfigurasi serupa atau yang berada dalam kedekatan geografis, serta mendorong diversifikasi lintas yurisdiksi, pusat data, sistem operasi, dan praktik keamanan.

Seluruh mekanisme ini secara kolektif meningkatkan ketahanan Arcium Network, memastikan kemampuannya untuk bertahan dan pulih dari upaya serangan Sybil yang terkoordinasi, sambil tetap menjaga keamanan yang kuat dan keandalan operasional.
