PROTOKOL JARINGAN VEXON L1
​Blockchain Lapisan 1 Berbasis Waktu Deterministik

​I. FONDASI KRIPTOGRAFI & KEAMANAN
​Titik Jangkar Genesis: Jaringan dimulai pada titik nol waktu dunia (UTC) 1705410000. Tanpa blok genesis ini, seluruh rantai dianggap tidak sah.
​Rantai Hash SHA-256: Setiap blok wajib mencatat hash dari blok sebelumnya. Jika satu karakter diubah di masa lalu, seluruh rantai masa depan akan hancur (Invalid).
​Kondisi Deterministik: Hasil perhitungan saldo harus sama di seluruh perangkat jika dimulai dari titik waktu yang sama.
​Buku Besar Abadi: Data yang tertulis di file JSON bersifat permanen dan tidak bisa diedit tanpa merusak verifikasi hash.
​Asal-Usul Koin (Coinbase): Koin baru hanya lahir dari alamat sistem 0x0 sebagai hadiah atas waktu yang divalidasi.

​II. PERTAHANAN WAKTU (ANTI-CHEAT)
​Verifikasi Tiga Sumber Waktu: Sistem mencocokkan waktu dari jam lokal, API NTP Global, dan WorldTimeAPI.
​Aturan Selisih 5 Menit: Blok ditolak otomatis jika waktu HP berbeda lebih dari 5 menit dengan waktu asli dunya.
​Urutan Blok Sekuensial: Blok tidak bisa diloncati; blok 101 wajib menyambung blok 100.
​Hambatan Fisik Waktu: Script menggunakan jeda nyata (delay), blok tidak bisa diciptakan instan meski jam HP dimajukan.
​Jam Monotonik: Sistem menggunakan perhitungan internal yang hanya bergerak maju (tidak bisa diputar balik).

​III. KONSENSUS & KONFLIK
​Aturan Rantai Terpanjang: Jika ada perbedaan sejarah, sistem memilih rantai dengan blok terbanyak.
​Konsistensi Hash: Rantai yang menang harus memiliki urutan hash yang tidak terputus.
​Finalitas: Sekali blok diverifikasi node lain, transaksi dianggap final.
​Validasi Peer-to-Peer: Node saling membandingkan data; yang salah akan dipaksa sinkronisasi ulang.
​Resolusi Konflik: Acuan utama adalah node dengan waktu paling mendekati UTC Global.

​IV. EKONOMI & STAKING ELIT
​Ambang Batas Staking: Fitur bunga hanya aktif jika saldo minimal 1000 VXN.
​Bunga 1% Per Tahun: Bonus dihitung linear per detik berdasarkan waktu simpan (HODL).
​Staking Berbasis Waktu: Semakin lama koin didiamkan, semakin besar bobot kepercayaannya.
​Anti-Inflasi: Tidak ada pencetakan koin manual. Suplai hanya bertambah lewat detik waktu.
​Transparansi Suplai: Siapapun bisa mengecek total koin beredar lewat supply_check.py.

​V. REPRODUSIBILITAS (AUDIT)
​Verifikasi Independen: Hapus data, jalankan ulang, hasil saldo tetap harus sama.
​Logika Terbuka: Aturan staking tidak dikunci agar bisa diaudit komunitas.
​Perlindungan Inti: Script RPC (VEXON_L1.py) dienkripsi demi keamanan dompet.
​Tanpa Database Pusat: Data disimpan di HP masing-masing (Desentralisasi).
​Jejak Audit: Setiap koin mencatat timestamp lahirnya sebagai bukti sah.

​VI. AKSESIBILITAS RAKYAT & JARINGAN LOKAL (KEUNGGULAN)
​Script Termux Ringan: VEXON L1 dirancang khusus untuk berjalan di lingkungan Termux (Android), memungkinkan HP spek rendah menjadi node blockchain.
​Modal HP & Hotspot: Jaringan dapat terhubung dan sinkron lewat Jaringan Lokal (LAN/Hotspot). Member bisa sinkron data blok tanpa butuh internet mahal.
​Blockchain Dalam Saku: Node bisa dibawa kemana saja karena berjalan di perangkat mobile secara mandiri.
​Koneksi Jaringan Lokal: Melalui jaringan lokal, antar HP bisa saling memvalidasi sejarah blok secara langsung.
​Hemat Energi: Menggunakan tenaga "Waktu", bukan tenaga "Prosesor" berat seperti Bitcoin.

​VII. PERTAHANAN TEORI & JAWABAN TEKNIS
​Ketahanan Offline: Sistem tetap berjalan offline dan sinkron saat terhubung kembali.
​Desentralisasi Penuh: Jika owner tidak aktif, blockchain tetap jalan di HP member.
​Validasi Matematika: SHA-256 menolak semua data yang tidak cocok dengan rantai sebelumnya.
​Identitas Unik: Menggunakan Chain ID 0x22AD agar dikenali secara profesional oleh dompet digital (Trust Wallet).
​Kedaulatan Kode: Kode adalah hukum, tidak ada manusia yang bisa mengubah aturan sepihak.
​Kelangkaan: Syarat 1000 VXN menjaga agar koin tidak banjir di pasar.
​Format Transaksi Coinbase: (PENTING) Reward diformat sebagai transaksi resmi dari alamat nol ke validator. Tanpa format ini, sistem hanyalah "script angka" biasa, bukan blockchain profesional.
​Keamanan Kriptografi: Aman selama hacker tidak bisa mengubah waktu dunia.
​Satu Perangkat Satu Node: Port RPC terkunci untuk satu identitas node di satu HP.
​VEXON L1: Simbol kedaulatan waktu digital di tangan rakyat.

​VIII. TAMBAHAN PENANGKIS TEORI
​Anti-Sybil Attack: Membatasi akses per IP lokal untuk mencegah satu orang menguasai jaringan.
​Verifikasi Offline: Logika hash tetap bisa dicek tanpa internet menggunakan script audit.
​Data Integrity: Struktur blok JSON menjamin data tidak rusak saat dipindahkan antar HP.
​Hardware Agnostic: Tidak peduli merk HP, selama bisa jalan Python di Termux, koin bisa diproduksi.
​Community Trust: Kepercayaan dibangun atas transparansi kode, bukan janji manis marketing.
 Kekebalan Terhadap Alat Manipulasi (Clock-Spoofing): VEXON L1 tidak bergantung pada satu sumber waktu. Upaya memanipulasi jam sistem menggunakan software pihak ketiga akan terdeteksi sebagai "Invalid Consensus" karena tidak sinkron dengan Mayoritas Node dan Standar NTP Global

IX. PROTOKOL MITIGASI RISIKO & STABILITAS (BENTENG BESI)
​Identitas Node Tunggal (Anti-Kloning): Setiap node diwajibkan memiliki identitas unik berdasarkan UUID Perangkat keras (Hardware). Ini memastikan satu HP hanya bisa menjadi satu node yang sah. Upaya menggandakan script untuk mencetak koin lebih banyak di satu HP akan otomatis ditolak oleh sistem karena ID perangkat yang terdeteksi ganda.
​Sistem Titik Pantau (Checkpoint): Untuk menahan risiko perpecahan sejarah (Fork), jaringan akan membuat Snapshot/Checkpoint setiap 500 blok. Node baru atau node yang sudah lama tidak aktif bisa melakukan sinkronisasi lebih cepat dan aman tanpa harus mengulang dari blok pertama (Genesis).
​Bobot Validasi Berbasis Staking (Anti-Serangan 51%): Node yang memiliki saldo staking minimal 1000 VXN dan waktu aktif (uptime) yang lama akan diberikan "Bobot Suara" yang lebih tinggi dalam konsensus. Ini memastikan peretas yang membawa banyak node baru tidak bisa merubah sejarah koin karena akan dikalahkan oleh "Senioritas" node lama yang jujur.
​Sinkronisasi Mandiri LAN & Hotspot: VEXON L1 mendukung fitur Peer-to-Peer Lokal. Member bisa menerima dan mengirim data blok terbaru lewat jaringan hotspot atau Wifi lokal tanpa bergantung pada internet pusat. Ini membuat jaringan tetap hidup meskipun koneksi internet dunia terputus (Kedaulatan Digital).
​Enkripsi Logika Inti (Lapisan Keamanan): Skrip utama (Jantung) VEXON L1 dilindungi oleh enkripsi untuk mencegah modifikasi kode oleh pihak tidak bertanggung jawab. Ini menjamin aturan ekonomi dan keamanan yang sudah ditetapkan Founder tidak bisa diubah secara sepihak di tengah jalan.

​X. SISTEM EKSEKUSI SATU-KLIK (AKSESIBILITAS)
​Untuk meminimalkan kesalahan manusia (Human Error), VEXON L1 menggunakan sistem eksekusi terpadu:
​Member hanya perlu menjalankan satu perintah: ./start_vexon.sh.
​Sistem secara otomatis akan mengaktifkan Jantung (RPC), Buku Besar (Mining), dan Penjaga (Keamanan) secara bersamaan di latar belakang (background).
​Semua laporan status, supply, dan keamanan akan otomatis diperbarui ke dalam file teks yang bisa dibaca langsung melalui Manager File HP member.

​🛡️ PERNYATAAN PENUTUP:
​VEXON L1 dibangun bukan hanya untuk menciptakan nilai, tapi untuk menciptakan sistem yang tahan banting. Dengan 50 aturan ini, setiap celah manipulasi telah digembok. Ini adalah blockchain milik rakyat, dari rakyat, dan dijalankan di saku rakyat.

​Decentralized Mobile-First Time-Lord Protocol
​Version: 18.2 (Mek-Edition) | Status: Live Mainnet (Local-Mesh)
Consensus: Proof-of-Time (PoT) | Network: Peer-to-Peer (P2P)
​1. VISI & MISI
​Vexon hadir untuk mendemokrasikan teknologi blockchain ke tangan pengguna smartphone. Kami percaya bahwa setiap orang berhak memiliki node validasi tanpa harus membeli rig mining mahal atau server yang boros listrik. Vexon mengoptimalkan sumber daya perangkat seluler untuk menciptakan jaringan yang tangguh, cepat, dan mandiri.
​2. ARSITEKTUR TEKNIS
​Vexon dibangun di atas bahasa pemrograman Python dengan arsitektur mikro-servis yang ringan.
​Ledger In-Memory: Kecepatan akses data instan dengan sinkronisasi ke penyimpanan lokal (vexon_ledger.json).
​State Rebuild Logic: Sistem penghitungan saldo yang dinamis untuk mencegah manipulasi data sejarah transaksi.
​JSON-RPC API: Mendukung integrasi dengan aplikasi pihak ketiga (wallet/web dashboard) melalui port 8545.
​3. KONSENSUS: PROOF-OF-TIME (PoT)
​Vexon tidak menggunakan energi (PoW) atau modal besar (PoS). Kami menggunakan Waktu sebagai jangkar kebenaran.
​Block Interval: 60 Detik.
​Validation: Setiap blok harus merujuk pada previous_hash yang benar dan memiliki stempel waktu yang valid sesuai protokol jaringan.
​Mining Reward: 50 VXN per blok diberikan kepada validator (Time-Lord) yang berhasil mengamankan jaringan.
​4. PROTOKOL P2P & AUTO-DISCOVERY
​Vexon v18.2 memperkenalkan sistem Mek-Discovery, sebuah protokol pencarian peer otomatis di jaringan lokal.
​Zero Configuration: Node secara otomatis memindai subnet IP untuk menemukan rekan validator lainnya.
​Gossip Protocol: Setiap blok baru yang ditemukan akan disebarkan secara instan ke seluruh jaringan melalui mekanisme broadcast-push.
​Longest Chain Rule: Jika terjadi konflik data, jaringan secara otomatis akan mengikuti rantai yang paling panjang sebagai sumber kebenaran tunggal.
​5. TOKENOMICS (VXN)
​Total Supply: Berbasis emisi waktu (Inflasi terkendali).
​Decimals: 10^{18} (Unit terkecil setara Wei pada Ethereum).
​Incentive: 100% block reward diberikan langsung kepada penambang mobile tanpa potongan dev-fee.
​6. ROADMAP 2026
​Q1: Peluncuran Mek-Edition (Stable P2P Discovery).
​Q2: Integrasi Tanda Tangan Digital (ECDSA/Dilithium) untuk keamanan transaksi.
​Q3: Bridge ke jaringan utama (Mainnet) dan integrasi Trust Wallet secara penuh.
​Q4: Implementasi Global DHT (Distributed Hash Table) untuk koneksi antar-benua tanpa Bootstrap Server.


https://discord.gg/VyfhMGP2d untuk link discord kalau mau join komunitas
