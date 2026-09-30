# Laporan Struktur File Aplikasi Vue "Gatherly"

Berikut adalah bagan sederhana dari struktur *file* Vue beserta penjelasan perannya di dalam aplikasi yang telah kita bangun.

## 📂 Bagan Struktur Direktori
```text
src/
│
├── App.vue                 # 📍 Komponen Root Aplikasi
├── main.js                 # 🚀 Entry point aplikasi Vue
│
├── router/
│   └── index.js            # 🔀 Konfigurasi Routing (Vue Router)
│
├── layouts/
│   └── App.vue             # 🏗️ Layout Utama (Bungkus kerangka web)
│
├── components/
│   └── app/
│       ├── Navbar.vue      # 🧭 Komponen Menu Navigasi & Dropdown
│       └── Breadcrumb.vue  # 📍 Komponen Indikator Lokasi (Jejak Halaman)
│
└── views/                  # 📄 Halaman-halaman Website
    ├── Home.vue            # Halaman Beranda
    ├── About.vue           # Halaman Tentang Kami
    ├── Contact.vue         # Halaman Kontak
    │
    ├── Browse.vue          # Halaman Induk Penelusuran (Parent)
    ├── EventList.vue       # ↳ Halaman Daftar Acara (Event)
    ├── EventDetail.vue     # ↳ Halaman Spesifik Detail Acara
    └── Category.vue        # ↳ Halaman Kategori
```

---

## 📝 Penjelasan Detail Komponen & File

### 1. File Utama & Konfigurasi
*   **`src/App.vue`**
    Komponen tingkat paling atas (*root*). Isinya sangat sederhana, hanya memanggil `<RouterView />` yang berfungsi memuat layout/halaman berdasarkan URL yang diakses pengunjung.
*   **`src/router/index.js`**
    Pusat pengatur lalu lintas halaman (*routing*). File ini mendaftarkan URL (seperti `/`, `/about`, `/browse/events/:id`) dan menghubungkannya dengan *file* `.vue` yang tepat.

### 2. Layout & Global Components (Digunakan di Semua Halaman)
*   **`src/layouts/App.vue`**
    Berfungsi sebagai kerangka utama website. Di sinilah letak desain statis yang membungkus semua halaman, yaitu memanggil komponen **Navbar**, komponen **Breadcrumb**, dan ruang kosong (`<router-view/>`) untuk disisipkan isi halamannya.
*   **`src/components/app/Navbar.vue`**
    Berisi kode untuk Navigasi Menu. Dilengkapi dengan logika *dropdown* (untuk menu Browse) dan efek visual penanda warna halaman aktif (*current active route*).
*   **`src/components/app/Breadcrumb.vue`**
    Menampilkan jejak halaman saat ini (Contoh: `Home / Browse / Event List`). Mengambil informasi *meta-data* rute dari Vue Router untuk merender jalur secara dinamis.

### 3. Views (Isi Konten Halaman Bebas Gambar & Minimalis)
*   **`Home.vue`**
    Halaman utama (URL `/`). Memiliki teks sambutan *(Hero Text)* yang besar di tengah, fitur grid acara, dan di bagian paling bawah terdapat **Sitemap Visual** berbentuk *tree* daftar tautan web.
*   **`About.vue`**
    Halaman informasi (URL `/about`). Berisi kolom teks tebal minimalis untuk Visi & Misi tanpa gambar penunjang.
*   **`Contact.vue`**
    Halaman hubungi kami (URL `/contact`). Berisi informasi kontak, letak kantor, dan formulir interaktif di sisi kanannya.
*   **`Browse.vue`**
    Halaman induk (URL `/browse`). Bertugas sebagai wadah pembungkus (`parent-view`) dengan judul *header*, yang akan merender anak-anak tamunya (Event atau Category) di bawahnya.
*   **`EventList.vue`**
    (URL `/browse/events`). Menampilkan sekumpulan "kartu" daftar acara yang berisikan Tanggal, Kategori, Judul, dan tombol Detail.
*   **`EventDetail.vue`**
    (URL `/browse/events/:id`). Tampilan tunggal sebuah acara yang mencakup agenda, meta info, dan *sticky card* pendaftaran tiket acara di pojok kanan.
*   **`Category.vue`**
    (URL `/browse/category`). Halaman sekunder yang menampilkan kumpulan kotak kategori dengan ikon (*emoji*), hitungan event, dan *border hover*.
