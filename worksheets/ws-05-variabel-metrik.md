# WS-05: Variabel & Metrik

> **Bab 5 — Metric, Measurement & Data**

---

## Ringkasan Materi

### Measurement Alignment Model

Setiap pengukuran yang valid harus bisa ditelusuri melalui rantai ini tanpa lompatan logis:

```
Problem → Concept → Variable → Metric → Data → Result
```

### Operationalization = Keputusan Desain

Menerjemahkan konsep abstrak menjadi variabel terukur bukan proses mekanis. "Code quality" yang diukur via SonarQube code smells membawa asumsi implisit. Setiap operasionalisasi harus didokumentasikan dan dijustifikasi.

### Empat Tipe Data (NOIR)

| Tipe | Ciri | Contoh | Operasi Valid |
|------|------|--------|---------------|
| **Nominal** | Kategori, tanpa urutan | Jenis algoritma (RF, SVM, CNN) | Modus, chi-square |
| **Ordinal** | Urutan, interval tidak sama | Skala Likert (1-5) | Median, Spearman |
| **Interval** | Jarak bermakna, tanpa nol absolut | Suhu Celsius | Mean, Pearson, t-test |
| **Ratio** | Jarak bermakna + nol absolut | Waktu eksekusi (ms) | Semua operasi |

Tipe data menentukan uji statistik yang valid. Kebanyakan metrik performa TI = ratio; persepsi pengguna = ordinal.

### Kriteria Pemilihan Metrik

- **Representative** — Mewakili konsep yang diteliti
- **Sensitive** — Cukup peka menangkap perbedaan bermakna (hindari ceiling effect)
- **Feasible** — Bisa dikumpulkan dalam batasan waktu dan biaya

### Pre-registration

Metrik harus ditentukan **sebelum** eksperimen. Memilih metrik setelah melihat data = **p-hacking**. Metrik tambahan yang ditemukan kemudian dilaporkan sebagai *exploratory*, bukan *confirmatory*.

### Primary vs Secondary Metric

- **Primary Metric** — Langsung terikat ke hipotesis, menentukan kesimpulan
- **Secondary Metric** — Pendukung, dilaporkan di samping primary; statusnya suplementer

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Pemilihan metrik | Berdasarkan kebiasaan/tool yang ada | Berdasarkan construct validity |
| Anomali | Dihapus untuk laporan bersih | Diinvestigasi — bisa jadi temuan |
| Kapan dipilih | Setelah sistem jadi (monitoring) | Sebelum eksperimen (by design) |

### Istilah Penting

- **Operationalization** — Transformasi konsep abstrak menjadi variabel terukur
- **Construct Validity** — Sejauh mana pengukuran benar-benar mengukur konsep yang dimaksud
- **Measurement Scale** — Klasifikasi data (NOIR) yang menentukan analisis valid
- **Multi-metric Evaluation** — Menggunakan beberapa metrik untuk menangkap konsep kompleks

---

## Template A.5 — Definisi Variabel, Metrik & Justifikasi

```
VARIABLE & METRIC DEFINITION

Research Question: ____________________

| Variabel | Tipe | Konsep | Metrik | Skala | Satuan | Cara Mengukur | Justifikasi |
|----------|------|--------|--------|-------|--------|---------------|-------------|
|Persepsi Kemudahan| IV   |Seberapa mudah 2FA dirasakan|Skor rata-rata skala Likert |Interval|Skor 1–5 |4 item kuesioner Likert |Kemudahan persepsian terbukti jadi prediktor adopsi teknologi (TAM, Davis 1989)|
| Persepsi manfaat  | IV   | Seberapa berguna 2FA dirasakan| Skor rata-rata skala Likert   | Interval| Skor 1–5      | 4 item kuesioner Likert                | Manfaat persepsian konsisten memengaruhi niat pakai teknologi keamanan |
| Kesadaran risiko  | IV   | Seberapa sadar thd ancaman akun| Skor rata-rata skala Likert  | Interval| Skor 1–5      | 3 item kuesioner Likert                | Studi Akraman et al. (2018) tunjukkan kesadaran risiko korelatif dengan perilaku keamanan |
| Pengaruh sosial   | IV   | Tekanan/dorongan dari lingkungan| Skor rata-rata skala Likert  | Interval| Skor 1–5      | 3 item kuesioner Likert                | Pengaruh sosial adalah prediktor signifikan adopsi teknologi (UTAUT, Venkatesh 2003) |
| Adopsi 2FA        | DV   | Perilaku nyata aktifkan 2FA   | Persentase adopsi + skor konsistensi | Rasio | % dan skor 1–5 | Pertanyaan dikotomis + frekuensi penggunaan | DV utama yang langsung menjawab RQ; konsisten dengan baseline Farida et al. 2024 |
| Usia & jurusan    | CV   | Karakteristik demografis      | Kategori usia + nama jurusan  | Nominal | Tahun / string| Isian pada kuesioner bagian demografi  | Perlu dikontrol karena mahasiswa TI cenderung lebih sadar keamanan (Muhammad, ITS 2023) |

Alignment Check:
  RQ → Concept → Variable → Metric → Data → Result
  [x] Setiap langkah terdokumentasi
  [x] Tidak ada "lompatan logis"
  [x] Metrik mengukur apa yang dimaksud (construct validity)
```

---

## Latihan 1 — Operationalization Chain

Gunakan RQ dari WS-04. Definisikan variabel dan metriknya.

**RQ:** Faktor persepsi apa yang secara signifikan berhubungan dengan rendahnya adopsi 2FA di kalangan mahasiswa pengguna Instagram di Kebumen?

| Variabel | Tipe | Konsep Abstrak | Metrik Konkret | Skala (NOIR) | Satuan |
|----------|------|---------------|----------------|-------------|--------|
| Persepsi kemudahan 2FA | IV | Rasa mudah/susahnya pakai 2FA | Skor rata-rata 4 item Likert | Interval | Skor 1-5 |
| persepsi manfaat 2FA | IV | Pemahaman tentang ancaman nyata terhadap akun IG | Skor rata-rata 3 item Likert | Interval | Skor 1-5 |
| Pengaruh sosial | IV | Dorongan dari teman/keluarga untuk pakai 2FA | Skor rata-rata 3 item Likert | Interval | Skor 1-5 |
| Adopsi 2FA | DV | Perilaku nyata mengaktifkan dan konsisten pakai 2FA | % adopsi + skor konsistensi penggunaan | Rasio | % dan skor 1-5 |
| Usia & jurusan | CV | Latar belakang demografis yang bisa confounding | Kategori usia + nama jurusan | Nominal | Tahun/string |

**Apakah ada lompatan logis dalam rantai?** [ ] Ya / [x] Tidak
> Jika ya, di mana? ____________________________________

---

## Latihan 2 — Evaluasi Metrik

Evaluasi metrik DV yang dipilih di Latihan 1 menggunakan 3 kriteria.

| Kriteria | Skor (1-5) | Justifikasi |
|----------|-----------|-------------|
| Representative | 4 | Kombinasi % adopsi + skor konsistensi lebih representatif dibanding sekadar ya/tidak — bisa bedain yang "pernah coba" vs yang "rutin pakai" |
| Sensitive | 3 | Skala Likert 1–5 cukup sensitif menangkap gradasi persepsi, tapi kalau distribusi responden menumpuk di skor 4–5 bisa muncul ceiling effect |
| Feasible | 5 | Kuesioner Google Form mudah disebar dan diisi mahasiswa, tidak butuh alat khusus atau akses teknis |

**Apakah perlu secondary metric?** [x] Ya / [ ] Tidak
> Jika ya, apa dan mengapa? Perlu tambahan Net Promoter Score (NPS) keamanan digital atau skor literasi keamanan sebagai secondary metric — untuk validasi silang apakah yang bilang "sadar risiko" di kuesioner beneran paham ancaman atau cuma merasa paham

**Contoh kasus ceiling effect untuk metrik ini:**
> Kalau mayoritas mahasiswa TI Kebumen udah sadar keamanan lebih tinggi dari rata-rata nasional, skor Likert mereka bakal numpuk di angka 4–5 semua — akibatnya variasi antar responden kecil banget dan korelasi antar variabel jadi susah terdeteksi secara statistik

---

## Latihan 3 — Data Quality Check

Bayangkan data yang akan dikumpulkan dari eksperimen. Evaluasi 4 dimensi kualitas data.

| Dimensi | Pertanyaan | Jawaban | Strategi Mitigasi |
|---------|-----------|---------|------------------|
| Completeness | Apakah semua data point terkumpul? | Risiko: ada responden yang skip pertanyaan tertentu atau tidak menyelesaikan kuesioner | Wajibkan semua pertanyaan di Google Form, tambahkan estimasi waktu pengisian (5 menit) biar responden nggak drop di tengah |
| Consistency | Apakah ada kontradiksi internal? | Risiko: responden bilang "sadar risiko tinggi" tapi sekaligus bilang "tidak pakai 2FA dan tidak berniat pakai" | Tambahkan 2–3 pertanyaan cek konsistensi (attention check) yang tersebar di tengah kuesioner |
| Validity | Apakah benar-benar mengukur yang dimaksud? | Risiko: pertanyaan Likert tentang "kemudahan 2FA" bisa dijawab berdasarkan asumsi, bukan pengalaman nyata | Tambahkan filter awal — pastikan responden sudah pernah tahu/mencoba 2FA sebelum menjawab item persepsi |
| Representativeness | Apakah sampel mewakili populasi target? | Risiko: kalau disebar cuma lewat grup chat satu jurusan, hasilnya bias ke mahasiswa TI yang sadarnya lebih tinggi | Sebar ke minimal 3–4 jurusan berbeda (TI, ekonomi, hukum, kesehatan) agar mewakili ragam latar belakang |

---

## Refleksi

> Mengapa memilih metrik setelah melihat data dianggap p-hacking? Apa bedanya dengan eksplorasi data yang sah?

**Jawaban:**
> Milih metrik setelah lihat data itu sama aja kayak ngintip jawaban dulu baru bikin soalnya — kelihatannya masuk akal, tapi sebenernya udah bias. Istilahnya p-hacking: peneliti milih metrik yang kebetulan bikin hasilnya "signifikan", bukan karena metrik itu emang paling tepat secara konseptual. Bedanya sama eksplorasi data yang sah adalah soal urutan dan tujuan — eksplorasi data (EDA) itu boleh dilakukan sebelum analisis untuk memahami distribusi dan anomali data, tapi keputusan metrik dan hipotesis tetap harus dikunci dulu sebelum data dikumpulkan. Kalau urutannya kebalik — data dulu, metrik belakangan — validitas seluruh kesimpulan penelitian jadi dipertanyakan.
