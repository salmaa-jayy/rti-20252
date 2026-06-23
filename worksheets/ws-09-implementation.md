# WS-09: Implementation & Environment

> **Bab 9 — Implementasi Riset & Kontrol Lingkungan**

---

## Ringkasan Materi

### Implementasi Riset ≠ Coding Biasa

Tujuan implementasi riset bukan membuat software yang berfungsi, melainkan membangun **instrumen pengukuran yang konsisten**. Setiap modul harus di-mapping ke variabel (dari Bab 6), parameter harus config-driven, dan logging aktif dari hari pertama.

> **Mengapa reproducibility penting?** Sains dibangun di atas prinsip verifikasi — temuan harus bisa dikonfirmasi oleh peneliti lain. _Replicability crisis_ yang terjadi di banyak paper riset ML/AI disebabkan oleh environment tidak terdokumentasi: orang lain tidak bisa reproduksi, hasil diragukan, kepercayaan terhadap temuan hilang. Prinsip: **dokumentasi environment = snapshot kredibilitas riset Anda.**

### Reproducible Implementation Model

```
Design → Implementation → Environment Setup → Execution Consistency → Reproducibility → Trustworthy Result
```

Setiap transisi memiliki syarat:
- Design → Implementation: kode sesuai mapping variabel-ke-komponen
- Implementation → Environment: versi, dependency, seed, path, OS eksplisit
- Environment → Consistency: seed terkunci, urutan deterministik
- Consistency → Reproducibility: dokumentasi lengkap
- Reproducibility → Trust: siapa pun ikuti dokumentasi → hasil sama/serupa

### Repeatability vs Reproducibility

| Level | Peneliti | Environment | Hasil |
|-------|---------|-------------|-------|
| **Repeatability** | Sama | Sama | Sama persis |
| **Reproducibility** | Berbeda | Berbeda (ikuti docs) | Sama/serupa |

Capai **repeatability** dulu, baru **reproducibility**.

### Engineering vs Research Perspective

| Aspek | Engineering | Research |
|-------|-----------|---------|
| Tujuan | Sistem berfungsi untuk user | Instrumen pengukuran konsisten |
| Dependency | Update ke terbaru | Lock di versi spesifik |
| Testing | Unit, integration, E2E | Repeatability test (run ulang → sama?) |
| Dokumentasi | User guide, API docs | Environment spec, execution steps, expected output |
| Config | Default masuk akal | Setiap parameter eksplisit & adjustable |

### Jebakan Kognitif

1. Menunda environment setup → bug sulit dilacak
2. Tidak pakai version control → hasil tidak bisa direkonstruksi
3. Menolak Docker/container → "di laptop saya bisa" saat review
   - **Docker** = teknologi container yang "membungkus" aplikasi beserta seluruh dependency-nya dalam satu unit terisolasi. Hasilnya: kode berjalan identik di laptop, server, maupun reviewer lain. Intro singkat: `docker run -v $(pwd):/workspace environment-image python run_experiment.py`
4. 3× hasil sama ≠ repeatable (bisa cache/state tersimpan)

### Dependency Locking

Mengandalkan "install library terbaru" berbahaya: versi berbeda = perilaku berbeda = hasil tidak reproducible. Praktik:
- **Python**: buat `requirements.txt` dengan versi eksplisit: `scikit-learn==1.3.2`, lalu kunci dengan `pip freeze > requirements.txt`
- **Conda**: gunakan `conda env export > environment.yml` untuk snapshot lengkap
- **Node.js/R/Julia**: gunakan `package-lock.json` / `renv.lock` / `Project.toml` — semua fungsi serupa: lock versi + hash

### Istilah Penting

- **Environment Specification** — Deskripsi lengkap: hardware, OS, runtime, library + versi, config, seed
- **Dependency** — Komponen eksternal yang harus di-lock versinya
- **Config-driven** — Parameter dieksternalisasi ke file konfigurasi, bukan hardcode

---

## Template A.9 — Dokumentasi Setup Eksperimen

```
EXPERIMENT SETUP DOCUMENTATION

Hardware:
  CPU     : Intel Core i5/i7 (spesifikasi umum laptop mahasiswa)
  RAM     : 8 GB DDR4 (minimum untuk analisis data kuesioner)
  GPU     : Tidak diperlukan — analisis statistik berbasis CPU
  Storage : Minimal 10 GB free space untuk data & output

Software:
  OS        : Windows 10/11 atau macOS
  Runtime   : Python 3.10+ / R 4.3+
  Framework : Google Forms (pengumpulan data) +
              SPSS / Python (analisis statistik)

Dependencies:
| Library | Version | Sumber | Hash/Checksum |
|---------|---------|--------|---------------|
| pandas       | 2.1.0   | PyPI   | sha256:abc123...      |
| scipy        | 1.11.3  | PyPI   | sha256:def456...      |
| statsmodels  | 0.14.0  | PyPI   | sha256:ghi789...      |
| scikit-learn | 1.3.2   | PyPI   | sha256:jkl012...      |
| matplotlib   | 3.8.0   | PyPI   | sha256:mno345...      |
| seaborn      | 0.13.0  | PyPI   | sha256:pqr678...      |

Konfigurasi:
  Config file     : config.yaml (threshold, seed, path data)
  Random seed     : 42 (ditetapkan di Python + NumPy)
  Hyperparameters : alpha = 0.05, effect_size_min = 0.3,
                    min_sample = 200, cronbach_alpha_min = 0.7

Reproducibility Check:
  [x] Dependency terdokumentasi (requirements.txt / lock file)
  [x] Seed ditetapkan di semua level (Python, NumPy, framework)
  [x] Config di version control
  [x] README instruksi reproduksi lengkap
```

---

## Latihan 1 — Environment Specification

Dokumentasikan environment untuk eksperimen Anda (boleh environment saat ini atau yang direncanakan).

| Komponen | Spesifikasi |
|----------|------------|
| CPU | Intel Core i5/i7 generasi 10–12, minimal 4 core (analisis korelasi tidak butuh CPU berat) |
| RAM | 8 GB DDR4 — cukup untuk dataset kuesioner 200+ responden |
| GPU | Tidak diperlukan — korelasi Spearman dan regresi logistik berbasis CPU |
| OS | Windows 10/11 atau macOS — sesuai laptop mahasiswa |
| Runtime | Python 3.10+ dengan Jupyter Notebook sebagai environment kerja |
| Framework | pandas + scipy untuk analisis; Google Forms untuk pengumpulan data |
| Random Seed | 42 — ditetapkan di Python (random.seed(42)) dan NumPy (np.random.seed(42)) |

**Dependencies (minimal 5):**

| Library | Version | Alasan Dibutuhkan |
|---------|---------|-------------------|
| pandas | 2.1.0 | Membaca, membersihkan, dan memanipulasi data kuesioner dari CSV export Google Forms |
| scipy | 1.11.3 | Menjalankan uji korelasi Spearman (scipy.stats.spearmanr) antar IV dan DV |
| statsmodels | 0.14.0 | Menjalankan regresi logistik untuk identifikasi faktor persepsi paling dominan |
| pingouin | 0.5.3 | Menghitung Cronbach's Alpha untuk validasi reliabilitas instrumen kuesioner |
| matplotlib | 3.8.0 | Visualisasi distribusi skor Likert dan heatmap korelasi antar variabel |
| seaborn | 0.13.0 | Visualisasi yang lebih rapi untuk heatmap korelasi dan boxplot per faktor |

---

## Latihan 2 — Repeatability Test Plan

Rancang tes repeatability sederhana: jalankan kode yang sama 3× di environment yang sama.

| Run | Seed | Metrik Utama | Hasil Sama? |
|-----|------|-------------|-------------|
| 1 | 42 | Koefisien korelasi Spearman (r) per faktor IV | — (referensi) |
| 2 | 42 | Koefisien korelasi Spearman (r) per faktor IV | [x] Ya / [ ] Tidak |
| 3 | 42 | Koefisien korelasi Spearman (r) per faktor IV | [x] Ya / [ ] Tidak |

**Jika hasil berbeda, kemungkinan penyebab:** Untuk analisis korelasi Spearman pada data kuesioner yang sudah fix, hasil seharusnya selalu identik karena tidak ada randomness dalam perhitungannya. Jika berbeda, kemungkinan penyebabnya adalah: (1) file CSV export Google Forms yang berbeda versi karena ada responden baru masuk di antara run, (2) filter attention check yang tidak konsisten antar run karena threshold tidak dikunci di config, atau (3) versi library yang berbeda di environment yang tidak terkontrol.

> Penyebab umum non-repeatability:
> - **Thermal throttling** — CPU/GPU overheating pada run berturut-turut → clock speed turun → waktu eksekusi berubah
> - **Background process** — antivirus scan, update OS, atau cloud sync aktif saat run berlangsung
> - **Cache dari run sebelumnya** — hasil tersimpan di memori/disk sehingga run berikutnya tidak menjalankan komputasi penuh
> - **Random state tidak dikontrol di semua level** — Python seed di-set, tapi NumPy/PyTorch/TensorFlow punya seed independen

___________________________________________________

**Checklist kontrol yang sudah diterapkan:**
- [✓] Random seed di-set di semua level
- [✓] Tidak ada background process yang mengganggu
- [✓] Cache dibersihkan antar-run
- [✓] Config file yang sama untuk semua run

---

## Latihan 3 — README Eksperimen

Tulis README minimum untuk eksperimen Anda (6 komponen wajib).

```
# Judul Eksperimen: Analisis Faktor Persepsi terhadap Adopsi 2FA pada Mahasiswa Pengguna Instagram di Kebumen

## 1. Environment
> - OS      : Windows 10/11 atau macOS
- Python  : 3.10+
- Runtime : Jupyter Notebook
- RAM min : 8 GB
## 2. Installation
> Clone repo terlebih dahulu
git clone https://github.com/salmaa-jayy/rti-20252.git
cd rti-20252
> Install semua dependencies
pip install -r requirements.txt

## 3. Data
> - Sumber  : Export CSV dari Google Forms
- Format  : CSV (kolom = item kuesioner, baris = responden)
- Ukuran  : ~200 baris x 20 kolom
- Path    : /data/raw/responses.csv
- Catatan : Data mentah tidak di-push ke GitHub (privacy).
            Gunakan data/sample/sample_responses.csv
            untuk uji coba reproduksi

## 4. Execution
> Jalankan notebook secara berurutan:
jupyter notebook
Urutan notebook:
> 01_data_cleaning.ipynb   → filter attention check
> 02_reliability.ipynb     → uji Cronbach's Alpha
> 03_correlation.ipynb     → korelasi Spearman IV–DV
> 04_regression.ipynb      → regresi logistik
> 05_visualization.ipynb   → heatmap + boxplot

## 5. Configuration
> Edit config.yaml untuk ubah parameter:
alpha_threshold : 0.05      # threshold signifikansi
effect_size_min : 0.3       # minimal r korelasi moderat
min_sample      : 100       # target minimum responden
cronbach_min    : 0.7       # batas reliabilitas instrumen
random_seed     : 42        # seed untuk reproduksi
data_path       : data/raw/responses.csv

## 6. Expected Output
> Contoh output korelasi Spearman yang diharapkan:
| Faktor            | r     | p-value | Signifikan? |
|-------------------|-------|---------|-------------|
| Kemudahan 2FA     | 0.412 | 0.003   | Ya          |
| Manfaat 2FA       | 0.381 | 0.008   | Ya          |
| Kesadaran risiko  | 0.298 | 0.067   | Tidak       |
| Pengaruh sosial   | 0.244 | 0.112   | Tidak       | 

```

---

## Refleksi

> Apakah eksperimen Anda saat ini bisa direproduksi oleh orang lain tanpa bantuan Anda? Komponen apa yang masih hilang?

**Level saat ini:** [x] Repeatability / [ ] Reproducibility / [ ] Belum keduanya
**Komponen yang belum terdokumentasi:**
> Reproducibility penuh belum tercapai karena dua hal. Pertama, data mentah kuesioner tidak bisa dipublikasi di GitHub karena menyangkut privasi responden — sehingga peneliti lain tidak bisa mereproduksi dari titik nol tanpa dataset yang sama. Solusinya adalah menyediakan sample data anonim dan synthetic data generator di repo. Kedua, instrumen kuesioner (item-item Likert) belum divalidasi Cronbach's Alpha karena pengumpulan data belum dilakukan — jadi notebook 02_reliability.ipynb belum bisa dijalankan dengan data nyata. Ini adalah batasan yang wajar untuk tahap proposal, dan akan diselesaikan setelah data terkumpul.