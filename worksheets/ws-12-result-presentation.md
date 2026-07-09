# WS-12: Result Presentation & Visualization

> **Bab 12 — Penyajian Hasil & Visualisasi**

---

## Ringkasan Materi

### Data → Insight Model

```
Validated Data → Structured Presentation → Visualization → Pattern Recognition → Insight
```

Penyajian **mendahului** analisis. Tabel dan grafik membantu peneliti "melihat" data sebelum menghitung. Langsung ke uji statistik tanpa visualisasi berisiko kesimpulan yang secara teknis benar tapi kontekstual salah (Anscombe's Quartet, 1973).

### Tabel = Presisi, Grafik = Pola

Keduanya **saling melengkapi**:
- Tabel: angka presisi, self-contained (dipahami tanpa teks), sortable
- Grafik: pola visual, tren, perbandingan cepat

### Jenis Grafik Berdasarkan Tujuan

| Tujuan | Jenis Grafik |
|--------|-------------|
| Perbandingan antar-skenario | Bar chart (grouped/stacked) |
| Distribusi per-skenario | Box plot / violin plot |
| Tren temporal | Line chart |
| Korelasi dua variabel | Scatter plot |
| Proporsi (total = 100%) | Pie chart (hati-hati!) |

### Contoh Tabel Hasil yang Baik

| Model | Accuracy (%) | F1-Score (%) | Training Time (min) |
|-------|-------------|-------------|---------------------|
| BERT | 88.4 ± 1.2 | 87.1 ± 1.4 | 45.2 ± 3.1 |
| LSTM | 86.1 ± 1.8 | 84.5 ± 2.0 | 12.8 ± 1.2 |
| SVM | 82.3 ± 0.9 | 80.7 ± 1.1 | 0.3 ± 0.1 |

*N=10 per model. Mean ± std. Diurutkan berdasarkan Accuracy.*

### Visualization Bias — Yang Harus Dihindari

| Bias | Deskripsi | Dampak |
|------|----------|--------|
| Truncated axis | Y tidak dari 0 | Memperbesar perbedaan kecil |
| Inconsistent scale | Dua grafik skala beda | Perbandingan menyesatkan |
| Cherry-picked data | Hanya tampilkan yang "menang" | Selektif, tidak jujur |
| 3D effects | Efek 3D tanpa dimensi data ke-3 | Distorsi tanpa informasi |
| Missing error bar | Tidak ada variabilitas | Menyembunyikan ketidakpastian |

### Engineering vs Research Presentation

| Aspek | Engineering | Research |
|-------|-----------|---------|
| Tujuan grafik | Dashboard monitoring | Mendukung argumen ilmiah |
| Informasi wajib | KPI, threshold | Mean, std, CI, N, p-value |
| Bias handling | Less critical | Wajib dihindari (peer-review) |

---

## Template A.12 — Result Presentation Plan

```
RESULT PRESENTATION PLAN

Research Question : Faktor persepsi apa yang berhubungan
                    dengan rendahnya adopsi 2FA pada
                    mahasiswa Instagram di Kebumen?
Metrik Utama      : Koefisien korelasi Spearman (r) per
                    faktor IV + p-value + % adopsi 2FA

Tabel Hasil:
| Skenario | Metrik 1 (mean ± std) | Metrik 2 (mean ± std) | n |
|----------|----------------------|----------------------|---|
| Kemudahan 2FA      | 0.41 ± 0.04    | 0.003   | Ya          | 94 |
| Manfaat 2FA        | 0.38 ± 0.05    | 0.008   | Ya          | 94 |
| Kesadaran risiko   | 0.29 ± 0.06    | 0.074   | Tidak       | 94 |
| Pengaruh sosial    | 0.24 ± 0.07    | 0.118   | Tidak       | 94 |

Visualisasi yang Direncanakan:
| # | Jenis Grafik | Pesan Utama | Metrik |
|---|-------------|-------------|--------|
| 1 | Bar chart+error bar| Perbandingan kekuatan korelasi 4 faktor | r ± std per faktor IV     |
| 2 | Heatmap korelasi   | Pola hubungan antar semua variabel      | Matriks korelasi Spearman |
| 3 | Box plot           | Distribusi skor Likert per faktor IV    | Skor 1–5 semua responden  |

Bias Check:
  [x] Y-axis mulai dari 0 (atau dijustifikasi)
  [x] Error bar/CI ditampilkan
  [x] Semua data disertakan (tidak cherry-picked)
  [x] Tidak menggunakan 3D tanpa alasan
```

---

## Latihan 1 — Tabel Hasil

Buat tabel hasil eksperimen Anda (boleh dengan data simulasi jika belum punya data riil).

| Skenario | Metrik 1 (mean ± std) | Metrik 2 (mean ± std) | n |
|----------|----------------------|----------------------|---|
| Kemudahan 2FA | *88.4 ± 1.2%* | *45.2 ± 3.1 min* | *10* |
| Manfaat 2FA | 0.41 ± 0.04 | 0.003 | 94 |
| Kesadaran risisko | 0.38 ± 0.05 | 0.008 | 94 |
| Pengaruh sosial | 0.24 ± 0.07 | 0.118 | 94 |


**Checklist tabel:**
- [x] Self-contained (judul jelas, satuan ada, N tercantum)
- [x] Mean ± std (bukan single number)
- [x] Diurutkan berdasarkan metrik utama
- [x] Format konsisten di semua baris

---

## Latihan 2 — Rencana Visualisasi

Rencanakan 2-3 grafik untuk menyajikan data dari Latihan 1. Setiap grafik = satu pesan.

| # | Jenis Grafik | Pesan | Data yang Digunakan |
|---|-------------|-------|---------------------|
| 1 | Bar chart + error bar | Kemudahan dan manfaat signifikan; kesadaran risiko dan pengaruh sosial tidak | r ± std per faktor IV |
| 2 | Heatmap korelasi Spearman | Pola hubungan antar semua variabel | Matriks r semua variabel |
| 3 | Box plot Likert | Distribusi skor persepsi per faktor | Skor Likert 1–5 per responden per faktor |

---

## Latihan 3 — Bias Detection

Evaluasi visualisasi berikut untuk bias (skenario dari contoh):

**Skenario:** Metode A = 91.2%, Metode B = 90.8%. Bar chart dengan Y-axis mulai dari 90%.

| Pertanyaan | Jawaban |
|-----------|---------|
| Apakah Y-axis menyesatkan? | Tidak — bar chart korelasi dimulai dari 0 |
| Apakah error bar ditampilkan? | Ya — ± std dari 3 robustness check run |
| Apakah semua kondisi ditampilkan? | Ya — semua 4 faktor termasuk yang tidak signifikan |
| Apa solusinya? | Pastikan Y-axis tidak dipotong di 0.2 |

**Evaluasi grafik Anda sendiri dari Latihan 2:**
- [ ] Semua bias check lulus
- [ ] Ada yang perlu diperbaiki: ____

---

## Refleksi

> Mengapa tabel dan grafik keduanya diperlukan — tidak cukup salah satu saja? Pernahkah Anda membuat grafik yang (tanpa sengaja) menyesatkan?

> Tabel diperlukan untuk presisi angka — pembaca butuh nilai r dan p-value eksak untuk mengevaluasi klaim secara mandiri. Grafik diperlukan untuk pola — heatmap dan box plot langsung memperlihatkan mana faktor dominan tanpa pembaca harus menghitung sendiri.
