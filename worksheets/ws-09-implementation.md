# WS-09: Implementation & Environment

> **Bab 9 — Implementasi Riset & Kontrol Lingkungan**

---

## Ringkasan Materi

### Implementasi Riset ≠ Coding Biasa

Tujuan implementasi riset bukan membuat software yang berfungsi, melainkan membangun **instrumen pengukuran yang konsisten**. Setiap modul harus di-mapping ke variabel (dari Bab 6), parameter harus config-driven, dan logging aktif dari hari pertama.

> **Mengapa reproducibility penting?** Sains dibangun di atas prinsip verifikasi — temuan harus bisa dikonfirmasi oleh peneliti lain. _Replicability crisis_ yang terjadi di banyak paper riset ML/AI disebabkan oleh environment tidak terdokumentasi: orang lain tidak bisa reproduksi, hasil diragukan, kepercayaan terhadap temuan hilang. Prinsip: **dokumentasi environment = snapshot kredibilitas riset Anda.**

### Reproducible Implementation Model

```
Design → Implementation → Environment Setup → Execution Consistency → Reproducibility → Trustworthy Result
```

Setiap transisi memiliki syarat:
- Design → Implementation: kode sesuai mapping variabel-ke-komponen
- Implementation → Environment: versi, dependency, seed, path, OS eksplisit
- Environment → Consistency: seed terkunci, urutan deterministik
- Consistency → Reproducibility: dokumentasi lengkap
- Reproducibility → Trust: siapa pun ikuti dokumentasi → hasil sama/serupa

### Repeatability vs Reproducibility

| Level | Peneliti | Environment | Hasil |
|-------|---------|-------------|-------|
| **Repeatability** | Sama | Sama | Sama persis |
| **Reproducibility** | Berbeda | Berbeda (ikuti docs) | Sama/serupa |

Capai **repeatability** dulu, baru **reproducibility**.

### Engineering vs Research Perspective

| Aspek | Engineering | Research |
|-------|-----------|---------|
| Tujuan | Sistem berfungsi untuk user | Instrumen pengukuran konsisten |
| Dependency | Update ke terbaru | Lock di versi spesifik |
| Testing | Unit, integration, E2E | Repeatability test (run ulang → sama?) |
| Dokumentasi | User guide, API docs | Environment spec, execution steps, expected output |
| Config | Default masuk akal | Setiap parameter eksplisit & adjustable |

### Jebakan Kognitif

1. Menunda environment setup → bug sulit dilacak
2. Tidak pakai version control → hasil tidak bisa direkonstruksi
3. Menolak Docker/container → "di laptop saya bisa" saat review
   - **Docker** = teknologi container yang "membungkus" aplikasi beserta seluruh dependency-nya dalam satu unit terisolasi. Hasilnya: kode berjalan identik di laptop, server, maupun reviewer lain. Intro singkat: `docker run -v $(pwd):/workspace environment-image python run_experiment.py`
4. 3× hasil sama ≠ repeatable (bisa cache/state tersimpan)

### Dependency Locking

Mengandalkan "install library terbaru" berbahaya: versi berbeda = perilaku berbeda = hasil tidak reproducible. Praktik:
- **Python**: buat `requirements.txt` dengan versi eksplisit: `scikit-learn==1.3.2`, lalu kunci dengan `pip freeze > requirements.txt`
- **Conda**: gunakan `conda env export > environment.yml` untuk snapshot lengkap
- **Node.js/R/Julia**: gunakan `package-lock.json` / `renv.lock` / `Project.toml` — semua fungsi serupa: lock versi + hash

### Istilah Penting

- **Environment Specification** — Deskripsi lengkap: hardware, OS, runtime, library + versi, config, seed
- **Dependency** — Komponen eksternal yang harus di-lock versinya
- **Config-driven** — Parameter dieksternalisasi ke file konfigurasi, bukan hardcode

---

## Template A.9 — Dokumentasi Setup Eksperimen

```
EXPERIMENT SETUP DOCUMENTATION

Hardware:
  CPU     : AMD Ryzen 7 5700U with Radeon Graphics
  RAM     : 16 GB
  GPU     : AMD Radeon™ Graphics (Integrated)
  Storage : SSD 477 GB

Software:
  OS        : Windows 11 Home 64-bit
  Runtime   : Google Chrome dan Microsoft Excel
  Framework : Google Forms sebagai media pengumpulan data

Dependencies:
| Library | Version | Sumber | Hash/Checksum |
|---------|---------|--------|---------------|
| IBM SPSS Statistic  | 27  | IBM  |    -          |
| microsoft  excel   | versi teraru  | microsoft  |  -    |
| google chrome | ver. terbaru  | google   | -  |

Konfigurasi:
  Config file     : Instrumen penelitian 
  Random seed     : 42
  Hyperparameters : Penelitian ini tidak menggunakan algoritma machine learning sehingga tidak memerlukan hyperparameter khusus. Parameter yang dijaga tetap adalah instrumen kuesioner, skala Likert 1–5, dan jumlah item pertanyaan.

Reproducibility Check:
  [x] Dependency terdokumentasi 
  [x] Seed ditetapkan di semua level 
  [x] Config di version control
  [✓] README reproduksi belum dibuat karena penelitian masih berada pada tahap proposal.
```

---

## Latihan 1 — Environment Specification

Dokumentasikan environment untuk eksperimen Anda (boleh environment saat ini atau yang direncanakan).

| Komponen | Spesifikasi |
|----------|------------|
| CPU | AMD Ryzen 7 5700U with Radeon Graphics (8 Core, 16 Threads, 1.80 GHz) |
| RAM | 16 GB |
| GPU | AMD Radeon™ Graphics (Integrated) |
| OS | Windows 11 Home 64-bit |
| Aplikasi | Google Forms, Google Chrome, Microsoft Excel, Microsoft Word |
| Instrumen | Kuesioner TAM |
| Random Seed | tidak digunakan |

**Dependencies (minimal 5):**

| Library | Alasan Dibutuhkan |
|---------|-------------------|
| Google Forms    | Menyebarkan dan mengumpulkan data kuesioner |
| Google Chrome   | Mengakses Google Forms                      |
| Microsoft Excel | Mengolah dan merekap data hasil kuesioner   |
| Microsoft Word  | Menyusun proposal penelitian                |

---

## Latihan 2 — Repeatability Test Plan

Rancang tes repeatability sederhana: jalankan kode yang sama 3× di environment yang sama.

| Run | Instrumen | Metrik Utama | Hasil Sama? |
| --- | --------- | ------------ | ----------- |
| 1   | Kuesioner TAM           | Skor PEOU, PU, dan Kepuasan Pengguna | —           |
| 2   | Kuesioner TAM yang sama | Skor PEOU, PU, dan Kepuasan Pengguna | ☑ Ya        |
| 3   | Kuesioner TAM yang sama | Skor PEOU, PU, dan Kepuasan Pengguna | ☑ Ya        |


**Jika hasil berbeda, kemungkinan penyebab:**
Perbedaan hasil dapat terjadi apabila karakteristik responden berbeda, jumlah responden tidak sama, atau terdapat jawaban yang tidak konsisten saat pengisian kuesioner.

> Penyebab umum non-repeatability:
> - **Thermal throttling** — CPU/GPU overheating pada run berturut-turut → clock speed turun → waktu eksekusi berubah
> - **Background process** — antivirus scan, update OS, atau cloud sync aktif saat run berlangsung
> - **Cache dari run sebelumnya** — hasil tersimpan di memori/disk sehingga run berikutnya tidak menjalankan komputasi penuh
> - **Random state tidak dikontrol di semua level** — Python seed di-set, tapi NumPy/PyTorch/TensorFlow punya seed independen

___________________________________________________

**Checklist kontrol yang sudah diterapkan:**
- [✓] Menggunakan instrumen kuesioner yang sama.
- [✓] Menggunakan indikator variabel yang sama.
- [✓] Menggunakan skala Likert 1–5 yang sama.
- [✓] Menggunakan prosedur penyebaran kuesioner yang sama.

---

## Latihan 3 — README Eksperimen

Tulis README minimum untuk eksperimen Anda (6 komponen wajib).

```
# Judul Eksperimen: Analisis Pengaruh Artificial Intelligence pada Aplikasi Duolingo terhadap Kepuasan Pengguna Menggunakan Technology Acceptance Model (TAM)

## 1. Environment
> Perangkat yang digunakan:
- Laptop Acer Aspire A314-42P
- AMD Ryzen 7 5700U
- RAM 16 GB
- Windows 11 Home 64-bit

Aplikasi:
- Google Forms
- Google Chrome
- Microsoft Excel
- Microsoft Word

## 2. Installation
> pip install -r requirements.txt

## 3. Data
> Data berupa jawaban responden terhadap indikator:
- Perceived Ease of Use (PEOU)
- Perceived Usefulness (PU)
- Kepuasan Pengguna

Skala pengukuran menggunakan Likert 1–5.

## 4. Execution
> 1. Menyusun instrumen penelitian.
2. Menyebarkan kuesioner kepada responden.
3. Mengumpulkan hasil kuesioner.
4. Merekap data menggunakan Microsoft Excel.
5. Menganalisis hasil sesuai metode penelitian.


## 5. Configuration
> Instrumen:
- Kuesioner TAM

Objek:
- Pengguna aplikasi Duolingo

Variabel:
- IV : Perceived Ease of Use (PEOU)
- IV : Perceived Usefulness (PU)
- DV : Kepuasan Pengguna

## 6. Expected Output
> Output penelitian berupa:
- Rekapitulasi data responden.
- Nilai setiap variabel penelitian.
- Hasil analisis hubungan PEOU dan PU terhadap kepuasan pengguna.
- Kesimpulan penelitian berdasarkan hasil analisis.
```

---

## Refleksi

> Apakah eksperimen Anda saat ini bisa direproduksi oleh orang lain tanpa bantuan Anda? Komponen apa yang masih hilang?

**Level saat ini:**
 ☑ Belum keduanya
 > Penelitian masih berada pada tahap proposal sehingga proses pengumpulan data dan analisis belum dilakukan. Meskipun instrumen penelitian, variabel, dan prosedur penelitian telah dirancang, eksperimen belum dapat direplikasi sepenuhnya karena data penelitian belum tersedia.
**Komponen yang belum terdokumentasi:**
>Dataset hasil penyebaran kuesioner, hasil analisis data, dokumentasi pelaksanaan penelitian, serta laporan hasil eksperimen. Seluruh komponen tersebut akan dilengkapi setelah penelitian memasuki tahap implementasi.
