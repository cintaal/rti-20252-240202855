# WS-05: Variabel & Metrik

> **Bab 5 — Metric, Measurement & Data**

---

## Ringkasan Materi

### Measurement Alignment Model

Setiap pengukuran yang valid harus bisa ditelusuri melalui rantai ini tanpa lompatan logis:

```
Problem → Concept → Variable → Metric → Data → Result
```

### Operationalization = Keputusan Desain

Menerjemahkan konsep abstrak menjadi variabel terukur bukan proses mekanis. "Code quality" yang diukur via SonarQube code smells membawa asumsi implisit. Setiap operasionalisasi harus didokumentasikan dan dijustifikasi.

### Empat Tipe Data (NOIR)

| Tipe | Ciri | Contoh | Operasi Valid |
|------|------|--------|---------------|
| **Nominal** | Kategori, tanpa urutan | Jenis algoritma (RF, SVM, CNN) | Modus, chi-square |
| **Ordinal** | Urutan, interval tidak sama | Skala Likert (1-5) | Median, Spearman |
| **Interval** | Jarak bermakna, tanpa nol absolut | Suhu Celsius | Mean, Pearson, t-test |
| **Ratio** | Jarak bermakna + nol absolut | Waktu eksekusi (ms) | Semua operasi |

Tipe data menentukan uji statistik yang valid. Kebanyakan metrik performa TI = ratio; persepsi pengguna = ordinal.

### Kriteria Pemilihan Metrik

- **Representative** — Mewakili konsep yang diteliti
- **Sensitive** — Cukup peka menangkap perbedaan bermakna (hindari ceiling effect)
- **Feasible** — Bisa dikumpulkan dalam batasan waktu dan biaya

### Pre-registration

Metrik harus ditentukan **sebelum** eksperimen. Memilih metrik setelah melihat data = **p-hacking**. Metrik tambahan yang ditemukan kemudian dilaporkan sebagai *exploratory*, bukan *confirmatory*.

### Primary vs Secondary Metric

- **Primary Metric** — Langsung terikat ke hipotesis, menentukan kesimpulan
- **Secondary Metric** — Pendukung, dilaporkan di samping primary; statusnya suplementer

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Pemilihan metrik | Berdasarkan kebiasaan/tool yang ada | Berdasarkan construct validity |
| Anomali | Dihapus untuk laporan bersih | Diinvestigasi — bisa jadi temuan |
| Kapan dipilih | Setelah sistem jadi (monitoring) | Sebelum eksperimen (by design) |

### Istilah Penting

- **Operationalization** — Transformasi konsep abstrak menjadi variabel terukur
- **Construct Validity** — Sejauh mana pengukuran benar-benar mengukur konsep yang dimaksud
- **Measurement Scale** — Klasifikasi data (NOIR) yang menentukan analisis valid
- **Multi-metric Evaluation** — Menggunakan beberapa metrik untuk menangkap konsep kompleks

---

## Template A.5 — Definisi Variabel, Metrik & Justifikasi

```
VARIABLE & METRIC DEFINITION

Research Question: Apakah Perceived Ease of Use (PEOU) dan Perceived Usefulness (PU) dari teknologi AI pada aplikasi Duolingo berpengaruh signifikan terhadap kepuasan pengguna?

| Variabel | Tipe | Konsep | Metrik | Skala | Satuan | Cara Mengukur | Justifikasi |
|----------|------|--------|--------|-------|--------|---------------|-------------|
| PEOU (Perceived Ease of Use) | IV | Persepsi kemudahan penggunaan | Skor kuesioner Likert (1-5) | Ordinal | Skor | Responden mengisi kuesioner terkait kemudahan penggunaan aplikasi | Mewakili persepsi kemudahan pengguna secara langsung |
| PU (Perceived Usefulness) | IV | Persepsi kegunaan/manfaat | Skor kuesioner Likert (1-5) | Ordinal | Skor | Responden mengisi kuesioner terkait manfaat aplikasi | Mengukur sejauh mana aplikasi dianggap bermanfaat |
| Kepuasan Pengguna | DV | Tingkat kepuasan pengguna | Skor kuesioner Likert (1-5) | Ordinal | Skor | Responden menilai kepuasan setelah menggunakan aplikasi | Langsung merepresentasikan outcome penelitian |
| Pengalaman penggunaan aplikasi | CV | Pengalaman sebelumnya menggunakan aplikasi | Lama penggunaan (bulan) | Ratio | Bulan | Responden mengisi durasi penggunaan aplikasi | Mengontrol pengaruh pengalaman terhadap kepuasan |

Alignment Check:
  RQ → Concept → Variable → Metric → Data → Result
  [✓] Setiap langkah terdokumentasi
  [✓] Tidak ada "lompatan logis"
  [✓] Metrik mengukur apa yang dimaksud (construct validity)
```

---

## Latihan 1 — Operationalization Chain

Gunakan RQ dari WS-04. Definisikan variabel dan metriknya.

**RQ:** Apakah PEOU dan PU berpengaruh terhadap kepuasan pengguna aplikasi Duolingo?

| Variabel | Tipe | Konsep Abstrak | Metrik Konkret | Skala (NOIR) | Satuan |
|----------|------|---------------|----------------|-------------|--------|
| PEOU              | IV   | Kemudahan penggunaan | Skor Likert 1-5 | Ordinal      | Skor   |
| PU                | IV   | Kegunaan aplikasi    | Skor Likert 1-5 | Ordinal      | Skor   |
| Kepuasan Pengguna | DV   | Kepuasan pengguna    | Skor Likert 1-5 | Ordinal      | Skor   |
| Lama penggunaan   | CV   | Pengalaman pengguna  | Lama penggunaan | Ratio        | Bulan  |

**Apakah ada lompatan logis dalam rantai?**  Tidak

> Karena semua konsep abstrak telah diterjemahkan menjadi variabel dan metrik yang dapat diukur secara langsung melalui kuesioner dan data penggunaan.

---

## Latihan 2 — Evaluasi Metrik

Evaluasi metrik DV yang dipilih di Latihan 1 menggunakan 3 kriteria.

| Kriteria | Skor (1-5) | Justifikasi |
|----------|-----------|-------------|
| Representative | 5          | Skala Likert secara langsung mengukur persepsi kepuasan pengguna                |
| Sensitive      | 4          | Skala 1-5 cukup mampu membedakan tingkat kepuasan, meskipun tidak sangat detail |
| Feasible       | 5          | Mudah dikumpulkan melalui kuesioner tanpa biaya besar                           |

**Apakah perlu secondary metric?** Ya 

> Jika ya, apa dan mengapa? Secondary metric: jumlah penggunaan aplikasi (frekuensi penggunaan) Alasan: untuk mendukung data kepuasan dengan perilaku nyata pengguna

**Contoh kasus ceiling effect untuk metrik ini:**
> Jika sebagian besar responden memberikan nilai 5 (sangat puas), maka metrik tidak mampu membedakan variasi kepuasan secara detail.

---

## Latihan 3 — Data Quality Check

Bayangkan data yang akan dikumpulkan dari eksperimen. Evaluasi 4 dimensi kualitas data.

| Dimensi | Pertanyaan | Jawaban | Strategi Mitigasi |
|---------|-----------|---------|------------------|
| Completeness | Apakah semua data point terkumpul?| Tidak selalu | Memastikan semua responden mengisi seluruh pertanyaan |
| Consistency | Apakah ada kontradiksi internal? | Mungkin ada | Validasi jawaban dan cek inkonsistensi      |
| Validity | Apakah benar-benar mengukur yang dimaksud? | Ya | Menggunakan indikator TAM yang sudah terbukti |
| Representativeness | Apakah sampel mewakili populasi target? | Belum sepenuhnya | Menambah jumlah responden dan variasi pengguna|

---

## Refleksi

> Mengapa memilih metrik setelah melihat data dianggap p-hacking? Apa bedanya dengan eksplorasi data yang sah?

**Jawaban:**

> Memilih metrik setelah melihat data dianggap sebagai p-hacking karena peneliti dapat secara tidak sengaja memilih metrik yang menghasilkan hasil yang signifikan, sehingga bias dan tidak objektif. Hal ini berbeda dengan eksplorasi data yang sah, di mana peneliti tetap melaporkan hasil secara transparan tanpa mengklaim sebagai hasil utama penelitian.
