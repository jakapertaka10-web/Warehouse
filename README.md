# WMS Mattress

Warehouse Management System prototype untuk pengelolaan bahan baku pembuatan mattress atau kasur.

<p align="center">
  <img src="assets/logo.svg" alt="WMS Mattress Logo" width="120" />
</p>

## Overview

Aplikasi membantu tim warehouse mengelola:
- material master
- supplier master
- lokasi gudang
- receiving barang
- kualitas (QC)
- putaway
- issuing
- stock monitoring
- inventory movement
- opname
- report ringkas

## Struktur repository

```text
WMS-MATTRESS/
├── app.js
├── dashboard.js
├── data.js
├── favicon.svg
├── .gitignore
├── index.html
├── issuing.js
├── locations.js
├── logo.svg
├── materials.js
├── movement.js
├── opname.js
├── putaway.js
├── qc.js
├── receiving.js
├── reports.js
├── stock.js
├── style.css
├── suppliers.js
├── utils.js
├── .nojekyll
├── README.md
├── assets/
│   ├── favicon.svg
│   ├── landing-preview.svg
│   └── logo.svg
├── css/
│   └── style.css
├── js/
│   ├── app.js
│   ├── dashboard.js
│   ├── data.js
│   ├── issuing.js
│   ├── locations.js
│   ├── materials.js
│   ├── movement.js
│   ├── opname.js
│   ├── putaway.js
│   ├── qc.js
│   ├── receiving.js
│   ├── reports.js
│   ├── stock.js
│   ├── suppliers.js
│   └── utils.js
└── server.js
```

Berkas frontend di root menjadi entrypoint untuk GitHub Pages. CSS root memuat stylesheet yang sudah ada di `css/style.css`, sedangkan skrip root meneruskan pemuatan skrip sumber di `js/`. Berkas sumber asli tetap dipertahankan.

## Demo / preview

Berikut gambaran dashboard yang sudah dibuat:

![Landing Preview](assets/landing-preview.svg)

## Cara menjalankan

Versi prototype berjalan tanpa Node.js, npm, API, database server, atau localhost.

Cukup buka file berikut di browser:

```text
file:///C:/WMS-MATTRESS/index.html
```

Atau buka langsung file `index.html` dari File Explorer/Windows Explorer.

## Catatan penting

- Aplikasi prototype memakai `localStorage`
- Data disimpan dengan key `wms_mattress_db`
- Data tidak akan hilang saat refresh halaman
- `server.js` hanya disiapkan sebagai placeholder backend untuk tahap 2
- `server.js` tidak diperlukan agar prototype bisa dijalankan

## Local storage behavior

- Database otomatis dibuat saat pertama kali aplikasi dibuka
- Jika data sudah ada, aplikasi akan memuat data lama dan tidak overwrite
- `localStorage.clear()` tidak digunakan
- Perubahan disimpan langsung saat data diubah

## Fitur utama

- Dashboard management
- Master material
- Master supplier
- Master lokasi gudang
- Receiving / GR
- QC
- Putaway
- Issuing
- Stock
- Movement log
- Opname
- Reports
- Ringkasan inventory aktual dan pemantauan receiving/issuing per periode
- Grafik stok aktual terhadap Minimum Stock dan Maximum Stock
- Alert dan rekomendasi rule-based berdasarkan kondisi persediaan

## Minimum–Maximum Stock

- Minimum Stock wajib berupa angka nol atau lebih; Maximum Stock dapat dikosongkan sampai batasnya diketahui.
- Status `NORMAL`, `BELOW MINIMUM`, dan `ABOVE MAXIMUM` hanya ditentukan jika kedua batas persediaan valid.
- Data material lama tanpa Maximum Stock tetap dipertahankan dan ditampilkan sebagai `PARAMETER INCOMPLETE`; aplikasi tidak mengisi batas buatan.
- Stockout dikenali dari stok aktual nol. Rekomendasi hanya memberi saran dan tidak mengubah stok atau membuat pengadaan otomatis.
- Prioritas rekomendasi: `HIGH` untuk stockout, `MEDIUM` untuk stok di luar batas atau parameter belum lengkap, dan `LOW` untuk pemantauan rutin pada stok normal.
- Filter dashboard menerapkan periode harian, mingguan, atau bulanan serta material dan kategori pada monitoring pergerakan.

## Roadmap backend (tahap 2)

Untuk pengembangan ke depan, project ini siap diperluas ke arsitektur:

```text
Frontend
  ↓
server.js / Express
  ↓
Supabase PostgreSQL
```

## GitHub Pages / upload repo

Folder ini sudah dibuat dalam satu direktori yang siap diupload ke GitHub. Untuk GitHub Pages, cukup push folder ini ke repository dan aktifkan Pages sebagai static site.

## License

Project ini dibuat untuk kebutuhan prototype internal dan dapat dikembangkan lebih lanjut sesuai kebutuhan bisnis.
