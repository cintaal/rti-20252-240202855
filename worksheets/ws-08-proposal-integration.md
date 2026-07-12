# WS-08: Proposal Integration (UTS)

> **Bab 8 — Proposal & Checkpoint**

---

## Ringkasan Materi

### Proposal = Satu Argumen Utuh

Proposal riset bukan kumpulan bab yang independen. Ia adalah **satu argumen** yang mengalir dari masalah ke rencana solusi. Jika satu koneksi putus, seluruh proposal kehilangan koherensi.

### Integration Map — 6 Koneksi Kritis

```
Problem (Bab 2) → Gap (Bab 3) → RQ & H (Bab 4) → Metrik (Bab 5) → Sistem (Bab 6) → Eksperimen (Bab 7)
```

| Koneksi | Pertanyaan Verifikasi |
|---------|----------------------|
| Problem → Gap | Apakah gap muncul dari analisis literatur terhadap masalah? |
| Gap → RQ | Apakah RQ langsung menjawab gap yang teridentifikasi? |
| RQ → Metrik | Apakah setiap variabel di RQ punya metrik terdefinisi? |
| Metrik → Sistem | Apakah setiap metrik bisa diukur oleh komponen sistem? |
| Sistem → Eksperimen | Apakah desain eksperimen menggunakan sistem sebagai instrumen? |

### Koherensi Vertikal + Horizontal

- **Vertikal** — Alur logis atas-ke-bawah (problem → experiment). Setiap section menjawab pertanyaan yang diangkat section sebelumnya dan memunculkan pertanyaan baru.
- **Horizontal** — Konsistensi terminologi (nama variabel di RQ = di hipotesis = di metrik = di desain)

**Operasionalisasi Red Thread** (benang merah):
```
Bab 2 (Problem) → | memperkenalkan masalah X + evidensi |
                          ↓ menimbulkan pertanyaan: "apa akar gap-nya?"
Bab 3 (Gap)     → | menjawab pertanyaan tadi + membuka "lalu apa yang perlu diteliti?" |
                          ↓
Bab 4 (RQ/H)    → | menjawab gap dengan pertanyaan spesifik + prediksi terukur |
                          ↓
Bab 5-7 (Method)→ | menjawab RQ melalui desain eksperimen yang tepat |
```
Jika ada lompatan (section B tidak menjawab pertanyaan section A), red thread putus.

### Jebakan Kognitif

| Jebakan | Deskripsi |
|---------|----------|
| "Selling" Introduction | Menulis promosi, bukan menyajikan data dan gap |
| Copy-paste Methodology | Menyalin deskripsi tekstbook tanpa menyesuaikan ke RQ |
| Optimistic Timeline | Meremehkan waktu implementasi; selalu tambah buffer 30-50% |
| No Possibility of Failure | Mengimplikasikan hasil pasti sukses — proposal jujur mengakui H₀ mungkin tidak ditolak |

### Struktur Proposal

1. **Pendahuluan** — Latar belakang + problem statement (Bab 1-2)
2. **Tinjauan Pustaka** — Literature review + gap + baseline (Bab 3)
3. **RQ / Kontribusi / Hipotesis** — (Bab 4)
4. **Metodologi** — Metrik + sistem + desain eksperimen (Bab 5-7)
5. **Timeline & Output**

### Istilah Penting

- **Integration Map** — Diagram 6 koneksi kritis antar komponen proposal
- **Vertical Coherence** — Alur logis atas-ke-bawah
- **Horizontal Coherence** — Konsistensi terminologi di semua bagian
- **Checkpoint** — Titik self-assessment sebelum transisi dari desain ke eksekusi

---

## Template A.8 — Integration Checklist

```
PROPOSAL INTEGRATION CHECKLIST

Koneksi Vertikal (Flow Atas-Bawah):
  [✓] Problem → Gap: masalah terdokumentasi di literatur
  [✓] Gap → RQ: pertanyaan menjawab gap spesifik
  [✓] RQ → Hypothesis: hipotesis memprediksi jawaban
  [✓] Hypothesis → Metric: metrik mengukur variabel dalam hipotesis
  [✓] Metric → System: komponen sistem menghasilkan/mengukur metrik
  [✓] System → Experiment: desain eksperimen menggunakan sistem

Koneksi Horizontal (Konsistensi):
  [✓] Istilah sama di semua bagian
  [✓] Variabel di RQ = variabel di hipotesis = metrik di desain
  [✓] Scope tidak berubah dari masalah ke eksperimen

Cognitive Trap Checklist:
  [✓] Tidak ada paragraf "promosi" di pendahuluan (hanya data & gap)
  [✓] Metodologi disesuaikan ke RQ, bukan copy-paste textbook
  [✓] Timeline sudah ditambah buffer 30-50% dari estimasi awal
  [✓] Proposal mengakui kemungkinan H0 tidak ditolak (honest uncertainty)
  [✓] Tidak ada klaim "pasti berhasil" atau "meningkatkan signifikan"

Rubrik Self-Assessment:
| Kriteria     | 1 (Lemah)                                        | 2 (Cukup)                                     | 3 (Baik)                                           | Skor |
|------------- |--------------------------------------------------|-----------------------------------------------|----------------------------------------------------|------|
| Koherensi    | >2 koneksi vertikal terputus                     | 1-2 koneksi lemah | Semua koneksi terhubung   |  3   |
| Specificity  | Variabel/metrik masih abstrak, tidak ada angka   | Sebagian metrik jelas           | Semua metrik dan variabel jelas   |   3   |
| Feasibility  | Timeline tidak realistis   | Timeline cukup realistis     | Timeline realistis dengan rencana detail |  3    |
| Rigor        | Baseline tidak jelas atau straw man              | 1-2 baseline dengan justifikasi partial       | 2+ baseline SOTA + justifikasi pemilihan lengkap   |      |
```

---

## Latihan 1 — Kompilasi Proposal Mini

Kumpulkan hasil dari WS-02 sampai WS-07 menjadi satu ringkasan proposal.

| Komponen | Sumber | Isi (1-2 kalimat) |
|----------|--------|-------------------|
| Problem Statement | WS-02 | Penggunaan Artificial Intelligence pada aplikasi pembelajaran bahasa semakin meningkat, tetapi belum diketahui secara jelas bagaimana pengaruh fitur AI terhadap kepuasan pengguna. Banyak penelitian hanya membahas efektivitas AI atau usability aplikasi secara terpisah. |
| Gap | WS-03 | Penelitian sebelumnya belum banyak menggabungkan Artificial Intelligence dengan model TAM untuk mengukur kepuasan pengguna secara spesifik pada aplikasi pembelajaran bahasa seperti Duolingo. |
| RQ | WS-04 | Apakah penggunaan fitur Artificial Intelligence pada aplikasi Duolingo berpengaruh signifikan terhadap kepuasan pengguna berdasarkan variabel Perceived Ease of Use (PEOU) dan Perceived Usefulness (PU)? |
| Hipotesis | WS-04 | H₁: PEOU dan PU pada fitur AI Duolingo berpengaruh positif terhadap kepuasan pengguna. H₀: PEOU dan PU tidak berpengaruh signifikan terhadap kepuasan pengguna. |
| Variabel & Metrik | WS-05 | IV = PEOU dan PU; DV = kepuasan pengguna; CV = usia pengguna, durasi penggunaan aplikasi, dan perangkat yang digunakan. Metrik menggunakan skala Likert 1–5 pada kuesioner TAM. |
| Sistem | WS-06 | Sistem penelitian berupa penyebaran kuesioner berbasis Google Form kepada pengguna Duolingo. Data diolah menggunakan analisis statistik untuk melihat hubungan antara variabel TAM dan kepuasan pengguna. |
| Desain Eksperimen | WS-07 | Penelitian menggunakan comparison study antara pengguna dengan persepsi AI tinggi dan rendah berdasarkan hasil kuesioner TAM. Semua responden menggunakan konteks aplikasi yang sama agar pengukuran lebih adil dan konsisten. |

---

## Latihan 2 — Integration Checklist

Verifikasi 6 koneksi kritis. Isi dengan merujuk tabel di Latihan 1.

| Koneksi | Status | Bukti |
|---------|--------|-------|
| Problem → Gap | ✅ - Terhubung | Permasalahan pada WS-02 menunjukkan bahwa belum diketahui secara jelas pengaruh fitur Artificial Intelligence terhadap kepuasan pengguna aplikasi pembelajaran bahasa. Pada WS-03, hasil telaah lima jurnal menunjukkan bahwa penelitian sebelumnya masih memisahkan pembahasan AI, TAM, dan kepuasan pengguna sehingga muncul research gap. |
| Gap → RQ | ✅ — terhubung | Research Question pada WS-04 secara langsung menjawab gap tersebut, yaitu meneliti pengaruh Artificial Intelligence pada aplikasi Duolingo terhadap kepuasan pengguna menggunakan model Technology Acceptance Model (TAM). |
| RQ → Hypothesis | ✅ — terhubung | Hipotesis H₁ menyatakan bahwa Perceived Ease of Use (PEOU) dan Perceived Usefulness (PU) berpengaruh positif terhadap kepuasan pengguna, sedangkan H₀ menyatakan tidak ada pengaruh yang signifikan. Hipotesis ini merupakan jawaban yang diprediksi dari RQ. |
| Hypothesis → Metric | ✅ — terhubung | Variabel PEOU, PU, dan kepuasan pengguna diukur menggunakan skor kuesioner skala Likert 1–5 sehingga hipotesis dapat diuji secara kuantitatif. |
| Metric → System | ✅ — terhubung | Sistem penelitian berupa kuesioner Google Form yang menghasilkan data numerik untuk setiap indikator PEOU, PU, dan kepuasan pengguna. Data tersebut kemudian dianalisis menggunakan metode statistik. |
| System → Experiment | ✅ — terhubung | Desain eksperimen menggunakan data hasil kuesioner sebagai instrumen utama untuk menguji hubungan antara variabel independen (PEOU dan PU) terhadap variabel dependen (kepuasan pengguna) pada kondisi yang sama untuk seluruh responden. |

**Koneksi mana yang paling lemah?**  
Problem → Gap

**Bagaimana cara memperkuatnya?**
> Menambahkan lebih banyak jurnal Indonesia yang secara khusus membahas Artificial Intelligence pada aplikasi pembelajaran bahasa sehingga hubungan antara masalah penelitian dan research gap menjadi semakin kuat dan didukung oleh lebih banyak bukti ilmiah.
> 
**Konsistensi horizontal — apakah istilah dan scope konsisten?** [✓] Ya / [ ] Tidak
>Istilah Artificial Intelligence (AI), Technology Acceptance Model (TAM), Perceived Ease of Use (PEOU), Perceived Usefulness (PU), dan kepuasan pengguna digunakan secara konsisten mulai dari latar belakang, research gap, research question, hipotesis, variabel penelitian, hingga desain eksperimen. Ruang lingkup penelitian juga tetap berfokus pada aplikasi Duolingo tanpa berubah pada bagian metodologi maupun eksperimen.
---

## Latihan 3 — Rubrik Self-Assessment

Evaluasi proposal mini menggunakan rubrik.

| Kriteria | Skor (1-3) | Justifikasi |
|----------|-----------|-------------|
| Koherensi | 3 | Alur proposal sudah konsisten mulai dari identifikasi masalah, research gap, research question, hipotesis, variabel, sistem, hingga desain eksperimen. Setiap bagian saling berkaitan dan membentuk satu alur penelitian yang utuh. |
| Specificity | 3 | Variabel penelitian (PEOU, PU, dan kepuasan pengguna), metrik pengukuran (skala Likert 1–5), instrumen (kuesioner TAM), serta objek penelitian (pengguna Duolingo) telah dijelaskan secara spesifik dan konsisten. |
| Feasibility | 3 | Penelitian dapat dilaksanakan dalam waktu 1–3 bulan menggunakan kuesioner online kepada pengguna Duolingo. Instrumen, metode analisis, serta jadwal penelitian sudah realistis dan sesuai dengan kemampuan penelitian tingkat mahasiswa. |
| Rigor | 2 | Proposal telah menggunakan dua baseline dari penelitian sebelumnya (model TAM dan analisis sentimen) serta didukung lima jurnal sebagai dasar research gap. Namun, jumlah referensi masih dapat ditambah agar landasan teori dan pembahasan menjadi lebih kuat. |

**Skor total:** 11 / 12

**Apakah proposal siap untuk fase eksekusi?**  Ya 

**Alasan:**
> Proposal sudah memiliki hubungan yang jelas antara masalah, research gap, research question, hipotesis, variabel, metode, hingga desain eksperimen. Instrumen penelitian dan teknik analisis juga telah ditentukan sehingga penelitian siap memasuki tahap pengumpulan data. Perbaikan yang masih dapat dilakukan adalah menambah referensi terbaru dan memperluas jumlah responden agar hasil penelitian lebih kuat dan mudah digeneralisasikan.
---

## Refleksi

> Dari seluruh proses WS-01 sampai WS-08, bagian mana yang paling mudah dan paling sulit? Mengapa? Apa yang akan dilakukan berbeda jika mengulang dari awal?

**Bagian termudah:** 
> Menentukan topik dan menyusun variabel penelitian karena topik AI dan aplikasi pembelajaran bahasa cukup dekat dengan penggunaan sehari-hari.

**Bagian tersulit:** 
> Mencari research gap dan menyusun hubungan antar bagian proposal agar tetap konsisten dari awal sampai akhir.

**Yang akan dilakukan berbeda:**
> Jika mengulang dari awal, pencarian jurnal akan dilakukan lebih sistematis sejak awal agar proses menemukan gap lebih mudah. Selain itu, penulisan proposal akan langsung disusun paralel dengan pengerjaan worksheet supaya revisi tidak terlalu banyak.
