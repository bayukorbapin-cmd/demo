# FA Tax and Accounting — Versi TRIAL (Single Perusahaan)

Aplikasi akuntansi & inventori (HTML statis, single-file, **tanpa fitur multi-perusahaan**), versi TRIAL dengan batas **maksimal 80 transaksi**.

## Login

| Peran | Kode | Password | Akses Menu |
|---|---|---|---|
| Admin (penuh) | `123` | `123` | Semua menu, termasuk Pengaturan |
| Staf/Demo | `demo` | `DEMO` | Semua menu **kecuali Pengaturan** |

- Login **Admin (123/123)** **tidak ditampilkan** di halaman login — hanya untuk Anda sendiri.
- Login **Staf/Demo (demo/DEMO)** ditampilkan di halaman login, supaya calon pengguna trial bisa langsung mencoba tanpa akses ke Pengaturan (tidak bisa ubah data perusahaan, akun penting, desain cetakan, akses pengguna, dsb).

## Batas Trial

Maksimal **80 transaksi** (dihitung dari seluruh modul: jurnal, kas/bank, penjualan, pembelian, piutang/utang, koperasi, payroll, aset tetap, stock opname, dll). Setelah 80 transaksi, aplikasi menampilkan peringatan dan menolak transaksi baru — data yang sudah ada tetap bisa dilihat/dicetak. Ada badge kuning di sidebar yang menunjukkan sisa kuota.

---

## 1. Upload ke GitHub

1. Buat repo baru di https://github.com/new (bisa Private).
2. Upload file-file ini: `index.html`, `README.md`, `vercel.json`, `.gitignore`, `supabase_setup.sql` (lewat **Add file → Upload files**, atau command line seperti biasa).

## 2. Deploy ke Vercel

1. Buka https://vercel.com → **Add New → Project → Import Git Repository** → pilih repo tadi.
2. Framework Preset: **Other**. Build Command & Output Directory: kosongkan.
3. Klik **Deploy**. Dapat URL seperti `https://nama-repo.vercel.app` — **inilah link yang dipakai/dibagikan**, bukan URL dashboard (`vercel.com/...`).
4. Setiap upload ulang `index.html` ke GitHub, Vercel otomatis redeploy.

## 3. Setup Supabase (untuk Cadangkan/Pulihkan ke Cloud)

1. Buat project baru di https://supabase.com/dashboard.
2. Buka **SQL Editor** → tempel isi `supabase_setup.sql` → **Run**.
3. Selesai — Project URL & Publishable Key sudah ditanam langsung di `index.html`, tidak perlu setting tambahan.

**Cara pakai:** menu **Pengaturan → Simpan & Cadangkan** (hanya terlihat oleh akun Admin, karena akun Demo tidak punya akses Pengaturan) → tombol **Cadangkan ke Cloud** / **Pulihkan dari Cloud**.

**Catatan:** karena aplikasi ini single-perusahaan (bukan multi-perusahaan), cadangan cloud memakai satu ID tetap (`trial-non-multi`) — cukup untuk kebutuhan trial. Kalau nanti dikembangkan jadi multi-pengguna/multi-perangkat dengan sinkronisasi realtime seperti versi multi-perusahaan, beri tahu saya untuk ditambahkan.

## Catatan Keamanan

- Password Admin (`123`) sengaja tidak ditampilkan di halaman login — cukup diketahui oleh Anda.
- Kebijakan akses tabel Supabase mengizinkan siapa saja yang tahu Project URL + Publishable Key untuk membaca/menulis — wajar untuk kebutuhan trial, bukan level keamanan produksi penuh.
