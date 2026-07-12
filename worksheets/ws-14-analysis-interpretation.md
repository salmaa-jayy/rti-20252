# WS-14: Analysis, Interpretation & Failure Analysis

> **Bab 14 — Analisis Data, Interpretasi & Failure Analysis**

---

## Ringkasan Materi

### Data → Knowledge Model

```
Data → Analysis → Interpretation → Explanation → Knowledge
```

Tiga level yang berbeda:
- **Analysis** — "Apa yang terjadi?" (deskriptif + inferensial)
- **Interpretation** — "Apa artinya?" (konteks RQ + literatur)
- **Failure Analysis** — "Mengapa tidak berhasil?" (boundary conditions)

### Beyond p-value

**Statistical significance ≠ practical significance.** Selalu laporkan:
1. p-value (signifikansi statistik)
2. Effect size (besarnya efek)
3. Confidence interval (rentang ketidakpastian)

| Effect Size (Cohen's d) | Interpretasi |
|-------------------------|-------------|
| < 0.2 | Small |
| 0.2 – 0.8 | Medium |
| > 0.8 | Large |

### Pemilihan Uji Statistik

| Kondisi | Uji yang Tepat |
|---------|---------------|
| 2 grup, normal, paired | Paired t-test |
| 2 grup, non-normal | Wilcoxon signed-rank |
| > 2 grup, normal | One-way ANOVA + post-hoc |
| > 2 grup, non-normal | Kruskal-Wallis + post-hoc |
| 2 variabel kontinu | Pearson (normal) / Spearman (rank) |

### Failure Analysis as Contribution

Hipotesis yang ditolak adalah **temuan yang berharga**:

| Dataset | New (F1) | Baseline (F1) | p-value | Cohen's d |
|---------|---------|--------------|---------|-----------|
| DS-1 (small, clean) | 94.2±1.1 | 89.3±1.5 | <0.001 | **3.7** |
| DS-4 (medium, noisy) | 78.3±3.2 | 82.1±2.8 | 0.008 | **-1.3** |
| DS-5 (large, noisy) | 71.6±4.1 | 80.5±3.0 | <0.001 | **-2.5** |

**Insight:** Metode baru unggul di data bersih tapi gagal di data noisy → asumsi Gaussian dilanggar → **boundary condition** ditemukan → hybrid approach direkomendasikan.

**Partial failure + deep analysis = kontribusi lebih kaya daripada full success tanpa analisis.**

### Limitation Types

| Jenis | Contoh |
|-------|--------|
| Internal validity | Confounders yang tidak dikontrol |
| External validity | Generalisasi ke domain lain |
| Construct validity | Metrik mengukur apa yang dimaksud? |
| Statistical limitation | Sample size, asumsi distribusi |

### Jebakan Kognitif

1. "Signifikan statistik = penting secara praktis" → cek effect size
2. "Hipotesis tidak didukung → cari sudut baru" → p-hacking
3. "Kegagalan tidak perlu dilaporkan detail" → missed insight
4. "Limitasi cukup disebutkan, tidak perlu dianalisis" → kedalaman hilang

---

## Template A.14 — Analysis & Interpretation Report

```
ANALYSIS & INTERPRETATION

1. Statistik Deskriptif:
   | Skenario | Mean | Std | Median | Min | Max | n |
   |----------|------|-----|--------|-----|-----|---|
   | Kemudahan 2FA    | 3.82 | 0.71 | 4.00   | 1.5 | 5.0 | 94 |
   | Manfaat 2FA      | 3.91 | 0.68 | 4.00   | 1.8 | 5.0 | 94 |
   | Kesadaran risiko | 3.54 | 0.83 | 3.67   | 1.0 | 5.0 | 94 |
   | Pengaruh sosial  | 3.21 | 0.92 | 3.33   | 1.0 | 5.0 | 94 |
  % adopsi 2FA aktif: 41% (39 dari 94 responden)

2. Uji Hipotesis:
   Uji yang digunakan  : Korelasi Spearman + Regresi Logistik
   Justifikasi          : Data Likert ordinal → Spearman;
                          DV dikotomis → Regresi Logistik
   Hasil kemudahan: r=0.41, p=0.003, CI 95% [0.21, 0.58]
   Hasil manfaat  : r=0.38, p=0.008, CI 95% [0.18, 0.55]
   Hasil risiko   : r=0.29, p=0.074 (tidak signifikan)
   Hasil sosial   : r=0.24, p=0.118 (tidak signifikan)

3. Keputusan:
   [x] H₀ ditolak → H₁ diterima ntuk 2 faktor
       (kemudahan dan manfaat signifikan pada p < 0.05)
   [ ] H₀ tidak ditolak

4. Interpretasi:
   Hubungan ke RQ        : Dari 4 faktor, kemudahan (r=0.41)
                           dan manfaat (r=0.38) terbukti
                           berhubungan signifikan dengan
                           adopsi 2FA
   Practical significance: r ≥ 0.3 — efek moderat, bermakna
                           secara praktis
   Perbandingan literatur : Konsisten dengan TAM Davis (1989);
                           sejalan Akraman et al. (2018)

5. Limitation:
   | Jenis | Ancaman | Dampak | Mitigasi |
   |-------|---------|--------|----------|
   | Construct  | Self-reported ≠ perilaku nyata | Overestimasi kesadaran    | Akui di limitasi                  |
   | External   | Hanya 94 mahasiswa Kebumen     | Tidak bisa digeneralisasi | Saran replikasi kota lain         |
   | Statistical| n=94, power terbatas           | Risiko Type II error      | Laporkan power analysis           |

6. Failure Analysis (jika H₀ tidak ditolak):
   Kesadaran risiko (p=0.074) dan pengaruh sosial (p=0.118)
   tidak signifikan — ini temuan, bukan kegagalan:
   Penyebab potensial  : Optimism bias — sadar risiko tapi
                         merasa "tidak akan terjadi padaku"
   Boundary condition   : Pengaruh sosial hanya efektif di
                          komunitas yang sudah punya norma
                          keamanan digital kuat
   Insight              : Edukasi harus fokus pada kemudahan
                          akses 2FA, bukan hanya kampanye
                          kesadaran risiko
```

---

## Latihan 1 — Pemilihan Uji Statistik

Tentukan uji statistik yang tepat untuk eksperimen Anda.

| Pertanyaan | Jawaban |
|-----------|---------|
| Berapa grup yang dibandingkan? | Bukan perbandingan grup, ini korelasi IV dan DV |
| Apakah data berpasangan (paired)? | Tidak, setiap responden mengisi sekali |
| Apakah distribusi normal? (uji normalitas) | Tidak sepenuhnya, data Likert ordinal |
| **Uji yang dipilih:** | Korelasi Spearman + Regresi Logistik |
| **Justifikasi:** | Spearman tepat untuk ordinal; Regresi Logistik untuk DV dikotomis |

**Effect size yang akan dilaporkan:** [ ] Cohen's d / [ ] Eta-squared / [ ] Lainnya: ____

---

## Latihan 2 — Interpretasi Hasil

Gunakan data berikut (atau data riil Anda) untuk berlatih interpretasi.

**Data:**
| Model | Accuracy (mean ± std) | n |
|-------|----------------------|---|
| A | 89.2 ± 1.5 | 10 |
| B | 87.8 ± 2.1 | 10 |

p = 0.045, Cohen's d = 0.74, CI 95% = [0.03, 2.77]

| Aspek | Interpretasi |
|-------|-------------|
| Signifikansi statistik | Kemudahan p=0.003, Manfaat p=0.008 → signifikan. Risiko & sosial p > 0.05 → tidak signifikan |
| Effect size | r=0.41 dan r=0.38 = efek moderat, melampaui threshold r≥0.3 |
| Practical significance | Peningkatan persepsi kemudahan berhubungan dengan peningkatan odds adopsi 2FA — cukup substansial untuk dasar intervensi |
| Hubungan ke RQ | RQ terjawab: kemudahan dan manfaat adalah faktor paling relevan |
| Perbandingan literatur | Konsisten TAM (Davis 1989) dan Akraman et al. (2018); lebih spesifik dari Farida et al. (2024) |

---

## Latihan 3 — Failure Analysis

Latih kemampuan failure analysis: hipotesis TIDAK didukung. Apa yang bisa dipelajari?

**Skenario:** Metode baru Anda mendapat F1 = 83.2%, baseline = 84.7%. p = 0.12 (tidak signifikan).

| Pertanyaan | Jawaban |
|-----------|---------|
| Apakah ini "gagal"? | Bukan, temuan valid yang memberikan informasi penting tentang batas efektivitas edukasi |
| Kemungkinan penyebab? | Optimism bias: sadar risiko tapi merasa tidak akan jadi korban. Norma keamanan digital belum terbentuk di kampus Kebumen |
| Boundary condition? | Kesadaran risiko mungkin hanya efektif sebagai prediktor di populasi yang pernah mengalami peretasan langsung |
| Insight yang bisa diambil? | Kampanye edukasi harus fokus pada kemudahan pengaktifan 2FA dan manfaat konkret, bukan hanya menakut-nakuti dengan risiko |
| Apakah layak dilaporkan? Mengapa? | Ya — negative result ini mencegah institusi membuang sumber daya pada kampanye yang tidak terbukti efektif |

**Limitation terkait:**
| Jenis | Ancaman | Dampak |
|-------|---------|--------|
| Statistical | n=94 mungkin underpowered untuk deteksi efek kecil (r < 0.3) | Risiko Type II error — faktor yang sebenarnya berhubungan lemah bisa tidak terdeteksi | 
| Construct | Self-reported data — responden menjawab berdasarkan persepsi, bukan perilaku nyata | Kesadaran risiko yang dilaporkan tinggi belum tentu mencerminkan tindakan nyata |
| External | Sampel hanya mahasiswa Kebumen | Hasil tidak bisa digeneralisasi ke populasi pengguna Instagram Indonesia yang lebih luas |

---

## Refleksi

> Apakah "failure" dalam riset benar-benar gagal, atau justru kontribusi? Bagaimana failure analysis mengubah cara Anda melihat hasil negatif?

> Failure analysis mengubah "hipotesis tidak terdukung" menjadi "boundary condition ditemukan." Dua faktor yang tidak signifikan justru memberikan insight praktis yang lebih berguna bagi perancang program edukasi daripada kalau keempat faktor semuanya signifikan.
