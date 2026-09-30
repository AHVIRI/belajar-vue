# Laporan Implementasi UI: Layout System & Visual Hierarchy
**Proyek:** Gatherly (Community Event Platform)

Laporan ini merangkum perubahan struktur visual dan tata letak yang telah diterapkan pada aplikasi Gatherly, dengan memetakan setiap perubahan ke dalam teori desain antarmuka.

---

## 1. Fondasi Tata Letak (Global System)
*Lokasi: `src/assets/main.css`*

*   **Spatial System (Base-8):** Alih-alih menebak ukuran piksel yang pas, kami menerapkan variabel berbasis kelipatan 8 (seperti `--space-2: 8px`, `--space-4: 16px`, `--space-8: 32px`). Ini memastikan seluruh margin, padding, dan jarak antarelemen di seluruh aplikasi memiliki ritme matematis yang konsisten.
*   **Grid System:** Kami mendefinisikan sistem 12-kolom global untuk memudahkan tata letak komponen yang kompleks.
*   **Box Model Fix:** Menerapkan `box-sizing: border-box` secara universal agar setiap penambahan *padding* tidak merusak *layout width 100%* (mencegah horizontal scroll).

---

## 2. Beranda (`Home.vue`) - Estetika & Kesan Pertama
Halaman utama direka ulang sepenuhnya dari sekadar wadah rute menjadi halaman pendaratan (Landing Page) profesional.

*   **The Fold:** Memastikan bagian *Hero Section* (sambutan utama dan tombol) minimal setinggi layar (`min-height: 80vh`). Ini memastikan pesan terpenting 100% terlihat *Above the Fold* sebelum pengunjung menyentuh tombol *scroll*.
*   **Visual Hierarchy (Scale & Contrast):** Judul utama dibuat raksasa (`font-size: 4rem`), menciptakan *Ranked Importance* nomor satu. Tombol "Discover Events" diberi kontras tinggi dan efek bayangan ungu.
*   **Z-Pattern:** Pengguna akan memindai dari kiri ke kanan di Navbar, diagonal turun ke judul utama, lalu berakhir pada tombol (CTA) di bagian tengah.
*   **Grouping & Grid (Features Section):** Mengganti sitemap lama dengan 3 kotak fitur (Discover, Ticketing, Host). Tiga kotak ini menggunakan *Adaptive Grid* dan mempraktikkan hukum *Common Regions*, di mana ikon, judul, dan teks disatukan dalam satu batas kotak berbayang.

---

## 3. Penelusuran Acara (`EventList.vue`) - Katalog Responsif
*   **Adaptive Columns Layout:** Menggunakan grid `auto-fill` dengan lebar minimal `320px`. Jika dibuka di laptop, ia akan membentuk 3 kolom. Jika di layar HP, ia akan melipat otomatis menjadi 1 kolom tanpa perlu koding media query yang panjang.
*   **Grouping (Proximity & Boundaries):** Sebuah acara direpresentasikan dalam satu *Card* (kartu). Garis luar (*border*) dan bayangan halus kartu menciptakan batas visual yang jelas, memberi isyarat ke otak bahwa teks di dalamnya saling terhubung secara proksimal.
*   **Recognition over Recall:** Menggunakan *badge* warna khusus untuk label tanggal dan kategori, membuat acara mudah dikenali sekilas.

---

## 4. Detail Acara (`EventDetail.vue`) - Mendorong Konversi
Ini adalah halaman tempat pengunjung akhirnya memutuskan untuk mendaftar, sehingga hierarki visual dibuat asimetris.

*   **Asymmetrical Layout:** Ruang dibagi dengan rasio 8:4. Delapan bagian kiri untuk teks panjang, empat bagian kanan untuk tombol aksi.
*   **F-Pattern (Kolom Kiri):** Agar pengguna tidak bosan membaca deskripsi acara yang panjang, teks dipecah dengan *Heading* (`<h2>`) dan daftar *bullet point* untuk agenda. Susunan ini sangat pas untuk dipindai dengan pergerakan mata berbentuk huruf "F".
*   **Focal Point & Squint Test (Kolom Kanan):** Area tiket pendaftaran dibuat diam mengambang (`position: sticky`) agar tidak hilang saat di-scroll. Tombol **Register Now** menggunakan warna *Primary Solid*. Jika Anda menyipitkan mata (*Squint Test*), blok warna ungu dari tombol ini akan menjadi satu-satunya bentuk yang paling memancing mata.

---

## 5. Dasbor Penyelenggara (`DashboardLayout.vue` & `Dashboard.vue`)
Kami membangun halaman baru untuk membedakan UI Pengunjung (Website Layout) dan UI Pekerja/Penyelenggara (Web App Layout).

*   **Rail & Pane System:** 
    *   **Rail:** Area kiri (Sidebar) statis berisi navigasi vertikal (Overview, My Events, QR Check-in) yang terkunci pada layarnya.
    *   **Pane:** Area kanan utama tempat data dinamis dimunculkan. Area ini memiliki ruang *scroll* yang mandiri dari bilah navigasi.
*   **Data Density & F-Pattern:** Di dalam *Pane*, metrik penting dikelompokkan pada baris pertama menggunakan 3 kartu statis, lalu diikuti oleh tabel pendaftar secara padat. Tabel adalah bentuk paling murni dari desain UI yang menuntut *F-Pattern reading* yang efisien.
