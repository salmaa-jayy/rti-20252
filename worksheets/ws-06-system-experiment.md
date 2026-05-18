# WS-06: System-Experiment Mapping

> **Bab 6 — System Design sebagai Experimental Artifact**

---
## Ringkasan Materi

### Sistem = Instrumen Pengujian, Bukan Produk

Seorang engineer bertanya "apakah sistem bekerja?" — seorang peneliti bertanya "apa yang bisa dibuktikan sistem ini?" Sistem dalam riset adalah **artifact** — objek yang sengaja dibuat untuk menguji klaim spesifik.

### System as Experiment Model

```
RQ → Variable → System Component → Experimental Setup → Output
```

Setiap komponen sistem harus bisa ditelusuri ke variabel riset (top-down), dan setiap pengukuran harus menjawab RQ (bottom-up).

### Mapping Variabel ke Komponen

| Tipe Variabel | Peran di Sistem | Contoh |
|---------------|----------------|--------|
| **IV** (Independent) | Modul yang bisa di-toggle/swap | Algoritma A vs B |
| **DV** (Dependent) | Modul pengukuran | Logger, metrics collector |
| **CV** (Control) | Config yang dikunci | Dataset, parameter tetap |

Jika variabel tidak bisa di-map ke komponen apapun → arsitektur perlu didesain ulang.

### 4 Prinsip Desain Eksperimental

| Prinsip | Pertanyaan Kunci |
|---------|-----------------|
| **Traceability** | Komponen ini melayani variabel yang mana? |
| **Modularity** | Bisakah IV diubah tanpa memengaruhi yang lain? |
| **Controllability** | Apakah CV dieksternalisasi ke config file? |
| **Measurability** | Apakah sistem otomatis menghasilkan data yang dibutuhkan? |

### Variable Isolation melalui Arsitektur

- **Modular architecture** — Pisahkan berdasarkan variabel
- **Configuration-driven** — Ubah config (YAML/JSON), bukan code
- **Feature toggles** — On/off flag untuk ablation study

  Contoh config YAML dengan feature toggles:
  ```yaml
  model:
    type: cnn          # IV: ganti "rf" untuk kondisi baseline
  features:
    use_temporal: true  # toggle komponen temporal
    use_normalization: true  # toggle preprocessing
  experiment:
    seed: 42
    runs: 5
  ```
  Dengan pendekatan ini, berbeda kondisi eksperimen = berbeda satu baris config, **tanpa mengubah kode**.

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan sistem | Memenuhi kebutuhan user | Menguji hipotesis, menghasilkan bukti |
| Arsitektur | Optimasi performa & skalabilitas | Optimasi isolasi variabel & reprodusibilitas |
| Konfigurasi | Sering hardcoded | Dieksternalisasi ke config file |
| Fitur tambahan | Menambah nilai user | Menambah noise jika tidak terkait RQ |

### Istilah Penting

- **Artifact** — Objek yang sengaja dibuat untuk memecahkan masalah atau menguji proposisi
- **Traceability** — Kemampuan menelusuri hubungan RQ → variabel → komponen → output
- **Variable Isolation** — Mengubah hanya satu variabel sambil menahan yang lain konstan
- **Ablation Study** — Menguji kontribusi tiap komponen dengan melepasnya satu per satu
- **Configuration-driven Execution** — Semua parameter di config file, bukan hardcoded

---

## Template A.6 — Mapping RQ ke Arsitektur Sistem

```
SYSTEM-EXPERIMENT MAPPING

Research Question: Faktor persepsi apa (kemudahan, manfaat, kesadaran risiko, pengaruh sosial) yang secara signifikan berhubungan dengan rendahnya adopsi 2FA di kalangan mahasiswa pengguna Instagram di Kebumen?

Variable → Component Mapping:
| Variabel | Tipe | Komponen Sistem | Cara Manipulasi/Pengukuran |
|----------|------|-----------------|---------------------------|
|Persepsi kemudahan| IV | Sub-modul kuesioner Blok A (4 item Likert) |Bisa ditambah/kurangi item tanpa ganggu blok lain|
|Persepsi manfaat 2FA| IV |Sub-modul kuesioner Blok B (4 item Likert)| Bisa diswap jadi pertanyaan skenario tanpa ubah DV |
|Kesadaran risiko| IV | Sub-modul kuesioner Blok C (3 item Likert) | Bisa dimodifikasi threshold skor tanpa ubah CV |
|Pengaruh sosial| IV | Sub-modul kuesioner Blok D (3 item Likert) | Bisa dihapus untuk ablation tanpa ganggu IV l |

4 Prinsip Desain:
  [x] Traceability — Setiap komponen bisa ditelusuri ke variabel
  [x] Variable Isolation — IV bisa diubah tanpa mengubah CV
  [x] Measurement Integration — Pengukuran DV built-in
  [x] Reproducibility — Setup bisa direkonstruksi

Experimental Setup:
  Input data     : Respons kuesioner Likert 1–5 dari 200 + mahasiswa pengguna Instagram Kebumen
  Parameter      : 4 faktor IV (kemudahan, manfaat, risiko, pengaruh sosial), threshold p-value < 0.05
  Output format  : Tabel koefisien korelasi Spearman per
  faktor + model regresi logistik adopsi 2FA
```

---

## Latihan 1 — Variable-to-Component Mapping

Gunakan RQ dan variabel dari WS-05. Petakan ke komponen sistem.

**RQ:** Faktor persepsi apa yang secara signifikan berhubungan dengan rendahnya adopsi 2FA di kalangan mahasiswa pengguna Instagram di Kebumen?

| Variabel | Tipe | Komponen Sistem | Cara Manipulasi / Pengukuran |
|----------|------|-----------------|---------------------------|
| Persepsi kemudahan 2FA | IV | Sub-modul kuesioner Blok A (4 item Likert) | Bisa ditambah/kurangi item tanpa ganggu blok lain |
| Persepsi manfaat 2FA | IV | Sub-modul kuesioner Blok B (4 item Likert) | Bisa diswap jadi pertanyaan skenario tanpa ubah DV |
| Kesadaran risiko | IV | Sub-modul kuesioner Blok C (3 item Likert) | Bisa dimodifikasi threshold skor tanpa ubah CV |
| Pengaruh sosial | IV | Sub-modul kuesioner Blok D (3 item Likert) | Bisa dihapus untuk ablation tanpa ganggu IV lain |
|Adopsi 2FA| DV | Modul pengukuran adopsi (dikotomis + Likert) | Diukur otomatis dari 2 pertanyaan akhir kuesioner |
|Usia & jurusan| CV |Modul filter demografis|Dikontrol via segmentasi saat analisis, bukan saat pengumpulan data|

**Apakah semua variabel bisa di-map?** [x] Ya / [ ] Tidak
> Jika tidak, komponen apa yang perlu ditambahkan? _________

---

## Latihan 2 — 4 Prinsip Desain

Evaluasi desain sistem terhadap 4 prinsip.

| Prinsip | Status | Bukti / Penjelasan |
|---------|--------|-------------------|
| Traceability |✅| Setiap blok kuesioner (A–D) berlabel eksplisit sesuai variabelnya — Blok A = kemudahan, Blok B = manfaat, dst. Hasil analisis bisa ditelusuri balik ke item spesifik |
| Modularity |✅|Setiap faktor IV adalah sub-modul terpisah — bisa hapus Blok D (pengaruh sosial) tanpa mengubah Blok A, B, C atau modul DV|
| Controllability |✅|CV (usia & jurusan) dikontrol di tahap analisis via filter segmentasi, bukan di tahap pengumpulan — jadi IV tetap bisa diukur bebas tanpa terganggu CV|
| Measurability |⚠️|Cukup terukur, tapi ada risiko ceiling effect kalau responden mayoritas dari mahasiswa TI yang sadarnya sudah tinggi — perlu diversifikasi jurusan|

**Prinsip mana yang paling sulit dipenuhi?** _______________
**Strategi untuk mengatasinya:**
> ___________________________________________________

---

## Latihan 3 — Ablation Study Planning

Jika sistem memiliki 3 komponen utama, rencanakan ablation study.

> **Panduan jumlah kondisi:** Untuk 3 komponen (A, B, C), kondisi minimal yang direkomendasikan:
> Full + (-A) + (-B) + (-C) = **4 kondisi dasar**. Jika waktu memungkinkan, tambahkan kombinasi ganda: (-A,-B), (-A,-C), (-B,-C) = **7 kondisi**. Sesuaikan dengan *computational cost* dan tenggat waktu penelitian.

| Kondisi | Komponen A | Komponen B | Komponen C | Hasil yang Diharapkan |
|---------|-----------|-----------|-----------|----------------------|
| Full | ✅semua 4 faktor IV| ✅ | ✅  | Model korelasi lengkap — baseline penuh penelitian ini |
| – A | ❌ (tanpa kemudahan) | ✅ | ✅ |Cek apakah persepsi kemudahan adalah faktor dominan atau bisa digantikan faktor lain|
| – B | ✅ | ❌ (tanpa kesadaran risiko) | ✅ |Cek apakah kesadaran risiko berdiri sendiri atau selalu berinteraksi dengan faktor lain|
| – C | ✅ | ✅ | ❌ (tanpa pengaruh sosial) |Cek apakah adopsi 2FA murni keputusan individu atau dipengaruhi lingkungan sosial|

**Komponen mana yang diprediksi paling berkontribusi?** _____
**Mengapa?**
> Berdasarkan Technology Acceptance Model (TAM, Davis 1989), persepsi kemudahan adalah prediktor adopsi teknologi yang paling konsisten terbukti signifikan di berbagai studi. Kalau pengguna merasa 2FA itu ribet, mereka tidak akan pakai meskipun tahu manfaat dan risikonya, ini yang paling sering jadi alasan pengguna skip fitur keamanan di aplikasi sehari-hari.

---

## Refleksi

> Apa risiko jika sistem dibangun seperti produk (monolitik, fitur lengkap) lalu baru dilakukan eksperimen? Mengapa arsitektur modular penting untuk riset?

**Jawaban:**
> Kalau sistem dibangun monolitik dulu baru dieksplorasi, kita tidak bisa tahu komponen mana yang sebenernya yang bikin hasil bagus atau jelek — semuanya nyampur jadi satu dan susah diisolasi. Misalnya kalau hasil korelasi ternyata tidak signifikan, kita tidak bisa bedain apakah masalahnya di instrumen kemudahan, di pengukuran DV, atau di cara kontrolnya. Arsitektur modular penting untuk riset justru karena riset itu sifatnya investigatif — kita perlu bisa cabut satu komponen, lihat apa yang berubah, dan dari situ baru bisa narik kesimpulan yang valid. Tanpa modularitas, eksperimen jadi tidak bisa direproduksi dan kontribusinya tidak bisa diklaim dengan jelas.
