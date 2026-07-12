# WS-16: Presentation & Defense (UAS)

> **Bab 16 — Presentasi & Pertahanan Ilmiah**

---

## Ringkasan Materi

### Scientific Defense Model

```
Research Work → Presentation → Questioning → Defense → Evaluation → Acceptance
```

### Presentasi ≠ Ringkasan Paper

| Paper | Presentasi |
|-------|-----------|
| Dibaca (self-paced) | Didengar (presenter-paced) |
| Detail lengkap | Ide kunci + highlight |
| Tabel numerik detail | Grafik visual + angka kunci |
| Pembaca bisa re-read | Audiens dengar sekali |

**Prinsip:** Presentasi membutuhkan **reformulasi**, bukan kompresi. Medium berbeda = pendekatan berbeda.

### Claim-Evidence-Reasoning (CER)

Setiap jawaban defense harus memiliki:
1. **Claim** — Pernyataan yang dijawab
2. **Evidence** — Data/fakta pendukung
3. **Reasoning** — Logika yang menghubungkan evidence ke claim

**Contoh:**
| Pertanyaan | Bad Answer | Good Answer (CER) |
|-----------|-----------|-------------------|
| "Kenapa hanya 3 dataset?" | "Tiga sudah cukup" | "3 dataset mewakili variasi: small-clean, medium-clean, medium-noisy [E]. Generalisasi perlu validasi lanjut — listed as limitation [R]" |
| "Hasil DS-3 menurun?" | "Itu outlier" | "Ya, karena distribusi heavy-tail melanggar asumsi Gaussian [E]. Ini menunjukkan boundary condition metode [R]" |
| "Effect size?" | "p=0.003, jadi signifikan" | "Cohen's d=1.2 (large effect) [E] — bukan hanya signifikan tapi substansial [R]" |

### Slide Design — One Slide, One Message

**Optimal 9-Slide Plan (15 menit):**

| # | Slide | Waktu | Pesan |
|---|-------|-------|-------|
| 1 | Title + context | 1 min | Apa ini tentang apa |
| 2 | Problem + motivation | 2 min | Mengapa penting |
| 3 | Gap + RQ | 1.5 min | Apa yang belum terjawab |
| 4 | Method overview | 2 min | Bagaimana dijawab (diagram) |
| 5 | Key result — tabel | 2 min | Temuan utama |
| 6 | Key result — grafik | 2 min | Pola visual |
| 7 | Interpretation + failure | 2 min | Apa artinya |
| 8 | Limitation + future | 1.5 min | Batasan & arah |
| 9 | Conclusion + contribution | 1 min | Closing message |

### Anticipatory Defense

Prediksi pertanyaan berdasarkan kategori:

| Kategori | Contoh Pertanyaan |
|---------|------------------|
| Problem | "Mengapa masalah ini penting?" |
| Gap | "Bagaimana dengan studi X yang sudah menjawab ini?" |
| Method | "Mengapa metode ini, bukan Y?" |
| Results | "Bagaimana menjelaskan anomali di DS-3?" |
| Generalization | "Apakah bisa diterapkan di domain lain?" |

### Tiga Prinsip Jawaban

1. **Direct** — Jawab dulu, elaborasi kemudian
2. **Data-based** — Tunjuk evidence spesifik
3. **Honest** — Akui limitasi jika memang ada

### Jebakan Kognitif

1. "Presentasi = semua yang ada di paper" → terlalu padat
2. "Slide cantik = presentasi bagus" → konten > estetika
3. "Tidak bisa jawab = gagal" → "I don't know, but..." menunjukkan kejujuran
4. "Tidak perlu latihan — saya paham riset saya" → latihan = menemukan celah

---

## Template A.16 — Defense Preparation Sheet

```
DEFENSE PREPARATION

Slide Deck Plan:
  Total slides   : 11 konten + 1 title + 1 closing
  Time per slide : ~1.5–2 menit
  Total time     : 15 menit

Slide Outline:
| # | Pesan Utama | Visual | Waktu |
|---|-------------|--------|-------|
| 1  | Title — riset faktor persepsi adopsi 2FA Kebumen | Title slide, logo UPB         | 30 det  |
| 2  | Problem — 88 juta pengguna, hanya 39% pakai 2FA  | Bar chart adopsi vs ancaman   | 2 min   |
| 3  | Gap + RQ — instrumen biner tidak jelaskan kenapa  | Tabel gap 5 literatur         | 1.5 min |
| 4  | Method — survei Likert, 94 mahasiswa Kebumen      | Diagram alur penelitian       | 2 min   |
| 5  | Variabel — IV, DV, CV                             | Tabel variabel berwarna       | 1.5 min |
| 6  | Hasil — tabel korelasi 4 faktor                   | Tabel r + p-value             | 2 min   |
| 7  | Hasil visual — bar chart korelasi                 | Bar chart r ± error bar       | 1.5 min |
| 8  | Interpretasi — kemudahan & manfaat dominan        | Highlight 2 faktor signifikan | 1.5 min |
| 9  | Failure analysis — kenapa risiko & sosial tidak   | Diagram optimism bias         | 1 min   |
| 10 | Limitasi + future work                            | Bullet singkat                | 1 min   |
| 11 | Conclusion + kontribusi                           | 3 poin kunci                  | 1 min   |

Anticipatory Defense Matrix:
| Kategori | Pertanyaan Potensial | Jawaban (CER) |
|----------|---------------------|---------------|
| Problem        | Mengapa fokus 2FA, bukan fitur keamanan lain?     | Claim: 2FA paling efektif tapi paling sedikit digunakan. Evidence: 39% adopsi (Farida 2024). Reasoning: gap antara ketersediaan dan adopsi paling urgen |
| Gap            | Farida et al. 2024 sudah meneliti ini?            | Claim: Farida meneliti "berapa", bukan "mengapa". Evidence: instrumen biner tidak bisa identifikasi faktor penyebab. Reasoning: tanpa penyebab, rekomendasi tidak operasional |
| Method         | Kenapa hanya 94 responden?                        | Claim: 94 cukup untuk uji korelasi Spearman dengan power yang memadai. Evidence: power analysis menunjukkan n=80+ cukup untuk deteksi r≥0.3 pada α=0.05. Reasoning: keterbatasan sumber daya dicatat sebagai limitasi |
| Results        | Kenapa kesadaran risiko tidak signifikan?         | Claim: Ini temuan, bukan kegagalan. Evidence: p=0.074, r=0.29. Reasoning: optimism bias — mahasiswa sadar risiko tapi merasa tidak akan terkena dampaknya |
| Generalization | Bisa diterapkan di luar Kebumen?                  | Claim: Belum bisa — limitasi yang diakui sejak awal. Evidence: sampel hanya 94 mahasiswa Kebumen. Reasoning: replikasi lintas kota adalah future work eksplisit |

Latihan:
  Latihan 1: [tanggal] — [catatan timing & feedback]
  Latihan 2: [tanggal] — [catatan timing & feedback]
  Latihan 3: [tanggal] — [catatan timing & feedback]
```

---

## Latihan 1 — Slide Outline

Rencanakan presentasi 15 menit untuk riset Anda.

| # | Pesan Utama | Visual yang Digunakan | Waktu |
|---|-------------|----------------------|-------|
| 1 | Judul + konteks singkat | Title slide, angka 88 juta pengguna30 det2 |
| 2 | Problem 39% adopsi 2FA meski ancaman nyata | Bar chart adopsi vs insiden | 2 min |
| 3 | Gap + RQ — studi terdahulu hanya tahu "berapa", belum "mengapa" | Tabel 5 literatur + kolom limitasi | 1.5 min
| 4 | Method — survei Likert 94 mahasiswa Kebumen, analisis Spearman | Diagram alur: instrumen → responden → analisis | 2 min |
| 5 | Variabel — 4 faktor IV, adopsi 2FA sebagai DV | Tabel IV/DV/CV berwarna | 1.5 min |
| 6 | Hasil utama — tabel korelasi + highlight 2 yang signifikan | Tabel hasil lengkap | 2 min |
| 7 | Visual — kemudahan dan manfaat jauh lebih kuat | Bar chart r ± error bar + garis threshold r=0.3 | 1.5 min |
| 8 | Interpretasi — konsisten TAM; fokus kemudahan bukan hanya risiko | Diagram TAM + implikasi praktis | 1.5 min |
| 9 | Limitasi + future work | Bullet: self-reported, n=94, saran replikasi | 1 min |
| 10 | Conclusion 3 poin kunci + kontribusi | 3 poin + ucapan terima kasih | 1 min |

**Total waktu estimasi:** 15 menit

---

## Latihan 2 — Anticipatory Defense

Prediksi 5 pertanyaan yang mungkin diajukan penguji, lalu siapkan jawaban CER.

| # | Kategori | Pertanyaan | Claim | Evidence | Reasoning |
|---|----------|-----------|-------|----------|-----------|
| 1 | Problem | Mengapa fokus 2FA? | 2FA paling efektif tapi paling sedikit digunakan | Adopsi hanya 39% meski tersedia gratis (Farida 2024) | Gap terbesar = peluang kontribusi terbesar
| 2 | GapFarida et al. 2024 sudah meneliti ini? | Farida meneliti "berapa", bukan "mengapa" | Instrumen biner tidak bisa identifikasi faktor penyebab | Tanpa penyebab, rekomendasi tidak operasional | 
| 3 | MethodKenapa sampel hanya 94 mahasiswa? | 94 cukup untuk deteksi r≥0.3 pada α=0.05 | Power analysis: n≥80 memadai untuk korelasi moderat | Keterbatasan tercatat sebagai limitasi + saran replikasi |
| 4 | ResultsKenapa kesadaran risiko tidak signifikan? | Ini temuan, bukan kegagalan | r=0.29, p=0.074 mendekati tapi tidak signifikan | Optimism bias: tahu risiko tapi merasa tidak akan terkena | 
| 5 | Generalization | Bisa diterapkan di luar Kebumen? | Belum bisa — limitasi yang diakui sejak awal | Sampel spesifik: 94 mahasiswa Kebumen | Replikasi lintas kota adalah future work eksplisit|

---

## Latihan 3 — Simulasi Q&A

Minta teman/kolega mengajukan 3 pertanyaan tentang riset Anda. Catat pertanyaan dan evaluasi jawaban Anda.

| # | Pertanyaan | Jawaban Saya | Evaluasi |
|---|-----------|-------------|---------|
| 1 | "Kenapa tidak pakai instrumen yang sudah tervalidasi dari literatur?" | Instrumen ya/tidak yang ada tidak mampu mengukur gradasi persepsi. Instrumen Likert baru dirancang karena belum ada instrumen tervalidasi untuk konteks adopsi 2FA Instagram di Indonesia ini bagian dari kontribusi metodologis penelitian ini. | [x] Direct [x] Data-based [x] Honest | 
| 2 | "n=94 itu kecil, hasilnya bisa dipercaya?" | Untuk uji korelasi Spearman, n=94 memadai untuk mendeteksi efek moderat (r≥0.3) pada α=0.05 berdasarkan power analysis. Keterbatasan ini sudah diakui di bagian limitasi dan menjadi salah satu alasan future work replikasi dengan sampel lebih besar. | [x] Direct [x] Data-based [x] Honest | 
| 3 | "Bagaimana kalau responden tidak jujur mengisi kuesioner?" | Itu memang limitasi utama self-reported research. Sudah dimitigasi dengan kuesioner anonim dan dua attention check question. Dari 100 responden awal, 6 dikeluarkan karena gagal attention check. Hasilnya tidak bisa 100% bebas dari bias ini — dan itu sudah diakui secara eksplisit di bagian limitasi. | [x] Direct [x] Data-based [x] Honest|

**Pertanyaan yang paling sulit dijawab:**
> Pertanyaan tentang ukuran sampel n=94, karena membutuhkan pemahaman tentang power analysis yang perlu disiapkan dengan angka konkret.
**Apa yang perlu disiapkan lebih baik:**
> Hafal nilai r, p-value, dan CI untuk semua 4 faktor. Siapkan penjelasan singkat power analysis dalam 2 kalimat. Latihan menjawab pertanyaan tentang generalisasi dengan tegas tapi tetap jujur mengakui limitasi.

---

## Refleksi

> Dari seluruh proses WS-01 sampai WS-16 — dari paradigma riset hingga presentasi — bagian mana yang paling mengubah cara Anda berpikir tentang riset? Apa satu hal yang akan selalu Anda terapkan di riset berikutnya?

**Insight terbesar:**
> Gap harus dibuktikan dari literatur — bukan diasumsikan. Sebelumnya "belum ada yang meneliti ini" terasa cukup, tapi ternyata harus ditunjukkan secara sistematis dari 5 paper bahwa semuanya punya limitasi yang sama.

**Yang akan selalu diterapkan:**
> Menetapkan metrik, threshold, dan hipotesis SEBELUM melihat data. Karena memilih metrik setelah melihat hasil adalah p-hacking — merusak validitas seluruh penelitian meskipun tidak disengaja.
