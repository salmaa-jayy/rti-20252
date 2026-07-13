# Tahap 1 — Proposal & Desain Penelitian

**Status:** Selesai

---

## 1. Komponen yang Dirancang

### 1.1 Framework Penelitian (WS-01–02)
Paradigma **positivis** dipilih karena penelitian menggunakan kuesioner terstruktur dengan analisis persentase kuantitatif. Distorsi utama yang diidentifikasi pada studi terdahulu: **social desirability bias** (format biner mendorong responden menjawab sesuai yang "seharusnya") dan **convenience sampling bias** (penyebaran via lingkaran sosial peneliti sendiri).

### 1.2 Gap Literatur (WS-03)
Dari 5 paper yang dipetakan, ditemukan dua gap utama:
- **Method gap:** semua studi pakai instrumen biner ya/tidak — tidak bisa bedain "tahu tapi tidak lakukan" vs "benar-benar tidak tahu"
- **Context gap:** belum ada studi yang fokus pada mahasiswa lintas jurusan di kota non-metropolitan seperti Kebumen

### 1.3 Research Question & Hipotesis (WS-04)
> *"Faktor persepsi apa yang secara signifikan berhubungan dengan rendahnya adopsi 2FA pada mahasiswa pengguna Instagram di Kebumen?"*

- **H₀:** Tidak ada hubungan signifikan antara faktor persepsi manapun dengan adopsi 2FA (p ≥ 0.05)
- **H₁:** Minimal satu faktor persepsi memiliki hubungan signifikan (p < 0.05), dengan prediksi persepsi kemudahan sebagai faktor paling dominan

### 1.4 Variabel & Metrik (WS-05)

| Variabel | Tipe | Metrik |
|----------|------|--------|
| Persepsi kemudahan 2FA | IV | Skor Likert 1–5 (4 item) |
| Persepsi manfaat 2FA | IV | Skor Likert 1–5 (4 item) |
| Kesadaran risiko | IV | Skor Likert 1–5 (3 item) |
| Pengaruh sosial | IV | Skor Likert 1–5 (3 item) |
| Adopsi 2FA | DV | % adopsi + skor konsistensi Likert |
| Usia & program studi | CV | Nominal |

Threshold: p < 0.05, effect size minimal r ≥ 0.3

### 1.5 Arsitektur Sistem (WS-06)
Tiga komponen modular:
- Sub-modul kuesioner Blok A–D (IV) — dapat dimodifikasi tiap blok tanpa ganggu yang lain
- Modul pengukuran adopsi (DV) — dikotomis + Likert
- Modul filter demografis (CV) — dikontrol di tahap analisis

### 1.6 Desain Eksperimen (WS-07)
- **Tipe:** Comparison study — baseline Farida et al. 2024 (instrumen biner) vs kondisi penelitian ini (instrumen Likert)
- **Threat utama:** Social desirability bias (mitigasi: anonim + attention check), construct validity (mitigasi: Cronbach's Alpha ≥ 0.7)
- **Statistical plan:** Korelasi Spearman + regresi logistik, alpha = 0.05

### 1.7 Integration Check (WS-08)
**Skor: 10/12** — semua 6 koneksi vertikal terhubung. Koneksi terlemah: Metric → System (perlu validasi Cronbach's Alpha sebelum eksekusi penuh).

## 2. Deliverable

- [x] Proposal lengkap A–H ([../01-proposal/proposal-penelitian.docx](../01-proposal/proposal-penelitian.docx))
- [x] Worksheets WS-01 s.d. WS-08 ([../01-proposal/](../01-proposal/))
- [x] Instrumen kuesioner 22 item dirancang
