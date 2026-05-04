# WS-03: Literature Mapping & Gap

> **Bab 3 — Literature Review, Research Gap & Baseline**

---

## Ringkasan Materi

### Literature Review = Positioning, Bukan Ringkasan

Literature review bukan merangkum paper satu per satu. Pendekatan yang benar adalah **concept-centric** — organisasi berdasarkan tema, metode, atau variabel. Tujuan: menemukan **pola, kontradiksi, dan gap**.

**Perbandingan pendekatan Author-centric vs Concept-centric:**

| Aspek | Author-centric (Hindari) | Concept-centric (Gunakan) |
|-------|--------------------------|---------------------------|
| Struktur | Per penulis/paper ("Rahman et al. menyatakan...") | Per konsep/metode ("Pendekatan berbasis transformer") |
| Tujuan | Ringkasan isi paper | Perbandingan metode & identifikasi gap |
| Contoh paragraph | "Rahman (2023) pakai CNN. Lee (2022) pakai LSTM. Zhang (2021) pakai RF." | "Tiga pendekatan dominan: CNN digunakan oleh 4 paper untuk representasi fitur visual; LSTM untuk data sekuensial; RF sebagai baseline klasik." |
| Hasil akhir | Daftar paper | Peta pengetahuan + gap yang teridentifikasi |

### Empat Jenis Research Gap

| Jenis Gap | Deskripsi | Contoh |
|-----------|----------|--------|
| **Performance Gap** | Performa belum memadai | Akurasi deteksi hanya 78% pada kasus tertentu |
| **Method Gap** | Pendekatan belum diterapkan | Belum ada yang pakai transformer untuk task ini |
| **Data Gap** | Dataset terbatas/tidak representatif | Semua studi pakai dataset sintetis |
| **Context Gap** | Belum diuji pada konteks berbeda | Belum ada evaluasi di negara berkembang |

Gap terkuat = kombinasi 2+ jenis.

### Systematic Search Strategy

1. **Database utama**: IEEE Xplore, ACM DL, Scopus
   - Akses IEEE/ACM melalui jaringan kampus atau VPN institusi
   - Alternatif bebas biaya: Google Scholar, ResearchGate ([researchgate.net](https://www.researchgate.net)), arXiv ([arxiv.org](https://arxiv.org))
2. **Boolean query** yang terdokumentasi eksplisit
   - Contoh: `("anomaly detection" OR "intrusion detection") AND ("deep learning" OR "neural network") NOT ("medical imaging")`
   - Gunakan tanda kutip untuk frasa eksak; AND/OR/NOT mengontrol scope
3. **Snowballing** — dua arah:
   - **Backward snowballing**: buka daftar referensi di paper kunci → telusuri paper yang dikutip
   - **Forward snowballing**: di Google Scholar, klik "Cited by" di bawah paper kunci → temukan paper yang mengutipnya
   - Ulangi 1–2 tingkat untuk membangun cakupan komprehensif
4. Klaim "belum ada penelitian" harus didukung **bukti pencarian**

### Baseline Selection — 3 Kriteria

| Kriteria | Pertanyaan |
|----------|-----------|
| **Relevan** | Apakah menyelesaikan masalah yang sama? |
| **Representatif** | Apakah mewakili common practice? |
| **State-of-the-Art** | Apakah terbaru/terbaik? |

Membandingkan deep learning 2024 dengan decision tree sederhana tanpa justifikasi = **straw man comparison** (perbandingan tidak jujur).

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan baca literatur | Mencari solusi yang sudah ada | Memahami apa yang belum terjawab |
| Cara membaca paper | Tutorial, how-to | Metode, limitasi, gap |
| Baseline | Framework terpopuler | State-of-the-art yang rigorous |
| Dokumentasi pencarian | Tidak diperlukan | Wajib (reproducible) |

### Istilah Penting

- **Concept-centric** — Organisasi literatur berdasarkan konsep/metode, bukan per penulis
- **Snowballing** — Backward (telusuri referensi) + Forward (cari yang mengutip paper kunci)
- **Research Position** — Pernyataan eksplisit posisi riset terhadap studi sebelumnya
- **Straw man comparison** — Memilih baseline lemah agar metode sendiri terlihat lebih baik

---

## Template A.3 — Literature Mapping & Gap Identification

```
LITERATURE MAPPING

Topik      : Pengaruh Artificial Intelligence pada aplikasi pembelajaran bahasa terhadap kepuasan pengguna
Database   : Google Scholar
Query      : ("Artificial Intelligence" OR "AI") AND ("pembelajaran" OR "learning app") AND ("TAM" OR "kepuasan pengguna")
Tahun      : 2020–2026
Hasil awal : 30 paper → Screening → 5 paper final

Literature Matrix (concept-centric):

| Study | Tahun | Method | Data | Result | Limitation |
|Makaruku & Manuhutu|2026|TAM|Survey pengguna e-learning|PEOU & PU berpengaruh signifikan terhadap kepuasan|Tidak spesifik AI|
|Agustina et al.|2024|TAM + TTF + ECM|Mahasiswa (85 responden)| AI meningkatkan kepuasan penggunaan| Fokus pada pemrograman, bukan bahasa|
| Mulyanto et al. | 2024 | E-SERVQUAL | 360 responden | 5 variabel berpengaruh ke kepuasan | Tidak pakai TAM |
| Tamtomo | 2024 | TAM | Mahasiswa pembelajar bahasa | AI (ChatGPT) dianggap bermanfaat | Tidak mengukur kepuasan secara spesifik |
| Saninah et al. | 2024 | Naïve Bayes (Sentiment) | 2000 ulasan Duolingo | Mayoritas sentimen positif | Tidak pakai model TAM |

Pola yang ditemukan:
  Metode dominan     : Technology Acceptance Model (TAM) dan analisis sentimen
  Dataset umum       : Kuesioner pengguna dan data ulasan aplikasi
  Limitasi berulang  : Tidak menggabungkan AI + kepuasan pengguna + konteks spesifik aplikasi pembelajaran bahasa

GAP IDENTIFICATION

Gap 1: [Jenis: method gap]
  Deskripsi    : Belum banyak penelitian yang menggabungkan teknologi Artificial Intelligence dengan model TAM untuk mengukur kepuasan pengguna
  Bukti        : Sebagian penelitian hanya menggunakan TAM tanpa fokus pada AI, sementara penelitian lain membahas AI tanpa menggunakan model TAM
  Signifikansi : Menggabungkan AI dan TAM dapat memberikan analisis yang lebih komprehensif terhadap kepuasan pengguna
Gap 2: [Jenis: ____]
  Deskripsi    : Penelitian belum secara spesifik dilakukan pada aplikasi pembelajaran bahasa seperti Duolingo
  Bukti        : Studi yang ada lebih banyak dilakukan pada sistem umum, e-learning, atau aplikasi lain
  Signifikansi : Konteks aplikasi pembelajaran bahasa memiliki karakteristik unik sehingga perlu diteliti secara khusus

Baseline Selection:
| Baseline | Relevansi | Representatif | Source |
| TAM (Makaruku, 2026) | Mengukur kepuasan pengguna | Banyak digunakan dalam penelitian TI | Jurnal Indonesia 2026 |
| Sentiment Analysis (Saninah, 2024) | Mengukur respon pengguna aplikasi | Umum digunakan dalam analisis aplikasi | Jurnal Indonesia 2024 |
```

---

## Latihan 1 — Concept-Centric Literature Table

Gunakan topik riset dari WS-02. Cari minimal 5 paper relevan menggunakan database akademik.

> **Panduan pencarian:**
> - Database: IEEE Xplore, ACM DL, Google Scholar, atau ResearchGate
> - Tulis query Boolean yang digunakan: contoh `("object detection" OR "image classification") AND ("edge computing") NOT ("medical")`. Dokumentasikan query secara eksplisit.
> - Akses gratis: buka Google Scholar → cari judul paper → klik [PDF] jika tersedia, atau akses lewat campus VPN

**Topik riset:** Pengaruh AI pada aplikasi pembelajaran bahasa terhadap kepuasan pengguna
**Query pencarian:** ("AI" OR "Artificial Intelligence") AND ("pembelajaran") AND ("TAM" OR "kepuasan pengguna")
**Database:** Google Scholar

| # | Study | Tahun | Method | Dataset | Result | Limitasi |
|---|-------|-------|--------|---------|--------|----------|
| 1 | Makaruku & Manuhutu | 2026  | TAM                | Survey        | PEOU & PU signifikan         | Tidak bahas AI       |
| 2 | Agustina et al.     | 2024  | TAM+TTF+ECM        | Mahasiswa     | AI bantu pembelajaran        | Bukan bahasa         |
| 3 | Mulyanto et al.     | 2024  | E-SERVQUAL         | 360 responden | Kepuasan dipengaruhi layanan | Tidak pakai TAM      |
| 4 | Tamtomo             | 2024  | TAM                | Mahasiswa     | AI bermanfaat                | Tidak fokus kepuasan |
| 5 | Saninah et al.      | 2024  | Sentiment Analysis | 2000 review   | Sentimen positif dominan     | Tidak pakai TAM|

**Pola yang terlihat — Metode dominan:** TAM dan analisis sentimen
**Limitasi yang berulang:** Penelitian belum menggabungkan AI + TAM + kepuasan pengguna dalam satu studi

---

## Latihan 2 — Gap Identification

Berdasarkan tabel di Latihan 1, identifikasi gap.

| Jenis Gap | Ditemukan? | Gap Statement |
|-----------|-----------|---------------|
| Performance Gap | Tidak | - |
| Method Gap | Ya | Belum ada penelitian yang menggabungkan AI dan TAM untuk mengukur kepuasan pengguna |
| Data Gap | Ya | Banyak penelitian hanya menggunakan survey tanpa data perilaku nyata |
| Context Gap | Ya | Belum fokus pada aplikasi pembelajaran bahasa seperti Duolingo |

**Gap utama yang dipilih:** Method Gap + Context Gap
**Mengapa gap ini penting (bukan sekadar "belum ada yang meneliti")?**
> Karena penelitian sebelumnya hanya membahas sebagian aspek (AI saja atau TAM saja), sehingga belum memberikan gambaran lengkap tentang bagaimana AI mempengaruhi kepuasan pengguna dalam konteks aplikasi pembelajaran bahasa secara spesifik.

---

## Latihan 3 — Baseline Selection

Pilih 2 baseline dari literatur yang sudah dibaca.

| # | Baseline | Mengapa Relevan | Mengapa Representatif | Apakah SOTA? | Sumber |
|---|----------|----------------|----------------------|-------------|--------|
| 1 | TAM (Makaruku, 2026)               | Sama-sama ukur kepuasan            | Banyak dipakai di penelitian TI | Tidak, tapi umum | 2026   |
| 2 | Sentiment Analysis (Saninah, 2024) | Sama-sama analisis user experience | Banyak dipakai untuk aplikasi   | Tidak            | 2024   |

**Apakah pemilihan baseline ini bisa dianggap straw man?** Tidak
> Justifikasi: Baseline berasal dari metode yang umum digunakan dalam penelitian kepuasan pengguna dan analisis aplikasi, sehingga perbandingan tetap adil.

---

## Refleksi

> Apa perbedaan antara "belum ada yang meneliti ini" (klaim tanpa bukti) dengan research gap yang valid? Bagaimana cara membuktikan bahwa sebuah gap benar-benar ada?

**Jawaban:**
> Pernyataan “belum ada yang meneliti” tidak cukup tanpa bukti. Research gap yang valid harus didukung oleh hasil penelusuran literatur yang menunjukkan adanya kekurangan atau keterbatasan penelitian sebelumnya. Cara membuktikannya adalah dengan melakukan pencarian sistematis, membandingkan beberapa jurnal, dan menunjukkan pola serta kekurangan yang konsisten dari penelitian yang ada.