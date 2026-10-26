# 🔥 FINAL PROJECT (TUGAS BESAR)
## Praktikum Pemrograman Web 2026 — Teknik Informatika Universitas Lampung

Selamat datang di repositori pusat **Tugas Besar Praktikum Pemrograman Web** Laboratorium Komputer Teknik Informatika Universitas Lampung (`Praktikum-LabKom-TI-Unila`). Repositori ini menggunakan arsitektur terpusat (*monorepo*) yang dilengkapi dengan sistem otomatisasi **CI/CD (GitHub Actions)** untuk memvalidasi setiap pengumpulan kode dari masing-masing kelompok.

---

## 📌 Daftar Topik Sistem (6 Judul Utama)
Setiap kelompok wajib membangun **1 (satu) sistem secara *native*** (HTML, CSS, JavaScript, PHP Native, dan MySQL/MariaDB tanpa *framework* backend) berdasarkan salah satu dari 6 topik yang telah dipelajari:

| Kode | Topik / Judul Sistem | Deskripsi Singkat |
| :--- | :--- | :--- |
| **01** | *[Isi Judul Sistem 1]* | *[Deskripsi singkat sistem 1]* |
| **02** | *[Isi Judul Sistem 2]* | *[Deskripsi singkat sistem 2]* |
| **03** | *[Isi Judul Sistem 3]* | *[Deskripsi singkat sistem 3]* |
| **04** | *[Isi Judul Sistem 4]* | *[Deskripsi singkat sistem 4]* |
| **05** | *[Isi Judul Sistem 5]* | *[Deskripsi singkat sistem 5]* |
| **06** | *[Isi Judul Sistem 6]* | *[Deskripsi singkat sistem 6]* |

---

## 📂 Struktur Direktori Repositori
Seluruh kelompok bekerja di dalam direktori `kelompok/` pada folder kelompoknya masing-masing. **Dilarang keras** mengubah file di luar folder kelompok sendiri.

```text
TUBES_PRK_PEMWEB_2026/
├── .github/
│   ├── workflows/
│   │   └── pr-validation.yml       # Robot CI/CD (JANGAN DIUBAH)
│   └── pull_request_template.md    # Template PR (JANGAN DIUBAH)
├── kelompok/
│   ├── README.md                   # Petunjuk direktori kelompok (JANGAN DIUBAH)
│   ├── kelompok_01/                # Folder khusus Kelompok 01
│   │   ├── assets/
│   │   ├── config/
│   │   ├── database/               # Simpan file .sql di sini
│   │   ├── index.php
│   │   └── README.md               # Dokumentasi sistem Kelompok 01
│   ├── kelompok_02/                # Folder khusus Kelompok 02
│   └── ...
├── .gitignore
└── README.md                       # Dokumentasi utama (JANGAN DIUBAH)
```

---

## 🚀 Panduan Setup & Alur Kerja (Workflow) Praktikan

Ikuti langkah-langkah berikut secara berurutan agar kode kelompok Anda dapat tergabung (*merge*) ke repositori utama tanpa ditolak oleh sistem CI/CD:

### 1. Fork Repositori Utama
1. Buka halaman repositori utama: `https://github.com/Praktikum-LabKom-TI-Unila/TUBES_PRK_PEMWEB_2026`
2. Klik tombol **Fork** di pojok kanan atas untuk menyalin repositori ini ke akun GitHub perwakilan kelompok Anda.

### 2. Clone Repositori Hasil Fork ke Lokal
Buka Terminal / Git Bash di komputer Anda (di dalam folder `www` Laragon atau `htdocs` XAMPP), lalu jalankan:
```bash
git clone [https://github.com/](https://github.com/)<username-github-anda>/TUBES_PRK_PEMWEB_2026.git
cd TUBES_PRK_PEMWEB_2026
```

### 3. Tambahkan Remote `upstream` (Wajib)
Agar Anda selalu bisa menarik (*pull*) pembaruan terbaru dari repositori utama LabKom:
```bash
git remote add upstream [https://github.com/Praktikum-LabKom-TI-Unila/TUBES_PRK_PEMWEB_2026.git](https://github.com/Praktikum-LabKom-TI-Unila/TUBES_PRK_PEMWEB_2026.git)
git remote -v
```

### 4. Buat Folder Kelompok & Kerjakan Kode
1. Buat branch baru untuk pengerjaan fitur:
   ```bash
   git checkout -b feat/kelompok-01-setup
   ```
   *(Ganti `01` dengan nomor kelompok Anda).*
2. Masuk ke dalam folder `kelompok/` dan buat folder dengan format **`kelompok_XX`** (huruf kecil semua, dua digit angka):
   - ✅ **Contoh benar:** `kelompok/kelompok_01/`, `kelompok/kelompok_09/`, `kelompok/kelompok_12/`
   - ❌ **Contoh salah:** `kelompok/Kelompok_1/`, `kelompok/kelompok-01/`, `kelompok_01/` (di luar folder `kelompok`)

### 5. Commit & Push ke Repositori Fork Anda
Sebelum melakukan *commit*, pastikan hanya file di dalam folder `kelompok/kelompok_XX/` Anda yang berubah:
```bash
git status
git add kelompok/kelompok_01/
git commit -m "feat(kelompok_01): menambahkan fitur autentikasi dan struktur database"
git push origin feat/kelompok-01-setup
```

### 6. Lakukan Pull Request (PR) ke Repositori Utama
1. Buka repositori hasil *fork* di akun GitHub Anda, lalu klik tombol **Compare & pull request**.
2. Pastikan arah PR adalah:
   - **base repository:** `Praktikum-LabKom-TI-Unila/TUBES_PRK_PEMWEB_2026` (branch `main`)
   - **head repository:** `<username-anda>/TUBES_PRK_PEMWEB_2026` (branch fitur Anda)
3. Isi deskripsi Pull Request sesuai *template* yang muncul, lalu klik **Create pull request**.

---

## 🔄 Cara Sinkronisasi Repo Sebelum Push Berikutnya
Sebelum membuat Pull Request baru, pastikan repositori Anda sudah sinkron dengan repositori utama:
```bash
git checkout main
git pull upstream main
git push origin main
```

---

## 🤖 Aturan Validasi Otomatis (CI/CD Rules)
Setiap Pull Request yang masuk akan diperiksa secara otomatis oleh **GitHub Actions**. Tombol **Merge** akan terkunci otomatis apabila PR Anda melanggar salah satu dari 4 aturan berikut:

1. **Isolasi Direktori Ketat:**
   - PR **hanya boleh** berisi perubahan di dalam folder `kelompok/kelompok_XX/` milik kelompok Anda sendiri.
   - Mengubah file di *root* (`README.md`, `.gitignore`), folder `.github/`, atau `kelompok/README.md` akan membuat CI/CD **Gagal (❌)**.
2. **Satu PR = Satu Kelompok:**
   - Satu Pull Request tidak boleh menyentuh lebih dari satu folder `kelompok_XX` sekaligus.
3. **Batas Ukuran File (Maksimal 5 MB):**
   - Dilarang mengunggah file berukuran lebih dari **5 MB** per file (seperti video mentah, file `.zip` / `.rar`, atau *installer*).
4. **Bebas *Syntax Error* PHP (`PHP Linter`):**
   - Seluruh file `.php` yang Anda unggah akan diuji menggunakan *PHP 8.2 Linter* (`php -l`). Jika terdapat kesalahan sintaks (seperti kurang titik koma `;` atau kurung kurawal `{}` tidak tertutup), PR akan **ditolak otomatis**.

---

## 📞 Bantuan & Kendala Teknis
Jika mengalami kendala terkait *merge conflict* atau kegagalan CI/CD yang tidak dapat diselesaikan, silakan hubungi **Asisten Praktikum Pemrograman Web** dengan menyertakan tautan (*link*) Pull Request kelompok Anda.