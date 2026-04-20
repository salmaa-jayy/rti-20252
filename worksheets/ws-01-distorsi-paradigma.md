# WS-01: Distorsi & Paradigma

> **Bab 1 — Research Mindset in IT**

---

## Ringkasan Materi

### Research Trust Model

Pengetahuan ilmiah tidak muncul langsung dari kenyataan. Ia melewati **6 tahap transformasi** yang masing-masing rawan distorsi:

```
Reality → Data → Processing → Analysis → Inference → Knowledge
```

Etika mencegah distorsi yang disengaja (fabrikasi, cherry-picking). Validitas mendeteksi distorsi yang tidak disengaja (confounding variable, sampling bias).

### Tiga Jenis Validitas

| Jenis | Pertanyaan | Contoh Ancaman |
|-------|-----------|----------------|
| **Internal Validity** | Apakah hubungan kausal benar ada? | Confounding variable |
| **External Validity** | Apakah bisa digeneralisasi? | Dataset terlalu homogen |
| **Construct Validity** | Apakah mengukur hal yang benar? | Metrik tidak sesuai klaim |

### Paradigma Riset

Mata kuliah ini menggunakan pendekatan **Positivist** (fenomena TI bisa diukur objektif melalui eksperimen terkontrol) diperkuat **Design Science Research** (DSR). Penting untuk membedakan keduanya:

| Paradigma | Cara Kerja | Contoh di TI |
|-----------|-----------|---------------|
| **Positivis** | Uji hipotesis dengan eksperimen terkontrol | Apakah CNN lebih akurat dari RF pada dataset X? |
| **Design Science Research** | Bangun artefak (sistem/model/framework) untuk menguji proposisi | Dapatkah arsitektur hybrid CNN+LSTM membuktikan peningkatan recall ≥5%? |
| **Interpretivis** | Pahami makna melalui konteks & kualitatif | Bagaimana peneliti manafsirkan anomali data sensor IoT? |

Dalam DSR, artefak **bukan tujuan akhir** — ia adalah instrumen untuk menghasilkan pengetahuan. Pertanyaan riset tetap harus difalsifikasi.

### Mode Berpikir Peneliti

**Curious** (mempertanyakan fenomena) → **Critical** (mengevaluasi klaim berdasarkan bukti) → **Systematic** (merancang investigasi terstruktur dan reproducible).

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan | Membuat sistem yang bekerja | Menghasilkan pengetahuan yang valid |
| Pertanyaan khas | "Bagaimana membuatnya jalan?" | "Apakah klaim ini benar?" |
| Ukuran sukses | Sistem berfungsi, client puas | Hipotesis terjawab, temuan tervalidasi |
| Kegagalan | Harus dihindari | Harus dilaporkan (negative result = kontribusi) |

### Istilah Penting

- **Research Mindset** — Pola pikir yang menuntut bukti dan mempertanyakan asumsi
- **Research Ethics** — Prinsip perilaku: kejujuran, objektivitas, keterbukaan, akuntabilitas
- **HARKing** — Hypothesizing After Results are Known — merumuskan hipotesis setelah melihat data
- **Falsifiability** — Hipotesis harus bisa dibuktikan salah

---

## Template A.1 — Research Mindset Self-Assessment

```
Nama Peneliti    : Salma Zaidah
Tanggal          : April 2026

1. Ketika membaca klaim "metode X 95% akurat":
   - Pertanyaan pertama saya: Siapa respondennya, berapa jumlahnya, dan apakah sampel benar-benar representatif?
   - Data yang dibutuhkan untuk verifikasi: Jumlah dan profil responden, metode sampling, instrumen pengukuran yang digunakan, dan apakah hasil sudah diuji validitas & reliabilitasnya

2. Posisi paradigma:
   - Pendekatan: [x] Positivis  [ ] Interpretivis  [ ] Design Science  [ ] Mixed
   - Alasan: Penelitian menggunakan kuesioner terstruktur dengan jawaban ya/tidak dan analisis persentase kuantitatif untuk mengukur tingkat kesadaran keamanan pengguna Instagram secara objektif dan terukur


3. Identifikasi distorsi:
   - Asumsi tersembunyi: Jawaban responden dianggap jujur dan akurat, padahal format ya/tidak mendorong responden menjawab sesuai yang "seharusnya" bukan kondisi nyata (social desirability bias)
   - Sumber bias potensial: Convenience sampling — kuesioner
     disebarkan lewat medsos peneliti sendiri (Instagram, WA, Telegram) sehingga responden cenderung berasal dari lingkaran sosial yang homogen
   - Langkah mitigasi: Tambahkan pertanyaan skenario konkret untuk mengukur perilaku nyata, perluas saluran distribusi kuesioner, dan tambahkan uji validitas instrumen


4. Komitmen etika:
   - Data yang tidak akan dimanipulasi: Persentase hasil kuesioner tidak akan dibulatkan atau diseleksi untuk mendukung kesimpulan tertentu — semua data dilaporkan apa adanya termasuk yang bertentangan dengan hipotesis
   - Batasan yang diakui sejak awal: Sampel 150 responden tidak dapat digeneralisasi ke seluruh pengguna Instagram Indonesia (88 juta pengguna), dan self-reported data tidak menjamin perilaku keamanan yang sebenarnya di lapangan
```

---

## Latihan 1 — Identifikasi Distorsi

Pilih satu paper riset di bidang TI yang mengklaim "metode X meningkatkan performa." Telusuri setiap tahap Research Trust Model.

> **Panduan pencarian paper:** Gunakan [IEEE Xplore](https://ieeexplore.ieee.org), [ACM Digital Library](https://dl.acm.org), atau Google Scholar. Pilih paper **tahun 2020 ke atas**, di topik yang Anda minati: deteksi anomali, klasifikasi citra, NLP, keamanan siber, IoT, dsb.
>
> **Contoh domain TI:** "Deteksi anomali lalu-lintas jaringan menggunakan CNN — akurasi meningkat 94% vs baseline SVM 87%." Distorsi potensial: apakah dataset normal/anomali seimbang? Apakah hanya diuji pada satu vendor traffic?

**Paper yang dipilih:**
> Judul: Analisis Kesadaran Keamanan Informasi Dan Privasi Pada Pengguna
Media Sosial Instagram
> Penulis (Tahun): 2024
> Sumber/Link DOI: https://www.ojs.udb.ac.id/Senatib/article/view/4626/3084

| Tahap | Apa yang Dilakukan | Potensi Distorsi |
|-------|-------------------|-----------------|
| Reality → Data | Menyebarkan kuesioner online via Google Form ke pengguna Instagram usia 18+ | Hanya menjangkau pengguna yang aktif di medsos — yang tidak aktif tidak terwakili |
| Data → Processing | Mengubah jawaban "ya/tidak" menjadi persentase per pertanyaan | Format ya/tidak terlalu menyederhanakan — tidak ada gradasi tingkat kesadaran |
| Processing → Analysis | Membandingkan persentase antar gender (laki-laki vs perempuan) | Hanya dibandingkan berdasarkan gender, tidak ada faktor usia, pendidikan, atau domisili |
| Analysis → Inference | Menyimpulkan tingkat kesadaran keamanan pengguna Instagram Indonesia | 150 responden tidak cukup representatif untuk 88 juta pengguna Instagram Indonesia |
| Inference → Knowledge | Merekomendasikan perlunya edukasi keamanan digital lebih lanjut | Rekomendasi bersifat umum, tidak ada langkah konkret yang terukur |

**Distorsi paling besar di tahap:** Data → Processing

**Dua distorsi spesifik yang teridentifikasi:**
1. Format jawaban hanya "ya" atau "tidak" — tidak bisa membedakan pengguna yang tahu tapi tidak melakukan dengan yang benar-benar tidak tahu sama sekali
2. Sampel 150 responden dipilih secara acak dari lingkaran medsos peneliti sendiri (disebarkan via Instagram, WA, Telegram) — berpotensi convenience sampling bias, bukan benar-benar random

---

## Latihan 2 — Analisis Kasus Etika

Skenario: Seorang peneliti menemukan bahwa jika 3 data point outlier dihapus, hasil eksperimennya menjadi signifikan. Dengan outlier, hasilnya tidak signifikan.

| Perspektif | Analisis |
|------------|---------|
| Kejujuran ilmiah | Laporkan kedua versi hasil — dengan dan tanpa outlier, lengkap dengan alasan statistik penghapusan |
| Transparansi | Jelaskan secara eksplisit di bagian metodologi mengapa outlier dihapus, lampirkan data mentah di appendix |
| Peer review | Reviewer berhak meminta justifikasi penghapusan outlier; tanpa transparansi, paper bisa ditolak atau dicabut |

**Keputusan akhir dan justifikasi:**
> Outlier tidak boleh dihapus hanya karena membuat hasil tidak signifikan. Dalam konteks jurnal ini misalnya — jika ada responden yang menjawab tidak konsisten, peneliti wajib melaporkannya sebagai limitasi, bukan menghapusnya diam-diam. Penghapusan selektif demi signifikansi disebut p-hacking dan merupakan pelanggaran etika penelitian.

---

## Latihan 3 — Posisi Paradigma

**Topik riset:** Analisis Kesadaran Keamanan Informasi dan Privasi pada Pengguna Media Sosial Instagram

> **Skala 1–5:** 1 = tidak sesuai sama sekali dengan topik ini, 5 = sangat sesuai dan dominan digunakan pada riset bertopik serupa.

| Kriteria | Positivis | Interpretivis | Design Science |
|----------|-----------|---------------|----------------|
| Kesesuaian dengan topik (1–5) | 5 — topik mengukur tingkat kesadaran secara numerik, cocok untuk uji statistik dan kuesioner terstruktur | 2 — topik tidak menggali makna atau pengalaman mendalam pengguna | 1 — tidak membangun artefak/sistem baru |
| Jenis data yang dikumpulkan | Persentase jawaban ya/tidak, perbandingan antar gender, angka statistik deskriptif | Wawancara mendalam, narasi pengalaman pengguna soal privasi | Prototipe fitur keamanan, hasil pengujian sistem |
| Limitasi paradigma | Tidak menangkap mengapa pengguna tidak mengaktifkan 2FA — hanya tahu berapa banyak yang tidak | Sulit digeneralisasi, tidak menghasilkan angka yang bisa dibandingkan lintas studi | Tidak relevan karena penelitian ini bukan membangun sistem |

**Paradigma yang dipilih:** Positivis
**Alasan:** Jurnal ini menggunakan pendekatan kuantitatif dengan kuesioner terstruktur dan analisis persentase. Tujuannya mengukur dan membandingkan tingkat kesadaran secara objektif — sesuai ciri khas paradigma positivis yang mengandalkan data numerik dan pengukuran yang dapat direplikasi.
---

## Refleksi

> Sebelum membaca materi ini, apakah pernah mempertanyakan klaim "95% akurat"? Setelah memahami rantai distorsi, pertanyaan apa yang sekarang akan diajukan saat membaca paper?

**Jawaban:**
> Sebelumnya, klaim "95% akurat" mungkin langsung diterima begitu saja karena terlihat meyakinkan secara angka. Setelah memahami rantai distorsi, pertanyaan yang sekarang akan diajukan adalah: Siapa 150 responden itu dan bagaimana cara mereka dipilih? Apakah format kuesioner benar-benar mengukur kesadaran nyata, atau sekadar pengakuan diri? Angka 80% pengguna pakai password kuat misalnya — apakah itu karena mereka benar-benar pakai, atau karena mereka merasa sudah pakai? Distorsi terbesar justru sering tersembunyi di instrumen pengukuran yang tampak sederhana.
