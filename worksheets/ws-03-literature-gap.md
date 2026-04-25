# WS-03: Literature Mapping & Gap

> **Bab 3 — Literature Review, Research Gap & Baseline**

---

## Ringkasan Materi

### Literature Review = Positioning, Bukan Ringkasan

Literature review bukan merangkum paper satu per satu. Pendekatan yang benar adalah **concept-centric** — organisasi berdasarkan tema, metode, atau variabel. Tujuan: menemukan **pola, kontradiksi, dan gap**.

**Perbandingan pendekatan Author-centric vs Concept-centric:**

| Aspek | Author-centric (Hindari) | Concept-centric (Gunakan) |
|-------|--------------------------|---------------------------|
| Struktur | Per penulis/paper ("Rahman et al. menyatakan...") | Per konsep/metode ("Pendekatan berbasis transformer") |
| Tujuan | Ringkasan isi paper | Perbandingan metode & identifikasi gap |
| Contoh paragraph | "Rahman (2023) pakai CNN. Lee (2022) pakai LSTM. Zhang (2021) pakai RF." | "Tiga pendekatan dominan: CNN digunakan oleh 4 paper untuk representasi fitur visual; LSTM untuk data sekuensial; RF sebagai baseline klasik." |
| Hasil akhir | Daftar paper | Peta pengetahuan + gap yang teridentifikasi |

### Empat Jenis Research Gap

| Jenis Gap | Deskripsi | Contoh |
|-----------|----------|--------|
| **Performance Gap** | Performa belum memadai | Akurasi deteksi hanya 78% pada kasus tertentu |
| **Method Gap** | Pendekatan belum diterapkan | Belum ada yang pakai transformer untuk task ini |
| **Data Gap** | Dataset terbatas/tidak representatif | Semua studi pakai dataset sintetis |
| **Context Gap** | Belum diuji pada konteks berbeda | Belum ada evaluasi di negara berkembang |

Gap terkuat = kombinasi 2+ jenis.

### Systematic Search Strategy

1. **Database utama**: IEEE Xplore, ACM DL, Scopus
   - Akses IEEE/ACM melalui jaringan kampus atau VPN institusi
   - Alternatif bebas biaya: Google Scholar, ResearchGate ([researchgate.net](https://www.researchgate.net)), arXiv ([arxiv.org](https://arxiv.org))
2. **Boolean query** yang terdokumentasi eksplisit
   - Contoh: `("anomaly detection" OR "intrusion detection") AND ("deep learning" OR "neural network") NOT ("medical imaging")`
   - Gunakan tanda kutip untuk frasa eksak; AND/OR/NOT mengontrol scope
3. **Snowballing** — dua arah:
   - **Backward snowballing**: buka daftar referensi di paper kunci → telusuri paper yang dikutip
   - **Forward snowballing**: di Google Scholar, klik "Cited by" di bawah paper kunci → temukan paper yang mengutipnya
   - Ulangi 1–2 tingkat untuk membangun cakupan komprehensif
4. Klaim "belum ada penelitian" harus didukung **bukti pencarian**

### Baseline Selection — 3 Kriteria

| Kriteria | Pertanyaan |
|----------|-----------|
| **Relevan** | Apakah menyelesaikan masalah yang sama? |
| **Representatif** | Apakah mewakili common practice? |
| **State-of-the-Art** | Apakah terbaru/terbaik? |

Membandingkan deep learning 2024 dengan decision tree sederhana tanpa justifikasi = **straw man comparison** (perbandingan tidak jujur).

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan baca literatur | Mencari solusi yang sudah ada | Memahami apa yang belum terjawab |
| Cara membaca paper | Tutorial, how-to | Metode, limitasi, gap |
| Baseline | Framework terpopuler | State-of-the-art yang rigorous |
| Dokumentasi pencarian | Tidak diperlukan | Wajib (reproducible) |

### Istilah Penting

- **Concept-centric** — Organisasi literatur berdasarkan konsep/metode, bukan per penulis
- **Snowballing** — Backward (telusuri referensi) + Forward (cari yang mengutip paper kunci)
- **Research Position** — Pernyataan eksplisit posisi riset terhadap studi sebelumnya
- **Straw man comparison** — Memilih baseline lemah agar metode sendiri terlihat lebih baik

---

## Template A.3 — Literature Mapping & Gap Identification

```
LITERATURE MAPPING

Topik      : Kesadaran Keamanan Informasi dan Privasi
             Pengguna Media Sosial Instagram
Database   : Google Scholar
Query      : ("kesadaran keamanan informasi" OR
             "information security awareness") AND
             ("Instagram" OR "media sosial") AND
             ("privasi" OR "privacy") NOT ("perusahaan")
Tahun      : 2018–2024
Hasil awal : 24 paper → Screening → 5 paper final

Literature Matrix (concept-centric):

| Study | Tahun | Method | Data | Result | Limitation |
|-------|-------|--------|------|--------|------------|
| Farida et al. | 2024 | Survei/Kuivisoner | 150 responden IG | 39% aktifkan 2FA, 31% baca kebijakan privasi | Sampel kecil, format ya/tidak, convenience sampling |
| Ratnadewati et al. | 2024  | Survei kuantitatif | Pengguna IG    | 17% kesadaran tinggi, 33% sedang, 33% rendah| Tidak menjelaskan faktor penyebab rendahnya kesadaran |
| Muhammad (ITS) | 2023  | Survei/Kuesioner| Mahasiswa SI ITS   | Kesadaran keamanan mahasiswa TI lebih tinggi dari rata-rata | Terbatas satu institusi, tidak general |
| Fauzia et al. (UI) | 2024  | Survei + SEM    | Pengguna TikTok/IG/YT Indonesia | Kekhawatiran privasi meningkat pasca data breach 2021 | Tidak mengukur perilaku nyata pengguna |
| Akraman et al. | 2018  | Survei kuantitatif | Pengguna smartphone Android Indonesia | Kesadaran privasi pengguna smartphone masih rendah | Data sudah lama, belum mencakup konteks Instagram terkini |

Pola yang ditemukan:
  Metode dominan     : Survei kuesioner kuantitatif
  Dataset umum       : Mahasiswa/pengguna aktif IG usia 18+
                     di Indonesia, ukuran 100–200 responden
  Limitasi berulang  : Sampel kecil & tidak representatif,
                     instrumen terlalu sederhana (ya/tidak),
                     tidak mengukur perilaku nyata vs persepsi

GAP IDENTIFICATION

Gap 1: [Jenis: performance / method / data / context]
  Deskripsi    : Belum ada studi yang membandingkan tingkat
                 kesadaran berdasarkan kelompok usia spesifik
                 (Gen Z vs Milenial) pengguna Instagram Indonesia
  Bukti        : Semua studi hanya membandingkan berdasarkan
                 gender, bukan kelompok usia atau latar belakang
                 pendidikan
  Signifikansi : Kelompok usia yang berbeda memiliki pola
                 penggunaan dan risiko yang berbeda — strategi
                 edukasi tidak bisa satu ukuran untuk semua

Gap 2: [Jenis: method]
  Deskripsi    : Semua studi menggunakan self-reported data
                 (ya/tidak) yang tidak mencerminkan perilaku
                 keamanan nyata pengguna di lapangan
  Bukti        : Farida et al. (2024) dan Ratnadewati et al.
                 (2024) keduanya mengandalkan kuesioner biner
                 tanpa validasi perilaku aktual
  Signifikansi : Ada celah antara "kesadaran yang dilaporkan"
                 dengan "perilaku keamanan yang dipraktikkan"
                 — studi observasional atau mixed method
                 diperlukan untuk menutup gap ini

Baseline Selection:
| Baseline | Relevansi | Representatif | Source |
|Farida et al. 2024|Topik identik: kesadaran keamanan IG Indonesia|Paling banyak dirujuk di studi sejenis 2024|SENATIB 2024 |
|Akraman et al. 2018 | Metodologi survei privasi Indonesia yang menjadi acuan banyak paper | Digunakan sebagi baseline di 4 dari 5 paper yang ditemukan | Jurnal Sistem Informasi Bisnis|
```

---

## Latihan 1 — Concept-Centric Literature Table

Gunakan topik riset dari WS-02. Cari minimal 5 paper relevan menggunakan database akademik.

> **Panduan pencarian:**
> - Database: IEEE Xplore, ACM DL, Google Scholar, atau ResearchGate
> - Tulis query Boolean yang digunakan: contoh `("object detection" OR "image classification") AND ("edge computing") NOT ("medical")`. Dokumentasikan query secara eksplisit.
> - Akses gratis: buka Google Scholar → cari judul paper → klik [PDF] jika tersedia, atau akses lewat campus VPN

**Topik riset:** Kesadaran Keamanan Informasi dan Privasi Pengguna Instagram Indonesia
**Query pencarian:**("kesadaran keamanan informasi" OR "information security awareness") AND ("Instagram" OR "social media") AND ("privasi" OR "privacy") NOT ("perusahaan" OR "enterprise")
**Database:** Google Scholar, Sinta (sinta.kemdikbud.go.id), ITS Repository

| # | Study | Tahun | Method | Dataset | Result | Limitasi |
|---|-------|-------|--------|---------|--------|----------|
| 1 | Farida, Bakhtiar, Rif'at | 2024 | Survei kuesioner (ya/tidak) | 150 pengguna IG Indonesia usia 18+ | 39% aktifkan 2FA; 80% pakai password kuat; 31% baca kebijakan privasi | Convenience sampling, format jawaban terlalu sederhana |
| 2 | Ratnadewati & Oktarina | 2024 | Survei Kuantitatif | Pengguna IG Aktif | Hanya 17% memiliki kesadaran tinggi; 33% sedang; 33% rendah | |
| 3 | Muhammad (ITS) | 2023 | Survei/Kuisioner | Mahasiswa Sistem Informasi ITS | Mahasiswa TI memiliki kesadaran lebih tinggi dibanding pengguna umum | Terbatas satu institusi, tidak dapat diregenerasi |
| 4 | Fauzia et al. (UI)| 2024 | Survei+analisis multivariat | Pengguna TikTok/IG/YouTube Indonesia | Kekhawatiran privasi meningkat pasca data breach 235 juta akun 2021 | Tidak membedakan platform secara spesifik |
| 5 | Akraman et al. | 2018 | Survei kuantitatif | Pengguna smartphone Android Indeonesia | Kesadaran privasi pengguna smartphone masih tergolong rendah | Data sudah usang, belum kontekstual dengan Instagram terkini |

**Pola yang terlihat — Metode dominan:** Survei kuisioner kuantitatif dengan analisis presentase deskriptif
**Limitasi yang berulang:** Sampel kecil dan tidak representatif secara nasional; instrumen self-reported tidak mencerminkan perilaku nyata; tidak menganalisis faktor penyebab di balik rendahnya kesadaran

---

## Latihan 2 — Gap Identification

Berdasarkan tabel di Latihan 1, identifikasi gap.

| Jenis Gap | Ditemukan? | Gap Statement |
|-----------|-----------|---------------|
| Performance Gap | [x] Ya | Tingkat kesadaran 2FA hanya 39% padahal ancaman peretasan akun terus meningkat — ada gap antara ketersediaan fitur keamanan dan adopsinya |
| Method Gap | [x] Ya  | Semua studi menggunakan kuesioner biner ya/tidak yang tidak dapat membedakan "tahu tapi tidak lakukan" vs "benar-benar tidak tahu" |
| Data Gap | [x] Ya | Tidak ada studi yang menggunakan data sampel lintas daerah dan usia di Indonesia secara representatif — semua terpusat di satu kota atau institusi |
| Context Gap | [x] Ya  | Belum ada studi yang membandingkan kesadaran keamanan berdasarkan kelompok usia (Gen Z vs Milenial) atau tingkat pendidikan |

**Gap utama yang dipilih:** Method Gap + Context Gap
**Mengapa gap ini penting (bukan sekadar "belum ada yang meneliti")?**
> Mengetahui berapa persen yang tidak pakai 2FA saja tidak cukup — yang lebih penting adalah mengapa mereka tidak menggunakannya. Apakah karena tidak tahu caranya, merasa tidak perlu, atau merasanya ribet? Tanpa menjawab pertanyaan ini, rekomendasi edukasi tidak akan tepat sasaran. Gap ini penting karena intervensi yang salah sasaran justru membuang sumber daya tanpa mengubah perilaku nyata pengguna.
---

## Latihan 3 — Baseline Selection

Pilih 2 baseline dari literatur yang sudah dibaca.

| # | Baseline | Mengapa Relevan | Mengapa Representatif | Apakah SOTA? | Sumber |
|---|----------|----------------|----------------------|-------------|--------|
| 1 | Farida et al. — Survei kuesioner ya/tidak | Topik dan konteks identik: kesadaran keamanan IG pengguna Indonesia 2024 | Paling baru dan paling banyak dikutip di studi sejenis tahun 2024 | Bukan SOTA, tapi merupakan practical baseline yang dominan digunakan | SENATIB 2024, UDB Surakarta |
| 2 | Akraman et al. — Pengukuran Kesadaran Privasi Pengguna Android Indonesia | Metodologi survei privasi digital Indonesia yang menjadi fondasi studi-studi sesudahnya | Dirujuk oleh 4 dari 5 paper yang ditemukan sebagai acuan instrumen pengukuran | Bukan SOTA tapi merupakan common practice & fondasi metodologis di bidang ini | Jurnal Sistem Informasi Bisnis, 2018 |

**Apakah pemilihan baseline ini bisa dianggap straw man?** [ ] Ya / [x] Tidak
> Justifikasi: Kedua baseline dipilih bukan karena mudah dikalahkan, melainkan karena benar-benar merepresentasikan praktik penelitian yang dominan di bidang ini. Farida et al. adalah studi terbaru yang paling relevan, sementara Akraman et al. adalah fondasi metodologis yang diakui komunitas. Membandingkan dengan keduanya justru memperkuat kredibilitas riset.

---

## Refleksi

> Apa perbedaan antara "belum ada yang meneliti ini" (klaim tanpa bukti) dengan research gap yang valid? Bagaimana cara membuktikan bahwa sebuah gap benar-benar ada?

**Jawaban:**
> Kalau bilang "belum ada yang neliti ini" tanpa bukti, itu cuma asumsi — bisa aja sebenernya udah ada, cuma belum ketemu aja pas nyari literaturnya. Research gap yang beneran valid itu harus bisa nunjukin penelitian apa yang udah ada dulu, baru jelasin secara spesifik kurangnya di mana — apakah dari sisi metode, data, konteks, atau hasilnya. Cara buktiin gap-nya ya lewat systematic literature review kayak di atas: cari pake query yang jelas, petain hasilnya, terus liat pola limitasi yang muncul terus-terusan di banyak paper. Jadi gap itu bukan berarti "kosong sama sekali" — tapi lebih ke sesuatu yang udah ada tapi belum bener-bener terjawab sama penelitian sebelumnya.