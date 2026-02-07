# Konfigurasi dan Keamanan

Setiap node Arx wajib mendeklarasikan **kapabilitas perangkat kerasnya**, karena hal ini memengaruhi kelayakan beban kerja node serta potensi pendapatannya.

Deklarasi yang akurat diberikan insentif untuk memastikan kinerja yang andal, sementara node yang melebih-lebihkan kapasitasnya dan gagal memenuhi persyaratan tugas akan dikenai penalti. Node dapat meningkatkan spesifikasinya dari waktu ke waktu, namun penurunan spesifikasi perangkat keras tunduk pada ketentuan tertentu untuk memastikan bahwa hal tersebut tidak berdampak pada kinerja Klaster yang sedang aktif. Lihat bagian [Gambaran Umum Staking](../staking/gambaran-umum.md) untuk informasi lebih lanjut.

### Pertimbangan **Manajemen dan Keamanan Keyshare**

Node Arx menangani _key share_ yang krusial untuk berpartisipasi dalam protokol MPC di dalam Klaster, dan _key share_ tersebut tidak boleh dikompromikan.

_Key share_ ini disimpan dan dikelola secara aman, sering kali dengan memanfaatkan **Trusted Execution Environment (TEE)** untuk meningkatkan kerahasiaan dan integritas data. TEE menyediakan enclave terisolasi yang melindungi _key share_ dari akses tidak sah, sehingga hanya proses tepercaya di dalam node yang dapat berinteraksi dengannya.

Selain itu, terdapat pertimbangan keamanan lainnya. Hal ini mencakup integrasi sistem fisik dan sistem berbasis cloud untuk memaksimalkan waktu aktif (_uptime_) serta mencegah penalti akibat ketidakikutsertaan. Sistem fisik merujuk pada penerapan perangkat keras node Arx di lingkungan _on-premise_ yang aman dan redundan guna memastikan keandalan. Sementara itu, sistem berbasis cloud memanfaatkan infrastruktur yang skalabel dan terdistribusi dari penyedia tepercaya untuk meningkatkan perlindungan _failover_ dan ketersediaan.

###
