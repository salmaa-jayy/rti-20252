# 06-output

Hasil olahan data & visualisasi — dihasilkan oleh notebook `05-kode/` dari data bersih `04-data/processed/`.

## Struktur

```
06-output/
├── stats/
│   ├── cronbach_alpha.csv          # Skor α per faktor IV (target ≥ 0.7)
│   ├── descriptive_stats.csv       # Mean, std, median per variabel
│   ├── spearman_results.csv        # r dan p-value per faktor IV vs DV
│   └── logistic_results.csv        # Koefisien regresi logistik
└── figures/
    ├── bar_chart_correlation.png   # Perbandingan r antar 4 faktor IV
    ├── heatmap_correlation.png     # Matriks korelasi semua variabel
    └── boxplot_likert.png          # Distribusi skor Likert per faktor
```

## tables/

| File | Isi |
|------|-----|
| `cronbach_alpha.csv` | Skor α per faktor IV — validasi reliabilitas instrumen sebelum analisis |
| `descriptive_stats.csv` | Statistik deskriptif (mean±std, median, min, max) per variabel, n=94 |
| `spearman_results.csv` | Koefisien r, p-value, CI 95% per faktor IV — hasil utama penelitian |
| `logistic_results.csv` | Koefisien regresi logistik — identifikasi faktor paling dominan |

## figures/

| File | Isi |
|------|-----|
| `bar_chart_correlation.png` | Bar chart r ± std per faktor IV, garis threshold r=0.3 |
| `heatmap_correlation.png` | Matriks korelasi Spearman semua variabel |
| `boxplot_likert.png` | Distribusi skor Likert 1–5 per faktor IV |

## Hasil Simulasi (diupdate setelah data nyata terkumpul)

### Korelasi Spearman (n=94)

| Faktor IV | r (mean±std) | p-value | Signifikan? |
|-----------|--------------|---------|-------------|
| Kemudahan 2FA | 0.41 ± 0.04 | 0.003 | ✅ Ya |
| Manfaat 2FA | 0.38 ± 0.05 | 0.008 | ✅ Ya |
| Kesadaran risiko | 0.29 ± 0.06 | 0.074 | ❌ Tidak |
| Pengaruh sosial | 0.24 ± 0.07 | 0.118 | ❌ Tidak |

> ⚠️ Angka di atas adalah simulasi — akan diupdate setelah data nyata terkumpul.

## Acuan

[../09-docs/ws-12-result-presentation.md](../09-docs/ws-12-result-presentation.md), [../09-docs/ws-14-analysis-interpretation.md](../09-docs/ws-14-analysis-interpretation.md)
