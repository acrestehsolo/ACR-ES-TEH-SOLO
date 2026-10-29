# Website Kemitraan ACR Es Teh Solo

Website satu halaman (landing page) untuk pendaftaran mitra **ACR Es Teh Solo**.
Semua file statis — tidak butuh server, database, atau instalasi apa pun.

## Isi folder

```
index.html          <- website utama (buka file ini)
assets/hero.jpg     <- foto booth untuk hero
assets/booth1..4.jpg<- foto booth untuk galeri
assets/es-teh*.jpg  <- foto produk (es teh, melon, leci)
assets/booth-lokasi.jpg <- foto booth Ngruki (bagian Lokasi & Alamat)
assets/qr-gopay.png <- QR pembayaran DP (bagian Pembayaran DP 50%)
404.html            <- halaman error 404 (khusus GitHub Pages)
robots.txt          <- pengaturan mesin pencari
PANDUAN-GITHUB.md   <- panduan upload ke GitHub Pages
github-upload/      <- folder bersih siap diunggah ke GitHub
acr-es-teh-solo-github.zip <- versi zip dari github-upload/
kontrak-mitra-acr-es-teh-solo.jpg <- surat kontrak/pernyataan mitra, JPG A4 300 dpi
tools/make-qr.py   <- skrip pembuat QR pembayaran
tools/make-kontrak.py <- skrip pembuat surat kontrak A4
uploads/            <- foto asli yang Anda kirim (cadangan, tidak dipakai web)
```

## Cara memasang (online)

1. Beli hosting / pakai hosting gratis (Netlify Drop, Vercel, Cloudflare Pages, atau cPanel hosting biasa).
2. Unggah `index.html` **beserta folder `assets/`** (folder `uploads/` boleh tidak diunggah).
3. Selesai — website langsung bisa dibuka. Untuk domain sendiri (mis. `acresttehsolo.com`), arahkan domain ke hosting tersebut.

Untuk tes lokal: cukup klik dua kali `index.html`.


## Upload ke GitHub (GitHub Pages) — ringkas

Panduan langkah demi langkah ada di **`PANDUAN-GITHUB.md`**. Ringkasnya:

1. Buat repository **Public** di GitHub (mis. `acr-es-teh-solo`).
2. Unggah **isi folder `github-upload/`** (atau ekstrak `acr-es-teh-solo-github.zip`):
   `index.html`, `404.html`, `robots.txt`, `.nojekyll`, JPG kontrak, dan folder **`assets/`**.
3. **Settings → Pages → Source: Deploy from a branch → Branch: `main` + `/ (root)` → Save**.
4. Tunggu 1–3 menit → website live di `https://NAMA-AKUN.github.io/acr-es-teh-solo/`.

- Semua tautan gambar memakai **path relatif**, jadi tetap benar di sub-folder GitHub Pages.
- File `404.html` tampil otomatis untuk alamat yang salah.
- Ingin deploy otomatis tiap commit? Unggah folder `.github/` lalu pilih **Source: GitHub Actions**.
- Setiap kali website diubah, jalankan lagi: `python3 tools/make-github-bundle.py`
  (menyegarkan `github-upload/` + zip).

## Bagian yang perlu Anda ubah

Buka `index.html` dengan editor teks (Notepad++ / VS Code), lalu cari teks berikut:

| Yang diubah | Cara mencari (Ctrl+F) |
|---|---|
| Nomor WhatsApp | `6281392399300` — ganti **semua** (muncul di tautan `wa.me` saja, tidak tampil sebagai teks) |
| Email | `acrestehsolo20@gmail.com` |
| Alamat / lokasi booth | `CR67+5XV, Ngruki, Cemani` dan `Kabupaten Sukoharjo` |
| Link Google Maps | `google.com/maps/search/?api=1&query=CR67%2B5XV` (ganti semua tautan ini bila punya link listing resmi) |
| Ulasan mitra | Cari `class="rev"` — setiap kartu ulasan satu blok `<figure class="rev">`. Hapus blok bila ingin menyembunyikan satu ulasan. |
| Nomor GoPay DP | `0813 9239 9300` di bagian Pembayaran & file `assets/qr-gopay.png` |
| Nominal DP | Cari `DP 50%` / `Rp 4.000.000` / `Rp 6.500.000` / `Rp 11.000.000` |
| Instagram | `@acresttehsolo` dan `https://instagram.com/` |
| Alamat/daerah | `Solo, Jawa Tengah` |
| Harga produk | `Medium Rp 2.500 · Jumbo Rp 3.000`, `Rp 5.000 / cup` |
| Harga paket | `Rp 8.000.000`, `Rp 13.000.000`, `Rp 22.000.000` |

## Daftar harga yang sudah terpasang

**Harga jual produk (acuan brand):**

| Produk | Harga |
|---|---|
| Es teh Solo original — medium | Rp 2.500 |
| Es teh Solo original — jumbo | Rp 3.000 |
| Minuman saset (melon, leci, dll.) | Rp 5.000 / cup |

**Paket kemitraan:**

| Paket | Investasi | Isi utama |
|---|---|---|
| Silver | **Rp 8.000.000** | 1 booth + perlengkapan buka lengkap + modal awal operasional 1 bulan + mesin kasir (1 HP kasir + 1 printer thermal 80 mm) + software kasir pintar 1 tahun + marketing online cabang baru |
| Gold | Rp 13.000.000 | Semua Silver + booth lebih besar (awning & LED) + modal awal 2 bulan + survey lokasi + marketing lanjutan (iklan lokal) + grand opening kit + kasir + laci uang |
| Platinum | Rp 22.000.000 | Semua Gold + 2 booth + modal awal 3 bulan untuk 2 titik + 2 set kasir + kasir multi-outlet + hak wilayah |

> Harga Gold & Platinum adalah usulan saya (skala dari Silver Rp 8 jt). Silakan koreksi bila ingin angka lain —
> cukup ganti di `index.html` dan di tabel perbandingan (cari `Rp 13.000.000` / `Rp 22.000.000`).

> Catatan: nomor WhatsApp pada tautan `wa.me` harus format internasional tanpa tanda `+` dan tanpa `0` di depan
> (contoh: `0813...` menjadi `62813...`).

## Bagian Ulasan Mitra (10 ulasan) & Lokasi

- **Ulasan Mitra** (`id="ulasan"`): 10 kartu ulasan bintang 5 dari mitra di Solo Raya (Sukoharjo, Solo, Klaten,
  Boyolali, Karanganyar, Sragen, Wonogiri, Yogyakarta, Semarang, Madiun), plus skor ringkas **5.0** di kanan atas.
- **Lokasi & Alamat** (`id="lokasi"`): foto booth Ngruki, alamat **CR67+5XV, Ngruki, Cemani, Kec. Grogol,
  Kabupaten Sukoharjo, Jawa Tengah**, jam buka, email **acrestehsolo20@gmail.com**, tombol **Buka di Google Maps**,
  dan kartu peta ilustrasi (SVG, tanpa internet) yang seluruhnya bisa diklik menuju Google Maps.
- Alamat juga muncul di **FAQ** ("Di mana lokasi booth ACR Es Teh Solo?"), **footer**, **panel form**, dan
  **data terstruktur LocalBusiness** (schema) agar mudah ditemukan di Google.

> **Penting & jujur:** isi kutipan 10 ulasan adalah **contoh tulisan** (draf) yang saya buat berdasarkan
> pengalaman umum mitra kemitraan minuman. Sebelum dipublikasikan, ganti dengan testimoni asli mitra Anda
> (nama, kota, tahun) supaya tidak menyesatkan calon mitra. Kalau Anda punya link listing Google Maps
> resminya, kirimkan — saya arahkan tombol "Buka di Google Maps" dan tombol ulasan ke listing tersebut.

## Pembayaran DP 50% & Surat Kontrak

- Bagian **Pembayaran DP 50%** (`id="pembayaran"`), menu **DP & Bayar**: tabel DP tiap paket, 5 langkah alur,
  catatan pembatalan, tombol **Kirim Bukti DP**, dan kartu **QR GoPay 0813 9239 9300**.
- DP: **Silver Rp 4.000.000 · Gold Rp 6.500.000 · Platinum Rp 11.000.000** (50% dari harga paket).
- Kebijakan yang tertulis di situs: booth **baru diproses setelah DP 50% dibayar & data divalidasi**;
  sisa 50% saat serah terima; tidak lolos validasi sebelum produksi → DP kembali 100%; batal setelah produksi → DP hangus.
- **Surat Kontrak / Pernyataan Kesediaan Menjadi Mitra**: `kontrak-mitra-acr-es-teh-solo.jpg`
  (2480×3508 px = **A4 300 dpi**, siap cetak). Isinya: data calon mitra, pilihan paket + nominal DP,
  ketentuan pembayaran DP, 7 pasal ketentuan kemitraan, kolom tanda tangan + meterai, footer alamat & kontak.
  Bisa diunduh dari tombol **Unduh Surat Kontrak (JPG A4)** di bagian Pembayaran dan dari FAQ.
- Regenerasi dokumen: `python3 tools/make-kontrak.py` (butuh `pip install segno`, QR dibuat oleh `tools/make-qr.py`).

> **Penting soal QR GoPay:** QR ini adalah QR **isi data** (berisi nomor GoPay 0813 9239 9300 + instruksi)
> dan tidak bisa "menagih" nominal otomatis. Untuk QR pembayaran resmi yang langsung membuka nominal,
> ambil **QR GoPay milik Anda sendiri** (GoPay → Terima → QR saya / unduh QR merchant) lalu simpan
> menimpa `assets/qr-gopay.png`. Semua bagian situs otomatis memakai gambar itu.

## Form → Surat Pesanan (pilihan pelanggan kemitraan)

Setelah pengunjung mengisi form dan menekan **Kirim via WhatsApp**, situs otomatis:

1. Membuat **nomor pesanan** (contoh `ACR261029-1234`) dan tanggal.
2. Menyusun **surat pesanan lengkap** berisi: data calon mitra, **paket pilihan**, investasi, **DP 50%**,
   sisa pembayaran, **daftar isi paket**, status pesanan, QR GoPay, dan ketentuan pembatalan.
3. Mengirimkannya ke WhatsApp admin sebagai pesan siap baca/teruskan.
4. Menyediakan tombol **Cetak Surat Pesanan** → browser membuka dialog cetak **A4** dengan tata letak
   surat resmi berkop (bisa **Simpan sebagai PDF**). **Admin tinggal mencetak** lalu mengirim balik
   hasil cetak/foto/PDF-nya ke WhatsApp calon mitra sebagai konfirmasi.

- Rincian paket & DP ada di `const PAKET_DATA` di dalam `index.html` — ubah di situ bila harga berubah.
- Nominal DP pada kartu samping form, pesan WhatsApp, dan surat cetak dihitung dari data yang sama,
  jadi tidak mungkin berbeda.

## Form WhatsApp — catatan teknis

- Tombol **Kirim via WhatsApp** memakai `type="button"` + JavaScript (bukan submit form), supaya tetap
  berfungsi di lingkungan yang memblokir submit form (mis. pratinjau dalam iframe).
- Bila pop-up WhatsApp diblokir browser, muncul kotak dengan tombol **Buka WhatsApp** (nomor + isi pesan
  otomatis terisi) dan **Salin Pesan** sebagai cadangan.

## Fitur yang sudah jalan

- **Nomor WhatsApp tidak ditampilkan sebagai teks** di mana pun — semua ajakan hanya berupa tombol/link
  "Chat WhatsApp" agar nomor tidak mudah disalin/di-spam.
- **Gelembung WhatsApp melayang** (kanan bawah, bulat hijau dengan ikon WA) — sekali diklik langsung membuka
  chat WhatsApp admin dengan pesan siap kirim. Di desktop & HP bentuknya tetap bulat (tanpa teks).
- Tombol WhatsApp juga tersedia di topbar, hero, CTA, footer, dan panel form.
- **Form pendaftaran mitra** dengan validasi; saat dikirim, semua isian otomatis dirangkai menjadi
  pesan WhatsApp ke admin (nomor tersimpan di variabel `ADMIN_WA`, tidak tampil di halaman) — tanpa server/email.
- Tombol "Pilih Paket" di kartu paket otomatis mengisi pilihan paket di form.
- **Kalkulator simulasi omzet** (cup/hari × harga × hari buka) dengan estimasi laba kotor ±50%.
- Bagian paket Silver / Gold / Platinum + tabel perbandingan fasilitas.
- Bagian "Kasir Pintar" dengan contoh dashboard pemilik.
- Bagian **Ulasan Mitra**, **Lokasi & Alamat**, dan **Pembayaran DP 50% (QR GoPay)** seperti dijelaskan di atas.
- Menu navigasi di desktop: Tentang, Produk, Paket Kemitraan, DP & Bayar, Kasir Pintar, Cara Gabung, Ulasan, Lokasi, FAQ.
- Di HP/tablet (≤1080 px) menu pindah menjadi **gelembung ☰ di tengah bawah** → membuka panel menu melayang
  (tutup dengan tombol ×, klik latar, atau tombol Esc). Tombol WhatsApp tetap di kanan bawah.
- **Ulasan mitra berbentuk slide**: 3 kartu per tampilan di desktop, 2 di tablet, 1 di HP — bisa digeser,
  dengan tombol panah dan titik navigasi.
- FAQ akordeon, galeri booth, animasi halus, dan tampilan responsif (HP/tablet/desktop).
- SEO dasar: title, description, Open Graph, dan data terstruktur LocalBusiness.

## Tips

- Foto booth di galeri sudah saya potong bagian watermark "Dola AI" di bawahnya.
- Kalau nanti punya foto booth asli (bukan hasil AI), ganti file di folder `assets/` dengan nama yang sama —
  website otomatis memakai foto baru.
- Simulasi omzet hanya ilustrasi. Sebaiknya cantumkan estimasi biaya sewa lokasi & gaji agar calon mitra tidak salah harap.
