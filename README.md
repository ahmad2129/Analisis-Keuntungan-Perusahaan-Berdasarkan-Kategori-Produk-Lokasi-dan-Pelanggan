# 📊 Analisa Keuntungan Perusahaan Berdasarkan Kategori Produk, Lokasi, dan Pelanggan

## 📌 Overview Project
Project ini bertujuan untuk menganalisis sumber keuntungan dan kerugian perusahaan berdasarkan kategori produk, lokasi transaksi, dan pelanggan.

Analisis dilakukan menggunakan **Amazon dataset** yang berisi data transaksi periode 2011–2014, seperti tanggal pemesanan, lokasi pengiriman, kategori produk, nilai penjualan, kuantitas, dan keuntungan.

Melalui analisis ini diharapkan dapat diperoleh insight yang membantu perusahaan mengenali kategori yang merugi, kategori yang paling menguntungkan, serta lokasi dan pelanggan yang paling berpotensi.

## ❗ Problem Statement
Menurut analisis pasar (Statista dan 6Wresearch) yang dirangkum dalam artikel *Printer Market and Printing Volume Trend in Indonesia 2026*, pasar printer dan copier di Indonesia diproyeksikan tumbuh sekitar 2,4% pada 2026, mencerminkan pertumbuhan yang moderat di tengah tren transformasi digital.

> Sumber: [AdminKom – Printer Market and Printing Volume Trend in Indonesia 2026](https://adminkom.org/printer-market-and-printing-volume-trend-in-indonesia-2026/) (7 Oktober 2025)

Dengan menganalisis data transaksi, kita dapat mengetahui kategori produk mana yang benar-benar menguntungkan dan mana yang justru merugi. Insight dari analisis ini dapat membantu:

- Manajemen dalam menetapkan harga jual dan modal yang lebih tepat
- Tim produk dalam mengevaluasi kategori yang merugi
- Tim sales dalam menentukan lokasi dan pelanggan yang perlu diprioritaskan

## ❓ Business Question
Beberapa pertanyaan yang ingin dijawab dalam analisis ini antara lain:

1. Apakah terdapat transaksi kategori tertentu yang menghasilkan kerugian?
2. Kategori apa yang menghasilkan keuntungan terbesar?
3. Di mana lokasi dan siapa pelanggan yang membeli kategori dengan keuntungan terbesar?

## 📊 Dataset
- **Nama file:** `Amazon.xlsx`
- **Sumber:** [Google Drive](https://drive.google.com/drive/folders/1AWksosjsTfN-Y7sukK3GzkImtAqSpf_8)
- **Format:** Excel
- **Jumlah baris:** 3.203
- **Jumlah kolom:** 10

| Kolom | Deskripsi |
|---|---|
| Order ID | Kode unik untuk setiap transaksi |
| Order Date | Tanggal pelanggan melakukan pemesanan |
| Ship Date | Tanggal pesanan mulai dikirimkan |
| EmailID | Alamat email pelanggan |
| Geography | Lokasi pengiriman (negara, kota, negara bagian) |
| Category | Kategori produk yang dibeli |
| Product Name | Nama dan deskripsi detail produk |
| Sales | Total nilai penjualan produk |
| Quantity | Jumlah barang yang dibeli |
| Profit | Nilai keuntungan bersih dari penjualan produk |

## 🧹 Data Preparation
1. **Data Exploration:** tidak ditemukan inkonsistensi, missing value, maupun duplicate value, dan tipe data seluruh kolom sudah sesuai.
2. **Outlier:** pemeriksaan dengan metode IQR menemukan outlier pada Sales (11,5%), Quantity (2%), dan Profit (14,5%). Outlier ditangani dengan **capping** (Sales dan Profit) serta **transformasi log** (Quantity), dengan hasilnya disimpan pada kolom baru.
3. **Distribusi:** uji Shapiro-Wilk menunjukkan tidak ada kolom yang terdistribusi normal, sehingga uji statistik yang disarankan adalah Mann–Whitney, Wilcoxon signed-rank, atau Kruskal–Wallis.
4. **Kolom Modal:** dibuat dari Sales dikurangi Profit untuk mengetahui modal yang dibutuhkan pada setiap transaksi.

## 🔍 Insight dari Data

Pada transaksi yang merugi, kategori **Tables** mencatat kerugian terbesar (-5.956,67), disusul **Machines** (-5.589,13) dan **Bookcases** (-4.223,64), karena modal yang dikeluarkan lebih besar daripada nilai penjualannya. Di sisi lain, **Copiers** menjadi kategori dengan keuntungan terbesar (19.327,24) meskipun kuantitas terjualnya hanya 88 unit, jauh lebih sedikit dibandingkan kategori lain seperti Binders (1.868 unit), sehingga masih ada ruang untuk meningkatkan penjualannya. Keuntungan Copiers terpusat di **United States, Seattle, Washington** (8.290,44), dan pelanggan penyumbang keuntungan terbesar di lokasi tersebut adalah **satu pelanggan tertentu** yang berpotensi dijadikan mitra B2B. Perlu diingat bahwa data berasal dari tahun 2011–2014 sehingga kondisi saat ini mungkin sudah berbeda.

## 💡 Recommendation

Disarankan untuk **mengevaluasi harga pada kategori yang merugi, khususnya Tables**, dengan menekan modal dan meningkatkan nilai penjualan agar transaksi mencapai titik impas (break even) dalam waktu 4 bulan. Mengingat data berasal dari periode 2011–2014, dapat dipertimbangkan pula **mengevaluasi kembali kategori Copiers** dengan data terbaru untuk memastikan apakah kategori ini masih relevan di era digital. Apabila masih relevan, disarankan **memperluas hubungan B2B di Seattle, Washington** dengan pelanggan korporat dan instansi pemerintah, termasuk pelanggan dengan keuntungan terbesar, dengan target mendapatkan 3 klien B2B dalam waktu 3 bulan.

## 📈 Data Manipulation dan Analisis
Analisis dilakukan menggunakan Pandas dengan tahapan berikut:

- Filtering transaksi dengan Profit kurang dari 0, lalu agregasi kerugian, sales, dan modal per kategori (Top 5)
- Agregasi total keuntungan dan kuantitas per kategori (Top 5)
- Agregasi keuntungan kategori Copiers berdasarkan Geography (Top 5)
- Agregasi keuntungan Copiers berdasarkan EmailID pada lokasi dengan keuntungan terbesar

## 📊 Presentasi Project
Untuk melihat penjelasan lengkap dari project ini, silakan lihat slide presentasi berikut:

🔗 [Slide Presentasi](https://github.com/ahmad2129/Analisis-Keuntungan-Perusahaan-Berdasarkan-Kategori-Produk-Lokasi-dan-Pelanggan/blob/main/report/Presentasi%20Mini%20Project%20Python%201%20Ahmad%20Malik%20Ibrahim.pdf)

## 🛠 Tools yang Digunakan
- **Python** (Data Exploration, Data Cleaning, Data Manipulation, dan Analisis)
- **Pandas** dan **NumPy** (Pengolahan data)

## 👤 Author
**Ahmad Malik Ibrahim**
Lulusan kedokteran dengan minat pada statistik, analisis, dan matematika, yang sedang menargetkan karir sebagai data analis.
