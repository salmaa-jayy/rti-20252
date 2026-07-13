# Tahap 4 — Analisis Data & Visualisasi

**Status:** Menunggu data  
**Bergantung pada:** [tahap-3-pengumpulan-data.md](tahap-3-pengumpulan-data.md)  
**Lokasi kode:** [../05-kode/](../05-kode/)

---

## Tujuan

Mengolah data mentah kuesioner menjadi statistik deskriptif, korelasi Spearman, regresi logistik, dan visualisasi untuk menjawab RQ penelitian.

## Pipeline Analisis

```
responses_clean.csv
  → 02_reliability.ipynb     (Cronbach's Alpha per faktor)
  → 03_descriptive.ipynb     (mean, std, median, distribusi)
  → 04_correlation.ipynb     (Spearman r per faktor IV vs DV)
  → 05_regression.ipynb      (regresi logistik faktor dominan)
  → 06_visualization.ipynb   (bar chart, heatmap, box plot)
```

Cara jalankan (dari root repo):
```bash
cd 05-kode
jupyter notebook
# Jalankan notebook 01–06 secara berurutan
```

## Modul Analisis

| Notebook | Fungsi | Output |
|----------|--------|--------|
| `01_data_cleaning.ipynb` | Filter attention check & flat response | `responses_clean.csv` |
| `02_reliability.ipynb` | Cronbach's Alpha per faktor IV | `cronbach_alpha.csv` |
| `03_descriptive.ipynb` | Statistik deskriptif per variabel | `descriptive_stats.csv` |
| `04_correlation.ipynb` | Korelasi Spearman IV–DV | `spearman_results.csv` |
| `05_regression.ipynb` | Regresi logistik faktor dominan | `logistic_results.csv` |
| `06_visualization.ipynb` | Bar chart, heatmap, box plot | 3 figure PNG |

## Definisi Metrik Utama

**Korelasi Spearman:**
- r ≥ 0.5 → efek besar
- 0.3 ≤ r < 0.5 → efek moderat (threshold relevansi praktis penelitian ini)
- r < 0.3 → efek kecil

**Keputusan hipotesis:**
- p < 0.05 → tolak H₀, faktor signifikan
- p ≥ 0.05 → gagal tolak H₀, faktor tidak signifikan

## Catatan untuk Tahap 5

- Laporkan effect size (r) selain p-value — signifikan statistik ≠ penting secara praktis
- Laporkan CI 95% untuk tiap faktor
- Failure analysis untuk faktor yang tidak signifikan — temukan boundary condition, jangan abaikan
- Robustness check 3 run (seed 42, 123, 999) untuk verifikasi konsistensi hasil

## Acuan

[ws-12-result-presentation.md](ws-12-result-presentation.md), [ws-13-preprocessing.md](ws-13-preprocessing.md), [ws-14-analysis-interpretation.md](ws-14-analysis-interpretation.md)
