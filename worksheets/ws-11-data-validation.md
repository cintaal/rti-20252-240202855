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
  [✓] Semua skenario tercakup (Control & Treatment)
  [ ] Jumlah run sesuai rencana (baru 4 dari 5 run selesai)
  [✓] Tidak ada file output hilang untuk run yang sudah selesai
  Missing: 1 dari 5 data points (gelombang ke-3 Treatment belum genap target responden)

Format Consistency:
  [✓] Semua file format sama (CSV hasil ekspor dari Google Sheets)
  [✓] Header konsisten (PEOU, PU, Kepuasan Pengguna, lama penggunaan)
  [✓] Tipe data konsisten (skor ordinal 1–5, durasi dalam bulan)

Range & Logic:
  [✓] Nilai dalam range masuk akal (skala Likert 1–5)
  [✓] Tidak ada waktu pengisian negatif
  [✓] Skor tidak ada yang di luar range 1–5
  Anomali ditemukan: skor rata-rata Kepuasan Pengguna pada gelombang ke-3 Treatment (2.9) menonjol rendah dibanding gelombang Treatment lainnya (4.2–4.3) — bukan pelanggaran range, tapi contextual anomaly

Cross-Validation:
  [✓] Run sejenis (Control-1 vs Control-2, Treatment-1 vs Treatment-2) → hasil saling mendekati
  [✓] Trend konsisten dengan ekspektasi teori (skor Treatment > Control)

Keputusan:
  [ ] Data siap analisis
  [✓] Perlu cleaning (investigasi gelombang ke-3 Treatment)
  [✓] Perlu re-run/pelengkapan (skenario: Treatment gelombang ke-3)

```

---

## Latihan 1 — Completeness Check

Verifikasi apakah semua data yang direncanakan sudah terkumpul.

| Skenario | Run Direncanakan | Run Tercatat | Missing | Alasan |
|----------|-----------------|-------------|---------|--------|
| Control | 2 | 2 | 0 | — |
| Treatment | 3 | 2 | 1 | Gelombang ke-3 (Shuffle-E) baru mencapai sebagian target responden saat rekap dilakukan |


**Total expected:** 5 | **Total actual:** 4 | **Missing:** 1

**Keputusan untuk data missing:**
> Gelombang ke-3 Treatment tetap dilanjutkan penyebarannya hingga target responden tercapai, tidak digabung ke analisis utama sebelum lengkap. Jika batas waktu penelitian tidak memungkinkan penambahan, data yang sudah masuk akan dilaporkan secara terpisah sebagai data parsial dengan catatan keterbatasan (bukan digabung diam-diam ke gelombang lain).
---

## Latihan 2 — Anomaly Investigation

Periksa data Anda untuk anomali. Gunakan metode IQR atau z-score.

**Dataset: rata-rata skor Kepuasan Pengguna per gelombang (skala 1–5):**

| Run | Skenario | Skor Rata-rata Kepuasan |
|-----|-------------|------------- |
| 1 | Control-1 | 3.6 |
| 2 | Treatment-1 | 4.3 |
| 3 | Control-2 | 3.5 |
| 4 | Treatment-2 | 4,2 |
| 5 | Treatment-3 (parsial) | 2.9 |

**Deteksi outlier:**
- Q1 = 3,2 | Q3 = 4,25 | IQR = 1,05
- Data terurut: 2.9, 3.5, 3.6, 4.2, 4.3
- Batas bawah (Q1 − 1.5×IQR) = 1.625
- Batas atas (Q3 + 1.5×IQR) = 5.825
- Outlier terdeteksi secara IQR ketat: tidak ada (2.9 masih di atas batas bawah — wajar untuk n kecil, rentang IQR jadi lebar)

  Namun secara kontekstual: skor 2.9 pada Run 5 jauh berbeda dari skor Treatment lain (4.2–4.3), padahal skenarionya sama (Treatment). Ini adalah contextual anomaly, bukan pelanggaran range.

**Investigasi (untuk setiap outlier):**

| Outlier | Nilai | Kemungkinan Penyebab | Keputusan |
|---------|-------|---------------------|-----------|
| Run 5 (Treatment-3, parsial) | 2.9 | Data belum lengkap (baru sebagian responden gelombang ke-3 tercatat saat rekap), sehingga rata-rata belum stabil; kemungkinan lain: karakteristik responden gelombang ke-3 berbeda dari gelombang sebelumnya | Tidak dihapus — dilanjutkan pengumpulannya hingga lengkap, lalu dihitung ulang; jika setelah lengkap tetap rendah, didokumentasikan sebagai temuan, bukan dibuang |

---

## Latihan 3 — Validation Report

Buat laporan validasi ringkas untuk dataset eksperimen Anda.

**1. Completeness:** 80% data terkumpul (4 dari 5 run)
**2. Format:** [✓] Konsisten (semua CSV dari Google Sheets, header dan tipe data seragam)
**3. Range check (anomali):** Tidak ada pelanggaran range (semua skor 1–5); ditemukan 1 contextual anomaly pada Run 5 (skor 2.9 pada gelombang Treatment yang belum lengkap)
**4. Logic check:** [✓] Ada ketidaksesuaian: gelombang ke-3 Treatment belum mencapai target responden sesuai rencana di WS-10

**Kesimpulan:**  [✓] Perlu tindakan: melengkapi pengumpulan gelombang ke-3 Treatment dan menginvestigasi penyebab skor rendahnya sebelum data digabung ke analisis akhir

---

## Refleksi

> Apa perbedaan antara "data yang benar" dan "data yang dipercaya"? Mengapa proses validasi formal diperlukan meskipun data dikumpulkan secara otomatis?

> Data yang benar berarti tercatat sesuai format teknis — misalnya semua jawaban kuesioner masuk ke Google Sheets tanpa error sistem dan nilainya berada dalam skala 1–5. Namun data yang benar secara teknis belum tentu data yang bisa dipercaya untuk mendukung kesimpulan penelitian. Data yang dipercaya harus melewati pemeriksaan tambahan: apakah semua gelombang yang direncanakan benar-benar lengkap, apakah ada pola jawaban yang tidak wajar (misalnya straight-lining), dan apakah perbedaan hasil antar gelombang punya penjelasan yang masuk akal atau justru menandakan masalah pengumpulan data. Proses validasi formal tetap diperlukan meskipun data dikumpulkan otomatis melalui Google Form, karena otomatisasi hanya menjamin data tercatat, bukan menjamin data tersebut valid, lengkap, dan bebas dari anomali yang bisa menyesatkan hasil analisis.
