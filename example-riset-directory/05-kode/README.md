# 05-kode

Notebook analisis Python — Tahap pengolahan & analisis data.

## Struktur

```
05-kode/
├── 01_data_cleaning.ipynb       # Filter attention check & flat response
├── 02_reliability.ipynb         # Uji Cronbach's Alpha per faktor IV
├── 03_descriptive.ipynb         # Statistik deskriptif (mean, std, median)
├── 04_correlation.ipynb         # Korelasi Spearman IV–DV
├── 05_regression.ipynb          # Regresi logistik faktor dominan
├── 06_visualization.ipynb       # Bar chart, heatmap, box plot
├── config.yaml                  # Parameter konfigurasi analisis
└── requirements.txt             # Dependencies Python
```

## Instalasi

```bash
git clone https://github.com/salmaa-jayy/rti-20252.git
cd rti-20252
pip install -r 05-kode/requirements.txt
jupyter notebook
```

## Dependencies

| Library | Version | Kegunaan |
|---------|---------|---------|
| pandas | 2.1.0 | Membaca & manipulasi data CSV |
| scipy | 1.11.3 | Uji korelasi Spearman |
| statsmodels | 0.14.0 | Regresi logistik |
| pingouin | 0.5.3 | Cronbach's Alpha |
| matplotlib | 3.8.0 | Visualisasi dasar |
| seaborn | 0.13.0 | Heatmap & box plot |

## Konfigurasi (config.yaml)

```yaml
alpha_threshold : 0.05      # threshold signifikansi
effect_size_min : 0.3       # minimal r korelasi moderat
min_sample      : 100       # target minimum responden
cronbach_min    : 0.7       # batas reliabilitas instrumen
random_seed     : 42        # seed untuk reproduksi
data_path       : 04-data/processed/responses_clean.csv
```

## Urutan Eksekusi

Jalankan notebook secara berurutan:
1. `01_data_cleaning.ipynb` → hasilkan `responses_clean.csv`
2. `02_reliability.ipynb` → validasi instrumen sebelum analisis
3. `03_descriptive.ipynb` → gambaran umum data
4. `04_correlation.ipynb` → jawab RQ utama
5. `05_regression.ipynb` → identifikasi faktor dominan
6. `06_visualization.ipynb` → hasilkan semua grafik untuk paper

## Acuan

- Rencana analisis: [../09-docs/ws-13-preprocessing.md](../09-docs/ws-13-preprocessing.md)
- Rencana visualisasi: [../09-docs/ws-12-result-presentation.md](../09-docs/ws-12-result-presentation.md)
