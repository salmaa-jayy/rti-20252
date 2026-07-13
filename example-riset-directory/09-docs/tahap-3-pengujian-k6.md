# Tahap 3 — Pengumpulan Data

**Status:** Belum dimulai  
**Bergantung pada:** [tahap-2-setup-eksperimen.md](tahap-2-setup-eksperimen.md)

---

## Tujuan

Mengumpulkan respons kuesioner dari 100 mahasiswa aktif pengguna Instagram di Kebumen menggunakan Google Forms yang sudah dirancang.

## Rencana Pelaksanaan

### Instrumen
Kuesioner 22 item total:
- Bagian 0: Screening & demografi (4 item)
- Attention Check 1 (1 item)
- Blok A: Persepsi kemudahan (4 item Likert)
- Blok B: Persepsi manfaat (4 item Likert)
- Blok C: Kesadaran risiko (3 item Likert)
- Attention Check 2 (1 item)
- Blok D: Pengaruh sosial (3 item Likert)
- Blok E: Adopsi 2FA — DV (2 item)

Estimasi waktu pengisian: **5–7 menit**

### Prosedur

1. **Pilot test** — sebarkan ke 15–20 responden awal
2. **Validasi** — uji Cronbach's Alpha per faktor (target α ≥ 0.7)
3. **Revisi** jika α < 0.7 pada faktor tertentu
4. **Penyebaran penuh** — 100 responden, 4+ program studi Kebumen
5. **Filter** — hapus responden gagal attention check + flat response

### Target Responden

| Program Studi | Target | Alasan |
|--------------|--------|--------|
| Teknologi Informasi | 25 | Representasi mahasiswa TI |
| Ekonomi/Bisnis | 25 | Representasi non-TI |
| Hukum | 25 | Representasi non-TI |
| Kesehatan | 25 | Representasi non-TI |

> Distribusi lintas jurusan penting untuk menghindari bias mahasiswa TI yang cenderung lebih sadar keamanan (Muhammad, ITS 2023).

## Output per Run

```
04-data/
├── raw/responses.csv              # Export mentah Google Forms
└── processed/responses_clean.csv  # Setelah filter attention check
```

## Acuan

[ws-10-execution-plan.md](ws-10-execution-plan.md), [ws-11-data-validation.md](ws-11-data-validation.md)
