# WS-07: Experimental Design & Validity

> **Bab 7 — Experimental Design & Validity**

---

## Ringkasan Materi

### Correlation ≠ Causality

Kausalitas membutuhkan 3 syarat:
1. **Covariance** — X dan Y bergerak bersama
2. **Temporal precedence** — X berubah sebelum Y
3. **Elimination of alternatives** — Tidak ada faktor lain yang menjelaskan Y

Controlled experiment adalah satu-satunya metode yang bisa membuktikan kausalitas.

### Empat Jenis Validitas

| Jenis | Pertanyaan | Ancaman Umum |
|-------|-----------|-------------|
| **Internal** | Apakah hubungan IV→DV nyata? | Confounding variable, selection bias |
| **External** | Apakah bisa digeneralisasi? | Dataset terlalu spesifik |
| **Construct** | Apakah mengukur konsep yang benar? | Metrik tidak sesuai |
| **Conclusion** | Apakah kesimpulan statistik valid? | Sample size kecil, uji salah |

Internal dan external validity sering berkonflik: semakin terkontrol (internal kuat) → semakin artificial (external lemah).

### Tiga Tipe Eksperimen dalam Riset TI

| Tipe | Deskripsi | Kapan Digunakan |
|------|----------|----------------|
| **Comparison Study** | Metode A vs B pada kondisi identik | Membandingkan pendekatan berbeda |
| **Ablation Study** | Full system → lepas komponen satu per satu | Mengukur kontribusi tiap komponen |
| **Parameter Study** | Variasikan satu parameter, amati dampak | Uji sensitifitas/robustness |

### Fairness dalam Perbandingan

Perbandingan yang adil = **kondisi identik** untuk semua metode: dataset sama, preprocessing sama, tuning effort sebanding, environment sama, metrik sama.

Contoh tidak adil: Transformer (30 fitur tambahan + Bayesian optimization) vs RF (default params) → hasilnya misleading.

### Threats to Validity = Diidentifikasi Sebelum Eksperimen

Ancaman validitas harus diidentifikasi **sebelum** eksperimen dan mitigasinya dirancang sebagai bagian dari desain — bukan ditulis sebagai boilerplate setelah selesai.

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan testing | Memastikan sistem memenuhi requirement | Membuktikan hubungan kausal antar variabel |
| Baseline | Versi sebelumnya (last release) | Metode tervalidasi dari literatur |
| Kegagalan | Bug → fix → release | H₀ tidak ditolak → tetap kontribusi ilmiah |
| Sukses | 100% test pass | Evidence valid — mendukung atau menolak hipotesis |

### Istilah Penting

- **Causality** — Hubungan sebab-akibat (covariance + temporal + elimination)
- **Controlled Experiment** — Ubah satu variabel, kontrol sisanya, amati efek
- **Fairness** — Semua metode diuji pada kondisi yang benar-benar identik
- **Threats to Validity** — Faktor yang bisa melemahkan kesimpulan jika tidak dimitigasi
- **Conclusion Validity** — Validitas statistik: power, sample size, uji yang tepat

---

## Template A.7 — Desain Eksperimen Lengkap

```
EXPERIMENT DESIGN

Research Question : Faktor persepsi apa (kemudahan, manfaat,
                    kesadaran risiko, pengaruh sosial) yang
                    secara signifikan berhubungan dengan
                    rendahnya adopsi 2FA pada mahasiswa
                    pengguna Instagram di Kebumen?
Hypothesis        : H₀ — Tidak ada hubungan signifikan antara
                    faktor persepsi manapun dengan adopsi 2FA
                    (p ≥ 0,05)
                    H₁ — Minimal satu faktor persepsi memiliki
                    hubungan signifikan dengan adopsi 2FA
                    (p < 0,05), dengan prediksi persepsi
                    kemudahan sebagai faktor paling dominan
Tipe Eksperimen   : [x] Comparison (kondisi existing baseline Farida et al. 2024 vs kondisi penelitian ini dengan instrumen Likert)  [ ] Ablation  [ ] Parameter

Kondisi Eksperimen:
| Kondisi | Deskripsi | IV Value | CV Settings |
|---------|-----------|----------|-------------|
| Control | Kondisi existing Farida et al. 2024 — instrumen biner ya/tidak, 150 responden | Instrumen biner (ya/tidak) | Pengguna Instagram Indonesia usia 18+, convenience sampling |
| Treatment | Kondisi penelitian ini — instrumen Likert 1–5, analisis faktor persepsi | Instrumen Likert 1–5 per faktor |Mahasiswa Kebumen lintas jurusan, purposive sampling, attention check|

Fairness Checklist:
  [x] Dataset identik untuk semua kondisi
  [x] Preprocessing setara
  [x] Tuning effort setara
  [x] Environment identik
  [x] Metrik evaluasi sama

Threat Analysis:
| Threat Type | Ancaman Spesifik | Mitigasi |
|-------------|-----------------|----------|
| Internal    | Social desirability bias — responden menjawab sesuai yang "seharusnya" bukan kondisi nyata | Kuesioner anonim + attention check question untuk filter jawaban tidak serius |
| External    | Sampel terbatas mahasiswa Kebumen — tidak representatif populasi Indonesia | Nyatakan secara eksplisit sebagai batasan; sebar ke 4+ jurusan berbeda |
| Construct   | Instrumen Likert belum tentu mengukur persepsi nyata — bisa jadi hanya mengukur pemahaman kognitif | Validasi instrumen dengan uji validitas dan reliabilitas (Cronbach's Alpha) sebelum penyebaran penuh |
| Conclusion  | Korelasi signifikan tidak berarti kausalitas — faktor yang berhubungan belum tentu menjadi penyebab | Nyatakan temuan sebagai "berhubungan signifikan" bukan "menyebabkan"; hindari klaim kausal |

Statistical Plan:
  Uji statistik   : Korelasi Spearman (hubungan IV–DV) +
                   Regresi Logistik (faktor dominan)
  Justifikasi      : Data Likert berskala ordinal sehingga
                   Spearman lebih tepat dari Pearson;
                   Regresi Logistik dipilih karena DV
                   bersifat dikotomis (aktif/tidak aktif)
  Alpha            : 0,05
  Effect size min  : r ≥ 0,3 (korelasi moderat) sebagai
                   batas minimal kontribusi praktis
```

---

## Latihan 1 — Desain Eksperimen

Susun desain eksperimen berdasarkan RQ, variabel, dan sistem dari WS-04 sampai WS-06.

**RQ:** Faktor persepsi apa yang secara signifikan berhubungan dengan rendahnya adopsi 2FA pada mahasiswa pengguna Instagram di Kebumen?
**Tipe eksperimen:** [x] Comparison / [ ] Ablation / [ ] Parameter

| Kondisi | Deskripsi | IV Value | CV Settings |
|---------|-----------|----------|-------------|
| Control | Kondisi baseline Farida et al. (2024), mengukur adopsi 2FA dengan instrumen biner ya/tidak pada pengguna Instagram Indonesia umum | Instrumen biner (ya/tidak), hasil: 39% adopsi | Responden usia 18+, convenience sampling via medsos peneliti |
| Treatment | Kondisi penelitian ini — mengukur faktor persepsi dengan instrumen Likert 1–5 dan menganalisis korelasinya dengan adopsi 2FA | Instrumen Likert 1–5 per faktor (kemudahan, manfaat, risiko, sosial) | Mahasiswa Kebumen, 4+ jurusan, purposive sampling, anonim, + attention check |

---

## Latihan 2 — Fairness Checklist

Evaluasi apakah desain eksperimen di Latihan 1 sudah fair.

| Kriteria | Status | Detail |
|----------|--------|--------|
| Dataset identik | ✅ | Kedua kondisi mengukur populasi yang sebanding, pengguna Instagram aktif usia mahasiswa; perbedaan lokasi (Indonesia vs Kebumen) diakui sebagai batasan |
| Preprocessing setara | ✅ | Kuesioner dirancang dengan urutan blok yang sama untuk semua responden; data cleaning menggunakan kriteria yang sama (hapus jawaban tidak konsisten dari attention check) |
| Tuning effort setara | ✅ | Tidak ada "tuning" model, kedua kondisi menggunakan instrumen standar yang dirancang sebelum pengumpulan data; tidak ada penyesuaian post-hoc |
| Environment identik | ⚠️ | Baseline menggunakan Google Form via WA/IG/Telegram; penelitian ini juga Google Form, namun konteks penyebaran (kampus Kebumen vs nasional) berbeda; diakui sebagai batasan |
| Metrik evaluasi sama | ✅ | Kedua kondisi mengukur adopsi 2FA sebagai DV utama; perbedaan hanya pada kedalaman instrumen IV yang memang menjadi intervensi penelitian |

**Ada yang tidak fair?** [x] Ya / [ ] Tidak
> Jika ya, bagaimana cara memperbaikinya? Perbedaan konteks penyebaran (nasional vs Kebumen) dan metode sampling (convenience vs purposive) membuat perbandingan tidak sepenuhnya apple-to-apple. Cara memperbaikinya: nyatakan secara eksplisit di bagian limitasi bahwa penelitian ini bukan replikasi langsung Farida et al. (2024), melainkan pengembangan metodologis yang menggunakan baseline tersebut sebagai titik acuan, bukan sebagai kondisi kontrol yang identik.

---

## Latihan 3 — Threat Analysis

Identifikasi ancaman validitas untuk desain eksperimen ini.

| Threat Type | Ancaman Spesifik | Mitigasi |
|-------------|-----------------|----------|
| Internal | Social desirability bias, responden cenderung menjawab "ya, saya sadar risiko" meskipun perilaku nyatanya tidak demikian, karena pertanyaan terasa seperti ujian moral | Kuesioner anonim + attention check question yang tersebar di tengah instrumen; tambahkan pertanyaan skenario konkret ("jika ada notif peretasan, apa yang kamu lakukan?") |
| External | Sampel hanya mencakup mahasiswa Kebumen — tidak dapat digeneralisasi ke seluruh pengguna Instagram Indonesia apalagi pengguna global | Nyatakan batasan generalisasi secara eksplisit di bagian limitasi; rekomendasikan studi lanjutan dengan cakupan lebih luas |
| Construct | Instrumen Likert mengukur persepsi bukan perilaku nyata, ada kemungkinan gap besar antara "merasa 2FA mudah" dengan "benar-benar mengaktifkan 2FA" | Validasi instrumen dengan Cronbach's Alpha (target α ≥ 0,7) sebelum penyebaran penuh; kombinasikan dengan pertanyaan dikotomis aktual sebagai DV |
| Conclusion | Korelasi signifikan bisa muncul karena sample size besar meskipun effect size kecil, bisa salah disimpulkan sebagai hubungan yang kuat | Laporkan effect size (r) selain p-value; gunakan batas minimal r ≥ 0,3 sebagai threshold relevansi praktis, bukan hanya signifikansi statistik |

**Ancaman mana yang paling sulit dimitigasi?** Construct Validity
**Mengapa?**
> Karena gap antara "persepsi yang dilaporkan" dengan "perilaku nyata" adalah masalah fundamental dari semua self-reported research. Satu-satunya cara memitigasi secara penuh adalah dengan observasi perilaku langsung (cek log pengaturan keamanan Instagram responden secara real-time), yang tidak realistis secara etika dan teknis untuk penelitian mahasiswa. Jadi mitigasinya bersifat parsial: validasi instrumen dan pengakuan jujur di bagian limitasi.
---

## Refleksi

> Sebuah paper melaporkan "metode kami mengalahkan semua baseline." Apa 3 pertanyaan pertama yang harus diajukan untuk mengevaluasi klaim ini?

**Jawaban:**
1. Baseline-nya siapa dan seberapa kuat? Apakah baseline yang "dikalahkan" adalah metode state-of-the-art yang sesungguhnya, atau sengaja dipilih yang lemah (straw man) agar terlihat mudah diungguli? Baseline yang tidak representatif membuat klaim "mengalahkan semua baseline" tidak bermakna.
2. Kondisi eksperimennya fair?  Apakah semua metode diuji pada dataset yang sama, preprocessing yang sama, dan tuning effort yang sebanding? Kalau metode baru di-tuning lebih banyak dari baseline, kemenangan itu bukan karena metodenya lebih baik — tapi karena usaha optimasinya lebih besar.
3. "Mengalahkan" sebesar berapa? Apakah perbedaannya signifikan secara statistik DAN bermakna secara praktis? Peningkatan akurasi 0,1% yang signifikan secara statistik belum tentu relevan di dunia nyata.