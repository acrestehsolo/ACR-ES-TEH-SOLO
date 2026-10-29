# Panduan Upload Website ke GitHub (GitHub Pages) — ACR Es Teh Solo

Website ini **100% file statis** (HTML + gambar), jadi bisa langsung dipublikasikan **gratis** lewat
GitHub Pages tanpa server, database, atau biaya hosting.

Hasil akhirnya berupa alamat seperti:

```
https://NAMA-AKUN.github.io/acr-es-teh-solo/
```

---

## Yang perlu diunggah (hanya ini)

```
index.html                          <- halaman utama website
404.html                            <- halaman "tidak ditemukan"
robots.txt                          <- pengaturan mesin pencari
.nojekyll                           <- agar GitHub tidak memproses file
kontrak-mitra-acr-es-teh-solo.jpg   <- surat kontrak A4 (untuk tombol unduh)
assets/                             <- semua foto, QR, dan gambar
   ├─ hero.jpg
   ├─ booth1.jpg … booth4.jpg
   ├─ booth-lokasi.jpg
   ├─ es-teh.jpg, es-teh-melon.jpg, es-teh-leci.jpg
   └─ qr-gopay.png
```

**Jangan diunggah** (file besar & tidak dipakai website):
`uploads/`, `_arsip/`, `tools/`, `github-upload/`.

> Semua gambar dipakai dengan alamat **relatif** (`assets/hero.jpg`), jadi website tetap tampil benar
> meskipun berada di sub-folder seperti `.../acr-es-teh-solo/`. Tidak perlu diubah apa pun.

---

# CARA 1 — Lewat browser (tanpa install apa pun) ⭐ paling mudah

## 1. Buat akun GitHub
Buka <https://github.com/signup> → daftar dengan email (gratis).

## 2. Buat repository baru
1. Buka <https://github.com/new>
2. **Repository name**: `acr-es-teh-solo` (boleh nama lain, tanpa spasi)
3. Pilih **Public** (wajib untuk GitHub Pages gratis)
4. **Jangan** centang "Add a README file"
5. Klik **Create repository**

## 3. Unggah file
1. Di halaman repository kosong, klik tulisan **“uploading an existing file”**
   (atau buka `https://github.com/NAMA-AKUN/acr-es-teh-solo/upload/main`)
2. Buka folder **`github-upload`** di komputer, lalu **seret semua isinya** ke area upload:
   - `index.html`, `404.html`, `robots.txt`, `.nojekyll`, file JPG kontrak, dan **folder `assets`**
   - Pastikan **folder `assets` ikut terseret** (bukan hanya isinya)
3. Tunggu semua file selesai diunggah, lalu klik **Commit changes**

> Cara paling aman: seret seluruh isi folder `github-upload` sekaligus, jangan pilih satu-satu.
> Kalau `.nojekyll` tidak muncul di daftar file, tidak masalah — website tetap jalan.

## 4. Aktifkan GitHub Pages
1. Masuk ke tab **Settings** (roda gigi di atas repository)
2. Menu kiri → **Pages**
3. Bagian **Build and deployment**:
   - **Source**: `Deploy from a branch`
   - **Branch**: `main` dan folder **`/ (root)`**
4. Klik **Save**
5. Tunggu **1–3 menit**, lalu refresh halaman Settings → Pages.
   Akan muncul tulisan: *“Your site is live at https://NAMA-AKUN.github.io/acr-es-teh-solo/”*

## 5. Buka websitenya
Buka alamat tersebut di HP dan komputer. Selesai ✅

---

# CARA 2 — Lewat Git di komputer (untuk yang sudah biasa)

```bash
# 1. masuk ke folder website
cd github-upload

# 2. inisialisasi repository
git init
git add .
git commit -m "Website kemitraan ACR Es Teh Solo"

# 3. hubungkan ke GitHub (ganti NAMA-AKUN)
git branch -M main
git remote add origin https://github.com/NAMA-AKUN/acr-es-teh-solo.git

# 4. kirim
git push -u origin main
```

Lalu aktifkan Pages seperti langkah 4 di Cara 1.

---

# Cara memperbarui isi website nanti

1. Buka repository → klik file `index.html` → ikon **pensil** (Edit) → ubah teks → **Commit changes**.
   GitHub Pages otomatis memperbarui website dalam ±1 menit.
2. Untuk mengganti foto: buka folder `assets` → klik gambar → **Delete** → unggah foto baru
   **dengan nama file yang sama** (mis. `hero.jpg`) agar tidak perlu mengubah kode.

---

# (Opsional) Deploy otomatis dengan GitHub Actions

Repository ini sudah berisi workflow `deploy-pages.yml`. Caranya:

1. Upload juga folder **`.github`** (berisi `workflows/deploy-pages.yml`) ke repository.
2. **Settings → Pages → Source** pilih **`GitHub Actions`** (bukan "Deploy from a branch").
3. Setiap kali Anda mengubah file dan **Commit**, website otomatis dipublikasikan ulang
   (lihat progres di tab **Actions**).

Gunakan salah satu saja: **Cara 1 (branch)** *atau* **Actions** — jangan keduanya.

---

# (Opsional) Pakai domain sendiri, mis. `acresttehsolo.com`

1. Beli domain (Niagahoster, Domainesia, Cloudflare, Namecheap, dll.).
2. Di GitHub: **Settings → Pages → Custom domain** → isi `acresttehsolo.com` → **Save**.
3. Di tempat pembelian domain, atur DNS:
   - **A record** `@` → `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - **CNAME** `www` → `NAMA-AKUN.github.io`
4. Tunggu 5 menit–24 jam, lalu centang **Enforce HTTPS** di Settings → Pages.

---

# Jika ada masalah

| Gejala | Penyebab & solusi |
|---|---|
| Halaman **404** setelah diaktifkan | Tunggu 1–3 menit lalu refresh. Pastikan Source = `main` + `/ (root)` dan file `index.html` ada di halaman utama repository (bukan di dalam folder). |
| Website tampil tapi **gambar kosong** | Folder `assets` belum terunggah, atau nama file berubah. Nama file di GitHub **peka huruf besar/kecil** (`Hero.jpg` ≠ `hero.jpg`). Unggah ulang folder `assets` apa adanya. |
| Muncul **tulisan kode**, bukan website | File tidak bernama `index.html` (mis. `Index.html` atau `index.html.txt`). Ganti nama dengan benar. |
| Tombol WhatsApp tidak membuka apa pun | Normal di pratinjau tanpa internet. Coba buka lewat browser HP/komputer biasa. |
| Ingin website **privat** | GitHub Pages gratis hanya untuk repository **Public**. Untuk privat perlu GitHub Pro, atau pakai hosting lain (Netlify/Cloudflare Pages). |
| Perubahan tidak muncul | Tekan **Ctrl + Shift + R** (hard refresh). Cek juga tab **Actions** bila memakai workflow. |

---

# Ringkasan file di repository

| File / folder | Fungsi |
|---|---|
| `index.html` | Seluruh website (halaman kemitraan, form, DP 50%, ulasan, kontrak) |
| `404.html` | Halaman yang muncul jika alamat salah |
| `assets/` | Foto booth, produk, QR GoPay, dan gambar pendukung |
| `kontrak-mitra-acr-es-teh-solo.jpg` | Surat kontrak A4 yang bisa diunduh pengunjung |
| `robots.txt`, `.nojekyll` | Pengaturan teknis GitHub Pages |
| `.github/workflows/deploy-pages.yml` | Deploy otomatis (opsional) |
| `tools/make-github-bundle.py` | Membuat ulang folder `github-upload` + zip |
| `PANDUAN-GITHUB.md` | Panduan ini |
| `README.md` | Panduan umum website + daftar teks yang bisa diedit |

---

## Membuat ulang paket unggahan

Setiap kali `index.html` atau foto diubah, jalankan:

```bash
python3 tools/make-github-bundle.py
```

Perintah ini menyegarkan folder **`github-upload/`** dan file **`acr-es-teh-solo-github.zip`**
sehingga isinya selalu sama dengan website terbaru.
