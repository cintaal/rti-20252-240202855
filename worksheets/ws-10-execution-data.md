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

| Run # | Skenario  | Seed      | Parameter                          | Status  | Waktu             | Output File          |
|-------|-----------|-----------|-------------------------------------|---------|-------------------|-----------------------|
| 1     | Control   | Shuffle-A | Kuesioner TAM 20 item, Likert 1-5   | Planned | 2026-07-20 09:00  | control_run1.csv      |
| 2     | Treatment | Shuffle-B | Kuesioner TAM 20 item, Likert 1-5   | Planned | 2026-07-20 09:00  | treatment_run1.csv    |
| 3     | Control   | Shuffle-C | Sama seperti Run 1, responden baru | Planned | 2026-07-27 09:00  | control_run2.csv      |
| 4     | Treatment | Shuffle-D | Sama seperti Run 2, responden baru | Planned | 2026-07-27 09:00  | treatment_run2.csv    |
| 5     | Treatment | Shuffle-E | Sama seperti Run 2, tambahan sampel | Planned | 2026-08-03 09:00 | treatment_run3.csv    |

Jumlah runs per skenario : 2-3 gelombang per skenario (Control dan Treatment)
Total runs               : 5

DATA LOG (per run):
  Run ID    : run-01-control
  Timestamp : 2026-07-20T09:00:00
  Skenario  : Control (TAM standar, non-AI)
  Input     : Link kuesioner Google Form v1.0 (kode shuffle Shuffle-A)
  Output    : Rekap skor PEOU, PU, Kepuasan Pengguna di Google Sheets
  Anomali   : -
  Catatan   : Gelombang pertama skenario Control, target 30 responden
```

---

## Latihan 1 — Execution Plan

Susun execution plan untuk eksperimen Anda. Tentukan skenario, jumlah run, dan seed sebelum eksekusi.

| Run # | Skenario | Seed (kode shuffle) | Parameter Kunci | Status |
|-------|----------|---------------------|----------------|--------|
| 1 | Control (TAM standar, non-AI) |Shuffle-A | Kuesioner TAM, 3 variabel (PEOU, PU, Kepuasan), skala Likert 1–5 | Planned |
| 2 | Treatment (TAM + fitur AI Duolingo) | Shuffle B | Kuesioner TAM, 3 variabel, skala Likert 1–5 | Planned |
| 3 | Control (gelombang ke-2) | Shuffle-C | Sama seperti Run 1, responden berbeda | Planned |
| 4 | Treatment (gelombang ke-2) | Shuffle-D | Sama seperti Run 2, responden berbeda | Planned |
| 5 | Treatment (gelombang ke-3, tambahan) |Shuffle-E | Sama seperti Run 2, untuk menambah jumlah sampel | Planned |

**Total skenario:** 
2 (Control dan Treatment)

**Run per skenario:**
minimal 2–3 gelombang per skenario (disesuaikan dengan target jumlah responden, bukan repetisi identik seperti eksperimen algoritmik)

**Total run keseluruhan:** 
5 (dapat ditambah jika jumlah responden per gelombang belum mencukupi target sampel)

---

## Latihan 2 — Data Log Terstruktur

Desain format data log untuk eksperimen Anda. Tentukan field apa saja yang akan dicatat.

**Identitas:**
| Field | Contoh |
|-------|--------|
| Run ID | run-01-control |
| Timestamp | 2026-07-20T09:00:00 |
| Skenario | Control / Treatment |

**Konfigurasi:**
| Field | Contoh |
|-------|--------|
| Seed (Kode shuffle)| Shuffle-A |
| kuesioner version | v1.0 (20 item, 3 variabel) |
| Channel Distribusi | Google Form via WhatsApp/Instagram |

**Hasil:**
| Metrik | Tipe Data | Range Valid |
|--------|----------|-------------|
| Skor PEOU | ordinal (Likert) | 1 – 5 |
| Skor PU | ordinal (Likert) |  1 – 5 |
|skor kepuasan pengguna | ordinal (Likert) |  1 – 5 |
|Lama penggunaan aplikasi (CV)|ratio|≥ 0 bulan|

**Format output:** [ ✓ ] CSV / [ ] JSON / [✓] Database / [ ] Lainnya: ____

---

## Latihan 3 — Anomaly Protocol

Rencanakan bagaimana menangani anomali. Untuk setiap jenis, tentukan langkah yang diambil.

| Jenis Anomali | Contoh | Tindakan |
|---------------|--------|----------|
| Respons gagal/tidak lengkap | Responden menutup form sebelum submit |Dokumentasikan, tidak dihitung sebagai data valid, dicatat jumlahnya |
| Hasil ekstrem | Straight-lining (semua jawaban skor 5) | Investigasi, tandai sebagai flagged, tetap didokumentasikan sebelum diputuskan dikeluarkan/tidak |
| Waktu eksekusi anomali | Form diisi kurang dari 30 detik | Dokumentasikan sebagai indikasi pengisian tidak serius, evaluasi lebih lanjut |
| Inkonsistensi dengan run lain | Skor rata-rata gelombang 2 jauh berbeda dari gelombang 1 pada skenario yang sama | Investigasi kemungkinan perbedaan karakteristik responden antar gelombang, dokumentasikan sebagai catatan analisis|

**Prinsip:** Detect → Investigate → Document → Decide

---

## Refleksi

> Pernahkah Anda melaporkan hasil riset/tugas dari single run? Apa risikonya? Bagaimana multiple run mengubah kepercayaan terhadap hasil?

**Pengalaman sebelumnya:**
> Sejauh ini penelitian masih berada pada tahap proposal (belum memasuki tahap pengumpulan data sesungguhnya), sehingga belum pernah melaporkan hasil dari satu gelombang pengumpulan data saja. Namun, dalam pengerjaan tugas lain, pernah mengandalkan satu kali pengumpulan data tanpa mempertimbangkan variasi sampel.

**Yang akan dilakukan berbeda:**
> Ke depannya, pengumpulan data akan dilakukan dalam beberapa gelombang untuk kedua skenario (Control dan Treatment), bukan hanya satu kali penyebaran. Hal ini penting agar hasil tidak bias akibat karakteristik responden pada satu gelombang tertentu, dan agar variasi skor PEOU, PU, serta Kepuasan Pengguna bisa diuji secara statistik dengan lebih meyakinkan, bukan hanya dilaporkan sebagai satu angka tunggal.
