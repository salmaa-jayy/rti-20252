# WS-08: Proposal Integration (UTS)

> **Bab 8 — Proposal & Checkpoint**

---

## Ringkasan Materi

### Proposal = Satu Argumen Utuh

Proposal riset bukan kumpulan bab yang independen. Ia adalah **satu argumen** yang mengalir dari masalah ke rencana solusi. Jika satu koneksi putus, seluruh proposal kehilangan koherensi.

### Integration Map — 6 Koneksi Kritis

```
Problem (Bab 2) → Gap (Bab 3) → RQ & H (Bab 4) → Metrik (Bab 5) → Sistem (Bab 6) → Eksperimen (Bab 7)
```

| Koneksi | Pertanyaan Verifikasi |
|---------|----------------------|
| Problem → Gap | Apakah gap muncul dari analisis literatur terhadap masalah? |
| Gap → RQ | Apakah RQ langsung menjawab gap yang teridentifikasi? |
| RQ → Metrik | Apakah setiap variabel di RQ punya metrik terdefinisi? |
| Metrik → Sistem | Apakah setiap metrik bisa diukur oleh komponen sistem? |
| Sistem → Eksperimen | Apakah desain eksperimen menggunakan sistem sebagai instrumen? |

### Koherensi Vertikal + Horizontal

- **Vertikal** — Alur logis atas-ke-bawah (problem → experiment). Setiap section menjawab pertanyaan yang diangkat section sebelumnya dan memunculkan pertanyaan baru.
- **Horizontal** — Konsistensi terminologi (nama variabel di RQ = di hipotesis = di metrik = di desain)

**Operasionalisasi Red Thread** (benang merah):
```
Bab 2 (Problem) → | memperkenalkan masalah X + evidensi |
                          ↓ menimbulkan pertanyaan: "apa akar gap-nya?"
Bab 3 (Gap)     → | menjawab pertanyaan tadi + membuka "lalu apa yang perlu diteliti?" |
                          ↓
Bab 4 (RQ/H)    → | menjawab gap dengan pertanyaan spesifik + prediksi terukur |
                          ↓
Bab 5-7 (Method)→ | menjawab RQ melalui desain eksperimen yang tepat |
```
Jika ada lompatan (section B tidak menjawab pertanyaan section A), red thread putus.

### Jebakan Kognitif

| Jebakan | Deskripsi |
|---------|----------|
| "Selling" Introduction | Menulis promosi, bukan menyajikan data dan gap |
| Copy-paste Methodology | Menyalin deskripsi tekstbook tanpa menyesuaikan ke RQ |
| Optimistic Timeline | Meremehkan waktu implementasi; selalu tambah buffer 30-50% |
| No Possibility of Failure | Mengimplikasikan hasil pasti sukses — proposal jujur mengakui H₀ mungkin tidak ditolak |

### Struktur Proposal

1. **Pendahuluan** — Latar belakang + problem statement (Bab 1-2)
2. **Tinjauan Pustaka** — Literature review + gap + baseline (Bab 3)
3. **RQ / Kontribusi / Hipotesis** — (Bab 4)
4. **Metodologi** — Metrik + sistem + desain eksperimen (Bab 5-7)
5. **Timeline & Output**

### Istilah Penting

- **Integration Map** — Diagram 6 koneksi kritis antar komponen proposal
- **Vertical Coherence** — Alur logis atas-ke-bawah
- **Horizontal Coherence** — Konsistensi terminologi di semua bagian
- **Checkpoint** — Titik self-assessment sebelum transisi dari desain ke eksekusi

---

## Template A.8 — Integration Checklist

```
PROPOSAL INTEGRATION CHECKLIST

Koneksi Vertikal (Flow Atas-Bawah):
  [x] Problem → Gap: masalah terdokumentasi di literatur
      (Farida et al. 2024 — 39% adopsi 2FA, instrumen biner)
  [x] Gap → RQ: pertanyaan menjawab gap spesifik
      (method gap + context gap → RQ faktor persepsi)
  [x] RQ → Hypothesis: hipotesis memprediksi jawaban
      (H₁: persepsi kemudahan paling signifikan, p < 0,05)
  [x] Hypothesis → Metric: metrik mengukur variabel hipotesis
      (skor Likert per faktor + % adopsi + koefisien korelasi)
  [x] Metric → System: komponen sistem mengukur metrik
      (Google Form + Spearman + regresi logistik)
  [x] System → Experiment: desain eksperimen pakai sistem
      (kuesioner sebagai instrumen utama eksperimen)

Koneksi Horizontal (Konsistensi):
  [x] Istilah sama di semua bagian ("adopsi 2FA", "persepsi kemudahan" konsisten dari RQ
      sampai desain eksperimen)
  [x] Variabel di RQ = variabel di hipotesis = metrik di desain (IV: 4 faktor persepsi; DV: adopsi 2FA — konsisten)
  [x] Scope tidak berubah dari masalah ke eksperimen (mahasiswa pengguna Instagram Kebumen — konsisten)

Cognitive Trap Checklist:
  [x] Tidak ada paragraf "promosi" di pendahuluan (pendahuluan berbasis data: 88,86 juta pengguna,
      39% adopsi 2FA dari Farida et al. 2024)
  [x] Metodologi disesuaikan ke RQ, bukan copy-paste textbook Metodologi disesuaikan ke RQ, bukan copy-paste textbook
      (Spearman dipilih karena data ordinal, bukan karena
      "metode umum")
  [x] Timeline sudah ditambah buffer 30-50% dari estimasi awal (8 fase dengan fase revisi di akhir sebagai buffer)
  [x] Proposal mengakui kemungkinan H0 tidak ditolak (H₀ dirumuskan eksplisit: tidak ada hubungan
      signifikan jika p ≥ 0,05)
  [x] Tidak ada klaim "pasti berhasil" (hasil dirumuskan sebagai "diharapkan" dan
      "diprediksi", bukan "pasti")

Rubrik Self-Assessment:
| Kriteria     | 1 (Lemah)                                        | 2 (Cukup)                                     | 3 (Baik)                                           | Skor |
|------------- |--------------------------------------------------|-----------------------------------------------|----------------------------------------------------|------|
| Koherensi   | >2 koneksi vertikal terputus | 1-2 koneksi lemah | Semua 6 koneksi terhubung | 3 |
| Specificity | Variabel abstrak | Sebagian terdefinisi | Semua metrik + threshold jelas | 3 |
| Feasibility | >6 bulan tanpa sumber | 3-6 bulan dengan asumsi | 1-3 bulan realistis | 2 |
| Rigor       | Baseline straw man | 1-2 baseline partial | 2+ baseline + justifikasi | 2 |
```

---

## Latihan 1 — Kompilasi Proposal Mini

Kumpulkan hasil dari WS-02 sampai WS-07 menjadi satu ringkasan proposal.

| Komponen | Sumber | Isi (1-2 kalimat) |
|----------|--------|-------------------|
| Problem Statement | WS-02 | Hanya 39% mahasiswa pengguna Instagram mengaktifkan 2FA, namun tidak ada studi yang menjelaskan faktor penyebab spesifiknya — sehingga rekomendasi edukasi keamanan yang ada tidak tepat sasaran. |
| Gap | WS-03 | Method gap: semua studi pakai instrumen biner ya/tidak yang tidak bisa menangkap gradasi persepsi. Context gap: belum ada studi yang fokus pada mahasiswa lintas jurusan di kota non-metropolitan seperti Kebumen. |
| RQ | WS-04 | Faktor persepsi apa (kemudahan, manfaat, kesadaran risiko, pengaruh sosial) yang secara signifikan berhubungan dengan rendahnya adopsi 2FA pada mahasiswa pengguna Instagram di Kebumen, diukur dengan Likert dan dianalisis dengan korelasi Spearman? |
| Hipotesis | WS-04 | H₁: Minimal satu faktor persepsi memiliki hubungan signifikan (p < 0,05) dengan adopsi 2FA, dengan prediksi persepsi kemudahan sebagai faktor paling dominan berdasarkan TAM (Davis, 1989). H₀: Tidak ada hubungan signifikan antara faktor persepsi manapun dengan adopsi 2FA (p ≥ 0,05). |
| Variabel & Metrik | WS-05 | IV: 4 faktor persepsi (skor Likert 1–5, 14 item); DV: adopsi 2FA (% adopsi + skor konsistensi Likert 1–5); CV: usia & jurusan (nominal). Threshold signifikansi p < 0,05, effect size minimal r ≥ 0,3. |
| Sistem | WS-06 | Tiga komponen modular: sub-modul kuesioner Likert Blok A–D (IV), modul pengukuran adopsi dikotomis + Likert (DV), modul filter demografis (CV). Setiap komponen dapat dimodifikasi tanpa mengganggu komponen lain. |
| Desain Eksperimen | WS-07 | Comparison study: kondisi kontrol (baseline Farida et al. 2024, instrumen biner) vs kondisi treatment (instrumen Likert, 200+ mahasiswa Kebumen, 4+ jurusan). Analisis: korelasi Spearman + regresi logistik. Alpha = 0,05. |

---

## Latihan 2 — Integration Checklist

Verifikasi 6 koneksi kritis. Isi dengan merujuk tabel di Latihan 1.

| Koneksi | Status | Bukti |
|---------|--------|-------|
| Problem → Gap | ✅ | Gap muncul dari 5 paper literatur (WS-03) yang semuanya terbukti menggunakan instrumen biner dan tidak menjawab faktor penyebab rendahnya adopsi 2FA |
| Gap → RQ | ✅ | RQ langsung menanyakan faktor persepsi spesifik yang menjadi penyebab — menutup method gap dan context gap yang diidentifikasi di WS-03 |
| RQ → Hypothesis | ✅ | H₁ memprediksi arah jawaban RQ secara spesifik: persepsi kemudahan sebagai faktor paling dominan, dengan threshold p < 0,05 |
| Hypothesis → Metric | ✅ | Setiap faktor IV di hipotesis punya metrik terdefinisi (skor Likert 1–5); DV diukur dengan % adopsi + skor konsistensi; threshold effect size r ≥ 0,3 sudah ditetapkan |
| Metric → System | ✅ | Setiap metrik diukur oleh komponen sistem yang spesifik — Blok A–D kuesioner untuk IV, modul adopsi untuk DV, modul demografis untuk CV |
| System → Experiment | ✅ | Desain eksperimen menggunakan kuesioner sebagai instrumen utama; prosedur pengisian 4 tahap dirancang agar setiap blok sistem berjalan sesuai urutan yang benar |

**Koneksi mana yang paling lemah?** Metric → System
**Bagaimana cara memperkuatnya?**
> Instrumen kuesioner perlu divalidasi terlebih dahulu dengan uji Cronbach's Alpha (target α ≥ 0,7) sebelum digunakan sebagai alat ukur resmi. Tanpa validasi ini, jalur dari metrik ke sistem belum sepenuhnya terjamin mengukur konstruk yang dimaksud

**Konsistensi horizontal — apakah istilah dan scope konsisten?** [x] Ya / [ ] Tidak
> Jika tidak, di bagian mana terjadi inkonsistensi? _________

---

## Latihan 3 — Rubrik Self-Assessment

Evaluasi proposal mini menggunakan rubrik.

| Kriteria | Skor (1-3) | Justifikasi |
|----------|-----------|-------------|
| Koherensi | 3 | Semua 6 koneksi vertikal terhubung dan red thread bisa ditelusuri dari problem (39% adopsi) → gap (instrumen biner tidak cukup) → RQ (faktor persepsi apa?) → hipotesis (kemudahan paling dominan) → metrik (Likert + Spearman) → eksperimen (kuesioner mahasiswa Kebumen) |
| Specificity | 3  | Semua metrik sudah terdefinisi numerik: skor Likert 1–5 per faktor, % adopsi 2FA, threshold p < 0,05, effect size minimal r ≥ 0,3, target sampel 200+ mahasiswa, Cronbach's Alpha ≥ 0,7 |
| Feasibility | 2 | Timeline 8 fase realistis untuk tugas kuliah, tapi instrumen belum diuji validitasnya dan pengumpulan 200+ responden lintas jurusan membutuhkan effort penyebaran yang tidak trivial — butuh rencana distribusi yang lebih detail |
| Rigor | 2 | Baseline utama (Farida et al. 2024) kuat dan relevan dengan justifikasi lengkap; Akraman et al. 2018 sebagai baseline metodologis sekunder. Namun hanya 2 baseline dan belum ada benchmark internasional yang setara — cukup untuk tugas kuliah tapi bisa diperkuat untuk publikasi |

**Skor total:** 10 / 12

**Apakah proposal siap untuk fase eksekusi?** [x] Ya / [ ] Belum
> Jika belum, apa yang perlu diperbaiki? __________________

---

## Refleksi

> Dari seluruh proses WS-01 sampai WS-08, bagian mana yang paling mudah dan paling sulit? Mengapa? Apa yang akan dilakukan berbeda jika mengulang dari awal?

**Bagian termudah:** WS-01 — Identifikasi distorsi dan paradigma penelitian
**Bagian tersulit:** WS-05 — Operasionalisasi variabel dan metrik
**Yang akan dilakukan berbeda:**
> Dari awal langsung menetapkan satu topik yang spesifik dan tidak ganti-ganti, banyak waktu yang terbuang ketika topik masih terlalu luas di awal. Selain itu, akan langsung mencari minimal 5 jurnal sebelum merumuskan RQ, bukan sesudah karena ternyata gap yang valid hanya bisa ditemukan setelah benar-benar membaca dan memetakan literatur, bukan dari intuisi awal tentang "apa yang belum diteliti."
