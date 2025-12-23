# IDX Financial Report Finder (Proxy)

Website **HTML + CSS + JavaScript** sederhana untuk **mencari dan mengunduh laporan keuangan emiten BEI/IDX**, khususnya untuk kebutuhan **tahun 2020 ke bawah** yang sering sulit diakses langsung dari browser (kendala **CORS** / request diblok).

Project ini memanggil endpoint IDX `ListedCompany/GetFinancialReport` melalui **proxy fetch**, sehingga halaman bisa berjalan tanpa backend.

---

## 🎯 Tujuan

Saya membuat tools ini karena saat ingin mencari laporan keuangan **tahun 2020 kebawah**, akses via browser sering terhambat:
- request API IDX terblokir **CORS**,
- UI resmi kadang tidak praktis untuk pencarian cepat per emiten/tahun,
- butuh cara cepat untuk mendapatkan link PDF/XLSX langsung.

Dengan project ini, kamu bisa:
- cari berdasarkan **Kode Emiten**
- pilih **Tahun**, **Periode** (audit / TW1 / TW2 / TW3 / tahunan)
- lihat **attachments** (PDF/XLSX/ZIP) dan klik untuk download
- **pagination** untuk menelusuri data lebih banyak
- UI aman untuk **mobile** (attachments dibuat accordion agar tidak merusak layout)

---

## ✨ Fitur

- ✅ 100% static: **cukup 1 file HTML**
- ✅ Responsive: desktop + mobile friendly
- ✅ Proxy fetch anti-CORS
- ✅ Filter: kode emiten, tahun, periode, report type, emiten type, sort order
- ✅ Pagination
- ✅ Attachments rapi (mobile accordion + file name clamp)

---

## 🔌 Sumber Data

Endpoint IDX:
- `https://www.idx.co.id/primary/ListedCompany/GetFinancialReport`

Project ini hanya menampilkan data yang dikembalikan endpoint tersebut.

---

## 🛡️ Proxy yang digunakan

Karena CORS, fetch dilakukan lewat proxy publik:

1) Cloudflare CORS Anywhere  
`https://cloudflare-cors-anywhere.queakchannel42.workers.dev/?` (URL IDX akan di-encode)

2) CodeTabs Proxy  
`https://api.codetabs.com/v1/proxy?quest=` (URL IDX raw)

> Catatan: proxy publik bisa down / limit sewaktu-waktu. Jika salah satu error, ganti pilihan proxy di UI.

---

## 🚀 Cara Pakai

### 1) Jalankan lokal
- Download / clone repo
- Buka `index.html`

Jika kamu ingin lebih aman (tanpa masalah file://), jalankan server lokal:

#### Python
```bash
python -m http.server 8000
