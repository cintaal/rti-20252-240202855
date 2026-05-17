# WS-07: Experimental Design & Validity

> **Bab 7 — Experimental Design & Validity**

---

## Ringkasan Materi

### Correlation ≠ Causality

Kausalitas membutuhkan 3 syarat:
1. **Covariance** — X dan Y bergerak bersama
2. **Temporal precedence** — X berubah sebelum Y
3. **Elimination of alternatives** — Tidak ada faktor lain yang menjelaskan Y

Controlled experiment adalah satu-satunya metode yang bisa membuktikan kausalitas.

### Empat Jenis Validitas

| Jenis | Pertanyaan | Ancaman Umum |
|-------|-----------|-------------|
| **Internal** | Apakah hubungan IV→DV nyata? | Confounding variable, selection bias |
| **External** | Apakah bisa digeneralisasi? | Dataset terlalu spesifik |
| **Construct** | Apakah mengukur konsep yang benar? | Metrik tidak sesuai |
| **Conclusion** | Apakah kesimpulan statistik valid? | Sample size kecil, uji salah |

Internal dan external validity sering berkonflik: semakin terkontrol (internal kuat) → semakin artificial (external lemah).

### Tiga Tipe Eksperimen dalam Riset TI

| Tipe | Deskripsi | Kapan Digunakan |
|------|----------|----------------|
| **Comparison Study** | Metode A vs B pada kondisi identik | Membandingkan pendekatan berbeda |
| **Ablation Study** | Full system → lepas komponen satu per satu | Mengukur kontribusi tiap komponen |
| **Parameter Study** | Variasikan satu parameter, amati dampak | Uji sensitifitas/robustness |

### Fairness dalam Perbandingan

Perbandingan yang adil = **kondisi identik** untuk semua metode: dataset sama, preprocessing sama, tuning effort sebanding, environment sama, metrik sama.

Contoh tidak adil: Transformer (30 fitur tambahan + Bayesian optimization) vs RF (default params) → hasilnya misleading.

### Threats to Validity = Diidentifikasi Sebelum Eksperimen

Ancaman validitas harus diidentifikasi **sebelum** eksperimen dan mitigasinya dirancang sebagai bagian dari desain — bukan ditulis sebagai boilerplate setelah selesai.

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan testing | Memastikan sistem memenuhi requirement | Membuktikan hubungan kausal antar variabel |
| Baseline | Versi sebelumnya (last release) | Metode tervalidasi dari literatur |
| Kegagalan | Bug → fix → release | H₀ tidak ditolak → tetap kontribusi ilmiah |
| Sukses | 100% test pass | Evidence valid — mendukung atau menolak hipotesis |

### Istilah Penting

- **Causality** — Hubungan sebab-akibat (covariance + temporal + elimination)
- **Controlled Experiment** — Ubah satu variabel, kontrol sisanya, amati efek
- **Fairness** — Semua metode diuji pada kondisi yang benar-benar identik
- **Threats to Validity** — Faktor yang bisa melemahkan kesimpulan jika tidak dimitigasi
- **Conclusion Validity** — Validitas statistik: power, sample size, uji yang tepat

---

## Template A.7 — Desain Eksperimen Lengkap

```
EXPERIMENT DESIGN

Research Question : Apakah Perceived Ease of Use (PEOU) dan Perceived Usefulness (PU) dari teknologi Artificial Intelligence pada aplikasi Duolingo berpengaruh signifikan terhadap kepuasan pengguna?
Hypothesis        : H₀ = PEOU dan PU tidak berpengaruh signifikan terhadap kepuasan pengguna Duolingo.
H₁ = PEOU dan PU berpengaruh signifikan terhadap kepuasan pengguna Duolingo.
Tipe Eksperimen   : [ ✓ ] Comparison  [ ] Ablation  [ ] Parameter

Kondisi Eksperimen:
| Kondisi | Deskripsi | IV Value | CV Settings |
|---------|-----------|----------|-------------|
| Control | Model TAM standar tanpa fokus AI | PEOU & PU umum | Skala Likert 1-5, responden pengguna aplikasi belajar bahasa, metode analisis regresi |
| Treatment |Model TAM pada fitur AI Duolingo |PEOU & PU berbasis AI| Skala Likert 1-5, responden pengguna Duolingo, metode analisis regresi |

Fairness Checklist:
  [ ✓ ] Dataset identik untuk semua kondisi
  [ ✓ ] Preprocessing setara
  [ ✓ ] Tuning effort setara
  [ ✓ ] Environment identik
  [ ✓ ] Metrik evaluasi sama

Threat Analysis:
| Threat Type | Ancaman Spesifik | Mitigasi |
|-------------|-----------------|----------|
| Internal    | Jawaban responden tidak konsisten |Validasi dan pengecekan jawaban kuesioner|
| External    |Sampel hanya berasal dari pengguna tertentu| Menambah variasi responden |
| Construct   |Pertanyaan kuesioner tidak merepresentasikan konsep TAM|Menggunakan indikator TAM dari penelitian terdahulu|
| Conclusion  | Jumlah responden terlalu sedikit |enentukan minimal jumlah sampel sebelum eksperimen 

Statistical Plan:
  Uji statistik   : Regresi linear dan uji t
  Justifikasi      : Digunakan untuk melihat pengaruh variabel independen terhadap variabel dependen
  Alpha            : 0.05
  Effect size min  : 0.3
```

---

## Latihan 1 — Desain Eksperimen

Susun desain eksperimen berdasarkan RQ, variabel, dan sistem dari WS-04 sampai WS-06.

**RQ:** Apakah PEOU dan PU dari teknologi AI pada aplikasi Duolingo berpengaruh terhadap kepuasan pengguna?
**Tipe eksperimen:** [ ✓ ] Comparison / [ ] Ablation / [ ] Parameter

| Kondisi | Deskripsi | IV Value | CV Settings |
|---------|-----------|----------|-------------|
| Control | Pengukuran TAM standar| PEOU & PU umum | Skala Likert, metode analisis sama |
| Treatment | Pengukuran TAM berbasis fitur AI Duolingo | PEOU & PU AI | Skala Likert, metode analisis sama |

---

## Latihan 2 — Fairness Checklist

Evaluasi apakah desain eksperimen di Latihan 1 sudah fair.

| Kriteria | Status | Detail |
|----------|--------|--------|
| Dataset identik |✅|Semua data berasal dari kuesioner pengguna aplikasi pembelajaran bahasa|
| Preprocessing setara |✅| Semua jawaban diproses dengan metode yang sama |
| Tuning effort setara |✅|Analisis statistik dilakukan dengan perlakuan yang sama |
| Environment identik |✅| Pengumpulan data dilakukan pada platform dan kondisi yang sama |
| Metrik evaluasi sama |✅| Semua variabel menggunakan skala Likert |

**Ada yang tidak fair?** [✓ ] Tidak
> Semua kondisi eksperimen menggunakan dataset, metode analisis, dan metrik yang sama sehingga tidak ada perlakuan yang berbeda secara tidak adil.
---

## Latihan 3 — Threat Analysis

Identifikasi ancaman validitas untuk desain eksperimen ini.

| Threat Type | Ancaman Spesifik | Mitigasi |
|-------------|-----------------|----------|
| Internal | Bias jawaban responden | Membuat pertanyaan yang jelas dan tidak ambigu |
| External | Hasil tidak dapat digeneralisasi ke semua pengguna aplikasi belajar | Menambah jumlah dan variasi responden |
| Construct | Variabel TAM tidak terukur dengan tepat | Menggunakan indikator dari penelitian sebelumnya |
| Conclusion | Kesimpulan statistik kurang kuat akibat sampel kecil | Menentukan jumlah minimal responden |

**Ancaman mana yang paling sulit dimitigasi?** External validity
**Mengapa?**
> Karena perilaku dan persepsi pengguna dapat berbeda-beda tergantung usia, pengalaman, dan kebiasaan penggunaan aplikasi sehingga hasil penelitian belum tentu berlaku untuk semua populasi pengguna.

---

## Refleksi

> Sebuah paper melaporkan "metode kami mengalahkan semua baseline." Apa 3 pertanyaan pertama yang harus diajukan untuk mengevaluasi klaim ini?

**Jawaban:**
1. Apakah semua baseline diuji pada kondisi dan dataset yang sama?
2. Apakah metrik evaluasi yang digunakan sama dan relevan?
3. Apakah metode pembanding mendapatkan perlakuan eksperimen yang adil?
