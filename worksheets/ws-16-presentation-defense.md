# WS-16: Presentation & Defense (UAS)

> **Bab 16 — Presentasi & Pertahanan Ilmiah**

---

## Ringkasan Materi

### Scientific Defense Model

```
Research Work → Presentation → Questioning → Defense → Evaluation → Acceptance
```

### Presentasi ≠ Ringkasan Paper

| Paper | Presentasi |
|-------|-----------|
| Dibaca (self-paced) | Didengar (presenter-paced) |
| Detail lengkap | Ide kunci + highlight |
| Tabel numerik detail | Grafik visual + angka kunci |
| Pembaca bisa re-read | Audiens dengar sekali |

**Prinsip:** Presentasi membutuhkan **reformulasi**, bukan kompresi. Medium berbeda = pendekatan berbeda.

### Claim-Evidence-Reasoning (CER)

Setiap jawaban defense harus memiliki:
1. **Claim** — Pernyataan yang dijawab
2. **Evidence** — Data/fakta pendukung
3. **Reasoning** — Logika yang menghubungkan evidence ke claim

**Contoh:**
| Pertanyaan | Bad Answer | Good Answer (CER) |
|-----------|-----------|-------------------|
| "Kenapa hanya 3 dataset?" | "Tiga sudah cukup" | "3 dataset mewakili variasi: small-clean, medium-clean, medium-noisy [E]. Generalisasi perlu validasi lanjut — listed as limitation [R]" |
| "Hasil DS-3 menurun?" | "Itu outlier" | "Ya, karena distribusi heavy-tail melanggar asumsi Gaussian [E]. Ini menunjukkan boundary condition metode [R]" |
| "Effect size?" | "p=0.003, jadi signifikan" | "Cohen's d=1.2 (large effect) [E] — bukan hanya signifikan tapi substansial [R]" |

### Slide Design — One Slide, One Message

**Optimal 9-Slide Plan (15 menit):**

| # | Slide | Waktu | Pesan |
|---|-------|-------|-------|
| 1 | Title + context | 1 min | Apa ini tentang apa |
| 2 | Problem + motivation | 2 min | Mengapa penting |
| 3 | Gap + RQ | 1.5 min | Apa yang belum terjawab |
| 4 | Method overview | 2 min | Bagaimana dijawab (diagram) |
| 5 | Key result — tabel | 2 min | Temuan utama |
| 6 | Key result — grafik | 2 min | Pola visual |
| 7 | Interpretation + failure | 2 min | Apa artinya |
| 8 | Limitation + future | 1.5 min | Batasan & arah |
| 9 | Conclusion + contribution | 1 min | Closing message |

### Anticipatory Defense

Prediksi pertanyaan berdasarkan kategori:

| Kategori | Contoh Pertanyaan |
|---------|------------------|
| Problem | "Mengapa masalah ini penting?" |
| Gap | "Bagaimana dengan studi X yang sudah menjawab ini?" |
| Method | "Mengapa metode ini, bukan Y?" |
| Results | "Bagaimana menjelaskan anomali di DS-3?" |
| Generalization | "Apakah bisa diterapkan di domain lain?" |

### Tiga Prinsip Jawaban

1. **Direct** — Jawab dulu, elaborasi kemudian
2. **Data-based** — Tunjuk evidence spesifik
3. **Honest** — Akui limitasi jika memang ada

### Jebakan Kognitif

1. "Presentasi = semua yang ada di paper" → terlalu padat
2. "Slide cantik = presentasi bagus" → konten > estetika
3. "Tidak bisa jawab = gagal" → "I don't know, but..." menunjukkan kejujuran
4. "Tidak perlu latihan — saya paham riset saya" → latihan = menemukan celah

---

## Template A.16 — Defense Preparation Sheet

```
DEFENSE PREPARATION

Slide Deck Plan:
  Total slides   : 9 (konten) + title/closing tergabung
  Time per slide : ~1.5-2 min
  Total time     : 15 menit

Slide Outline:
| # | Pesan Utama | Visual | Waktu |
|---|-------------|--------|-------|
| 1 | Title + konteks: pengaruh fitur AI Duolingo terhadap kepuasan pengguna (TAM) | Title slide | 1 min |
| 2 | Problem: adopsi AI di aplikasi pembelajaran bahasa meningkat, pengaruhnya terhadap kepuasan belum banyak diteliti | Ilustrasi konteks + poin masalah | 2 min |
| 3 | Gap + RQ: belum ada studi yang gabungkan AI+TAM khusus Duolingo | Tabel ringkas gap dari 5 jurnal (WS-03) | 1.5 min |
| 4 | Method: desain Comparison Control vs Treatment, kuesioner TAM | Diagram alur metode (System-Experiment Mapping, WS-06) | 2 min |
| 5 | Key result — tabel: Control (n=55, 3.55±0.5) vs Treatment (n=80, 4.13±0.5), p<0.001, d=1.16 | Tabel hasil | 2 min |
| 6 | Key result — grafik: perbandingan skor & distribusi | Bar chart + box plot (WS-12) | 2 min |
| 7 | Interpretation + temuan sekunder: PU tidak signifikan pada regresi terpisah | Diagram interpretasi | 2 min |
| 8 | Limitation + future work: confounding, generalisasi sampel, uji moderasi durasi penggunaan | Daftar poin | 1.5 min |
| 9 | Conclusion + kontribusi: RQ terjawab, bukti empiris TAM+AI pada Duolingo | Closing slide | 1 min |

Anticipatory Defense Matrix:
| Kategori | Pertanyaan Potensial | Jawaban (CER) |
|----------|---------------------|---------------|
| Problem  | Mengapa fokus kepuasan, bukan efektivitas belajar bahasa? | Kepuasan adalah prediktor keberlanjutan penggunaan aplikasi [E: literatur TAM soal retensi pengguna] [R: aplikasi efektif tapi tidak memuaskan berisiko ditinggalkan sebelum manfaat belajarnya tercapai] |
| Gap      | Bukankah TAM di aplikasi edukasi sudah banyak diteliti? | Sudah banyak, tapi belum spesifik pada fitur AI di aplikasi pembelajaran bahasa [E: telaah 5 jurnal WS-03 masih memisahkan AI dan usability] [R: kombinasi AI+TAM+konteks Duolingo mengisi gap tersebut] |
| Method   | Kenapa pakai Comparison, bukan survei ke pengguna Duolingo saja? | Comparison diperlukan untuk mengisolasi pengaruh AI [E: kelompok Control sebagai baseline non-AI] [R: tanpa baseline, tidak bisa dipastikan kepuasan tinggi disebabkan AI atau faktor lain] |
| Results  | Effect size besar, tapi apa bukan karena sampel kurang representatif? | Effect size tetap didukung data statistik yang kuat [E: CI 95% [0.41, 0.75], p<0.001] [R: meski keterbatasan sampel sudah dicatat, besarnya efek konsisten dan bukan kebetulan statistik] |
| Generalization | Apakah hasil bisa digeneralisasi ke aplikasi bahasa lain? | Belum bisa digeneralisasi langsung [E: instrumen dirancang spesifik untuk konteks Duolingo] [R: replikasi di aplikasi lain (Babbel, Memrise) diperlukan, dicatat sebagai future work] |

Latihan:
  Latihan 1: [direncanakan] — menyusun outline 9 slide sesuai porsi waktu 15 menit
  Latihan 2: [direncanakan] — menyiapkan 5 CER untuk kategori pertanyaan utama
  Latihan 3: [direncanakan] — simulasi Q&A dengan teman sejawat, evaluasi kejujuran & data-based-ness jawaban

```

---

## Latihan 1 — Slide Outline

Rencanakan presentasi 15 menit untuk riset Anda.

| # | Pesan Utama | Visual yang Digunakan | Waktu |
|---|-------------|----------------------|-------|
| 1 | Judul + konteks: pengaruh fitur AI Duolingo terhadap kepuasan pengguna| Title slide | 1 min |
| 2 | Problem: AI makin banyak dipakai di aplikasi pembelajaran bahasa, pengaruhnya ke kepuasan belum jelas | Poin masalah + ilustrasi Duolingo |2 menit|
| 3 | Gap + RQ: belum ada studi AI+TAM khusus Duolingo | Tabel ringkas gap literatur | 1.5 min |
| 4 | Method: desain Comparison, kuesioner TAM (PEOU, PU, Kepuasan) |Diagram alur metode | 2 min |
| 5 | Hasil utama (tabel): Control vs Treatment, p<0.001, d=1.16 | Tabel statistik deskriptif + hasil uji | 2 min |
| 6 | Hasil utama (grafik): perbandingan & distribusi skor | Bar chart + box plot | 2 min |
| 7 | Interpretasi: AI berasosiasi kepuasan lebih tinggi + temuan sekunder PU | Diagram interpretasi ringkas | 2 min |
| 8 | Limitasi & arah lanjutan | Daftar poin | 1.5 min |
| 9 | Kesimpulan & kontribusi | Closing slide | 1 min |

**Total waktu estimasi:** 15 menit

---

## Latihan 2 — Anticipatory Defense

Prediksi 5 pertanyaan yang mungkin diajukan penguji, lalu siapkan jawaban CER.

| # | Kategori | Pertanyaan | Claim | Evidence | Reasoning |
|---|----------|-----------|-------|----------|-----------|
| 1 | Problem | Mengapa fokus pada kepuasan pengguna, bukan efektivitas belajar bahasa? | Kepuasan pengguna adalah prediktor penting keberlanjutan penggunaan aplikasi |Literatur TAM menunjukkan kepuasan berkorelasi dengan retensi pengguna jangka panjang | Aplikasi yang efektif secara pedagogis tapi tidak memuaskan berisiko ditinggalkan sebelum manfaat belajarnya tercapai |
| 2 | Gap | Bukankah sudah banyak penelitian TAM tentang aplikasi edukasi? | Penelitian TAM sudah banyak, tapi belum spesifik pada fitur AI di aplikasi pembelajaran bahasa seperti Duolingo | Telaah 5 jurnal di WS-03 menunjukkan penelitian umumnya membahas AI atau usability secara terpisah | Kombinasi AI+TAM+konteks Duolingo yang mengisi gap tersebut |
| 3 | Method | Kenapa pakai desain Comparison, bukan survei ke pengguna Duolingo saja? | Comparison diperlukan untuk mengisolasi pengaruh fitur AI | Kelompok Control (aplikasi non-AI) memberi baseline pembanding | Tanpa baseline, tidak bisa dipastikan skor kepuasan tinggi disebabkan AI atau faktor lain di luar AI |
| 4 | Results | Effect size besar (d=1.16), tapi apa bukan karena sampel kurang representatif? | Effect size besar tetap didukung data statistik yang kuat | CI 95% selisih mean [0.41, 0.75], p<0.001 | Meski keterbatasan representativitas sampel sudah dicatat, besarnya efek dan signifikansi tetap menunjukkan pola yang kuat, bukan sekadar kebetulan statistik |
| 5 | Generalization | Apakah hasil ini bisa digeneralisasi ke aplikasi pembelajaran bahasa lain? | Belum bisa digeneralisasi langsung ke semua aplikasi pembelajaran bahasa lain | Sampel dan instrumen dirancang spesifik untuk konteks Duolingo | Diperlukan replikasi pada aplikasi lain untuk menguji apakah pola yang sama berlaku — dicatat sebagai future work |

---

## Latihan 3 — Simulasi Q&A

Minta teman/kolega mengajukan 3 pertanyaan tentang riset Anda. Catat pertanyaan dan evaluasi jawaban Anda.

| # | Pertanyaan | Jawaban Saya | Evaluasi |
|---|-----------|-------------|---------|
| 1 | Kenapa tidak sekalian pakai wawancara, bukan cuma kuesioner? | Kuesioner Likert lebih efisien mengukur PEOU dan PU secara terstruktur pada 135 responden; wawancara mendalam lebih cocok untuk sampel kecil. Keterbatasan ini dicatat sebagai future work untuk penelitian kualitatif lanjutan | [✓] Direct [✓] Data-based [✓] Honest |
| 2 | Kalau PU tidak signifikan di regresi tambahan, apa berarti PU tidak penting? | PU tetap penting secara konseptual, tapi kontribusi uniknya kemungkinan tumpang tindih dengan PEOU dalam konteks ini (indikasi multikolinearitas). Ini temuan sekunder yang perlu diuji lebih lanjut, bukan berarti PU diabaikan | [✓] Direct [✓] Data-based [✓] Honest|
| 3 | Bagaimana kalau ada bias karena pengguna Treatment memang sudah suka teknologi baru dari awal? | Itu ancaman internal validity yang sudah dicatat sebagai limitasi — kemungkinan confounding karena karakteristik responden Treatment lebih terbuka pada teknologi. Penelitian lanjutan perlu mengontrolnya secara eksplisit sebagai kovariat | [✓] Direct [✓] Data-based [✓] Honest |

**Pertanyaan yang paling sulit dijawab:**
> Pertanyaan ke-3 tentang kemungkinan confounding karena karakteristik responden Treatment. Ini kelemahan riil dalam desain penelitian yang tidak bisa dibantah dengan argumen saja — harus diakui secara jujur sebagai limitasi, dan itu terasa lebih sulit dibanding menjawab pertanyaan yang jawabannya sudah didukung data statistik langsung.
**Apa yang perlu disiapkan lebih baik:**
> Menyiapkan data karakteristik responden (misalnya lama penggunaan aplikasi, frekuensi penggunaan teknologi) sebagai bahan pendukung tambahan saat ditanya soal confounding, serta berlatih menjawab pertanyaan sulit dengan lebih ringkas tanpa terkesan defensif.
---

## Refleksi

> Dari seluruh proses WS-01 sampai WS-16 — dari paradigma riset hingga presentasi — bagian mana yang paling mengubah cara Anda berpikir tentang riset? Apa satu hal yang akan selalu Anda terapkan di riset berikutnya?

**Insight terbesar:**
> Bagian yang paling mengubah cara berpikir adalah menyadari bahwa setiap tahap riset — dari RQ (WS-04) sampai presentasi (WS-16) — harus saling terhubung sebagai satu argumen utuh (red thread), bukan kumpulan tugas yang berdiri sendiri. Ini terlihat jelas saat menyusun consistency matrix di WS-15 dan menemukan bahwa temuan sekunder soal PU belum diperkenalkan sejak Method — sebuah koneksi yang putus persis seperti yang dijelaskan sejak WS-08. Selain itu, memahami bahwa hasil yang tidak signifikan atau anomali (seperti gelombang data yang belum lengkap di WS-11, atau kontribusi PU yang tidak signifikan di WS-14) bukan kegagalan, melainkan bagian sah dari proses ilmiah yang harus didokumentasikan, bukan disembunyikan.

**Yang akan selalu diterapkan:**
> Melakukan pengecekan konsistensi menyeluruh (seperti consistency matrix) sebelum menganggap sebuah tulisan atau penelitian selesai — memastikan setiap klaim di bagian akhir benar-benar bisa ditelusuri balik ke RQ dan data di bagian awal, dan tidak menyembunyikan atau meremehkan hasil yang tidak sesuai harapan, melainkan menjelaskannya secara jujur beserta kemungkinan penyebabnya.
