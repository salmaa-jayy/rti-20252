# WS-10: Experiment Execution & Data Collection

> **Bab 10 — Eksekusi Eksperimen & Pengumpulan Data**

---

## Ringkasan Materi

### Experiment Execution Pipeline

```
Design → Execution Plan → Controlled Execution → Data Collection → Data Logging → Dataset for Analysis
```

### Multiple Run = Non-Negotiable

Single run **tidak pernah cukup** untuk klaim ilmiah. Minimum 5-10 run per skenario dengan seed berbeda. Multiple run menghasilkan:
- Mean, std, confidence interval
- Distribusi hasil → uji statistik
- Variabilitas → error bar di grafik

### Execution Plan

Setiap eksperimen harus memiliki plan sebelum eksekusi:
- Daftar skenario
- Jumlah run per skenario
- Random seed per run (pre-determined!)
- Urutan eksekusi (randomisasi/counterbalancing)
- Pre-execution checklist

### Data Logging Komprehensif

Setiap run menghasilkan log terstruktur:
1. **Identitas** — Run ID, timestamp, skenario
2. **Konfigurasi** — Semua parameter, seed, code version
3. **Hasil** — Semua metrik, output detail
4. **Metadata** — Waktu eksekusi, resource usage, warning/error

Format: CSV/JSON/database — **bukan stdout yang di-copy-paste**.

### Engineering vs Research Execution

| Aspek | Engineering | Research |
|-------|-----------|---------|
| Run | Sekali (deploy) | Multiple (min 5-10, seed berbeda) |
| Logging | Error log, access log | Semua parameter, metrik, metadata |
| Anomali | Bug → fix → redeploy | Investigasi → dokumentasi → analisis |
| Urutan | Tidak penting | Bisa bias — perlu randomisasi |

### Anomali = Dokumentasi, Bukan Hapus

Run gagal/anomali tidak boleh dihapus tanpa dokumentasi. Bisa jadi:
- **Bug** → fix & re-run (dokumentasikan!)
- **Batas kemampuan metode** → DNF = temuan
- **Data yang bias** jika hanya simpan run "berhasil"

### Jebakan Kognitif

1. "Satu angka cukup" → tanpa distribusi, tidak bisa diuji
2. "Seed tidak penting" → bahkan algoritma deterministik bisa dipengaruhi library stokastik
3. "Run gagal langsung hapus" → kehilangan temuan potensial
4. "Semua run harus hari ini" → thermal throttling, fatigue

---

## Template A.10 — Execution Plan & Data Log

```
EXECUTION PLAN

| Run # | Skenario                        | Seed | Parameter                          | Status  | Waktu   | Output File                    |
|-------|---------------------------------|------|------------------------------------|---------|---------|-------------------------------|
| 1     | Validasi instrumen (pilot test) | 42   | n=20, cronbach_min=0.7             | Planned | ~1 hari | output/cronbach_pilot.csv     |
| 2     | Pengumpulan data penuh          | 42   | n=200+, 4 jurusan, attention check | Planned | ~2 minggu | output/responses_clean.csv  |
| 3     | Analisis korelasi Spearman      | 42   | alpha=0.05, effect_min=0.3         | Planned | ~1 hari | output/spearman_results.csv   |
| 4     | Regresi logistik                | 42   | alpha=0.05, cv=5                   | Planned | ~1 hari | output/logistic_results.csv   |
| 5     | Robustness check (subsampel)    | 42   | n=150, random subsample            | Planned | ~1 hari | output/robustness_check.csv   |
| 6     | Robustness check (subsampel)    | 123  | n=150, random subsample            | Planned | ~1 hari | output/robustness_check_2.csv |
| 7     | Robustness check (subsampel)    | 999  | n=150, random subsample            | Planned | ~1 hari | output/robustness_check_3.csv |

Jumlah runs per skenario : 1–3 (robustness check 3x)
Total runs               : 7

DATA LOG (per run):
  Run ID    : ____________________
  Timestamp : ____________________
  Skenario  : ____________________
  Input     : ____________________
  Output    : ____________________
  Anomali   : ____________________
  Catatan   : ____________________
```

---

## Latihan 1 — Execution Plan

Susun execution plan untuk eksperimen Anda. Tentukan skenario, jumlah run, dan seed sebelum eksekusi.

| Run # | Skenario | Seed | Parameter Kunci | Status |
|-------|----------|------|----------------|--------|
| 1 | Pilot test validasi instrumen Likert | 42 | n=20 responden awal, cronbach_min=0.7 | Planned |
| 2 | Pengumpulan data penuh lintas jurusan | 42 | n=100+, 4 jurusan, filter attention check aktif | Planned |
| 3 | Korelasi Spearman IV–DV (full sample) | 42 | alpha=0.05, effect_size_min=0.3 | Planned |
| 4 | Regresi logistik faktor dominan | 42 | alpha=0.05, 5-fold cross validation | Planned |
| 5 | Robustness check subsampel run 1 | 42 | n=150, random subsample dari data penuh | Planned |
| 6 | Robustness check subsampel run 3 | 999 | n=150, random subsample dari data penuh | Planned |

**Total skenario:** 4(validasi, pengumpulan, korelasi, regresi) +1 robustness check
**Run per skenario:** 1 untuk skenario utama, 3 untuk robustness check
**Total run keseluruhan:** 7

---

## Latihan 2 — Data Log Terstruktur

Desain format data log untuk eksperimen Anda. Tentukan field apa saja yang akan dicatat.

**Identitas:**
| Field | Contoh |
|-------|--------|
| Run ID | run-003 |
| Timestamp | 2025-05-01T09:30:00 |
| Peneliti | Salma Zaidah |
| Versi notebook | commit a3f1b2c (GitHub rti-20252) |

**Konfigurasi:**
| Field | Contoh |
|-------|--------|
| Seed | 42 |
| Code version | commit a3f1b2c |
| Config file | config.yamlv1.2 |

**Hasil:**
| Metrik | Tipe Data | Range Valid |
|--------|----------|-------------|
| Cronbach's Alpha per faktor | float | 0.0 – 1.0 (target ≥ 0.7) |
| Koefisien korelasi Spearman (r) | float | -1.0-1.0 |
| p-value per faktor | float | 0.0 – 1.0 (signifikan jika < 0.05) |
| % adopsi 2FA | float | 0.0 – 100.0 |
| Koefisien relasi logistik | float | tidak terbatas |
| Skor konsistensi pengguna 2FA | float | 1.0 – 5.0 |



**Format output:** [x] CSV / [ ] JSON / [ ] Database / [ ] Lainnya: ____

---

## Latihan 3 — Anomaly Protocol

Rencanakan bagaimana menangani anomali. Untuk setiap jenis, tentukan langkah yang diambil.

| Jenis Anomali | Contoh | Tindakan |
|---------------|--------|----------|
| Run gagal/data corrupt | Export CSV Google Forms rusak atau kolom tidak sesuai skema | Detect: cek jumlah kolom vs skema; Investigate: buka file mentah manual; Document: catat di log anomali; Decide: re-export dari Google Forms dengan filter tanggal yang sama |
| Hasil ekstrem | Cronbach's Alpha sangat rendah (α < 0.5) pada satu faktor IV | Detect: cek output cronbach.csv; Investigate: review item pertanyaan faktor tersebut — kemungkinan item ambigu; Document: catat faktor mana dan α-nya; Decide: revisi item dan ulangi pilot test sebelum pengumpulan data penuh |
| Waktu eksekusi anomali | Notebook analisis berjalan >10 menit padahal dataset hanya 200 baris | Detect: monitor waktu eksekusi per cell; Investigate: cek apakah ada loop yang tidak efisien atau data tidak ter-filter; Document: catat cell mana yang lambat; Decide: optimasi kode atau restart kernel dan clear cache |
| Inkonsistensi dengan run lain | Hasil korelasi Spearman berbeda di robustness check run 1 vs run 2 | Detect: bandingkan output/spearman_results.csv ketiga run; Investigate: cek apakah seed dan filter attention check konsisten; Document: catat perbedaan nilai r dan kemungkinan penyebab; Decide: jika perbedaan > 0.05, laporkan sebagai limitasi stabilitas; jika < 0.05, laporkan rata-rata ketiga run |

**Prinsip:** Detect → Investigate → Document → Decide

---

## Refleksi

> Pernahkah Anda melaporkan hasil riset/tugas dari single run? Apa risikonya? Bagaimana multiple run mengubah kepercayaan terhadap hasil?

**Pengalaman sebelumnya:**
> Pernah mengumpulkan tugas laporan dari single run percobaan di lab — misalnya mencatat satu hasil pengukuran dan langsung menjadikannya kesimpulan. Risikonya adalah hasil tersebut bisa saja kebetulan — noise, kondisi yang tidak representatif, atau error yang tidak terdeteksi. Kalau ternyata run kedua hasilnya beda, seluruh kesimpulan bisa runtuh.
**Yang akan dilakukan berbeda:**
> Selalu jalankan minimal 3 run dengan seed berbeda untuk bagian yang melibatkan randomness (subsampel, split data), dan dokumentasikan setiap run di log terstruktur sejak awal — bukan dicatat belakangan dari ingatan. Dengan multiple run, kepercayaan terhadap hasil jauh lebih tinggi karena bisa ditunjukkan bahwa temuan konsisten, bukan kebetulan satu kali.
