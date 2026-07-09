# WS-13: Data Preprocessing

> **Bab 13 — Preprocessing & Persiapan Data untuk Analisis**

---

## Ringkasan Materi

### Data Refinement Pipeline

```
Raw Data → Cleaning → Transformation → Normalization → Processed Data → Analysis Ready
```

Setiap tahap memiliki tujuan berbeda. **Preprocessing bukan langkah teknis biasa** — setiap keputusan preprocessing adalah keputusan riset yang bisa mengubah kesimpulan.

### Empat Prinsip Preprocessing

| Prinsip | Deskripsi |
|---------|----------|
| **Consistency** | Metode sama untuk data yang sama |
| **Transparency** | Setiap langkah terdokumentasi |
| **Reproducibility** | Orang lain bisa mengulang dengan hasil sama |
| **Minimal Distortion** | Ubah sesedikit mungkin; jika normalisasi tidak perlu, jangan lakukan |

### Cleaning Triad

| Masalah | Strategi | Risiko |
|---------|---------|--------|
| **Missing values** | | |
| — Listwise deletion | Missing < 5%, random | Data loss |
| — Mean/median imputation | Sedikit missing, dist. normal | Mengurangi variabilitas |
| — Model-based imputation | Banyak missing, pola sistematis | Introduces dependency |
| — Flag & separate | Missing karena alasan substantif | Kompleksitas analisis |
| **Duplikat** | Identifikasi → verifikasi → hapus | False positive (data mirip ≠ duplikat) |
| **Error format** | Standardisasi tipe, encoding | Kehilangan informasi saat konversi |

### Normalisasi — Kapan & Metode Mana

| Metode | Formula | Output | Sensitif Outlier? |
|--------|---------|--------|-------------------|
| Min-max | (x-min)/(max-min) | [0, 1] | Ya |
| Z-score | (x-mean)/std | Unbounded | Lebih robust |
| Robust scaling | (x-median)/IQR | Unbounded | Paling robust |

**Kunci:** Parameter normalisasi harus dihitung dari **training set saja** — bukan seluruh data. Pelanggaran = **data leakage**.

### Data Leakage Prevention

Data leakage terjadi ketika informasi dari test set "bocor" ke preprocessing:
- Normalisasi parameter dari seluruh dataset ← **SALAH**
- Cross-validation dilakukan sebelum split ← **SALAH**
- Feature selection menggunakan label test set ← **SALAH**

### Jebakan Kognitif

1. "Preprocessing cuma teknis — tidak perlu detail" → bisa ubah kesimpulan
2. "Lebih banyak preprocessing = lebih bersih = lebih baik" → over-processing distorsi data
3. "Normalisasi selalu diperlukan" → belum tentu, tergantung metode analisis
4. "Imputation sama untuk semua situasi" → strategi harus sesuai konteks

---

## Template A.13 — Preprocessing Documentation Log

```
PREPROCESSING LOG

Dataset           : Respons kuesioner online Google Forms
                    mahasiswa Instagram Kebumen
Jumlah data awal  : 100 responden (sebelum cleaning)

Cleaning:
| Masalah | Jumlah Kasus | Penanganan | Justifikasi |
|---------|-------------|------------|-------------|
|Gagal attention check|4 dari 100|Listwise deletion|Jawaban tidak valid — asal isi|
|Flat response|2 dari 100|Listwise deletion|Terindikasi tidak membaca pertanyaan|
|Item tidak lengkap|     0       |      —     |Dicegah via Google Forms wajib isi|
|Duplikat|     0       |      —     |Tidak ditemukan|

Transformation:
| Transformasi | Variabel | Detail | Alasan |
|-------------|----------|--------|--------|
| Reverse scoring   | —           | Semua item sudah searah         | Tidak diperlukan                          |
| Agregasi skor     | Blok A–D    | Rata-rata per blok = skor faktor| Sederhanakan 14 item jadi 4 skor IV       |
| Encoding dikotomis| DV adopsi   | Ya=1, Tidak=0                   | Diperlukan untuk regresi logistik         |

Normalization:
  Metode    : Tidak diperlukan
  Alasan    : Korelasi Spearman berbasis ranking tidak sensitif terhadap skala absolut
  Parameter : —

Leakage Check:
  [ ] Parameter normalisasi dari training set saja
  [x] Tidak ada informasi test set dalam preprocessing
  [x] Cross-validation dilakukan setelah split

Jumlah data akhir : 94 responden valid
Script tersedia   : [x] Ya → path: ____ | [ ] Belum
```

---

## Latihan 1 — Cleaning Plan

Periksa dataset Anda (atau dataset contoh) dan dokumentasikan masalah yang ditemukan.

| Masalah | Jumlah Kasus | Penanganan | Justifikasi |
|---------|-------------|------------|-------------|
|Gagal attention check|4 dari 100 (4%)|Listwise deletion|Jawaban tidak dapat dipercaya|
|Flat response|2 dari 100 (2%)|Listwise deletion setelah verifikasi|Pola jawaban menunjukkan pengisian tidak sungguh-sungguh|
|Item tidak lengkap|0|—|Dicegah sejak awal dengan Google Forms|
|Duplikat|0|—|Tidak ditemukan|

**Jumlah data sebelum cleaning:** 100
**Jumlah data setelah cleaning:** 94
**Persentase data yang hilang/berubah:** 6%

---

## Latihan 2 — Normalisasi Decision

Tentukan apakah data Anda perlu normalisasi, dan jika ya, metode apa yang tepat.

| Variabel | Range Asli | Distribusi | Outlier? | Metode Normalisasi | Alasan |
|----------|-----------|-----------|----------|-------------------|--------|
|Skor kemudahan|1.0–5.0|Sedikit left-skewed|Tidak| Tidak perlu|Tidak perlu|
|Skor manfaat|1.0–5.0|Normal|Tidak|Tidak perlu|Sama|
|Skor risiko|1.0–5.0|Normal|Tidak|Tidak perlu|Sama|
|Skor sosial|1.0–5.0|Slightly right-skewed|Tidak|Tidak perlu|Sama|
|Adopsi 2FA|(DV)0 atau 1|Dikotomis|N/AE|ncoding 0/1|Diperlukan untuk regresi logistik|

**Apakah normalisasi diperlukan?** [ ] Ya / [ ] Tidak
**Justifikasi:**
> Untuk analisis Spearman, normalisasi tidak mengubah apapun karena Spearman hanya peduli urutan ranking. Over-preprocessing di sini tidak berbahaya tapi membuang langkah yang tidak perlu dan bisa membingungkan pembaca.
**Leakage check:**
- [ ] Parameter dihitung dari training set saja
- [ ] Normalisasi diterapkan setelah train-test split

---

## Latihan 3 — Preprocessing Report

Buat ringkasan preprocessing lengkap — dokumentasi yang cukup bagi orang lain untuk mereplikasi.

```
PREPROCESSING SUMMARY

1. Dataset: Respons kuesioner online Google Forms mahasiswa pengguna Instagram di Kebumen
2. Data awal: 100 records, 20 features (item kuesioner)
3. Cleaning:
   - Gagal attention check : 4 kasus → listwise deletion
   - Flat response         : 2 kasus → listwise deletion
   - Item tidak lengkap    : 0 kasus (dicegah Google Forms)
   - Duplikat              : 0 kasus
4. Transformation:
   - Agregasi skor per blok: rata-rata 3–4 item Likert
     per faktor → 4 skor IV
   - Encoding DV: Ya=1, Tidak=0 untuk regresi logistik
5. Normalisasi: Tidak diperlukan — Spearman berbasis ranking, tidak sensitif skala absolut
6. Data akhir: 94 records, 6 features (4 skor IV, 1 DV, 1 CV demografis)
7. Leakage check: [x] Lulus — tidak ada train-test split karena analisis korelasi, bukan prediktif
```

---

## Refleksi

> Apakah Anda pernah melakukan normalisasi "karena biasa dilakukan" tanpa mempertimbangkan apakah benar-benar diperlukan? Apa risiko over-preprocessing?

> Sebelumnya mungkin langsung normalisasi "karena biasa dilakukan." Tapi untuk Spearman, normalisasi tidak mengubah apapun karena hanya peduli urutan ranking. Over-preprocessing di sini tidak berbahaya tapi membuang langkah yang tidak perlu dan bisa membingungkan pembaca laporan.