# WS-13: Data Preprocessing

> **Bab 13 — Preprocessing & Persiapan Data untuk Analisis**

---

## Ringkasan Materi

### Data Refinement Pipeline

```
Raw Data → Cleaning → Transformation → Normalization → Processed Data → Analysis Ready
```

Setiap tahap memiliki tujuan berbeda. **Preprocessing bukan langkah teknis biasa** — setiap keputusan preprocessing adalah keputusan riset yang bisa mengubah kesimpulan.

### Empat Prinsip Preprocessing

| Prinsip | Deskripsi |
|---------|----------|
| **Consistency** | Metode sama untuk data yang sama |
| **Transparency** | Setiap langkah terdokumentasi |
| **Reproducibility** | Orang lain bisa mengulang dengan hasil sama |
| **Minimal Distortion** | Ubah sesedikit mungkin; jika normalisasi tidak perlu, jangan lakukan |

### Cleaning Triad

| Masalah | Strategi | Risiko |
|---------|---------|--------|
| **Missing values** | | |
| — Listwise deletion | Missing < 5%, random | Data loss |
| — Mean/median imputation | Sedikit missing, dist. normal | Mengurangi variabilitas |
| — Model-based imputation | Banyak missing, pola sistematis | Introduces dependency |
| — Flag & separate | Missing karena alasan substantif | Kompleksitas analisis |
| **Duplikat** | Identifikasi → verifikasi → hapus | False positive (data mirip ≠ duplikat) |
| **Error format** | Standardisasi tipe, encoding | Kehilangan informasi saat konversi |

### Normalisasi — Kapan & Metode Mana

| Metode | Formula | Output | Sensitif Outlier? |
|--------|---------|--------|-------------------|
| Min-max | (x-min)/(max-min) | [0, 1] | Ya |
| Z-score | (x-mean)/std | Unbounded | Lebih robust |
| Robust scaling | (x-median)/IQR | Unbounded | Paling robust |

**Kunci:** Parameter normalisasi harus dihitung dari **training set saja** — bukan seluruh data. Pelanggaran = **data leakage**.

### Data Leakage Prevention

Data leakage terjadi ketika informasi dari test set "bocor" ke preprocessing:
- Normalisasi parameter dari seluruh dataset ← **SALAH**
- Cross-validation dilakukan sebelum split ← **SALAH**
- Feature selection menggunakan label test set ← **SALAH**

### Jebakan Kognitif

1. "Preprocessing cuma teknis — tidak perlu detail" → bisa ubah kesimpulan
2. "Lebih banyak preprocessing = lebih bersih = lebih baik" → over-processing distorsi data
3. "Normalisasi selalu diperlukan" → belum tentu, tergantung metode analisis
4. "Imputation sama untuk semua situasi" → strategi harus sesuai konteks

---

## Template A.13 — Preprocessing Documentation Log

```
PREPROCESSING LOG

Dataset           : Kuesioner TAM Duolingo (Control & Treatment), gabungan seluruh gelombang WS-10/11
Jumlah data awal  : 143 responden (58 Control, 85 Treatment)

Cleaning:
| Masalah  | Jumlah Kasus     | Penanganan            | Justifikasi |
|----------|------------------|------------------------|-------------|
| Missing  | 5 dari 143 (3.5%)| Listwise deletion      | < 5%, item terlewat tersebar acak (MCAR), bukan pola sistematis |
| Duplikat | 3 dari 143 (2.1%)| Verifikasi lalu hapus (simpan submission pertama) | Link kuesioner sempat tersebar ulang, responden yang sama mengisi 2x |
| Error    | 4 dari 143 (2.8%)| Standardisasi format (kolom "lama penggunaan" ditulis teks, dikonversi ke angka bulan) | Tidak menghilangkan informasi, hanya standardisasi tipe data |

Transformation:
| Transformasi | Variabel | Detail | Alasan |
|--------------|----------|--------|--------|
| Konversi ke numerik | Lama penggunaan aplikasi | "6 bulan" → 6 | Dibutuhkan sebagai variabel kontrol (CV) numerik dalam regresi |

Normalization:
  Metode    : Robust scaling, hanya untuk variabel kontrol "lama penggunaan aplikasi"
  Alasan    : Skor PEOU, PU, Kepuasan Pengguna sudah bounded (skala Likert 1-5) dan dipakai apa adanya; lama penggunaan punya rentang lebar (1-72 bulan) dengan sedikit outlier (pengguna lama), sehingga robust scaling lebih sesuai daripada min-max
  Parameter : dihitung dari seluruh data yang dipakai analisis (bukan train/test split — penelitian ini bersifat deskriptif-inferensial/regresi, bukan predictive modeling, sehingga tidak ada pemisahan train-test)

Leakage Check:
  [✓] Parameter normalisasi dihitung dari seluruh data analisis (tidak relevan konsep training/test split karena bukan predictive modeling)
  [✓] Tidak ada informasi yang "bocor" dari proses lain ke preprocessing
  [ ] Cross-validation dilakukan setelah split — tidak berlaku, desain penelitian tidak menggunakan train-test split

Jumlah data akhir : 135 responden (55 Control, 80 Treatment)
Script tersedia   : [ ] Belum (masih diolah manual di Excel/SPSS)
```

---

## Latihan 1 — Cleaning Plan

Periksa dataset Anda (atau dataset contoh) dan dokumentasikan masalah yang ditemukan.

| Masalah | Jumlah Kasus | Penanganan | Justifikasi |
|---------|-------------|------------|-------------|
| Missing di beberapa item kuesioner | 5 dari 143 (3.5%) | Listwise deletion | Di bawah 5%, tersebar acak antar item (MCAR) |
| Duplikat submission | 3 dari 143 (2.1%) | Verifikasi (cek timestamp/identitas), hapus submission kedua | Kuesioner disebar ulang di grup yang sama, sebagian responden mengisi dua kali |
| Error format kolom "lama penggunaan" | 4 dari 143 (2.8%) | Standardisasi ke format numerik (bulan) | Menjaga informasi tetap terpakai, bukan dihapus |
| | | | |

**Jumlah data sebelum cleaning:** 143
**Jumlah data setelah cleaning:** 135
**Persentase data yang hilang/berubah:** 56%

---

## Latihan 2 — Normalisasi Decision

Tentukan apakah data Anda perlu normalisasi, dan jika ya, metode apa yang tepat.

| Variabel | Range Asli | Distribusi | Outlier? | Metode Normalisasi | Alasan |
|----------|-----------|-----------|----------|-------------------|--------|
| Skor Kepuasan Pengguna | 1-5 | Sedikit menceng kiri (terkonsentrasi di skor 4) | Tidak signifikan | Tidak perlu | Sudah bounded dalam skala Likert, dipakai sesuai desain kuesioner |
| Skor PEOU / PU | 1 – 5 | Mendekati normal| *Tidak* | *Tidak perlu* | Sama seperti Kepuasan Pengguna — skala sudah standar |
| Lama penggunaan aplikasi (bulan) | 1 – 72 | Right-skewed | Ya (beberapa pengguna >48 bulan) | Robust scaling | Rentang lebar dan ada outlier ringan, robust scaling (median & IQR) lebih tahan terhadap outlier dibanding min-max |
| | | | | | |

**Apakah normalisasi diperlukan?**  Ya 

**Justifikasi:**
> Normalisasi hanya diperlukan untuk variabel kontrol "lama penggunaan aplikasi" karena rentang dan skalanya berbeda jauh dari skor Likert. Variabel utama (PEOU, PU, Kepuasan Pengguna) tidak dinormalisasi karena sudah bounded dan menormalisasinya justru mengubah makna skor Likert yang dimaksudkan apa adanya — sesuai prinsip minimal distortion.
**Leakage check:**
- [✓] Parameter dihitung dari seluruh data analisis (tidak ada train-test split   karena desain bukan predictive modeling)
- Normalisasi diterapkan setelah train-test split — tidak berlaku untuk desain     penelitian ini

---

## Latihan 3 — Preprocessing Report

Buat ringkasan preprocessing lengkap — dokumentasi yang cukup bagi orang lain untuk mereplikasi.

```
PREPROCESSING SUMMARY

1. Dataset: Kuesioner TAM Duolingo (Control & Treatment)
2. Data awal: 143 records, 4 variabel utama (PEOU, PU, Kepuasan Pengguna, Lama Penggunaan) + identitas
3. Cleaning:
   - Missing values: 5 kasus, metode: listwise deletion
   - Duplikat: 3 kasus, tindakan: verifikasi lalu hapus submission kedua
   - Error: 4 kasus, tindakan: standardisasi format ke numerik
4. Transformation: konversi kolom "lama penggunaan" dari teks ke angka (bulan)
5. Normalisasi: robust scaling, hanya untuk "lama penggunaan aplikasi"; parameter dihitung dari seluruh data (tidak ada train-test split)
6. Data akhir: 135 records (55 Control, 80 Treatment), 4 variabel utama
7. Leakage check: [✓] Lulus (dengan catatan konsep leakage kurang relevan untuk desain non-predictive ini)

```

---

## Refleksi

> Apakah Anda pernah melakukan normalisasi "karena biasa dilakukan" tanpa mempertimbangkan apakah benar-benar diperlukan? Apa risiko over-preprocessing?

>Saat menyusun Latihan 2, sempat terpikir untuk menormalisasi semua variabel termasuk skor PEOU, PU, dan Kepuasan Pengguna, karena "biasanya" data numerik dinormalisasi sebelum dianalisis. Setelah dipikir ulang, itu tidak diperlukan dan justru berisiko — menormalisasi skor Likert yang sudah bounded 1-5 bisa mendistorsi makna aslinya (misalnya perbedaan antara skor 3 dan 4 pada skala asli menjadi tidak lagi jelas artinya setelah diubah ke rentang lain). Risiko over-preprocessing di sini adalah kehilangan interpretasi langsung terhadap skala Likert yang justru menjadi kekuatan utama kuesioner TAM, hanya demi mengikuti kebiasaan teknis yang sebenarnya tidak relevan untuk jenis data ini.
