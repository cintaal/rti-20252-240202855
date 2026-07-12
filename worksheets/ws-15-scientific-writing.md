# WS-15: Scientific Writing

> **Bab 15 — Penulisan Ilmiah**

---

## Ringkasan Materi

### Scientific Argument Flow

```
Problem → Gap → RQ → Method → Result → Analysis → Conclusion → Contribution
```

Paper ilmiah adalah **satu argumen utuh** dari masalah ke kontribusi. Setiap node harus terhubung logis ke node sebelum dan sesudahnya.

### Struktur IMRAD

| Section | Peran | Pertanyaan Kunci |
|---------|-------|-----------------|
| **Introduction** | Motivasi + frame | Why is this needed? |
| **Method** | Deskripsi (reproducible) | How was it done? |
| **Results** | Laporan objektif | What was found? |
| **Discussion** | Interpretasi + refleksi | What does it mean? |
| **Conclusion** | Ringkasan + kontribusi | So what? |

### Logical Flow — "Red Thread"

Setiap paragraf menjawab satu pertanyaan dan memicu pertanyaan berikutnya. Alur logis ini harus terasa di tiga level:
1. **Antar-kalimat** dalam paragraf
2. **Antar-paragraf** dalam section
3. **Antar-section** dalam paper

### Internal Consistency

Setiap elemen yang dijanjikan di Introduction harus hadir di Discussion/Conclusion.

**Consistency Matrix:**
```
           Intro  Method  Result  Discuss  Conclude
RQ1          ✓      ✓       ✓       ✓        ✓
RQ2          ✓      ✓       ✓       ✗ ←      ✓
Metrik-X     ✗      ✗       ✓ ←     ✗        ✗
```
**Masalah:** RQ2 dibahas di semua bagian kecuali Discussion. Metrik-X muncul di Result tapi tidak diperkenalkan di Method.

### Writing Quality Triad

| Kualitas | Deskripsi | Contoh Buruk → Baik |
|----------|----------|---------------------|
| **Clarity** | Dipahami sekali baca | "Performa meningkat" → "Accuracy meningkat dari 85.3% ke 89.7%" |
| **Precision** | Istilah eksak, tanpa ambiguitas | "signifikan" → "signifikan secara statistik (p=0.003, d=1.2)" |
| **Conciseness** | Setiap kata menambah informasi | Hapus kalimat redundan, filler words |

### Urutan Penulisan yang Disarankan

1. **Method & Results** — paling stabil, tulis pertama
2. **Discussion** — interpretasi berdasarkan hasil
3. **Introduction** — frame sesuai temuan aktual
4. **Abstract & Conclusion** — terakhir

### Target Jumlah Kata

| Section | Target |
|---------|--------|
| Introduction | 500–700 |
| Related Work | 700–1000 |
| Method | 800–1200 |
| Results | 500–800 |
| Discussion | 600–900 |
| Conclusion | 200–400 |

### Jebakan Kognitif

1. "Lebih panjang = lebih lengkap" → conciseness lebih berharga
2. "Introduction harus ditulis pertama" → justru ditulis terakhir
3. "Jargon teknis = lebih ilmiah" → clarity lebih penting
4. "Discussion = ringkasan Results" → Discussion = interpretasi + konteks

---

## Template A.15 — Paper Structure Checklist

```
PAPER STRUCTURE CHECKLIST

Title   : Pengaruh Fitur Artificial Intelligence pada Aplikasi Duolingo terhadap Kepuasan Pengguna: Pendekatan Technology Acceptance Model (TAM)
Target  : [ ] Jurnal  [ ] Konferensi  [✓] Laporan

Section Check:
  [✓] Abstract — masalah, metode, hasil utama, kontribusi (max 250 kata)
  [✓] Introduction — konteks → gap → RQ → kontribusi → struktur paper
  [✓] Related Work — concept-centric, gap positioning
  [✓] Method — reproducible: desain, variabel, metrik, setup, prosedur
  [✓] Results — tabel + grafik + observasi (tanpa interpretasi)
  [✓] Discussion — interpretasi, perbandingan, implikasi, limitation
  [✓] Conclusion — jawaban RQ, kontribusi, future work

Consistency Matrix:
  [✓] RQ di Introduction = RQ di Method = RQ di Conclusion
  [✓] Variabel di Method = variabel di Results
  [~] Klaim di Discussion didukung data di Results — ada 1 klaim (analisis regresi tambahan PU) yang belum didukung penuh di Results, lihat Latihan 2
  [ ] Limitasi di Discussion di-address di Conclusion/Future Work — belum sepenuhnya, perlu ditambahkan

Writing Quality:
  [✓] Clarity — mudah dipahami tanpa re-read
  [✓] Precision — tidak ada istilah ambigu
  [✓] Conciseness — tidak ada kalimat redundan
```

---

## Latihan 1 — Paper Outline

Buat outline paper untuk riset Anda menggunakan struktur IMRAD.

| Section | Konten Utama (2-3 kalimat) | Target Kata |
|---------|---------------------------|------------|
| Abstract | Penggunaan fitur AI pada aplikasi pembelajaran bahasa meningkat, namun pengaruhnya terhadap kepuasan pengguna belum banyak diteliti melalui TAM. Studi ini membandingkan skor PEOU, PU, dan Kepuasan Pengguna antara pengguna aplikasi non-AI (Control) dan pengguna Duolingo (Treatment). Hasil independent t-test menunjukkan Treatment memiliki Kepuasan Pengguna signifikan lebih tinggi (p<0.001, d=1.16). | 200-250 |
| Introduction | Konteks: adopsi AI pada aplikasi pembelajaran bahasa terus meningkat. Gap: belum banyak penelitian yang menggabungkan AI dan model TAM secara spesifik pada aplikasi seperti Duolingo. RQ: apakah PEOU dan PU dari fitur AI berpengaruh signifikan terhadap kepuasan pengguna? | 500-700 |
| Related Work | Tinjauan model TAM klasik (PEOU, PU sebagai prediktor kepuasan/penerimaan teknologi), studi-studi AI pada aplikasi edukasi, dan penempatan gap: minimnya studi TAM yang fokus pada fitur AI di aplikasi pembelajaran bahasa. | 700-1000 |
| Method | Desain Comparison Control vs Treatment (WS-07), instrumen kuesioner TAM via Google Form skala Likert 1-5, variabel PEOU/PU (IV), Kepuasan Pengguna (DV), lama penggunaan (CV). Pengumpulan data 2-3 gelombang per skenario, dengan preprocessing (cleaning missing/duplikat, robust scaling untuk CV). | 800-1200 |
| Results | Statistik deskriptif Control (n=55, Kepuasan 3.55±0.5) vs Treatment (n=80, Kepuasan 4.13±0.5). Hasil independent t-test: p<0.001, Cohen's d=1.16, CI 95% [0.41, 0.75]. Disertai bar chart perbandingan skor dan box plot distribusi Kepuasan Pengguna. | 500-800 |
| Discussion | Interpretasi bahwa fitur AI berasosiasi dengan kepuasan pengguna lebih tinggi, sejalan dengan literatur TAM. Dibahas juga temuan sekunder: kontribusi PU tidak signifikan saat PEOU dikontrol dalam regresi terpisah, mengindikasikan kemungkinan multikolinearitas atau efek moderasi durasi penggunaan. Limitasi: confounding karakteristik responden, generalisasi sampel, dan penggunaan uji parametrik pada data ordinal. | 600-900 |
| Conclusion | RQ terjawab: PEOU dan PU dari fitur AI Duolingo berpengaruh signifikan terhadap kepuasan pengguna. Kontribusi: bukti empiris penerapan TAM pada konteks AI di aplikasi pembelajaran bahasa. Future work: uji peran moderasi durasi penggunaan terhadap kontribusi PU, perluasan sampel. | 200-400 |

---

## Latihan 2 — Consistency Matrix

Buat consistency matrix untuk memverifikasi internal consistency paper Anda.

|  | Intro | Method | Result | Discussion | Conclusion |
|--|-------|--------|--------|-----------|-----------|
| RQ1 (pengaruh PEOU & PU terhadap Kepuasan) | *✓* | *✓* | *✓* | *✓* | *✓* |
| *Contoh: Metrik-X* | *✗ ←* | *✗ ←* | *✓* | *✗ ←* | *✗ ←* |
| RQ1 | N/A — penelitian ini hanya menggunakan 1 RQ utama | | | | |
| RQ2 | | | | | |
| Metrik utama |  *✓* | *✓* | *✓* | *✓* | *✓* |
| Variabel IV | *✓* | *✓* | *✓* | *✓* | *✓* | 
| Variabel DV | *✓* | *✓* | *✓* | *✓* | *✓* |
| Analisis regresi tambahan (kontribusi PU terpisah) | *✗ ←* | *✗ ←* | - | *✓* | *✗ ←* |

**Isi setiap sel:** ✓ (ada & konsisten), ✗ (missing), ~ (ada tapi inkonsisten)

**Inkonsistensi yang ditemukan:**
> Analisis regresi tambahan mengenai kontribusi PU secara terpisah (setelah PEOU dikontrol) — yang dibahas cukup panjang di Discussion (dari temuan WS-14 Latihan 3) — ternyata tidak pernah diperkenalkan di Introduction maupun Method, hanya disinggung sekilas di Results, dan tidak ditindaklanjuti sebagai future work eksplisit di Conclusion. Ini persis pola "Metrik-X" pada contoh di materi: muncul tiba-tiba di satu bagian tanpa fondasi di bagian sebelumnya.

**Tindakan perbaikan:**
> Tambahkan satu-dua kalimat di Method yang menyebutkan bahwa selain uji perbandingan utama, dilakukan juga analisis regresi tambahan untuk melihat kontribusi PEOU dan PU secara terpisah. Sertakan hasil regresi tersebut secara ringkas di bagian Results (bukan hanya di Discussion). Di Conclusion/Future Work, eksplisit sebutkan rencana menguji durasi penggunaan sebagai variabel moderasi, sebagai tindak lanjut dari temuan ini.
---

## Latihan 3 — Writing Quality Check

Ambil satu paragraf dari tulisan Anda (atau tulis paragraf baru) dan evaluasi kualitasnya.

**Paragraf asli:**
> Hasil penelitian menunjukkan bahwa performa aplikasi Duolingo lebih baik dibandingkan aplikasi lain. Hal ini signifikan dan menunjukkan bahwa AI berpengaruh terhadap penggunanya. Selain itu, hasil ini juga konsisten dengan penelitian-penelitian sebelumnya yang membahas tentang teknologi serupa.

| Kriteria | Evaluasi | Perbaikan |
|----------|---------|-----------|
| Clarity | "Performa" ambigu — bisa berarti kepuasan, PEOU, PU, atau kecepatan aplikasi, tidak jelas metrik mana yang dimaksud | Ganti dengan istilah spesifik: "skor Kepuasan Pengguna" |
| Precision | "Signifikan" tanpa angka pendukung; "penelitian-penelitian sebelumnya" tidak disebutkan konkret merujuk ke apa | Sertakan p-value dan effect size (p<0.001, d=1.16); sebutkan eksplisit merujuk ke literatur TAM |
| Conciseness | Kalimat kedua ("Hal ini signifikan dan menunjukkan bahwa AI berpengaruh...") redundan dengan kalimat pertama | Gabungkan menjadi satu kalimat yang langsung menyatakan hasil dan signifikansinya |

**Paragraf setelah perbaikan:**
> Skor rata-rata Kepuasan Pengguna pada kelompok Treatment (pengguna Duolingo dengan fitur AI) secara signifikan lebih tinggi dibanding kelompok Control (M = 4.13 vs M = 3.55; p < 0.001; Cohen's d = 1.16). Temuan ini konsisten dengan penelitian TAM sebelumnya yang menunjukkan bahwa peningkatan Perceived Ease of Use dan Perceived Usefulness berkorelasi positif dengan kepuasan pengguna terhadap teknologi baru.
---

## Refleksi

> Apa perbedaan antara menulis "tentang" riset dan menulis sebagai "argumen" riset? Bagaimana urutan penulisan (Method → Discussion → Introduction) mengubah kualitas tulisan?

> Menulis "tentang" riset berarti sekadar melaporkan apa yang dilakukan secara berurutan tanpa mempedulikan apakah satu bagian benar-benar menjawab pertanyaan dari bagian sebelumnya — seperti paragraf asli di Latihan 3 yang menyebut "performa lebih baik" tanpa menghubungkannya secara eksplisit ke RQ atau data. Menulis sebagai "argumen" berarti setiap section secara sengaja membangun ke satu kesimpulan: Introduction mengajukan pertanyaan, Method menjelaskan cara menjawabnya, Results menyajikan buktinya, dan Discussion menutup argumen dengan mengaitkan bukti tersebut kembali ke RQ.
> Menulis Method dan Results lebih dulu (karena datanya sudah pasti dan stabil, tidak berubah-ubah) membuat Discussion bisa ditulis berdasarkan apa yang benar-benar ditemukan — termasuk temuan sekunder seperti kontribusi PU yang tidak signifikan pada regresi terpisah. Setelah itu, Introduction ditulis terakhir supaya framing masalah dan gap benar-benar sesuai dengan apa yang akhirnya dibahas di Discussion, bukan janji di awal yang tidak pernah ditepati di akhir — seperti yang justru ditemukan pada Latihan 2 (analisis regresi tambahan yang tidak diperkenalkan sejak awal).
