 # WS-04: Research Question & Hypothesis

> **Bab 4 — Research Question, Contribution & Hypothesis**

---

## Ringkasan Materi

### RQ Bukan Pertanyaan Biasa

Research Question yang baik secara implisit mengandung cetak biru eksperimen: subjek, baseline, metrik, domain, dataset.

| Kualitas | Contoh |
|----------|--------|
| **Buruk** | "Bagaimana pengaruh deep learning terhadap deteksi malware?" |
| **Baik** | "Apakah CNN menghasilkan F1-Score lebih tinggi dari RF pada CIC-MalMem-2022?" |

Perbedaan: RQ yang baik menyebutkan **metode spesifik**, **metrik terukur**, **baseline**, dan **dataset**.

### Tiga Jenis RQ

| Jenis | Pola | Kebutuhan |
|-------|------|-----------|
| **Comparison** | A vs B → mana lebih baik? | ≥ 2 metode, metrik sama |
| **Improvement** | A' vs A → modifikasi lebih baik? | Pre/post, bukti perbaikan |
| **Exploratory** | Faktor X₁...Xₙ → pengaruh terhadap Y? | Multi-variabel, korelasi/regresi |

### Contribution Statement

Tiga jenis kontribusi: **Improvement** (metode terbukti lebih baik), **Comparison** (perbandingan sistematis yang belum ada), **Novel Approach** (pendekatan baru). Kontribusi harus terhubung langsung dengan gap — kontribusi tanpa gap = klaim tanpa justifikasi.

### Hypothesis H₀ / H₁

- **H₀** (Null) = Tidak ada perbedaan signifikan — asumsi default, harus dibuktikan salah
- **H₁** (Alternative) = Ada perbedaan signifikan — diterima hanya jika H₀ ditolak
- Harus **falsifiable**, mengandung **metrik terukur**, dirumuskan **SEBELUM eksperimen**

### Rantai Operasionalisasi

```
RQ → Variable → Metric → Data → Analysis
```

Jika rantai ini tidak lengkap, RQ belum mature. Bi-directional: RQ yang tidak bisa jadi hipotesis testable harus direvisi mundur.

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan pertanyaan | Apa yang harus dibangun? | Apa yang harus dibuktikan? |
| Bentuk jawaban | Sistem yang berfungsi | Bukti empiris terukur |
| Sukses diukur oleh | User satisfaction, uptime | Signifikansi statistik, effect size |
| Jika gagal | Debug dan perbaiki | Laporkan, analisis mengapa |

### Istilah Penting

- **Research Question (RQ)** — Pertanyaan spesifik: variabel terukur + metrik + konteks
- **Contribution Statement** — Apa yang diketahui setelah riset selesai yang sebelumnya belum ada
- **H₀ / H₁** — Null vs Alternative Hypothesis
- **Falsifiability** — Kondisi hipotesis ditolak harus bisa didefinisikan sebelum eksperimen
- **Operationalization** — Proses mewujudkan konsep abstrak menjadi variabel terukur

---

## Template A.4 — RQ-Contribution-Hypothesis

```
RQ-CONTRIBUTION-HYPOTHESIS

Gap Statement  : Studi yang ada cuma ngukur "berapa persen" pengguna yang sadar atau tidak, tapi tidak menjelaskan KENAPA mereka tidak menerapkan praktik keamanan kayak 2FA, padahal tanpa tau penyebabnya, rekomendasi edukasi tidak akan tepat sasaran
Research Question:
  Tipe         : [ ] Comparison  [ ] Improvement  [x] Exploratory
  Formulasi    : Faktor apa saja yang memengaruhi rendahnya adopsi autentikasi dua faktor (2FA) di kalangan mahasiswa pengguna Instagram di Kebumen?
  Variabel IV  : Faktor persepsi (kemudahan, manfaat, kesadaran risiko, pengaruh sosial)
  Variabel DV  : Tingkat adopsi 2FA dan praktik keamanan akun Instagram
  Metrik       : Skor Likert per faktor, persentase adopsi 2FA, korelasi antar variabel
  Dataset      : Survei 200+ mahasiswa aktif pengguna Instagram di Kebumen
  Baseline     : Farida et al. (2024) — 39% adopsi 2FA pada pengguna Instagram Indonesia

Quality Check RQ:
  [x] Variabel spesifik
  [x] Metrik jelas
  [x] Baseline ada
  [x] Konteks disebutkan
  [x] Memerlukan eksperimen (bukan hanya survei literatur)

Contribution Statement:
  Apa yang baru diketahui : Faktor-faktor spesifik yang jadi penghambat adopsi 2FA pada mahasiswa Indonesia — bukan sekadar angka persentase adopsi
  Jenis kontribusi        : [ ] Improvement  [ ] Comparison  [x] Novel approach
  Gap yang diisi          : Method gap — dari instrumen biner ya/tidak ke skala Likert yang bisa nangkep gradasi persepsi pengguna; dan context gap — fokus mahasiswa Kebumen yang belum pernah diteliti

Hypothesis Pair:
  H₀ : Tidak ada hubungan signifikan antara persepsi kemudahan penggunaan 2FA dengan tingkat adopsinya di kalangan mahasiswa pengguna Instagram Kebumen
  H₁ : Terdapat hubungan signifikan antara persepsi kemudahan penggunaan 2FA dengan tingkat adopsinya di kalangan mahasiswa pengguna Instagram Kebumen
  Threshold              : p-value < 0,05
  Justifikasi threshold  : Threshold 0,05 adalah standar umum dalam penelitian sosial kuantitatif dan konsisten dengan studi keamanan informasi sejenis (Akraman et al., 2018)
```

---

## Latihan 1 — Dari Gap ke RQ

Gunakan gap yang ditemukan di WS-03. Transformasikan menjadi Research Question.

**Gap dari WS-03:** Semua studi cuma pakai kuesioner biner (ya/tidak) yang tidak bisa dibedakan "tahu tapi nggak lakuin" vs "beneran nggak tahu" — dan belum ada yang neliti faktor penyebab di balik rendahnya adopsi 2FA khususnya di kalangan mahasiswa
**RQ versi pertama (tulis bebas):**
> Kenapa mahasiswa pengguna Instagram banyak yang tidak aktifin 2FA padahal mereka tahu fitur itu ada?

**Evaluasi RQ:**

| Komponen | Ada? | Isi |
|----------|------|-----|
| Metode spesifik | Belum | Perlu ditambah — survei Likert + analisis korelasi |
| Metrik terukur | Belum | Perlu ditambah — skor per faktor, koefisien korelasi |
| Baseline | Belum | Perlu ditambah — Farida et al. 2024 (39% adopsi 2FA) |
| Dataset/konteks | Sebagian | Sudah ada "mahasiswa Instagram" tapi belum ada lokasi spesifik |

**Tipe RQ:** [ ] Comparison / [ ] Improvement / [x] Exploratory

**RQ versi revisi (setelah evaluasi):**
> Faktor persepsi apa saja (kemudahan, manfaat, kesadaran risiko, pengaruh sosial) yang secara signifikan berhubungan dengan rendahnya adopsi autentikasi dua faktor (2FA) di kalangan mahasiswa pengguna Instagram di Kebumen, dibandingkan baseline adopsi 39% dari Farida et al. (2024)?
---

## Latihan 2 — Hypothesis Pair

Rumuskan pasangan hipotesis dari RQ di Latihan 1.

| Komponen | Isi |
|----------|-----|
| H₀ | Tidak ada hubungan signifikan antara faktor persepsi kemudahan, manfaat, kesadaran risiko, dan pengaruh sosial dengan tingkat adopsi 2FA pada mahasiswa pengguna Instagram di Kebumen |
| H₁ | Minimal satu faktor persepsi (kemudahan, manfaat, kesadaran risiko, atau pengaruh sosial) memiliki hubungan signifikan dengan tingkat adopsi 2FA pada mahasiswa pengguna Instagram di Kebumen |
| Metrik | Koefisien korelasi Spearman / skor regresi logistik per faktor |
| Threshold | p-value < 0,05 |
| Justifikasi threshold | Standar konvensional penelitian sosial kuantitatif; digunakan konsisten di studi keamanan informasi sejenis di Indonesia |

**Apakah hipotesis ini falsifiable?** [x] Ya / [ ] Tidak
> Bagaimana cara membuktikannya salah? Cara membuktikannya salah: Kalau hasil uji statistik menunjukkan p-value ≥ 0,05 untuk semua faktor, berarti H₁ gagal didukung dan H₀ tidak bisa ditolak — artinya faktor persepsi yang diuji tidak terbukti berhubungan dengan adopsi 2FA
---

## Latihan 3 — Rantai Operasionalisasi

Lengkapi rantai dari RQ hingga metode analisis.

| Tahap | Isi |
|-------|-----|
| RQ | Faktor persepsi apa yang berhubungan dengan rendahnya adopsi 2FA mahasiswa pengguna Instagram di Kebumen? |
| Variable (IV) | Persepsi kemudahan (perceived ease of use), persepsi manfaat (perceived usefulness), kesadaran risiko, pengaruh sosial |
| Variable (DV) | Tingkat adopsi 2FA — apakah aktif menggunakan atau tidak, dan seberapa konsisten |
| Metric | Skor Likert 1–5 per faktor IV; persentase & frekuensi adopsi 2FA sebagai DV; koefisien korelasi Spearman |
| Data source | Kuesioner online Google Form, 200+ mahasiswa aktif Instagram usia 18–25 tahun di Kebumen |
| Analysis method | Analisis deskriptif (distribusi frekuensi) + uji korelasi Spearman + regresi logistik untuk identifikasi faktor dominan |

**Apakah rantai lengkap?** [x] Ya / [ ] Tidak
> Jika tidak, tahap mana yang perlu direvisi? 

---

## Refleksi

> Ambil satu judul skripsi/paper yang pernah dibaca. Coba ekstrak RQ-nya. Apakah RQ tersebut memenuhi semua komponen (metode, metrik, baseline, konteks)? Jika tidak, apa yang hilang?

**Judul:** Analisis Kesadaran Keamanan Informasi dan Privasi pada Pengguna Media Sosial Instagram (Farida et al., 2024)
**RQ yang diekstrak:** Seberapa tinggi tingkat kesadaran keamanan informasi dan privasi pengguna Instagram di Indonesia?
**Komponen yang hilang:** Metode spesifik tidak disebutkan di RQ-nya — cuma bilang "seberapa tinggi" tanpa jelasin pakai instrumen apa dan dibandingkan sama apa. Baseline juga tidak ada, jadi tidak jelas "tinggi" itu relatif terhadap apa. Harusnya RQ-nya lebih ke: "Seberapa tinggi tingkat kesadaran keamanan informasi pengguna Instagram Indonesia diukur menggunakan instrumen X, dibandingkan standar literasi digital minimum Y?" — baru bisa dievaluasi secara ilmiah.
