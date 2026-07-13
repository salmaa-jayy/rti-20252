# Laporan Penelitian

**Judul:** Analisis Faktor Persepsi yang Berhubungan dengan Rendahnya Adopsi Autentikasi Dua Faktor (2FA) pada Mahasiswa Pengguna Instagram di Kebumen

**Peneliti:** Salma Zaidah  
**Program Studi:** Inforatika/Ilmu Komputer Universitas Putra Bangsa Kebumen  
**Mata Kuliah:** Riset Teknologi Informasi  
**Target Publikasi:** Sinta 3–4 (Jurnal JUSTIN atau Jurnal Sistem Informasi Bisnis)  
**Status Penelitian:** Tahap 1–2 selesai (proposal & setup); Tahap 3–5 menunggu pengumpulan data ([../09-docs/rencana-penelitian.md](../09-docs/rencana-penelitian.md))

---

## 1. Ringkasan Eksekutif

Penelitian ini merancang dan merencanakan evaluasi empiris terhadap **faktor-faktor persepsi** yang berhubungan dengan rendahnya adopsi **autentikasi dua faktor (2FA)** di kalangan mahasiswa pengguna Instagram di Kebumen. Studi terdahulu (Farida et al., 2024) menunjukkan hanya **39% pengguna Instagram Indonesia** yang mengaktifkan 2FA, namun tidak ada penelitian yang menjelaskan *mengapa* angka tersebut rendah khususnya di kalangan mahasiswa.

Penelitian ini mengisi gap tersebut dengan menggunakan **instrumen Likert bertingkat** (bukan instrumen biner ya/tidak seperti studi terdahulu) untuk mengukur empat faktor persepsi sebagai IV kemudahan, manfaat, kesadaran risiko, dan pengaruh sosial terhadap adopsi 2FA sebagai DV, dianalisis menggunakan **korelasi Spearman** dan **regresi logistik** pada target **100 responden mahasiswa Kebumen**.

**Prediksi hasil berdasarkan TAM (Davis, 1989):**

- Persepsi kemudahan diprediksi sebagai faktor paling signifikan (r ≥ 0.3, p < 0.05)
- Persepsi manfaat diprediksi signifikan sebagai faktor kedua
- Kesadaran risiko dan pengaruh sosial diprediksi tidak signifikan (optimism bias)

Seluruh dokumen perencanaan, worksheet WS-01 s.d. WS-16, instrumen kuesioner, dan skrip analisis tersedia di repository ini (lihat §7 Lampiran untuk peta artefak).

---

## 2. Latar Belakang dan Rumusan Masalah

### 2.1 Latar Belakang

Platform media sosial Instagram telah menjadi bagian tak terpisahkan dari kehidupan mahasiswa di Indonesia. Dengan **88,86 juta pengguna aktif** pada awal 2024, Instagram menjadi salah satu platform dengan potensi risiko keamanan informasi paling besar mulai dari peretasan akun, pencurian identitas, hingga penyalahgunaan data pribadi.

Fitur autentikasi dua faktor (2FA) tersedia gratis di Instagram sebagai lapisan keamanan tambahan. Namun studi Farida et al. (2024) menunjukkan hanya **39% pengguna** yang mengaktifkannya. Ironisnya, tidak ada studi yang menjelaskan *mengapa* angka adopsi tersebut rendah seluruh studi terdahulu hanya menggunakan instrumen biner ya/tidak yang tidak mampu mengidentifikasi faktor penyebab secara spesifik.

### 2.2 Rumusan Masalah

1. Faktor persepsi apa saja yang secara signifikan berhubungan dengan rendahnya adopsi 2FA pada mahasiswa pengguna Instagram di Kebumen?
2. Di antara faktor kemudahan, manfaat, kesadaran risiko, dan pengaruh sosial mana yang paling dominan memprediksi adopsi 2FA?
3. Apakah temuan ini konsisten dengan prediksi Technology Acceptance Model (TAM)?

### 2.3 Tujuan Penelitian

Detail tujuan & kontribusi: lihat [../01-proposal/proposal-penelitian.docx](../01-proposal/proposal-penelitian.docx) Bagian D dan E, serta [../09-docs/ws-04-rq-hypothesis.md](../09-docs/ws-04-rq-hypothesis.md).

---

## 3. Metodologi dan Pelaksanaan

Penelitian dilaksanakan dalam 5 tahap. Bagian ini merangkum perencanaan dan pelaksanaan setiap tahap; detail lengkap ada pada dokumen `09-docs/` yang dirujuk.

### 3.1 Tahap 1 — Proposal & Desain Penelitian

**Status: Selesai.** Dirancang keseluruhan framework penelitian: identifikasi masalah (WS-01–02), pemetaan literatur dan gap (WS-03), perumusan RQ dan hipotesis (WS-04), operasionalisasi variabel IV/DV/CV (WS-05), mapping ke arsitektur sistem (WS-06), desain eksperimen lengkap dengan threat analysis (WS-07), dan integration checklist (WS-08) dengan skor 10/12.

**Keputusan desain utama:**
- Paradigma: **positivis** pengukuran kuantitatif dengan instrumen Likert
- IV: 4 faktor persepsi (kemudahan, manfaat, kesadaran risiko, pengaruh sosial) — masing-masing 3–4 item Likert 1–5
- DV: adopsi 2FA kombinasi dikotomis (aktif/tidak) + skor konsistensi Likert
- CV: usia & program studi dikontrol di tahap analisis via segmentasi
- Baseline: Farida et al. (2024) instrumen biner, 39% adopsi
- Analisis: korelasi Spearman + regresi logistik, threshold p < 0.05, effect size r ≥ 0.3

Detail: [../09-docs/](../09-docs/), proposal lengkap: [../01-proposal/proposal-penelitian.docx](../01-proposal/proposal-penelitian.docx).

### 3.2 Tahap 2 — Setup Eksperimen & Validasi

**Status: Selesai.** Dirancang dokumentasi environment Python (WS-09), execution plan 7 run termasuk 3 robustness check dengan seed berbeda (WS-10), dan data validation checklist lengkap (WS-11).

**Keputusan teknis:**
- Environment: Python 3.10+, Jupyter Notebook, pandas + scipy + statsmodels + pingouin + seaborn
- Instrumen: Google Forms dengan 22 item total (14 Likert IV, 2 DV, 4 screening, 2 attention check)
- Cleaning: filter responden gagal attention check + flat response
- Normalisasi: **tidak diperlukan** — Spearman berbasis ranking, tidak sensitif skala absolut
- Random seed: 42 (ditetapkan di Python dan NumPy)

Catatan: validasi instrumen (Cronbach's Alpha ≥ 0.7) akan dilakukan pada pilot test 15–20 responden awal sebelum penyebaran penuh.

Detail: [../09-docs/ws-09-experiment-setup.md](../09-docs/ws-09-experiment-setup.md), kode: [../05-kode/](../05-kode/).

### 3.3 Tahap 3 — Pengumpulan Data

**Status: Belum dimulai.** Kuesioner Google Forms dengan 22 item akan disebarkan ke **100 mahasiswa** aktif pengguna Instagram berusia 18–25 tahun di Kebumen, lintas minimal 4 program studi (TI, ekonomi, hukum, kesehatan).

**Rencana penyebaran:**
- Platform: Google Forms, disebarkan via WhatsApp ke grup mahasiswa lintas jurusan
- Durasi: target 2 minggu penyebaran
- Filter: responden wajib tahu fitur 2FA Instagram (screening awal)
- Quality control: 2 attention check question tersebar di tengah kuesioner

Target: minimal **94 responden valid** setelah filter attention check dan flat response.

### 3.4 Tahap 4 — Analisis Data

**Status: Menunggu data.** Pipeline analisis Python sudah dirancang dan siap dijalankan. Urutan eksekusi: `01_data_cleaning.ipynb` → `02_reliability.ipynb` → `03_descriptive.ipynb` → `04_correlation.ipynb` → `05_regression.ipynb` → `06_visualization.ipynb`.

Output yang diharapkan: 4 tabel CSV dan 3 figure PNG di [../06-output/](../06-output/). Detail: [../09-docs/ws-12-result-presentation.md](../09-docs/ws-12-result-presentation.md) dan [../09-docs/ws-14-analysis-interpretation.md](../09-docs/ws-14-analysis-interpretation.md).

### 3.5 Tahap 5 — Penulisan & Presentasi

**Status: Draf awal selesai, menunggu data nyata.** Outline paper IMRAD, consistency matrix, dan writing quality check sudah selesai (WS-15). Defense preparation sheet dengan 11 slide 15 menit dan anticipatory Q&A 5 pertanyaan sudah disiapkan (WS-16).

Bagian yang masih perlu dilengkapi setelah data terkumpul:
1. Update angka simulasi di Hasil & Analisis dengan hasil nyata
2. Pemindahan naskah ke template jurnal tujuan
3. Revisi berdasarkan feedback dosen/reviewer

Detail: [../07-manuskrip/](../07-manuskrip/), [../09-docs/ws-15-scientific-writing.md](../09-docs/ws-15-scientific-writing.md).

---

## 4. Hasil (Simulasi — akan diupdate setelah data terkumpul)

### 4.1 Statistik Deskriptif

| Faktor IV | Mean | Std | Median | n |
|-----------|------|-----|--------|---|
| Kemudahan 2FA | 3.82 | 0.71 | 4.00 | 94 |
| Manfaat 2FA | 3.91 | 0.68 | 4.00 | 94 |
| Kesadaran risiko | 3.54 | 0.83 | 3.67 | 94 |
| Pengaruh sosial | 3.21 | 0.92 | 3.33 | 94 |

% adopsi 2FA aktif: ~41% (39 dari 94 responden)

### 4.2 Korelasi Spearman

| Faktor IV | r (mean±std) | p-value | Signifikan? |
|-----------|--------------|---------|-------------|
| Kemudahan 2FA | 0.41 ± 0.04 | 0.003 | ✅ Ya |
| Manfaat 2FA | 0.38 ± 0.05 | 0.008 | ✅ Ya |
| Kesadaran risiko | 0.29 ± 0.06 | 0.074 | ❌ Tidak |
| Pengaruh sosial | 0.24 ± 0.07 | 0.118 | ❌ Tidak |

> ⚠️ Angka di atas adalah simulasi berdasarkan prediksi TAM — akan diupdate dengan hasil nyata.

### 4.3 Temuan Utama (Prediksi)

- Mitigasi melalui edukasi **harus fokus pada kemudahan dan manfaat** — bukan hanya kampanye risiko
- Kesadaran risiko tidak cukup mendorong adopsi (kemungkinan: **optimism bias**)
- Pengaruh sosial tidak signifikan keputusan mengaktifkan 2FA bersifat individual
- Konsisten dengan prediksi TAM (Davis, 1989)

---

## 5. Kendala dan Catatan

| Kendala | Dampak | Mitigasi |
|---------|--------|----------|
| Data self-reported responden mungkin menjawab "seharusnya" bukan kondisi nyata | Overestimasi kesadaran | Kuesioner anonim + attention check |
| Sampel terbatas 94 mahasiswa Kebumen | Tidak bisa digeneralisasi nasional | Akui sebagai limitasi; rekomendasikan replikasi |
| n=94 mungkin underpowered untuk efek kecil (r < 0.3) | Risiko Type II error | Power analysis; laporkan CI selain p-value |
| Belum ada instrumen tervalidasi untuk konteks adopsi 2FA IG Indonesia | Perlu validasi Cronbach's Alpha dulu | Pilot test 15–20 responden sebelum penyebaran penuh |

---

## 6. Kesimpulan

Penelitian ini telah menyelesaikan tahap perancangan secara komprehensif dari identifikasi masalah, pemetaan literatur, perumusan RQ dan hipotesis, hingga desain eksperimen dan persiapan presentasi. Kebaruan utama terletak pada **penggunaan instrumen Likert bertingkat** sebagai perbaikan metodologis dari studi terdahulu yang hanya menggunakan instrumen biner, dan **fokus pada identifikasi faktor penyebab** bukan sekadar pengukuran persentase adopsi.

Setelah data terkumpul, temuan diharapkan memberikan **rekomendasi edukasi keamanan digital yang operasional** berbasis faktor penyebab spesifik, bukan imbauan umum.

---

## 7. Lampiran — Peta Artefak

| Folder | Isi | Status |
|--------|-----|--------|
| [01-proposal/](../01-proposal/) | Proposal lengkap + WS-01–08 | ✅ Selesai |
| [02-literatur/](../02-literatur/) | 5 paper + matriks literatur | ✅ Selesai |
| [03-teori/](../03-teori/) | Landasan teori TAM + kerangka konseptual | ✅ Selesai |
| [04-data/](../04-data/) | Data kuesioner (raw + processed) | ⏳ Menunggu |
| [05-kode/](../05-kode/) | 6 notebook analisis Python | ✅ Siap dijalankan |
| [06-output/](../06-output/) | Tabel CSV + figure PNG | ⏳ Menunggu data |
| [07-manuskrip/](../07-manuskrip/) | Draf paper IMRAD | ⏳ Draf awal |
| [09-docs/](../09-docs/) | WS-01 s.d. WS-16 lengkap | ✅ Selesai |
