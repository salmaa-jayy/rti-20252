# WS-02: Problem Statement

> **Bab 2 — Problem Formulation & System Context**

---

## Ringkasan Materi

### Problem Formation Model

Masalah riset melewati 5 tahap transformasi. Melompat langsung dari Reality ke Variable adalah kesalahan paling umum.

```
Reality → Observed Issue (Symptom) → Diagnosed Problem (Root Cause)
→ Researchable Problem (Scoped) → Measurable Variable (Operationalized)
```

### Topic ≠ Problem ≠ Research Problem

| Level | Contoh | Status |
|-------|--------|--------|
| **Topik** | Keamanan IoT | Terlalu luas, tidak bisa diuji |
| **Problem** | MQTT tidak terenkripsi | Spesifik tapi belum riset |
| **Research Problem** | Belum ada studi membandingkan overhead TLS 1.3 vs DTLS pada MQTT di IoT RAM < 64KB | Bisa dirancang eksperimennya |

### Symptom vs Root Cause

Apa yang diamati (gejala) ≠ mengapa terjadi (akar masalah). Gunakan **5 Whys** atau **Fishbone Diagram** untuk menggali.

Contoh: "User meninggalkan checkout" (symptom) → "Waktu loading > 8 detik karena API call sequential" (root cause).

### System Thinking

Setiap masalah riset TI harus terikat pada komponen sistem: **Input → Process → Output → Outcome → Constraints → Stakeholders**.

### Problem Quality Check

Masalah riset yang layak harus memenuhi 5 kriteria:
- **Clarity** — Satu orang membaca akan paham
- **Measurability** — Ada metrik kuantitatif
- **Relevance** — Penting untuk domain
- **Testability** — Bisa gagal (falsifiable)
- **Impact** — Ada kontribusi jika terjawab

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan | Menyelesaikan masalah (*solve*) | Memahami dan membuktikan (*understand & prove*) |
| Masalah | Bug, error, fitur belum ada | Gap dalam pengetahuan |
| Scope | Selesaikan semua yang perlu | Batasi agar bisa dibuktikan |
| Output | Working system | Evidence, paper, replicable findings |

### Istilah Penting

- **Problem Statement** — Formulasi tertulis: konteks sistem + gap + dampak + justifikasi
- **System Context** — Deskripsi lengkap: input, proses, output, outcome, constraints, stakeholders
- **Problem Drift** — Masalah "bermutasi" dari pendahuluan ke metodologi karena statement awal tidak presisi
- **Solution-First Thinking** — Memulai dari solusi tanpa masalah yang jelas — berbahaya dalam riset
- **Operational Definition** — Definisi variabel yang cukup jelas agar peneliti lain bisa mengukur hal yang sama

---

## Template A.2 — Problem Statement Builder

```
PROBLEM STATEMENT BUILDER

Domain & Konteks
  Domain   : Keamanan Informasi / Cybersecurity
  Konteks  : Penggunaan media sosial Instagram di       kalangan mahasiswa Indonesia

System Context
  Input       : Perilaku dan kebiasaan pengguna Instagram dalam mengamankan akun dan data pribadi
  Process     : Survei kuesioner untuk mengukur tingkat kesadaran keamanan informasi dan privasi
  Output      : Persentase tingkat kesadaran pengguna berdasarkan aspek keamanan dan privasi
  Outcome     : Rekomendasi edukasi keamanan digital untuk meningkatkan literasi pengguna
  Constraints : Self-reported data, sampel terbatas 150 responden, format jawaban ya/tidak
  Stakeholders: Pengguna Instagram, peneliti, institusi pendidikan, platform Instagram

Fenomena → Problem
  Fenomena yang diamati             : Pengguna Instagram aktif membagikan data pribadi tanpa memahami risikonya
  Gejala (symptom) yang terukur     : Hanya 39% pengguna aktifkan 2FA, hanya 31% membaca kebijakan privasi Instagram
  Masalah yang didiagnosis          : Rendahnya literasi keamanan digital pengguna Instagram di Indonesia
  Masalah riset (researchable)      : Seberapa tinggi tingkat kesadaran keamanan informasi dan privasi pengguna
                                      Instagram di Indonesia?
  Variabel yang terukur             : Persentase penggunaan 2FA, kekuatan password, aktivasi pengaturan privasi, pemahaman
                                      kebijakan privasi

Problem Quality Check
  [x] Clarity — Apakah satu orang membaca akan paham?
  [x] Measurability — Apakah ada metrik kuantitatif?
  [x] Relevance — Apakah penting untuk domain?
  [x] Testability — Apakah bisa gagal?
  [x] Impact — Apakah ada kontribusi jika terjawab?

Problem Statement (1 paragraf):
  Meskipun pengguna Instagram di Indonesia telah mencapai 88,86 juta pada 2024, tingkat kesadaran keamanan informasi dan privasi pengguna masih rendah — ditandai dengan hanya 39% yang mengaktifkan autentikasi dua faktor dan 31% yang membaca kebijakan privasi platform. Kondisi ini meningkatkan risiko pencurian identitas dan penyalahgunaan data pribadi. Oleh karena itu, diperlukan analisis terukur terhadap tingkat kesadaran keamanan informasi dan privasi pengguna Instagram guna menjadi dasar rekomendasi edukasi literasi digital yang efektif.
```

---

## Latihan 1 — Dari Topik ke Masalah Riset

Pilih satu topik di bidang TI yang diminati. Transformasikan melalui 5 tahap Problem Formation Model.

**Topik awal:** Kesadaran Keamanan Informasi Pengguna Instagram

| Tahap | Hasil |
|-------|-------|
| Reality | Jutaan pengguna Instagram aktif membagikan data pribadi setiap hari tanpa mempertimbangkan risiko keamanan |
| Observed Issue (Symptom) | Hanya 39% pengguna mengaktifkan 2FA dan hanya 31% membaca kebijakan privasi Instagram |
| Diagnosed Problem (Root Cause) | Rendahnya literasi digital pengguna terkait praktik keamanan akun dan perlindungan data pribadi |
| Researchable Problem | Seberapa tinggi tingkat kesadaran keamanan informasi dan privasi pengguna Instagram Indonesia, dan faktor apa yang mempengaruhinya? |
| Measurable Variable | Persentase penggunaan 2FA, kekuatan password, aktivasi privacy setting, frekuensi ganti password |

**Apakah terjebak solution-first thinking?** [] Ya / [x] Tidak
> Jika ya, kembali ke tahap mana? ________________________

---

## Latihan 2 — System Context Decomposition

Gambarkan konteks sistem dari masalah riset di Latihan 1.

| Komponen | Deskripsi |
|----------|----------|
| Input | Jawaban kuesioner ya/tidak dari 150 pengguna Instagram usia 18+ |
| Process | Analisis persentase per pertanyaan, perbandingan berdasarkan gender |
| Output | Skor persentase kesadaran keamanan dan privasi per aspek |
| Outcome | Rekomendasi edukasi literasi digital untuk pengguna Instagram Indonesia |
| Constraints | Format jawaban terbatas ya/tidak, sampel tidak merepresentasikan seluruh demografi Indonesia |
| Stakeholders | Pengguna Instagram, peneliti TI, institusi pendidikan, tim keamanan Meta/Instagram |

**Komponen mana yang paling relevan dengan masalah riset?** Process — karena metode analisis menentukan seberapa valid kesimpulan yang dihasilkan dari data kuesioner

---

## Latihan 3 — Problem Quality Check

Evaluasi problem statement yang sudah dibuat menggunakan 5 kriteria.

| Kriteria | Skor (1-5) | Justifikasi |
|----------|-----------|-------------|
| Clarity | 4 | Masalah cukup jelas — rendahnya kesadaran 2FA dan kebijakan privasi mudah dipahami, namun belum spesifik pada kelompok usia tertentu |
| Measurability | 4 | Ada metrik kuantitatif berupa persentase, namun instrumen ya/tidak kurang menangkap gradasi kesadaran secara mendalam |
| Relevance | 5 | Sangat relevan — 88 juta pengguna Instagram Indonesia menjadikan isu ini krusial untuk keamanan digital nasional |
| Testability | 3 | Bisa diuji lewat survei, namun hasil bisa bias karena responden menjawab sesuai yang "seharusnya" bukan kondisi nyata |
| Impact | 4 | Jika terjawab, memberikan dasar kebijakan edukasi digital — namun perlu skala sampel lebih besar agar berdampak lebih luas |

**Skor total:** 20 / 25

**Problem statement versi final (1 paragraf):**
> Rendahnya kesadaran keamanan informasi pengguna Instagram di Indonesia — yang tercermin dari minimnya adopsi autentikasi dua faktor (39%) dan pemahaman kebijakan privasi (31%) — menciptakan celah risiko pencurian identitas dan penyalahgunaan data pribadi yang signifikan. Penelitian ini bertujuan menganalisis tingkat kesadaran tersebut secara terukur sebagai landasan rekomendasi edukasi literasi keamanan digital yang tepat sasaran.

---

## Refleksi

> Bandingkan "masalah" yang biasa ditemui saat coding (bug, error) dengan masalah riset. Apa perbedaan fundamental dalam cara mendefinisikan dan mendekati keduanya?

**Jawaban:**
> Bug atau error saat coding bersifat konkret dan langsung terlihat — ada pesan error, ada baris kode yang salah, dan solusinya bisa langsung dicoba. Masalah riset justru sebaliknya: tidak selalu terlihat jelas, harus didefinisikan dulu sebelum bisa dijawab, dan "solusi" belum boleh diasumsikan sejak awal. Perbedaan fundamentalnya adalah — bug punya jawaban benar yang pasti, sedangkan masalah riset punya jawaban yang perlu dibuktikan dan bisa saja hasilnya mengejutkan atau bahkan menggugurkan asumsi awal peneliti.