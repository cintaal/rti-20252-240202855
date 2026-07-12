# WS-12: Result Presentation & Visualization

> **Bab 12 — Penyajian Hasil & Visualisasi**

---

## Ringkasan Materi

### Data → Insight Model

```
Validated Data → Structured Presentation → Visualization → Pattern Recognition → Insight
```

Penyajian **mendahului** analisis. Tabel dan grafik membantu peneliti "melihat" data sebelum menghitung. Langsung ke uji statistik tanpa visualisasi berisiko kesimpulan yang secara teknis benar tapi kontekstual salah (Anscombe's Quartet, 1973).

### Tabel = Presisi, Grafik = Pola

Keduanya **saling melengkapi**:
- Tabel: angka presisi, self-contained (dipahami tanpa teks), sortable
- Grafik: pola visual, tren, perbandingan cepat

### Jenis Grafik Berdasarkan Tujuan

| Tujuan | Jenis Grafik |
|--------|-------------|
| Perbandingan antar-skenario | Bar chart (grouped/stacked) |
| Distribusi per-skenario | Box plot / violin plot |
| Tren temporal | Line chart |
| Korelasi dua variabel | Scatter plot |
| Proporsi (total = 100%) | Pie chart (hati-hati!) |

### Contoh Tabel Hasil yang Baik

| Model | Accuracy (%) | F1-Score (%) | Training Time (min) |
|-------|-------------|-------------|---------------------|
| BERT | 88.4 ± 1.2 | 87.1 ± 1.4 | 45.2 ± 3.1 |
| LSTM | 86.1 ± 1.8 | 84.5 ± 2.0 | 12.8 ± 1.2 |
| SVM | 82.3 ± 0.9 | 80.7 ± 1.1 | 0.3 ± 0.1 |

*N=10 per model. Mean ± std. Diurutkan berdasarkan Accuracy.*

### Visualization Bias — Yang Harus Dihindari

| Bias | Deskripsi | Dampak |
|------|----------|--------|
| Truncated axis | Y tidak dari 0 | Memperbesar perbedaan kecil |
| Inconsistent scale | Dua grafik skala beda | Perbandingan menyesatkan |
| Cherry-picked data | Hanya tampilkan yang "menang" | Selektif, tidak jujur |
| 3D effects | Efek 3D tanpa dimensi data ke-3 | Distorsi tanpa informasi |
| Missing error bar | Tidak ada variabilitas | Menyembunyikan ketidakpastian |

### Engineering vs Research Presentation

| Aspek | Engineering | Research |
|-------|-----------|---------|
| Tujuan grafik | Dashboard monitoring | Mendukung argumen ilmiah |
| Informasi wajib | KPI, threshold | Mean, std, CI, N, p-value |
| Bias handling | Less critical | Wajib dihindari (peer-review) |

---

## Template A.12 — Result Presentation Plan

```
RESULT PRESENTATION PLAN

Research Question : Apakah Perceived Ease of Use (PEOU) dan Perceived Usefulness (PU) dari fitur AI pada aplikasi Duolingo berpengaruh signifikan terhadap kepuasan pengguna?
Metrik Utama      : Skor Kepuasan Pengguna (skala Likert 1-5), didukung oleh PEOU dan PU

Tabel Hasil:
| Skenario  | PEOU (mean ± std) | PU (mean ± std) | Kepuasan Pengguna (mean ± std) | n  |
|-----------|--------------------|------------------|----------------------------------|----|
| Control   | 3.4 ± 0.5          | 3.3 ± 0.6        | 3.55 ± 0.5                       | 58 |
| Treatment | 4.1 ± 0.4          | 4.2 ± 0.5        | 4.13 ± 0.5                       | 85 |

Visualisasi yang Direncanakan:
| # | Jenis Grafik            | Pesan Utama                                                        | Metrik                              |
|---|-------------------------|---------------------------------------------------------------------|--------------------------------------|
| 1 | Bar chart + error bar   | Perbandingan skor rata-rata PEOU, PU, dan Kepuasan antara Control vs Treatment | Mean ± std ketiga variabel per skenario |
| 2 | Box plot                | Distribusi skor Kepuasan Pengguna per skenario (bukan cuma rata-rata) | Seluruh skor Kepuasan per responden  |
| 3 | Scatter plot            | Korelasi antara PU dan Kepuasan Pengguna                            | Skor PU vs skor Kepuasan tiap responden |

Bias Check:
  [✓] Y-axis mulai dari 0 (skala Likert 1-5 divisualisasikan dari 0, bukan dipotong dari 3 atau 4)
  [✓] Error bar/CI ditampilkan (std pada bar chart)
  [✓] Semua data disertakan (termasuk gelombang ke-3 Treatment, tidak cherry-picked)
  [✓] Tidak menggunakan 3D tanpa alasan
```

---

## Latihan 1 — Tabel Hasil

Buat tabel hasil eksperimen Anda (boleh dengan data simulasi jika belum punya data riil).

| Skenario | PEOU (mean ± std) | PU (mean ± std) | n | 
|----------|----------------------|----------------------|---|
| Control | 3.4 ± 0.5 |3.3 ± 0.6| 58 |
| Treatment | 4.1 ± 0.4 | 4.2 ± 0.5 | 85 |
| | | | |

**Checklist tabel:**
- [✓] Self-contained (judul jelas, satuan skala Likert 1-5, N tercantum)
- [✓] Mean ± std (bukan single number)
- [✓] Diurutkan berdasarkan metrik utama (Kepuasan Pengguna, Control lalu Treatment)
- [✓] Format konsisten di semua baris

---

## Latihan 2 — Rencana Visualisasi

Rencanakan 2-3 grafik untuk menyajikan data dari Latihan 1. Setiap grafik = satu pesan.

| # | Jenis Grafik | Pesan | Data yang Digunakan |
|---|-------------|-------|---------------------|
| 1 | Bar chart + error bar | Treatment (Duolingo AI) memiliki skor PEOU, PU, dan Kepuasan lebih tinggi dari Control | Mean ± std PEOU, PU, Kepuasan per skenario |
| 2 | *Box plot* | Sebaran skor Kepuasan Pengguna pada Treatment lebih terkonsentrasi di nilai tinggi dibanding Control | Seluruh skor Kepuasan Pengguna individual per responden, per skenario |
| 3 | *Scatter plot* | Semakin tinggi skor PU, semakin tinggi skor Kepuasan Pengguna (indikasi korelasi positif) | Pasangan skor PU dan Kepuasan tiap responden |

---

## Latihan 3 — Bias Detection

Evaluasi visualisasi berikut untuk bias (skenario dari contoh):

**Skenario:** Metode A = 91.2%, Metode B = 90.8%. Bar chart dengan Y-axis mulai dari 90%.

| Pertanyaan | Jawaban |
|-----------|---------|
| Apakah Y-axis menyesatkan? | Ya — selisih sebenarnya hanya 0.4%, tapi dengan Y-axis dipotong mulai 90%, batang A terlihat jauh lebih tinggi dari B, seolah perbedaannya besar |
| Apakah error bar ditampilkan? | Tidak disebutkan — kemungkinan tidak ada, sehingga tidak diketahui apakah selisih 0.4% ini berada dalam rentang variabilitas normal atau benar-benar signifikan |
| Apakah semua kondisi ditampilkan? | Tidak jelas — hanya dua metode dibandingkan, tidak diketahui apakah ada kondisi/metode lain yang sengaja tidak disertakan |
| Apa solusinya? | Mulai Y-axis dari 0%, tampilkan error bar/std pada tiap batang, dan sertakan seluruh kondisi yang diuji agar pembaca bisa menilai signifikansi perbedaan secara jujur |

**Evaluasi grafik Anda sendiri dari Latihan 2:**
- [✓] Semua bias check lulus
  (Y-axis dari 0, error bar disertakan, semua gelombang termasuk Treatment ke-3 disertakan, tidak ada efek 3D)

---

## Refleksi

> Mengapa tabel dan grafik keduanya diperlukan — tidak cukup salah satu saja? Pernahkah Anda membuat grafik yang (tanpa sengaja) menyesatkan?

> Tabel dan grafik saling melengkapi: tabel memberi angka presisi (mean, std, n) yang bisa dikutip ulang secara akurat, sementara grafik memperlihatkan pola dan perbandingan secara cepat yang sulit ditangkap hanya dari deretan angka — misalnya seberapa jauh sebaran skor Kepuasan Pengguna antar responden pada Treatment dibanding Control, yang baru terlihat jelas lewat box plot. Kalau hanya pakai tabel, pola distribusi bisa terlewat; kalau hanya pakai grafik, presisi angka (misalnya nilai std yang menentukan signifikansi) bisa hilang.
> Dalam merancang visualisasi untuk Latihan 2 di atas, sempat terpikir untuk memulai Y-axis dari skor 3 saja (bukan 0) supaya perbedaan Control vs Treatment terlihat lebih "menonjol" di bar chart. Setelah mengerjakan Latihan 3, disadari bahwa itu termasuk truncated axis bias — perbedaan PEOU/PU/Kepuasan yang sebenarnya masih dalam skala wajar (sekitar 0.6-0.9 poin dari skala 1-5) bisa terlihat seolah jauh lebih besar. Karena itu, keputusan akhirnya tetap memulai Y-axis dari 0 dan menyertakan error bar.
