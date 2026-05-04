# WS-02: Problem Statement

> **Bab 2 — Problem Formulation & System Context**

---

## Ringkasan Materi

### Problem Formation Model

Masalah riset melewati 5 tahap transformasi. Melompat langsung dari Reality ke Variable adalah kesalahan paling umum.

```
Reality → Observed Issue (Symptom) → Diagnosed Problem (Root Cause)
→ Researchable Problem (Scoped) → Measurable Variable (Operationalized)
```

### Topic ≠ Problem ≠ Research Problem

| Level | Contoh | Status |
|-------|--------|--------|
| **Topik** | Keamanan IoT | Terlalu luas, tidak bisa diuji |
| **Problem** | MQTT tidak terenkripsi | Spesifik tapi belum riset |
| **Research Problem** | Belum ada studi membandingkan overhead TLS 1.3 vs DTLS pada MQTT di IoT RAM < 64KB | Bisa dirancang eksperimennya |

### Symptom vs Root Cause

Apa yang diamati (gejala) ≠ mengapa terjadi (akar masalah). Gunakan **5 Whys** atau **Fishbone Diagram** untuk menggali.

Contoh: "User meninggalkan checkout" (symptom) → "Waktu loading > 8 detik karena API call sequential" (root cause).

### System Thinking

Setiap masalah riset TI harus terikat pada komponen sistem: **Input → Process → Output → Outcome → Constraints → Stakeholders**.

### Problem Quality Check

Masalah riset yang layak harus memenuhi 5 kriteria:
- **Clarity** — Satu orang membaca akan paham
- **Measurability** — Ada metrik kuantitatif
- **Relevance** — Penting untuk domain
- **Testability** — Bisa gagal (falsifiable)
- **Impact** — Ada kontribusi jika terjawab

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan | Menyelesaikan masalah (*solve*) | Memahami dan membuktikan (*understand & prove*) |
| Masalah | Bug, error, fitur belum ada | Gap dalam pengetahuan |
| Scope | Selesaikan semua yang perlu | Batasi agar bisa dibuktikan |
| Output | Working system | Evidence, paper, replicable findings |

### Istilah Penting

- **Problem Statement** — Formulasi tertulis: konteks sistem + gap + dampak + justifikasi
- **System Context** — Deskripsi lengkap: input, proses, output, outcome, constraints, stakeholders
- **Problem Drift** — Masalah "bermutasi" dari pendahuluan ke metodologi karena statement awal tidak presisi
- **Solution-First Thinking** — Memulai dari solusi tanpa masalah yang jelas — berbahaya dalam riset
- **Operational Definition** — Definisi variabel yang cukup jelas agar peneliti lain bisa mengukur hal yang sama

---

## Template A.2 — Problem Statement Builder

```
PROBLEM STATEMENT BUILDER

Domain & Konteks
  Domain   :  Teknologi Informasi (Artificial Intelligence dalam pembelajaran digital) 
  Konteks  : Penggunaan aplikasi Duolingo berbasis AI untuk pembelajaran bahasa

System Context
  Input       : Data interaksi pengguna, jawaban latihan, aktivitas belajar pengguna
  Process     : AI memproses data untuk menyesuaikan materi, memberikan feedback, dan rekomendasi belajar
  Output      : Materi pembelajaran yang dipersonalisasi, skor, dan evaluasi otomatis
  Outcome     : Tingkat kepuasan pengguna dan efektivitas pembelajaran
  Constraints : Jumlah responden terbatas (100 orang), metode hanya kuantitatif
  Stakeholders: Pengguna Duolingo, pengembang aplikasi, peneliti

Fenomena → Problem
  Fenomena yang diamati             : Penggunaan aplikasi Duolingo berbasis AI semakin meningkat dalam pembelajaran bahasa.
  Gejala (symptom) yang terukur     : Tingkat penggunaan tidak selalu konsisten dan kepuasan pengguna bervariasi
  Masalah yang didiagnosis          : Belum diketahui secara jelas pengaruh teknologi AI terhadap kepuasan pengguna
  Masalah riset (researchable)      : Belum ada analisis terstruktur menggunakan model TAM untuk mengukur pengaruh AI terhadap kepuasan pengguna Duolingo
  Variabel yang terukur             : Perceived Ease of Use (PEOU), Perceived Usefulness (PU), Attitude Toward Use (AT), Behavioral Intention (BI), Actual Usage (AU)

Problem Quality Check
  [✓] Clarity — Apakah satu orang membaca akan paham?
  [✓] Measurability — Apakah ada metrik kuantitatif?
  [✓] Relevance — Apakah penting untuk domain?
  [✓] Testability — Apakah bisa gagal?
  [✓] Impact — Apakah ada kontribusi jika terjawab?

Problem Statement (1 paragraf):
 Penggunaan teknologi Artificial Intelligence (AI) dalam aplikasi pembelajaran bahasa seperti Duolingo semakin berkembang dan memberikan pengalaman belajar yang lebih adaptif dan personal. Namun, masih belum jelas sejauh mana teknologi AI tersebut mempengaruhi tingkat kepuasan pengguna. Oleh karena itu, diperlukan analisis yang terstruktur untuk mengukur pengaruh AI terhadap kepuasan pengguna dengan menggunakan model Technology Acceptance Model (TAM), melalui variabel perceived ease of use, perceived usefulness, attitude toward use, behavioral intention, dan actual usage, sehingga dapat memberikan pemahaman yang lebih jelas mengenai penerimaan teknologi AI dalam aplikasi pembelajaran.
```

---

## Latihan 1 — Dari Topik ke Masalah Riset

Pilih satu topik di bidang TI yang diminati. Transformasikan melalui 5 tahap Problem Formation Model.

**Topik awal:** Pemanfaatan Artificial Intelligence pada aplikasi pembelajaran bahasa

| Tahap | Hasil |
|-------|-------|
| Reality | Banyak pengguna menggunakan aplikasi pembelajaran bahasa seperti Duolingo. |
| Observed Issue (Symptom) | Tingkat penggunaan tidak konsisten dan kepuasan pengguna berbeda-beda. |
| Diagnosed Problem (Root Cause) |Pengaruh fitur AI terhadap kepuasan pengguna belum diketahui secara pasti.|
| Researchable Problem | Belum ada penelitian terstruktur yang mengukur pengaruh AI terhadap kepuasan pengguna menggunakan model TAM.|
| Measurable Variable | PEOU, PU, AT, BI, AU. |

**Apakah terjebak solution-first thinking?** [ ] Tidak

---

## Latihan 2 — System Context Decomposition

Konteks sistem dari masalah riset di Latihan 1.

| Komponen | Deskripsi |
|----------|----------|
| Input | Data aktivitas pengguna, jawaban latihan. |
| Process | AI mengolah data untuk personalisasi pembelajaran.|
| Output | Materi yang disesuaikan, skor, feedback.|
| Outcome |Kepuasan pengguna dan efektivitas belajar.|
| Constraints | Jumlah responden terbatas, metode kuantitatif.|
| Stakeholders | Pengguna, pengembang, peneliti.|

**Komponen mana yang paling relevan dengan masalah riset?**  Process dan Outcome.

Komponen process menjadi paling relevan karena dalam penelitian ini yang dianalisis adalah bagaimana teknologi Artificial Intelligence (AI) bekerja dalam aplikasi Duolingo, seperti dalam menyesuaikan materi, memberikan umpan balik otomatis, dan mempersonalisasi pengalaman belajar pengguna. Proses inilah yang secara langsung memengaruhi persepsi pengguna terhadap kemudahan penggunaan (perceived ease of use) dan kegunaan (perceived usefulness).

Sementara itu, komponen outcome juga sangat penting karena berkaitan langsung dengan hasil akhir yang ingin diketahui dalam penelitian, yaitu tingkat kepuasan pengguna. Outcome mencerminkan dampak dari proses yang terjadi, sehingga dapat digunakan untuk menilai apakah penerapan AI benar-benar memberikan manfaat dan meningkatkan pengalaman belajar pengguna.

Dengan demikian, hubungan antara process dan outcome menjadi inti dari penelitian ini, karena proses AI dalam sistem akan menentukan hasil berupa kepuasan pengguna.

---

## Latihan 3 — Problem Quality Check

Evaluasi problem statement yang sudah dibuat menggunakan 5 kriteria.

| Kriteria | Skor (1-5) | Justifikasi |
|----------|-----------|-------------|
| Clarity | 4 | Sudah jelas namun bisa dipersempit lagi|
| Measurability | 5 | Menggunakan variabel yang bisa diukur |
| Relevance | 5 | Sangat relevan dengan perkembangan AI |
| Testability | 5 | Bisa diuji dengan data |
| Impact | 4 | Memberikan kontribusi pada pengembangan aplikasi |

**Skor total:** 23 / 25

**Problem statement versi final (1 paragraf):**
> Penggunaan teknologi Artificial Intelligence (AI) dalam aplikasi pembelajaran bahasa seperti Duolingo semakin berkembang dan memberikan pengalaman belajar yang lebih adaptif dan personal. Namun, masih belum jelas sejauh mana teknologi AI tersebut mempengaruhi tingkat kepuasan pengguna. Oleh karena itu, diperlukan analisis yang terstruktur untuk mengukur pengaruh AI terhadap kepuasan pengguna dengan menggunakan model Technology Acceptance Model (TAM), melalui variabel perceived ease of use, perceived usefulness, attitude toward use, behavioral intention, dan actual usage, sehingga dapat memberikan pemahaman yang lebih jelas mengenai penerimaan teknologi AI dalam aplikasi pembelajaran.

---

## Refleksi

> Bandingkan "masalah" yang biasa ditemui saat coding (bug, error) dengan masalah riset. Apa perbedaan fundamental dalam cara mendefinisikan dan mendekati keduanya?

**Jawaban:**
> Masalah dalam coding biasanya berupa error atau bug yang harus segera diperbaiki agar sistem dapat berjalan dengan baik, sehingga fokusnya adalah pada penyelesaian masalah secara langsung.
> Sedangkan masalah riset lebih berfokus pada memahami penyebab suatu fenomena dan membuktikannya secara ilmiah. Masalah riset harus dapat diukur, diuji, dan memiliki kontribusi terhadap pengetahuan, bukan hanya menyelesaikan masalah teknis.
