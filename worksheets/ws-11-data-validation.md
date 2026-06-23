# WS-11: Data Validation & Integrity

> **Bab 11 — Validasi Data & Integritas**

---

## Ringkasan Materi

### Data Trust Model

```
Raw Data → Data Cleaning → Consistency Check → Validation Process → Trusted Data
```

Data mentah belum bisa dipercaya. Harus melewati pipeline validasi sebelum siap untuk analisis statistik.

### Empat Pilar Data Quality

| Pilar | Deskripsi | Contoh Pelanggaran |
|-------|----------|-------------------|
| **Accuracy** | Nilai dalam range masuk akal | Akurasi = 1.5 (di luar [0,1]) |
| **Consistency** | Format seragam di semua run | Run 1: CSV, Run 2: JSON |
| **Completeness** | Tidak ada data hilang dari plan | 97 dari 100 run tercatat |
| **Validity** | Data sesuai desain eksperimen | Parameter baseline tercampur treatment |

### Proses Validasi Progresif

1. **Format validation** — Tipe file, header, kolom
2. **Range validation** — Nilai dalam batas logis
3. **Consistency validation** — Format seragam antar-run
4. **Logic validation** — Data cocok dengan desain eksperimen

Jika gagal di langkah awal → tidak perlu lanjut.

### Anomaly Detection — 3 Jenis

| Jenis | Deskripsi | Deteksi |
|-------|----------|---------|
| **Statistical outlier** | Nilai di luar distribusi normal | IQR: < Q1-1.5×IQR atau > Q3+1.5×IQR |
| **Contextual anomaly** | Normal absolut, abnormal dalam konteks | Run 1-10: ~91%, Run 11-20: ~88% |
| **Pattern anomaly** | Pola sistematis (bukan random) | Performa menurun berurutan |

**Prinsip:** Detect → Investigate → Document → Decide — **JANGAN langsung hapus.**

### Engineering vs Research Validation

| Aspek | Engineering | Research |
|-------|-----------|---------|
| Tujuan | Data sesuai spesifikasi bisnis | Data layak untuk analisis statistik |
| Missing data | Impute / set default | Investigasi penyebab → dokumentasi |
| Outlier | Bug → fix | Mungkin temuan → investigasi |
| Dokumentasi | Minimal (log error) | Komprehensif (anomali + keputusan) |

### Jebakan Kognitif

1. "Logging otomatis ≠ data benar" → bisa ada bug di logger
2. "Outlier = hapus" → bisa jadi temuan penting
3. "Dataset kecil tidak perlu validasi" → justru lebih rentan
4. "Mean normal = data benar" → [94, 95, 93, **44**, 94] → mean 84% terlihat wajar

---

## Template A.11 — Data Validation Checklist

```
DATA VALIDATION CHECKLIST

Completeness:
  [x] Semua skenario tercakup (pilot + full + analisis)
  [x] Jumlah run sesuai rencana (7 run total)
  [x] Tidak ada file output hilang
  Missing: 0 dari 7 data points (kondisi ideal pasca pengumpulan)

Format Consistency:
  [x] Semua file format sama (CSV)
  [x] Header konsisten (kolom = item kuesioner, baris = responden)
  [x] Tipe data konsisten (skor Likert = integer 1–5,
      % adopsi = float, p-value = float)

Range & Logic:
  [x] Nilai dalam range masuk akal
  [x] Tidak ada waktu negatif
  [x] Metrik 0–100%, tidak di luar range
  Anomali ditemukan: Responden dengan jawaban flat
                     (semua item = 5 atau semua = 1)
                     terindikasi tidak membaca pertanyaan

Cross-Validation:
  [x] Run identik → hasil mendekati (robustness check
      3 run dengan seed berbeda, perbedaan r < 0.05)
  [x] Trend konsisten dengan ekspektasi teori (persepsi kemudahan diprediksi paling signifikan
      sesuai TAM Davis 1989)

Keputusan:
  [x] Data siap analisis (setelah cleaning attention check)
  [ ] Perlu cleaning
  [ ] Perlu re-run (skenario: ____)
```

---

## Latihan 1 — Completeness Check

Verifikasi apakah semua data yang direncanakan sudah terkumpul.

| Skenario | Run Direncanakan | Run Tercatat | Missing | Alasan |
|----------|-----------------|-------------|---------|--------|
| Pilot test validasi instrumen | 1 | 1 | 0 | — |
| Pengumpulan data penuh (100 responden) | 1 | 1 | 0 | — |
| Analisis korelasi Spearman | 1 | 1 | 0 | — |
| Regresi logistik | 1 | 1 | 0 | — |
| Robustness check seed 42 | 1 | 1 | 0 | — |
| Robustness check seed 123 | 1 | 1 | 0 | — |
| Robustness check seed 999 | 1 | 1 | 0 | — |

**Total expected:** 7 | **Total actual:** 7 | **Missing:** 0

**Keputusan untuk data missing:**
> Tidak ada data missing pada kondisi ideal. Namun jika terjadi missing pada skenario pengumpulan data penuh (misalnya responden tidak menyelesaikan kuesioner), keputusannya adalah: responden dengan lebih dari 3 item tidak diisi dinyatakan invalid dan dikeluarkan dari dataset, kemudian penyebaran kuesioner dilanjutkan hingga total responden valid mencapai 100+.
---

## Latihan 2 — Anomaly Investigation

Konteks riset ini: metrik utama adalah skor Likert per faktor (1–5), bukan accuracy. Berikut simulasi deteksi anomali pada skor rata-rata faktor kemudahan 2FA per responden:

**Dataset sampel (atau data Anda sendiri):**

| Run | Accuracy (%) |
|-----|-------------|
| 1 | *91.2* |
| 2 | *90.8* |
| 3 | *91.5* |
| 4 | *78.3* |
| 5 | *91.0* |

**Deteksi outlier:**
- Q1 = ____ | Q3 = ____ | IQR = ____
- Batas bawah (Q1 - 1.5×IQR) = ____
- Batas atas (Q3 + 1.5×IQR) = ____
- Outlier terdeteksi: ____

**Investigasi (untuk setiap outlier):**

| Outlier | Nilai | Kemungkinan Penyebab | Keputusan |
|---------|-------|---------------------|-----------|
| *Run 4* | *78.3* | *Contoh: thermal throttling setelah 3 run berturut* | *Re-run dengan cooling interval* |

---

## Latihan 3 — Validation Report

Buat laporan validasi ringkas untuk dataset eksperimen Anda.

**1. Completeness:** 100% data terkumpul
**2. Format:** [x] Konsisten / [ ] Ada inkonsistensi: ____
**3. Range check (anomali):** ____
**4. Logic check:** [ ] Parameter sesuai plan / [ ] Ada ketidaksesuaian: ____

**Kesimpulan:** [ ] Data siap analisis / [ ] Perlu tindakan: ____

---

## Refleksi

> Apa perbedaan antara "data yang benar" dan "data yang dipercaya"? Mengapa proses validasi formal diperlukan meskipun data dikumpulkan secara otomatis?

> ___________________________________________________
> ___________________________________________________
