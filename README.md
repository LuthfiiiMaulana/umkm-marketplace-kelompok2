# UMKM Marketplace — Kelompok 2 (RPL)

Platform *e-commerce marketplace* berbasis web yang menjembatani pelaku Usaha Mikro, Kecil, dan Menengah (UMKM) lokal dengan konsumen secara digital. Sistem ini dibangun menggunakan arsitektur **MVC (Model-View-Controller)** dengan PHP Native untuk memisahkan logika bisnis, akses database, dan antarmuka secara terstruktur, serta menyediakan akses terpisah untuk **Pembeli**, **Penjual (Mitra UMKM)**, dan **Super Admin**.

## Tech Stack
- **Arsitektur:** MVC (Model-View-Controller) — PHP Native
- **Frontend:** HTML5, CSS3, JavaScript (Desain UI/UX via Figma)
- **Backend:** PHP 8.x (OOP / Procedural Terstruktur)
- **Database:** MySQL Server (XAMPP)
- **Tools & Kolaborasi:** Google Antigravity, Git & GitHub

---

## Anggota Kelompok 2
1. **Michael Hafidz** — Lead Project Manager
2. **Muhammad Reihan Zafiandy** — System Analyst & Backend/Logic Developer
3. **Giatri Maharani Putri** — Lead UI/UX Designer & Frontend Developer
4. **Muhammad Luthfi Maulana** — GitHub Coordinator & Backend Developer
5. **Andhika Hendra** — Frontend / Module Developer (Panel UMKM & Admin)
6. **Gerry Abiguel** — QA Tester & Technical Writer

---

## Rencana Kerja Proyek (Pertemuan 7 – Pertemuan 14)
- **Pertemuan 7:** Analisis kebutuhan (*requirements*) & setup repositori GitHub tim.
- **Pertemuan 8:** Perancangan sistem menggunakan UML (*Use Case*, *Activity*, dan *Sequence Diagram* pendekatan B-C-E).
- **Pertemuan 9:** Desain antarmuka UI/UX & *prototype* interaktif menggunakan Figma.
- **Pertemuan 10:** Setup database MySQL Server, arsitektur MVC, koneksi database, autentikasi 3 *role*, dan halaman katalog produk.
- **Pertemuan 11:** Pengembangan fitur detail produk, keranjang belanja, dan transaksi *checkout*.
- **Pertemuan 12:** Pengembangan dashboard Penjual UMKM dan panel Super Admin.
- **Pertemuan 13:** Pengujian sistem (*Black-Box Testing*) dan perbaikan *bug*.
- **Pertemuan 14:** Finalisasi dokumen laporan RPL dan pengumpulan proyek.

---

## Rencana Struktur Folder Lengkap (Arsitektur MVC)
```text
umkm-marketplace-kelompok2/
├── app/
│   ├── config/
│   │   ├── database.php           # Konfigurasi koneksi PHP ke MySQL Server
│   │   └── app.php                # Konfigurasi BASE_URL & konstanta global aplikasi
│   ├── core/
│   │   ├── Router.php             # Pengatur routing URL bersih ke Controller & Method
│   │   ├── Controller.php         # Base Controller (penghubung Model dan View)
│   │   └── Session.php            # Manajemen session, flash message, & proteksi role
│   ├── models/                    # Layer Model (Query & interaksi langsung ke tabel MySQL)
│   │   ├── UserModel.php          # Query tabel users (login, register, profil, verifikasi)
│   │   ├── TokoModel.php          # Query tabel toko_umkm (data toko & status mitra)
│   │   ├── KategoriModel.php      # Query tabel kategori produk
│   │   ├── ProdukModel.php        # Query tabel produk (katalog, search, filter, detail, stok)
│   │   ├── KeranjangModel.php     # Query tabel keranjang belanja per user
│   │   └── PesananModel.php       # Query tabel pesanan & detail_pesanan (transaksi & riwayat)
│   └── controllers/               # Layer Controller (Logika bisnis & pemrosesan request)
│       ├── AuthController.php     # Proses login, registrasi pembeli/UMKM, & logout
│       ├── HomeController.php     # Logika halaman beranda, katalog, filter, & detail produk
│       ├── PembeliController.php  # Logika keranjang, checkout, & riwayat pesanan pembeli
│       ├── PenjualController.php  # Logika dashboard toko, CRUD produk, & kelola pesanan masuk
│       └── AdminController.php    # Logika dashboard admin, verifikasi UMKM, kategori, & monitoring
├── views/                         # Layer View (Antarmuka pengguna berbasis komponen)
│   ├── layouts/                   # Komponen tampilan reusable agar konsisten & tidak duplikat kode
│   │   ├── header.php             # Tag <head>, pemanggilan CSS global, & judul halaman
│   │   ├── navbar.php             # Navigasi atas (search bar, menu kategori, ikon keranjang, profil)
│   │   ├── sidebar_panel.php      # Navigasi samping khusus dashboard Penjual & Super Admin
│   │   └── footer.php             # Bagian bawah halaman & pemanggilan script JS
│   ├── auth/
│   │   ├── login.php              # Halaman login terpadu (Admin, Penjual, Pembeli)
│   │   └── register.php           # Halaman pendaftaran akun pembeli & buka toko UMKM
│   ├── pembeli/
│   │   ├── index.php              # Halaman beranda, banner promo, & produk unggulan UMKM
│   │   ├── katalog.php            # Halaman daftar produk lengkap, pencarian, & filter kategori
│   │   ├── detail_produk.php      # Halaman detail produk (foto, harga, stok, info toko, ulasan)
│   │   ├── keranjang.php          # Halaman keranjang belanja & ubah kuantitas
│   │   ├── checkout.php           # Halaman pengisian alamat pengiriman & konfirmasi pesanan
│   │   └── riwayat_pesanan.php    # Halaman daftar transaksi & pelacakan status pesanan
│   ├── penjual/
│   │   ├── dashboard.php          # Ringkasan statistik penjualan & pendapatan toko UMKM
│   │   ├── kelola_produk.php      # Tabel daftar produk serta form tambah/edit produk UMKM
│   │   ├── pesanan_masuk.php      # Daftar pesanan pelanggan & tombol update status kirim
│   │   └── profil_toko.php        # Pengaturan informasi & deskripsi toko UMKM
│   └── admin/
│       ├── dashboard.php          # Statistik keseluruhan platform (total user, UMKM, omzet)
│       ├── kelola_umkm.php        # Verifikasi pendaftaran & manajemen status mitra UMKM
│       ├── kelola_kategori.php    # Manajemen master kategori produk marketplace
│       ├── kelola_user.php        # Manajemen data pengguna terdaftar
│       └── semua_transaksi.php    # Monitoring seluruh transaksi berjalan di platform
├── public/                        # Folder publik untuk seluruh aset statis (CSS, JS, Gambar)
│   ├── css/
│   │   ├── style.css              # Stylesheet utama pembeli (Design System Figma)
│   │   └── dashboard.css          # Stylesheet khusus panel Penjual & Super Admin
│   ├── js/
│   │   └── main.js                # Script interaksi UI, modal, validasi form, & hitung keranjang
│   └── img/
│       ├── ui/                    # Ikon, logo, dan banner hasil ekspor Figma
│       └── produk/                # Folder penyimpanan foto produk yang di-upload penjual UMKM
├── database/
│   └── umkm_marketplace.sql       # Skema database MySQL Server & data dummy awal
├── .htaccess                      # Aturan URL rewriting agar routing MVC rapi
├── index.php                      # Front Controller (titik masuk tunggal seluruh aplikasi)
└── README.md                      # Dokumentasi rencana & struktur proyek
