# WS-01: Distorsi & Paradigma

> **Bab 1 — Research Mindset in IT**

---

## Ringkasan Materi

### Research Trust Model

Pengetahuan ilmiah tidak muncul langsung dari kenyataan. Ia melewati **6 tahap transformasi** yang masing-masing rawan distorsi:

```
Reality → Data → Processing → Analysis → Inference → Knowledge
```

Etika mencegah distorsi yang disengaja (fabrikasi, cherry-picking). Validitas mendeteksi distorsi yang tidak disengaja (confounding variable, sampling bias).

### Tiga Jenis Validitas

| Jenis | Pertanyaan | Contoh Ancaman |
|-------|-----------|----------------|
| **Internal Validity** | Apakah hubungan kausal benar ada? | Confounding variable |
| **External Validity** | Apakah bisa digeneralisasi? | Dataset terlalu homogen |
| **Construct Validity** | Apakah mengukur hal yang benar? | Metrik tidak sesuai klaim |

### Paradigma Riset

Mata kuliah ini menggunakan pendekatan **Positivist** (fenomena TI bisa diukur objektif melalui eksperimen terkontrol) diperkuat **Design Science Research** (DSR). Penting untuk membedakan keduanya:

| Paradigma | Cara Kerja | Contoh di TI |
|-----------|-----------|---------------|
| **Positivis** | Uji hipotesis dengan eksperimen terkontrol | Apakah CNN lebih akurat dari RF pada dataset X? |
| **Design Science Research** | Bangun artefak (sistem/model/framework) untuk menguji proposisi | Dapatkah arsitektur hybrid CNN+LSTM membuktikan peningkatan recall ≥5%? |
| **Interpretivis** | Pahami makna melalui konteks & kualitatif | Bagaimana peneliti manafsirkan anomali data sensor IoT? |

Dalam DSR, artefak **bukan tujuan akhir** — ia adalah instrumen untuk menghasilkan pengetahuan. Pertanyaan riset tetap harus difalsifikasi.

### Mode Berpikir Peneliti

**Curious** (mempertanyakan fenomena) → **Critical** (mengevaluasi klaim berdasarkan bukti) → **Systematic** (merancang investigasi terstruktur dan reproducible).

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan | Membuat sistem yang bekerja | Menghasilkan pengetahuan yang valid |
| Pertanyaan khas | "Bagaimana membuatnya jalan?" | "Apakah klaim ini benar?" |
| Ukuran sukses | Sistem berfungsi, client puas | Hipotesis terjawab, temuan tervalidasi |
| Kegagalan | Harus dihindari | Harus dilaporkan (negative result = kontribusi) |

### Istilah Penting

- **Research Mindset** — Pola pikir yang menuntut bukti dan mempertanyakan asumsi
- **Research Ethics** — Prinsip perilaku: kejujuran, objektivitas, keterbukaan, akuntabilitas
- **HARKing** — Hypothesizing After Results are Known — merumuskan hipotesis setelah melihat data
- **Falsifiability** — Hipotesis harus bisa dibuktikan salah

---

## Template A.1 — Research Mindset Self-Assessment

```
Nama Peneliti    : ____________________
Tanggal          : ____________________

1. Ketika membaca klaim "metode X 95% akurat":
   - Pertanyaan pertama saya: ____________________
   - Data yang dibutuhkan untuk verifikasi: ____________________

2. Posisi paradigma:
   - Pendekatan: [ ] Positivis  [ ] Interpretivis  [ ] Design Science  [ ] Mixed
   - Alasan: ____________________

3. Identifikasi distorsi:
   - Asumsi tersembunyi: ____________________
   - Sumber bias potensial: ____________________
   - Langkah mitigasi: ____________________

4. Komitmen etika:
   - Data yang tidak akan dimanipulasi: ____________________
   - Batasan yang diakui sejak awal: ____________________
```

---

## Latihan 1 — Identifikasi Distorsi

Pilih satu paper riset di bidang TI yang mengklaim "metode X meningkatkan performa." Telusuri setiap tahap Research Trust Model.

> **Panduan pencarian paper:** Gunakan [IEEE Xplore](https://ieeexplore.ieee.org), [ACM Digital Library](https://dl.acm.org), atau Google Scholar. Pilih paper **tahun 2020 ke atas**, di topik yang Anda minati: deteksi anomali, klasifikasi citra, NLP, keamanan siber, IoT, dsb.
>
> **Contoh domain TI:** "Deteksi anomali lalu-lintas jaringan menggunakan CNN — akurasi meningkat 94% vs baseline SVM 87%." Distorsi potensial: apakah dataset normal/anomali seimbang? Apakah hanya diuji pada satu vendor traffic?

**Paper yang dipilih:**
> Judul: Klasifikasi Kualitas dan Kematangan Pisang Candevish Menggunakan Convolutional Neural Network
> Penulis (Tahun): Hastungkoro, A.W,, Wicaksono, A.D.P., Rosita, Y.D. (2024) 
> Sumber/Link DOI: Jurnal SAINTEKOM Vol. 14 No. 2 (2024) I DOI: https://doi.org/10.33020/saintekom.v14i2.686 

| Tahap | Apa yang Dilakukan | Potensi Distorsi |
|-------|-------------------|-----------------|
| Reality → Data | Mengambil foto pisang Cavendish langsung dari satu kebun di Kab. Banyumas sebanyak 400 gambar, dikategorikan ke 4 kelas ; Mentah Bagus, Mentah Buruk, Matang Bagus, Matang Buruk. | Hanya dari satu lokasi dan satu jenis pisang. Variasi cahaya, sudut foto, dan kondisi kebun tidak dikontrol secara eksplisit, sehingga data tidak representatif untuk kondisi nyata yang lebih beragam. |
| Data → Processing | Preprocessing berupa augmentasi data (flip, rotasi, zoom) untuk menambah jumlah sampel, diikuti normalisasi nilai piksel RGB.  | Augmentasi dari dataset kecil (400 foto) berisiko menciptakan sampel yang terlalu mirip satu sama lain (data leakage antar split), sehingga model terlihat akurat padahal hanya 'menghapal' variasi yang sangat terbatas.|
| Processing → Analysis | Membangun 36 model CNN dengan variasi epoch (5, 10, 20), batch size (16, 32), dan split dataset (60:40,70:30, 80:20, 90:10), lalu membandingkan akurasi antar skenario.  | Melaporkan hanya akurasi tertinggi (95%) dari skenario
saling menguntungkan (split 90:10). Ini rawan cherry-picking, skenario lain yang menghasilkan akurasi lebih rendah tidak dijadikan kesimpulan utama.|
| Analysis → Inference | Membangun 36 model CNN dengan variasi epoch (5, 10, 20), batch size (16, 32), dan split dataset (60:40, 70:30, 80:20, 90:10), lalu membandingkan akurasi antar skenario.| Tidak ada perbandingan dengan
metode baseline (SVM, KNN, dsb). Klaim 'CNN efektif' lemah secara ilmiah tanpa tolok ukur komparatif - bisa jadi metode lebih sederhana pun menghasilkan akurasi serupa.|
| Inference → Knowledge | Kesimpulan penelitian disebarkan lewat jurnal: 'CNN bisa mengklasifikasikan pisang dengan akurasi 95%'. | Klaim ini sebenarnya hanya berlaku untuk pisang dari kebun itu saja, dengan kondisi foto yang sama persis. Belum tentu berlaku di tempat lain - tapi pembaca bisa salah sangka itu berlaku secara umum. |

**Distorsi paling besar di tahap:** Analysis → Inference 

**Dua distorsi spesifik yang teridentifikasi:**
1. Dataset terlalu sempit (satu lokasi, 400 foto): Seperti kita menilai semua masakan Padang hanya dari satu warung. Hasilnya tidak bisa dianggap mewakili kenyataan yang lebih luas.
2. Cherry-picking skenario terbaik: Peneliti memilih hasil dengan split 90:10 (data uji cuma 40 foto) sebagai kesimpulan utama, padahal skenario lain hasilnya lebih rendah. Ini membuat klaim terlihat lebih kuat dari sebenarnya.

---

## Latihan 2 — Analisis Kasus Etika

Skenario: Seorang peneliti menemukan bahwa jika 3 data point outlier dihapus, hasil eksperimennya menjadi signifikan. Dengan outlier, hasilnya tidak signifikan.

| Perspektif | Analisis |
|------------|---------|
| Kejujuran ilmiah | Penghapusan data hanya dibenarkan apabila terdapat alasan metodologis yang jelas, misalnya data tersebut terbukti merupakan hasil kesalahan pengukuran atau kesalahan teknis. Menghapus data semata-mata agar hasil menjadi signifikan merupakan bentuk manipulasi yang melanggar prinsip kejujuran ilmiah. Peneliti seharusnya melaporkan kedua versi hasil: dengan dan tanpa outlier. |
| Transparansi | Peneliti wajib mendokumentasikan secara terbuka proses identifikasi outlier, alasan penghapusannya, serta dampaknya terhadap hasil. Tanpa dokumentasi ini, pembaca dan reviewer tidak memiliki informasi yang cukup untuk menilai validitas penelitian secara mandiri, yang merupakan pelanggaran terhadap prinsip reproducibility. |
| Peer review | Reviewer bertanggung jawab untuk mempertanyakan justifikasi penghapusan outlier. Apakah alasannya bersifat statistik (misalnya nilai di luar tiga standar deviasi) atau berbasis domain keilmuan? Apabila alasan yang diberikan tidak memadai, reviewer seharusnya meminta peneliti menyertakan analisis sensitivitas sebagai bahan evaluasi tambahan. |

**Keputusan akhir dan justifikasi:**
>  Data outlier tidak boleh dihapus dengan tujuan utama untuk menghasilkan temuan yang signifikan. Tindakan tersebut termasuk dalam kategori p-hacking, yaitu praktik memanipulasi data atau analisis hingga diperoleh nilai yang diinginkan, yang merupakan pelanggaran serius terhadap etika penelitian. Keputusan yang tepat adalah melaporkan hasil dengan seluruh data sebagai temuan utama, menyertakan analisis tambahan tanpa outlier sebagai perbandingan, dan mendiskusikan kemungkinan penyebab munculnya outlier tersebut. Perlu diingat bahwa hasil yang tidak signifikan tetap merupakan kontribusi ilmiah yang valid.

---

## Latihan 3 — Posisi Paradigma

**Topik riset:** Klasifikasi kualitas buah menggunakan deep learning (CNN) 

> **Skala 1–5:** 1 = tidak sesuai sama sekali dengan topik ini, 5 = sangat sesuai dan dominan digunakan pada riset bertopik serupa.

| Kriteria | Positivis | Interpretivis | Design Science |
|----------|-----------|---------------|----------------|
| Kesesuaian dengan topik (1–5) | 5 - Sangat sesuai. Penelitian ini bersifat kuantitatif dan terukur (akurasi, presisi, recall), serta bertujuan menguji apakah suatu metode lebih unggul dibanding yang lain melalui eksperimen terkontrol. | 1 - Tidak sesuai. Paradigma Interpretivis digunakan untuk memahami makna dan pengalaman manusia secara kualitatif, bukan untuk mengukur kinerja model komputasi. | 4 - Sesuai. Penelitian ini membangun model CNN sebagai artefak untuk membuktikan proposisi tertentu, yang merupakan inti pendekatan Design Science Research. |
| Jenis data yang dikumpulkan | Data numerik berupa metrik evaluasi: akurasi, presisi, recall, dan F1-score yang dapat diukur dan dibandingkan secara objektif. | Wawancara,
observasi kualitatif, dan catatan lapangan. Jenis data ini tidak digunakan dalam penelitian ini. | Hasil pengujian 36
skenario model, perbandingan konfigurasi parameter, dan evaluasi kinerja artefak terhadap data nyata. |
| Limitasi paradigma | Hanya mengukur bahwa CNN bekerja, tanpa menjelaskan mengapa. Juga tidak mempertimbangkan konteks implementasi di lapangan secara nyata. | Tidak menghasilkan metrik yang dapat dibandingkan secara kuantitatif. Tidak cocok untuk penelitian yang berfokus pada klaim performa.| Terdapat risiko peneliti terlalu berfokus pada pembangunan sistem (orientasi engineering) sehingga melupakan kewajiban menghasilkan pengetahuan baru yang dapat difalsifikasi. |

**Paradigma yang dipilih:** Positivis (dominan) + Design Science Research (Komplementer) 
**Alasan:** Penelitian ini pada dasarnya bertujuan mengukur dan membandingkan kinerja metode secara kuantitatif, sehingga paradigma Positivis menjadi landasan utama. Design Science Research berperan secara komplementer karena penelitian ini juga membangun artefak berupa model CNN sebagai instrumen untuk menghasilkan pengetahuan - bukan sekadar mengembangkan sistem yang berfungsi. 

---

## Refleksi

> Sebelum membaca materi ini, apakah pernah mempertanyakan klaim "95% akurat"? Setelah memahami rantai distorsi, pertanyaan apa yang sekarang akan diajukan saat membaca paper?

**Jawaban:**
> Sebelumnya, klaim dengan angka akurasi tinggi cenderung langsung diterima tanpa mempertanyakan asal-usul data, ukuran sampel, atau keberadaan metode pembanding. Angka yang tinggi terasa sudah cukup meyakinkan sebagai bukti keberhasilan suatu metode. 
> Pertanyaan yang sekarang akan diajukan saat membaca paper: 
> 1. Dari mana data berasal dan seberapa beragam kondisinya? Apabila data hanya dikumpulkan dari satu lokasi dengan kondisi seragam,angka akurasi yang tinggi belum tentu mencerminkan kemampuan model secara umum.
> 2. Apakah hasil yang dilaporkan merupakan hasil terbaik dari banyak percobaan? Jika ya, apakah seluruh hasil percobaan juga dilaporkan secara transparan, atau hanya skenario yang paling menguntungkan yang ditonjolkan?
> 3. Metode apa yang digunakan sebagai pembanding? Tanpa metode baseline, klaim bahwa suatu metode 'meningkatkan performa' tidak dapat diverifikasi secara objektif. 
> 4. Apakah eksperimen ini dapat direplikasi oleh peneliti lain dengan data yang berbeda? Apabila tidak, maka temuan tersebut belum dapat dianggap sebagai pengetahuan yang berlaku secara luas.
