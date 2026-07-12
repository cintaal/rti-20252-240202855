# WS-14: Analysis, Interpretation & Failure Analysis

> **Bab 14 — Analisis Data, Interpretasi & Failure Analysis**

---

## Ringkasan Materi

### Data → Knowledge Model

```
Data → Analysis → Interpretation → Explanation → Knowledge
```

Tiga level yang berbeda:
- **Analysis** — "Apa yang terjadi?" (deskriptif + inferensial)
- **Interpretation** — "Apa artinya?" (konteks RQ + literatur)
- **Failure Analysis** — "Mengapa tidak berhasil?" (boundary conditions)

### Beyond p-value

**Statistical significance ≠ practical significance.** Selalu laporkan:
1. p-value (signifikansi statistik)
2. Effect size (besarnya efek)
3. Confidence interval (rentang ketidakpastian)

| Effect Size (Cohen's d) | Interpretasi |
|-------------------------|-------------|
| < 0.2 | Small |
| 0.2 – 0.8 | Medium |
| > 0.8 | Large |

### Pemilihan Uji Statistik

| Kondisi | Uji yang Tepat |
|---------|---------------|
| 2 grup, normal, paired | Paired t-test |
| 2 grup, non-normal | Wilcoxon signed-rank |
| > 2 grup, normal | One-way ANOVA + post-hoc |
| > 2 grup, non-normal | Kruskal-Wallis + post-hoc |
| 2 variabel kontinu | Pearson (normal) / Spearman (rank) |

### Failure Analysis as Contribution

Hipotesis yang ditolak adalah **temuan yang berharga**:

| Dataset | New (F1) | Baseline (F1) | p-value | Cohen's d |
|---------|---------|--------------|---------|-----------|
| DS-1 (small, clean) | 94.2±1.1 | 89.3±1.5 | <0.001 | **3.7** |
| DS-4 (medium, noisy) | 78.3±3.2 | 82.1±2.8 | 0.008 | **-1.3** |
| DS-5 (large, noisy) | 71.6±4.1 | 80.5±3.0 | <0.001 | **-2.5** |

**Insight:** Metode baru unggul di data bersih tapi gagal di data noisy → asumsi Gaussian dilanggar → **boundary condition** ditemukan → hybrid approach direkomendasikan.

**Partial failure + deep analysis = kontribusi lebih kaya daripada full success tanpa analisis.**

### Limitation Types

| Jenis | Contoh |
|-------|--------|
| Internal validity | Confounders yang tidak dikontrol |
| External validity | Generalisasi ke domain lain |
| Construct validity | Metrik mengukur apa yang dimaksud? |
| Statistical limitation | Sample size, asumsi distribusi |

### Jebakan Kognitif

1. "Signifikan statistik = penting secara praktis" → cek effect size
2. "Hipotesis tidak didukung → cari sudut baru" → p-hacking
3. "Kegagalan tidak perlu dilaporkan detail" → missed insight
4. "Limitasi cukup disebutkan, tidak perlu dianalisis" → kedalaman hilang

---

## Template A.14 — Analysis & Interpretation Report

```
ANALYSIS & INTERPRETATION

1. Statistik Deskriptif:
   | Skenario  | Mean | Std  | Median | Min | Max | n  |
   |-----------|------|------|--------|-----|-----|----|
   | Control   | 3.55 | 0.50 | 3.5    | 2.0 | 4.5 | 55 |
   | Treatment | 4.13 | 0.50 | 4.0    | 3.0 | 5.0 | 80 |

2. Uji Hipotesis:
   Uji yang digunakan  : Independent samples t-test (Welch's t-test)
   Justifikasi          : 2 grup independen (responden berbeda), n cukup besar untuk asumsi normalitas rata-rata (CLT), varians tidak diasumsikan sama karena n1 ≠ n2 (Welch correction)
   Hasil: p < 0.001, effect size (Cohen's d) = 1.16
   CI 95% (selisih mean) : [0.41, 0.75]

3. Keputusan:
   [✓] H₀ ditolak → H₁ diterima
   [ ] H₀ tidak ditolak

4. Interpretasi:
   Hubungan ke RQ        : Mendukung RQ dan H₁ dari WS-04 — pengguna Duolingo dengan fitur AI (Treatment) menunjukkan skor Kepuasan Pengguna yang signifikan lebih tinggi dibanding pengguna aplikasi non-AI (Control)
   Practical significance: Effect size besar (d = 1.16) menunjukkan perbedaan bukan hanya signifikan secara statistik tapi juga besar secara praktis — bukan sekadar signifikan karena n besar
   Perbandingan literatur : Konsisten dengan penelitian TAM sebelumnya yang menunjukkan PEOU dan PU berkorelasi positif dengan kepuasan pengguna terhadap teknologi baru

5. Limitation:
   | Jenis       | Ancaman | Dampak | Mitigasi |
   |-------------|---------|--------|----------|
   | Internal    | Confounding: responden Treatment mungkin secara alami lebih terbuka pada teknologi baru | Perbedaan kepuasan bisa sebagian dijelaskan karakteristik responden, bukan murni fitur AI | Kumpulkan data pengalaman teknologi sebagai kovariat pada penelitian lanjutan |
   | External    | Sampel mayoritas dari satu lingkungan penyebaran (grup tertentu) | Generalisasi ke seluruh pengguna Duolingo terbatas | Perluas sumber sampel pada penelitian mendatang |
   | Statistical | Data ordinal (Likert) dianalisis dengan uji parametrik | Asumsi interval pada data ordinal masih bisa diperdebatkan | Lakukan cross-check dengan uji non-parametrik (Mann-Whitney U) sebagai sensitivity analysis |

6. Failure Analysis (jika H₀ tidak ditolak):
   Tidak berlaku untuk analisis utama (H₀ ditolak). Skenario sekunder yang menunjukkan hasil tidak signifikan didokumentasikan terpisah di Latihan 3.
```

---

## Latihan 1 — Pemilihan Uji Statistik

Tentukan uji statistik yang tepat untuk eksperimen Anda.

| Pertanyaan | Jawaban |
|-----------|---------|
| Berapa grup yang dibandingkan? | 2 (Control dan Treatment) |
| Apakah data berpasangan (paired)? | Tidak — responden Control dan Treatment adalah individu yang berbeda (independent groups) |
| Apakah distribusi normal? (uji normalitas) | Data individual ordinal (Likert), tapi dengan n cukup besar (55 dan 80), distribusi rata-rata dianggap mendekati normal berdasarkan Central Limit Theorem |
| **Uji yang dipilih:** | Independent samples t-test (Welch's t-test) |
| **Justifikasi:** | 2 grup independen, ukuran sampel besar mendukung asumsi normalitas rata-rata, dan varians tidak diasumsikan sama karena jumlah responden kedua grup berbeda |

**Effect size yang akan dilaporkan:** [✓] Cohen's d / [ ] Eta-squared / [ ] Lainnya: ____

---

## Latihan 2 — Interpretasi Hasil

Gunakan data berikut (atau data riil Anda) untuk berlatih interpretasi.

**Data:**
| Skenario | Kepuasan Pengguna (mean ± std) | n |
|-------|----------------------|---|
| Control | 3.55 ± 0.50 | 55 |
| Treatment | 4.13 ± 0.50 | 80 |

p < 0.001, Cohen's d = 1.16, CI 95% = [0.41, 0.75]

| Aspek | Interpretasi |
|-------|-------------|
| Signifikansi statistik | p < 0.001 → sangat signifikan pada α = 0.05, jauh di bawah ambang batas |
| Effect size | d = 1.16 → large effect (di atas ambang 0.8), perbedaan antar grup besar bukan hanya sekadar signifikan |
| Practical significance | Selisih rata-rata sekitar 0.58 poin pada skala 1-5 tergolong cukup besar secara praktis untuk konteks kepuasan pengguna aplikasi — bukan perbedaan marjinal |
| Hubungan ke RQ | Langsung mendukung H₁: fitur AI (PEOU, PU yang lebih tinggi pada Treatment) berasosiasi dengan kepuasan pengguna yang lebih tinggi |
| Perbandingan literatur | Sejalan dengan studi TAM terdahulu bahwa peningkatan persepsi kemudahan dan kegunaan berbanding lurus dengan kepuasan pengguna teknologi |

---

## Latihan 3 — Failure Analysis

Latih kemampuan failure analysis: hipotesis TIDAK didukung. Apa yang bisa dipelajari?

**Skenario:** (hipotetis, sebagai latihan): Pada analisis regresi tambahan yang menguji kontribusi PEOU dan PU secara terpisah terhadap Kepuasan Pengguna, koefisien PU ternyata tidak signifikan (p = 0.12) setelah PEOU dikontrol, meskipun secara deskriptif skor Treatment tetap lebih tinggi dari Control.

| Pertanyaan | Jawaban |
|-----------|---------|
| Apakah ini "gagal"? | Bukan gagal total — ini temuan valid bahwa kontribusi unik PU terhadap Kepuasan mungkin tumpang tindih dengan PEOU, bukan berarti PU tidak relevan sama sekali |
| Kemungkinan penyebab? | PEOU dan PU kemungkinan berkorelasi tinggi (multikolinearitas) pada konteks Duolingo, sehingga saat dimasukkan bersama dalam regresi, sebagian besar varians Kepuasan sudah "terserap" oleh PEOU lebih dulu |
| Boundary condition? | PU mungkin baru berkontribusi signifikan secara independen pada pengguna dengan durasi penggunaan lebih lama, yang sudah lebih memahami manfaat fitur AI dibanding sekadar kemudahannya |
| Insight yang bisa diambil? | Ada indikasi PEOU menjadi jalur utama menuju kepuasan pada tahap awal penggunaan, sementara peran PU mungkin lebih terlihat seiring durasi penggunaan bertambah — layak diuji sebagai variabel moderasi pada penelitian lanjutan |
| Apakah layak dilaporkan? Mengapa? |Ya — hasil regresi yang tidak signifikan pada satu prediktor tetap penting dilaporkan sebagai bagian dari transparansi hasil, bukan disembunyikan hanya karena tidak sesuai ekspektasi awal (menghindari p-hacking) |

**Limitation terkait:**
| Jenis | Ancaman | Dampak |
|-------|---------|--------|
| Statistical | Multikolinearitas antara PEOU dan PU tidak diuji secara eksplisit (misalnya via VIF) | Interpretasi kontribusi individual masing-masing variabel jadi kurang tegas |
| Construct | Item kuesioner PEOU dan PU mungkin sedikit tumpang tindih secara konsep dalam konteks fitur AI Duolingo | Sulit memisahkan efek murni masing-masing konstruk terhadap Kepuasan Pengguna |

---

## Refleksi

> Apakah "failure" dalam riset benar-benar gagal, atau justru kontribusi? Bagaimana failure analysis mengubah cara Anda melihat hasil negatif?

> Dari Latihan 3, terlihat bahwa hasil yang tidak signifikan (kontribusi PU yang tidak signifikan setelah PEOU dikontrol) bukan berarti penelitian gagal — justru itu membuka insight baru tentang kemungkinan PEOU dan PU punya peran yang berbeda tergantung durasi penggunaan, sesuatu yang tidak akan ditemukan kalau hasil "gagal" itu buru-buru disingkirkan atau dicari-cari cara agar terlihat signifikan. Failure analysis mengubah cara melihat hasil negatif: dari "hipotesis ini salah, lupakan" menjadi "hipotesis ini tidak terbukti dalam kondisi ini, apa yang bisa dipelajari dari batasannya?" — sehingga hasil negatif pun tetap punya nilai kontribusi selama dianalisis dan didokumentasikan dengan jujur, bukan disembunyikan.
