# Tahap 2 — Setup Eksperimen & Validasi

**Status:** Selesai  
**Bergantung pada:** [tahap-1-proposal-desain.md](tahap-1-proposal-desain.md)  
**Lokasi kode:** [../05-kode/](../05-kode/)

---

## Tujuan

Menyiapkan environment analisis, mendokumentasikan execution plan, dan merancang prosedur validasi data sebelum pengumpulan dimulai.

## Deliverable

- [x] Dokumentasi environment Python (WS-09): pandas 2.1.0, scipy 1.11.3, statsmodels 0.14.0, pingouin 0.5.3, matplotlib 3.8.0, seaborn 0.13.0
- [x] Execution plan 7 run (WS-10): pilot test → full collection → Spearman → logistik → 3 robustness check (seed 42, 123, 999)
- [x] Data validation checklist (WS-11): completeness, format, range, logic, cross-validation
- [x] README eksperimen dengan 6 komponen wajib
- [x] config.yaml dengan semua parameter terkunci sebelum data dikumpulkan

## Keputusan Teknis

| Keputusan | Pilihan | Justifikasi |
|-----------|---------|-------------|
| Uji korelasi | Spearman | Data Likert berskala ordinal — Pearson tidak valid |
| Analisis DV | Regresi logistik | DV bersifat dikotomis (aktif/tidak aktif) |
| Normalisasi | Tidak diperlukan | Spearman berbasis ranking, tidak sensitif skala |
| Random seed | 42 | Ditetapkan di Python & NumPy untuk reproduksi |
| Threshold | p < 0.05, r ≥ 0.3 | Ditetapkan SEBELUM data dikumpulkan (anti p-hacking) |

## Catatan Lingkungan

- Platform pengumpulan: Google Forms (online, anonim)
- Format data: CSV export dari Google Forms
- Pilot test: 15–20 responden awal untuk validasi Cronbach's Alpha sebelum penyebaran penuh
- Target: 100 responden → estimasi 94 valid setelah filter ~6%
