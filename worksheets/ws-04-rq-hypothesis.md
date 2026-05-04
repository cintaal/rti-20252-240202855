# WS-04: Research Question & Hypothesis

> **Bab 4 — Research Question, Contribution & Hypothesis**

---

## Ringkasan Materi

### RQ Bukan Pertanyaan Biasa

Research Question yang baik secara implisit mengandung cetak biru eksperimen: subjek, baseline, metrik, domain, dataset.

| Kualitas | Contoh |
|----------|--------|
| **Buruk** | "Bagaimana pengaruh deep learning terhadap deteksi malware?" |
| **Baik** | "Apakah CNN menghasilkan F1-Score lebih tinggi dari RF pada CIC-MalMem-2022?" |

Perbedaan: RQ yang baik menyebutkan **metode spesifik**, **metrik terukur**, **baseline**, dan **dataset**.

### Tiga Jenis RQ

| Jenis | Pola | Kebutuhan |
|-------|------|-----------|
| **Comparison** | A vs B → mana lebih baik? | ≥ 2 metode, metrik sama |
| **Improvement** | A' vs A → modifikasi lebih baik? | Pre/post, bukti perbaikan |
| **Exploratory** | Faktor X₁...Xₙ → pengaruh terhadap Y? | Multi-variabel, korelasi/regresi |

### Contribution Statement

Tiga jenis kontribusi: **Improvement** (metode terbukti lebih baik), **Comparison** (perbandingan sistematis yang belum ada), **Novel Approach** (pendekatan baru). Kontribusi harus terhubung langsung dengan gap — kontribusi tanpa gap = klaim tanpa justifikasi.

### Hypothesis H₀ / H₁

- **H₀** (Null) = Tidak ada perbedaan signifikan — asumsi default, harus dibuktikan salah
- **H₁** (Alternative) = Ada perbedaan signifikan — diterima hanya jika H₀ ditolak
- Harus **falsifiable**, mengandung **metrik terukur**, dirumuskan **SEBELUM eksperimen**

### Rantai Operasionalisasi

```
RQ → Variable → Metric → Data → Analysis
```

Jika rantai ini tidak lengkap, RQ belum mature. Bi-directional: RQ yang tidak bisa jadi hipotesis testable harus direvisi mundur.

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan pertanyaan | Apa yang harus dibangun? | Apa yang harus dibuktikan? |
| Bentuk jawaban | Sistem yang berfungsi | Bukti empiris terukur |
| Sukses diukur oleh | User satisfaction, uptime | Signifikansi statistik, effect size |
| Jika gagal | Debug dan perbaiki | Laporkan, analisis mengapa |

### Istilah Penting

- **Research Question (RQ)** — Pertanyaan spesifik: variabel terukur + metrik + konteks
- **Contribution Statement** — Apa yang diketahui setelah riset selesai yang sebelumnya belum ada
- **H₀ / H₁** — Null vs Alternative Hypothesis
- **Falsifiability** — Kondisi hipotesis ditolak harus bisa didefinisikan sebelum eksperimen
- **Operationalization** — Proses mewujudkan konsep abstrak menjadi variabel terukur

---

## Template A.4 — RQ-Contribution-Hypothesis

```
RQ-CONTRIBUTION-HYPOTHESIS

Gap Statement  : Belum ada penelitian yang menggabungkan Artificial Intelligence dengan model TAM untuk mengukur kepuasan pengguna pada aplikasi pembelajaran bahasa seperti Duolingo

Research Question:
  Tipe         : [✓] Exploratory
  Formulasi    : Apakah perceived ease of use dan perceived usefulness dari teknologi AI pada aplikasi Duolingo berpengaruh signifikan terhadap kepuasan pengguna?
  Variabel IV  : Perceived Ease of Use (PEOU), Perceived Usefulness (PU)
  Variabel DV  : Kepuasan pengguna
  Metrik       : Skor kuesioner (skala Likert), nilai regresi/signifikansi
  Dataset      : Data kuesioner pengguna Duolingo (±100 responden)
  Baseline     : Model TAM standar tanpa fokus AI

Quality Check RQ:
  [✓] Variabel spesifik
  [✓] Metrik jelas
  [✓] Baseline ada
  [✓] Konteks disebutkan
  [✓] Memerlukan eksperimen (bukan hanya survei literatur)

Contribution Statement:
  Apa yang baru diketahui : Pengaruh spesifik teknologi AI dalam meningkatkan kepuasan pengguna melalui variabel TAM
  Jenis kontribusi        : [✓] Exploratory
  Gap yang diisi          : Menggabungkan AI dan TAM dalam konteks aplikasi pembelajaran bahasa

Hypothesis Pair:
  H₀ : Tidak terdapat pengaruh signifikan antara Perceived Ease of Use (PEOU) dan Perceived Usefulness (PU) terhadap kepuasan pengguna aplikasi Duolingo
  H₁ : Terdapat pengaruh signifikan antara Perceived Ease of Use (PEOU) dan Perceived Usefulness (PU) terhadap kepuasan pengguna aplikasi Duolingo
  Threshold              : 0.05
  Justifikasi threshold  : Nilai 0.05 merupakan standar umum dalam penelitian kuantitatif untuk menentukan signifikansi statistik
```

---

## Latihan 1 — Dari Gap ke RQ

Gunakan gap yang ditemukan di WS-03. Transformasikan menjadi Research Question.

**Gap dari WS-03:** Belum ada penelitian yang menggabungkan AI + TAM + kepuasan pengguna dalam konteks aplikasi pembelajaran bahasa

**RQ versi pertama (tulis bebas):**
> Bagaimana pengaruh AI terhadap kepuasan pengguna aplikasi pembelajaran bahasa?

**Evaluasi RQ:**

| Komponen | Ada? | Isi |
|----------|------|-----|
| Metode spesifik | -    | Belum ada                    |
| Metrik terukur  | -    | Belum jelas                  |
| Baseline        | -   | Belum ada                    |
| Dataset/konteks | Ya   | Aplikasi pembelajaran bahasa |

**Tipe RQ:** [✓] Exploratory

**RQ versi revisi (setelah evaluasi):**
> Apakah perceived ease of use dan perceived usefulness dari teknologi AI pada aplikasi Duolingo berpengaruh signifikan terhadap kepuasan pengguna berdasarkan model TAM?
---

## Latihan 2 — Hypothesis Pair

Rumuskan pasangan hipotesis dari RQ di Latihan 1.

| Komponen | Isi |
|----------|-----|
| H₀ | Tidak terdapat pengaruh signifikan antara perceived ease of use dan perceived usefulness terhadap kepuasan pengguna aplikasi Duolingo |
| H₁ | Terdapat pengaruh signifikan antara perceived ease of use dan perceived usefulness terhadap kepuasan pengguna aplikasi Duolingo |
| Metrik | Nilai signifikansi (p-value), koefisien regresi |
| Threshold | 0.05 |
| Justifikasi threshold | Nilai 0.05 merupakan standar umum dalam penelitian kuantitatif untuk menentukan signifikansi statistik |

**Apakah hipotesis ini falsifiable?** Ya 

> Bagaimana cara membuktikannya salah? Jika hasil analisis menunjukkan nilai p-value lebih besar dari 0.05, maka hipotesis alternatif ditolak dan H₀ diterima.

---

## Latihan 3 — Rantai Operasionalisasi

Lengkapi rantai dari RQ hingga metode analisis.

| Tahap | Isi |
|-------|-----|
| RQ    | Apakah perceived ease of use dan perceived usefulness berpengaruh terhadap kepuasan pengguna Duolingo |
| Variable (IV)   | PEOU, PU                    |
| Variable (DV)   | Kepuasan pengguna           |
| Metric          | Skor Likert, nilai regresi  |
| Data source     | Kuesioner pengguna Duolingo |
| Analysis method | Regresi linear / analisis statistik  |

**Apakah rantai lengkap?** Ya

> Karena seluruh komponen dalam rantai operasionalisasi telah terpenuhi, yaitu Research Question (RQ), variabel independen (PEOU dan PU), variabel dependen (kepuasan pengguna), metrik yang digunakan (skala Likert dan analisis regresi), sumber data (kuesioner pengguna Duolingo), serta metode analisis (regresi statistik). Setiap komponen saling terhubung dan dapat digunakan untuk menguji hipotesis secara empiris.

---

## Refleksi

> Ambil satu judul skripsi/paper yang pernah dibaca. Coba ekstrak RQ-nya. Apakah RQ tersebut memenuhi semua komponen (metode, metrik, baseline, konteks)? Jika tidak, apa yang hilang?

**Judul:** Pengaruh Teknologi Artificial Intelligence pada aplikasi Duolingo terhadap kepuasan pengguna

**RQ yang diekstrak:** Apakah AI pada aplikasi Duolingo berpengaruh terhadap kepuasan pengguna?

**Komponen yang hilang:** RQ tersebut belum menyebutkan metrik yang digunakan, metode analisis, serta baseline pembanding, sehingga perlu diperjelas agar dapat diuji secara ilmiah.
