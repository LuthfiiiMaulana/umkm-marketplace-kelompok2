# UMKM Marketplace — Kelompok 2 (RPL)

Platform *e-commerce marketplace* berbasis web yang menjembatani pelaku Usaha Mikro, Kecil, dan Menengah (UMKM) lokal dengan konsumen secara digital. Sistem ini menyediakan akses terpisah untuk **Pembeli**, **Penjual (Mitra UMKM)**, dan **Super Admin**.

## Tech Stack
- **Frontend:** HTML5, CSS3, JavaScript (Desain UI/UX via Figma)
- **Backend:** PHP Native
- **Database:** MySQL Server (XAMPP)
- **Tools & Kolaborasi:** Google Antigravity, Git & GitHub

---

## Anggota Kelompok 2
1. **Michael Hafidz** — Lead Project Manager
2. **Muhammad Reihan Zafiandy** — System Analyst & Backend/Logic Developer
3. **Giatri Maharani Putri** — Lead UI/UX Designer & Frontend Developer
4. **Muhammad Luthfi Maulana** — , GitHub Coordinator & Backend Developer
5. **Andhika Hendra** — Frontend / Module Developer (Panel UMKM & Admin)
6. **Gerry Abiguel** — QA Tester & Technical Writer

---

## Rencana Kerja Proyek (Pertemuan 7 – Pertemuan 14)
- **Pertemuan 7:** Analisis kebutuhan (*requirements*) & setup repositori GitHub tim.
- **Pertemuan 8:** Perancangan sistem menggunakan UML (*Use Case*, *Activity*, dan *Sequence Diagram* pendekatan B-C-E).
- **Pertemuan 9:** Desain antarmuka UI/UX & *prototype* interaktif menggunakan Figma.
- **Pertemuan 10:** Setup database MySQL Server, koneksi backend, autentikasi 3 *role*, dan halaman katalog produk.
- **Pertemuan 11:** Pengembangan fitur keranjang belanja dan transaksi *checkout*.
- **Pertemuan 12:** Pengembangan dashboard Penjual UMKM dan panel Super Admin.
- **Pertemuan 13:** Pengujian sistem (*Black-Box Testing*) dan perbaikan *bug*.
- **Pertemuan 14:** Finalisasi dokumen laporan RPL dan pengumpulan proyek.

---

## Rencana Struktur Folder Lengkap
```text
umkm-marketplace-kelompok2/
├── assets/
│   ├── css/
│   │   ├── style.css              # Stylesheet global dari Design System Figma
│   │   └── dashboard.css          # Stylesheet khusus panel penjual & admin
│   ├── js/
│   │   └── main.js                # Script interaksi antarmuka & validasi
│   └── img/
│       ├── ui/                    # Ikon, logo, dan banner hasil ekspor Figma
│       └── produk/                # Folder penyimpanan foto produk yang di-upload UMKM
├── views/
│   ├── auth/
│   │   ├── login.php              # Halaman login terpadu (Admin, Penjual, Pembeli)
│   │   └── register.php           # Halaman pendaftaran akun pembeli & buka toko UMKM
│   ├── pembeli/
│   │   ├── index.php              # Halaman beranda & produk unggulan UMKM
│   │   ├── katalog.php            # Halaman daftar produk & filter kategori
│   │   ├── detail_produk.php      # Halaman detail informasi & stok produk
│   │   ├── keranjang.php          # Halaman keranjang belanja
│   │   ├── checkout.php           # Halaman pengisian alamat & konfirmasi pesanan
│   │   └── riwayat_pesanan.php    # Halaman status pengiriman pesanan pembeli
│   ├── penjual/
│   │   ├── dashboard.php          # Ringkasan penjualan toko UMKM
│   │   ├── kelola_produk.php      # Tampilan daftar, tambah, & edit produk UMKM
│   │   └── pesanan_masuk.php      # Daftar pesanan masuk & update status kirim
│   └── admin/
│       ├── dashboard.php          # Statistik keseluruhan platform marketplace
│       ├── kelola_umkm.php        # Verifikasi & manajemen akun mitra UMKM
│       ├── kelola_kategori.php    # Manajemen master kategori produk
│       └── semua_transaksi.php    # Monitoring seluruh transaksi pembeli
├── backend/
│   ├── config/
│   │   └── koneksi.php            # Konfigurasi koneksi PHP ke MySQL Server
│   ├── auth/
│   │   ├── proses_login.php       # Validasi login & redirect otomatis berdasarkan role
│   │   ├── proses_register.php    # Simpan data akun baru ke MySQL
│   │   └── logout.php             # Hapus session pengguna
│   ├── pembeli/
│   │   ├── proses_keranjang.php   # Logika tambah, ubah qty, & hapus item keranjang
│   │   └── proses_checkout.php    # Logika buat pesanan & potong stok otomatis
│   ├── penjual/
│   │   ├── crud_produk.php        # Proses tambah, edit, hapus produk & upload foto
│   │   └── update_status.php      # Proses ubah status pesanan (Diproses/Dikirim)
│   └── admin/
│       ├── crud_kategori.php      # Proses tambah, edit, hapus kategori produk
│       └── verifikasi_toko.php    # Proses aktivasi/nonaktif toko UMKM
├── database/
│   └── umkm_marketplace.sql       # File skema tabel MySQL Server (users, toko, produk, keranjang, pesanan)
├── index.php                      # File utama pengarah ke views/pembeli/index.php
└── README.md                      # Dokumentasi rencana & struktur proyek
