# WS-15: Scientific Writing

> **Bab 15 — Penulisan Ilmiah**

---

## Ringkasan Materi

### Scientific Argument Flow

```
Problem → Gap → RQ → Method → Result → Analysis → Conclusion → Contribution
```

Paper ilmiah adalah **satu argumen utuh** dari masalah ke kontribusi. Setiap node harus terhubung logis ke node sebelum dan sesudahnya.

### Struktur IMRAD

| Section | Peran | Pertanyaan Kunci |
|---------|-------|-----------------|
| **Introduction** | Motivasi + frame | Why is this needed? |
| **Method** | Deskripsi (reproducible) | How was it done? |
| **Results** | Laporan objektif | What was found? |
| **Discussion** | Interpretasi + refleksi | What does it mean? |
| **Conclusion** | Ringkasan + kontribusi | So what? |

### Logical Flow — "Red Thread"

Setiap paragraf menjawab satu pertanyaan dan memicu pertanyaan berikutnya. Alur logis ini harus terasa di tiga level:
1. **Antar-kalimat** dalam paragraf
2. **Antar-paragraf** dalam section
3. **Antar-section** dalam paper

### Internal Consistency

Setiap elemen yang dijanjikan di Introduction harus hadir di Discussion/Conclusion.

**Consistency Matrix:**
```
           Intro  Method  Result  Discuss  Conclude
RQ1          ✓      ✓       ✓       ✓        ✓
RQ2          ✓      ✓       ✓       ✗ ←      ✓
Metrik-X     ✗      ✗       ✓ ←     ✗        ✗
```
**Masalah:** RQ2 dibahas di semua bagian kecuali Discussion. Metrik-X muncul di Result tapi tidak diperkenalkan di Method.

### Writing Quality Triad

| Kualitas | Deskripsi | Contoh Buruk → Baik |
|----------|----------|---------------------|
| **Clarity** | Dipahami sekali baca | "Performa meningkat" → "Accuracy meningkat dari 85.3% ke 89.7%" |
| **Precision** | Istilah eksak, tanpa ambiguitas | "signifikan" → "signifikan secara statistik (p=0.003, d=1.2)" |
| **Conciseness** | Setiap kata menambah informasi | Hapus kalimat redundan, filler words |

### Urutan Penulisan yang Disarankan

1. **Method & Results** — paling stabil, tulis pertama
2. **Discussion** — interpretasi berdasarkan hasil
3. **Introduction** — frame sesuai temuan aktual
4. **Abstract & Conclusion** — terakhir

### Target Jumlah Kata

| Section | Target |
|---------|--------|
| Introduction | 500–700 |
| Related Work | 700–1000 |
| Method | 800–1200 |
| Results | 500–800 |
| Discussion | 600–900 |
| Conclusion | 200–400 |

### Jebakan Kognitif

1. "Lebih panjang = lebih lengkap" → conciseness lebih berharga
2. "Introduction harus ditulis pertama" → justru ditulis terakhir
3. "Jargon teknis = lebih ilmiah" → clarity lebih penting
4. "Discussion = ringkasan Results" → Discussion = interpretasi + konteks

---

## Template A.15 — Paper Structure Checklist

```
PAPER STRUCTURE CHECKLIST

Title   : nalisis Faktor Persepsi yang Berhubungan dengan
          Rendahnya Adopsi 2FA pada Mahasiswa Pengguna
          Instagram di Kebumen
Target  : [x] Jurnal  [ ] Konferensi  [ ] Laporan

Section Check:
  [x] Abstract — masalah, metode, hasil utama, kontribusi (max 250 kata)
  [x] Introduction — konteks → gap → RQ → kontribusi → struktur paper
  [x] Related Work — concept-centric, gap positioning
  [x] Method — reproducible: desain, variabel, metrik, setup, prosedur
  [x] Results — tabel + grafik + observasi (tanpa interpretasi)
  [x] Discussion — interpretasi, perbandingan, implikasi, limitation
  [x] Conclusion — jawaban RQ, kontribusi, future work

Consistency Matrix:
  [x] RQ di Introduction = RQ di Method = RQ di Conclusion
  [x] Variabel di Method = variabel di Results
  [x] Klaim di Discussion didukung data di Results
  [x] Limitasi di Discussion di-address di Conclusion/Future Work

Writing Quality:
  [x] Clarity — mudah dipahami tanpa re-read
  [x] Precision — tidak ada istilah ambigu
  [x] Conciseness — tidak ada kalimat redundan
```

---

## Latihan 1 — Paper Outline

Buat outline paper untuk riset Anda menggunakan struktur IMRAD.

| Section | Konten Utama (2-3 kalimat) | Target Kata |
|---------|---------------------------|------------|
| Abstract | *Contoh: Sistem rekomendasi memiliki akurasi tinggi tapi satisfaction rendah. Studi ini menguji CF+context signal. Hasil: satisfaction naik 38% tanpa penurunan RMSE signifikan.*Hanya 39% mahasiswa aktifkan 2FA. Studi menguji 4 faktor persepsi dengan Likert + Spearman pada 94 mahasiswa Kebumen. Hasil: kemudahan (r=0.41) dan manfaat (r=0.38) signifikan. | 220 |
| Introduction | Konteks: 88 juta pengguna Instagram Indonesia, 39% adopsi 2FA. Gap: studi terdahulu hanya ukur persentase tanpa jelaskan penyebab. RQ: faktor persepsi apa yang berhubungan? | 600 |
| Related Work | TAM Davis (1989). Review 5 studi keamanan Instagram Indonesia. Method gap + context gap. | 1000 |
| Method | Survei korelasional. IV: 4 faktor (14 item Likert). DV: adopsi 2FA. CV: usia & jurusan. 100 target responden (94 valid). Spearman + regresi logistik. | 1000 |
| Results | Tabel korelasi 4 faktor. Bar chart r ± std. Heatmap. % adopsi 41%. 2 faktor signifikan. | 650 |
| Discussion | Interpretasi konsisten TAM. Failure analysis: optimism bias. Limitasi n=94 + self-reported. | 750 |
| Conclusion | Kemudahan (r=0.41) dan manfaat (r=0.38) paling berhubungan. Kontribusi instrumen Likert. Future work: replikasi lintas kota. | 300 |

---

## Latihan 2 — Consistency Matrix

Buat consistency matrix untuk memverifikasi internal consistency paper Anda.

|  | Intro | Method | Result | Discussion | Conclusion |
|--|-------|--------|--------|-----------|-----------|
| RQ (faktor persepsi → adopsi 2FA) | ✓ | ✓ | ✓ | ✓ |
| IV: 4 faktor persepsi | ✓ | ✓ | ✓ | ✓ | ✓ |
DV: adopsi 2FA | ✓ | ✓ | ✓ | ✓ | ✓ |
Metrik: r Spearman + p-value | ~ | ✓ | ✓ | ✓ | ✓ |
Baseline Farida et al. 2024 | ✓ | ✓ | ~ | ✓ | ~ |
TAM Davis 1989 | ✓ | ~ | ✗ | ✓ | ✓ |
n=94 responden | ✗ |✓ | ✓ | ✓ | ~ | 
Klaim kontribusi | ✓ | ✗ | ✗ | ✓ | ✓ |

**Isi setiap sel:** ✓ (ada & konsisten), ✗ (missing), ~ (ada tapi inkonsisten)

**Inkonsistensi yang ditemukan:**
> Jumlah responden (n=94) perlu disebutkan di Introduction sebagai bagian konteks metodologi. Klaim kontribusi perlu satu kalimat singkat di akhir Method.
**Tindakan perbaikan:**
> Tambahkan "...dengan melibatkan 94 mahasiswa Kebumen" di paragraf terakhir Introduction. Tambahkan satu kalimat di akhir Method: "Pendekatan ini merupakan perbaikan metodologis dari studi terdahulu yang hanya menggunakan instrumen biner."_

---

## Latihan 3 — Writing Quality Check

Ambil satu paragraf dari tulisan Anda (atau tulis paragraf baru) dan evaluasi kualitasnya.

**Paragraf asli:**
> (Hasil penelitian menunjukkan bahwa persepsi kemudahan berhubungan signifikan dengan adopsi 2FA. Hal ini menunjukkan bahwa faktor kemudahan penting untuk diperhatikan dalam upaya meningkatkan keamanan digital mahasiswa.)

| Kriteria | Evaluasi | Perbaikan |
|----------|---------|-----------|
| Clarity | "Berhubungan signifikan" ambigu seberapa kuat? | Tambahkan r=0.41 dan p=0.003 |
| Precision |"Penting untuk diperhatikan" terlalu umum | Spesifikkan: fokus pada penyederhanaan proses pengaktifan |
| Conciseness | Kalimat kedua mengulang kalimat pertama | Gabungkan jadi satu kalimat pada |

**Paragraf setelah perbaikan:**
> (Persepsi kemudahan penggunaan 2FA menunjukkan korelasi moderat yang signifikan dengan adopsi aktualnya pada 94 mahasiswa Kebumen (r=0.41, p=0.003), mengindikasikan bahwa penyederhanaan proses pengaktifan 2FA — bukan sekadar kampanye kesadaran risiko — merupakan intervensi yang lebih menjanjikan untuk meningkatkan keamanan akun mahasiswa.i)

---

## Refleksi

> Apa perbedaan antara menulis "tentang" riset dan menulis sebagai "argumen" riset? Bagaimana urutan penulisan (Method → Discussion → Introduction) mengubah kualitas tulisan?

> 
Menulis sebagai "argumen" berarti setiap kalimat mendorong pembaca menuju satu kesimpulan yang logis. Urutan Method → Discussion → Introduction memaksa kita menulis Introduction berdasarkan temuan aktual hasilnya jauh lebih jujur dan koherensi argumentasinya lebih kuat._
