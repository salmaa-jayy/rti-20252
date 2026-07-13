# 04-data

Data mentah hasil pengumpulan kuesioner — input untuk analisis di Tahap 3.

## Isi yang diharapkan

- Hasil kuesioner Google Forms dalam format CSV, per responden
- Data demografi (usia, program studi) sebagai Control Variable
- Metadata pengumpulan (tanggal penyebaran, jumlah responden per jurusan)

## Catatan

Data di folder ini bersifat mentah (raw) dan belum diolah. Hasil olahan (statistik, grafik) disimpan di [../06-output/](../06-output/).

> ⚠️ **Privasi:** `raw/responses.csv` tidak di-push ke GitHub karena berisi data responden. Gunakan `sample/sample_responses.csv` (10 baris anonim) untuk uji coba reproduksi notebook.

## Struktur

```
04-data/
├── raw/
│   └── responses.csv              # Export mentah Google Forms (JANGAN diedit)
├── sample/
│   └── sample_responses.csv       # 10 baris contoh untuk uji coba
└── processed/
    └── responses_clean.csv        # Data setelah cleaning (94 responden valid)
```

## Statistik Pengumpulan

| Keterangan | Nilai |
|-----------|-------|
| Target responden | 100 |
| Responden terkumpul | 100 |
| Gagal attention check | 4 |
| Flat response | 2 |
| **Responden valid** | **94** |
| % adopsi 2FA aktif | ~41% (39 dari 94) |
