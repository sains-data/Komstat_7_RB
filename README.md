# 🩸 Penerapan Metode Pembangkit Bilangan Acak untuk Pemodelan Umur Deteksi dan Asal Penyandang Thalassemia di Provinsi Lampung

## 🚀 Proyek Tugas Besar Komputasi Statistika (Kelompok 7 RB)

Proyek ini mengimplementasikan teknik simulasi berbasis Pembangkit Bilangan Acak Semu (PRNG) dan Metode Transformasi Invers untuk memodelkan dan mereplikasi pola distribusi dua variabel kunci pada penyandang Thalassemia di Provinsi Lampung: **Umur Saat Terdeteksi** (kontinu) dan **Asal Kabupaten/Kota** (diskrit).

Data sintetis ini (N=5.000 kasus) bertujuan untuk mengatasi keterbatasan data riil yang sensitif, menyediakan alternatif data untuk analisis skenario, perencanaan layanan kesehatan, dan studi epidemiologi lanjutan di Lampung.

---

## 👨‍💻 Anggota Tim

| NIM | Nama | 
| :--- | :--- | 
| 123450019 | Anadia Carana |
| 123450048 | Fadil Prasetyo Alfarizzi | 
| 123450064 | Muhammad Hanif Dzaky | 
| 123450077 | Wan Nashwa Alhasni Yuska | 

**Program Studi:** Sains Data

**Institusi:** Institut Teknologi Sumatera (ITERA) 

---

## 🛠️ Metode dan Implementasi Kunci

### 1. Data Sumber dan Karakteristik Empiris

Data primer dikumpulkan melalui kuesioner Google Form dari penyandang Thalassemia atau keluarganya.

| Variabel | Jenis | Karakteristik Utama (Data Asli) |
| :--- | :--- | :--- |
| **Umur Saat Terdeteksi** | Kuantitatif Kontinu | Distribusi **Miring ke Kanan** (*Positively Skewed*). Mayoritas terdeteksi usia dini (Median = 3 Tahun, Q3 = 6 Tahun, Max = 55 Tahun). |
| **Asal Kabupaten/Kota** | Kualitatif Diskrit (Kategori) | Sangat didominasi oleh kategori **Bandar Lampung** (46%). |

### 2. Pembangkit Bilangan Acak (RNG)

* **Algoritma:** **Linear Congruential Generator (LCG)** diimplementasikan secara manual dalam bahasa R untuk menghasilkan bilangan seragam U ~ U(0,1).
    * *Catatan:* LCG manual digunakan untuk ilustrasi, namun `runif()` bawaan R juga digunakan untuk simulasi yang lebih stabil.

### 3. Transformasi Distribusi (Inverse Transform Method)

Teknik ini mengubah bilangan acak $U \sim U(0,1)$ menjadi variabel yang diinginkan, sesuai dengan karakteristik data asli.

| Variabel Target | Metode Transformasi | Implementasi |
| :--- | :--- | :--- |
| **Umur (Kontinu)** | **Inverse Transform Empiris** | Pemetaan U ke **Kuantil Umur** berdasarkan Fungsi Distribusi Kumulatif Empiris (**CDF**) data asli.|
| **Asal Daerah (Diskrit)** | **Sampling Invers Diskrit** | Pencocokan U terhadap interval **Probabilitas Kumulatif** yang dihitung dari frekuensi relatif setiap wilayah. |

---

## 📈 Hasil Simulasi dan Validasi

Simulasi berhasil menghasilkan N=5.000 data sintetis yang divalidasi dengan membandingkan pola distribusi terhadap data observasi asli.

### A. Validasi Distribusi Umur

![Distribusi Umur Asli vs Simulasi](https://drive.google.com/file/d/1X2OwVz-K-VsJUxRFg3AzCJpipsbVbMjD/view?usp=sharing)
Metode Inverse Transform Empiris terbukti superior, menghasilkan distribusi simulasi yang sangat berimpit dengan pola *skewness* distribusi umur asli.



### B. Validasi Distribusi Asal Penyandang
![Distribusi Asal Penyandang Asli vs Simulasi](https://drive.google.com/file/d/1BPzNU8A75ysxSQr25IMywg_Q9dX-orCX/view?usp=sharing)

Teknik Sampling Invers Diskrit berhasil mengonservasi proporsi relatif kategori wilayah. Dominasi wilayah **Bandar Lampung** (proporsi tertinggi) di data simulasi terjaga.



---

## 💡 Kesimpulan dan Saran Praktis

### Kesimpulan 

1.  Model yang dihasilkan mampu merepresentasikan pola distribusi data riil, divalidasi melalui kecocokan kurva kepadatan umur dan proporsi kategori asal daerah.
2.  **Inverse Transform Empiris** adalah metode yang efektif untuk mensimulasikan variabel kontinu dengan bentuk distribusi non-standar (misalnya, *highly skewed*).

### Saran untuk Pengembangan Lanjutan

1.  **Penggunaan RNG Modern:** Untuk aplikasi praktis, gunakan generator bawaan R (`runif`) karena lebih stabil dan memiliki periode yang jauh lebih panjang dibandingkan LCG manual.
2.  **Penghalusan Kategori Langka:** Pertimbangkan agregasi wilayah atau penerapan **Penghalusan Probabilitas** (misalnya, Bayesian) untuk kategori wilayah dengan frekuensi sangat kecil (misalnya, hanya 1 kasus), guna meningkatkan stabilitas estimasi pada data langka.
3.  **Pengembangan Model:** Penelitian selanjutnya dapat mempertimbangkan pemodelan multivariat atau menguji metode pembangkitan lain (misalnya, *Acceptance-Rejection*).

---

## 📢 Poster Tugas Besar

![Poster Kelompok 7 RB](Tugas%20Besar/Poster_7_RB.jpeg)

