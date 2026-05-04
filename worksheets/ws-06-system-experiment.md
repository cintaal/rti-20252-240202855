# WS-06: System-Experiment Mapping

> **Bab 6 — System Design sebagai Experimental Artifact**

---

## Ringkasan Materi

### Sistem = Instrumen Pengujian, Bukan Produk

Seorang engineer bertanya "apakah sistem bekerja?" — seorang peneliti bertanya "apa yang bisa dibuktikan sistem ini?" Sistem dalam riset adalah **artifact** — objek yang sengaja dibuat untuk menguji klaim spesifik.

### System as Experiment Model

```
RQ → Variable → System Component → Experimental Setup → Output
```

Setiap komponen sistem harus bisa ditelusuri ke variabel riset (top-down), dan setiap pengukuran harus menjawab RQ (bottom-up).

### Mapping Variabel ke Komponen

| Tipe Variabel | Peran di Sistem | Contoh |
|---------------|----------------|--------|
| **IV** (Independent) | Modul yang bisa di-toggle/swap | Algoritma A vs B |
| **DV** (Dependent) | Modul pengukuran | Logger, metrics collector |
| **CV** (Control) | Config yang dikunci | Dataset, parameter tetap |

Jika variabel tidak bisa di-map ke komponen apapun → arsitektur perlu didesain ulang.

### 4 Prinsip Desain Eksperimental

| Prinsip | Pertanyaan Kunci |
|---------|-----------------|
| **Traceability** | Komponen ini melayani variabel yang mana? |
| **Modularity** | Bisakah IV diubah tanpa memengaruhi yang lain? |
| **Controllability** | Apakah CV dieksternalisasi ke config file? |
| **Measurability** | Apakah sistem otomatis menghasilkan data yang dibutuhkan? |

### Variable Isolation melalui Arsitektur

- **Modular architecture** — Pisahkan berdasarkan variabel
- **Configuration-driven** — Ubah config (YAML/JSON), bukan code
- **Feature toggles** — On/off flag untuk ablation study

  Contoh config YAML dengan feature toggles:
  ```yaml
  model:
    type: cnn          # IV: ganti "rf" untuk kondisi baseline
  features:
    use_temporal: true  # toggle komponen temporal
    use_normalization: true  # toggle preprocessing
  experiment:
    seed: 42
    runs: 5
  ```
  Dengan pendekatan ini, berbeda kondisi eksperimen = berbeda satu baris config, **tanpa mengubah kode**.

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan sistem | Memenuhi kebutuhan user | Menguji hipotesis, menghasilkan bukti |
| Arsitektur | Optimasi performa & skalabilitas | Optimasi isolasi variabel & reprodusibilitas |
| Konfigurasi | Sering hardcoded | Dieksternalisasi ke config file |
| Fitur tambahan | Menambah nilai user | Menambah noise jika tidak terkait RQ |

### Istilah Penting

- **Artifact** — Objek yang sengaja dibuat untuk memecahkan masalah atau menguji proposisi
- **Traceability** — Kemampuan menelusuri hubungan RQ → variabel → komponen → output
- **Variable Isolation** — Mengubah hanya satu variabel sambil menahan yang lain konstan
- **Ablation Study** — Menguji kontribusi tiap komponen dengan melepasnya satu per satu
- **Configuration-driven Execution** — Semua parameter di config file, bukan hardcoded

---

## Template A.6 — Mapping RQ ke Arsitektur Sistem

```
SYSTEM-EXPERIMENT MAPPING

Research Question: Apakah Perceived Ease of Use (PEOU) dan Perceived Usefulness (PU) dari teknologi AI pada aplikasi Duolingo berpengaruh signifikan terhadap kepuasan pengguna?

Variable → Component Mapping:
| Variabel | Tipe | Komponen Sistem | Cara Manipulasi/Pengukuran |
|----------|------|-----------------|---------------------------|
| PEOU | IV | Modul kuesioner (indikator kemudahan) | Mengubah/menampilkan pertanyaan terkait kemudahan penggunaan |
| PU | IV | Modul kuesioner (indikator manfaat) | Mengubah/menampilkan pertanyaan terkait kegunaan aplikasi |
| Kepuasan pengguna | DV | Modul evaluasi hasil (scoring & analisis) | Menghitung skor Likert dan analisis regresi |
| Lama penggunaan | CV | Input profil responden | Dikunci sebagai variabel kontrol dalam analisis |

4 Prinsip Desain:
  [✓] Traceability — Setiap komponen bisa ditelusuri ke variabel
  [✓] Variable Isolation — IV bisa diubah tanpa mengubah CV
  [✓] Measurement Integration — Pengukuran DV built-in
  [✓] Reproducibility — Setup bisa direkonstruksi

Experimental Setup:
  Input data     : Data kuesioner pengguna Duolingo
  Parameter      : Skala Likert (1-5), jumlah responden, variabel PEOU & PU
  Output format  : Dataset (Excel/CSV) + hasil analisis statistik (regresi)
```

---

## Latihan 1 — Variable-to-Component Mapping

Gunakan RQ dan variabel dari WS-05. Petakan ke komponen sistem.

**RQ:** Apakah PEOU dan PU berpengaruh terhadap kepuasan pengguna Duolingo?

| Variabel | Tipe | Komponen Sistem | Cara Manipulasi / Pengukuran |
|----------|------|-----------------|---------------------------|
| PEOU            | IV   | Modul pertanyaan kemudahan | Mengatur indikator pertanyaan |
| PU              | IV   | Modul pertanyaan manfaat   | Mengatur indikator pertanyaan |
| Kepuasan        | DV   | Modul scoring & analisis   | Menghitung skor Likert        |
| Lama penggunaan | CV   | Data profil responden      | Dikontrol dalam analisis      |

**Apakah semua variabel bisa di-map?** Ya 
> Semua variabel memiliki representasi dalam sistem, baik sebagai input (kuesioner), proses (analisis), maupun kontrol (profil responden).

---

## Latihan 2 — 4 Prinsip Desain

Evaluasi desain sistem terhadap 4 prinsip.

| Prinsip | Status | Bukti / Penjelasan |
|---------|--------|-------------------|
| Traceability    | ✅      | Setiap variabel memiliki komponen sistem yang jelas |
| Modularity      | ✅      | Modul kuesioner dan analisis terpisah               |
| Controllability | ✅      | Variabel kontrol dipisahkan dalam data responden    |
| Measurability   | ✅      | Sistem menghasilkan skor dan data siap analisis     |

**Prinsip mana yang paling sulit dipenuhi?**  Controllability

**Strategi untuk mengatasinya:**
> Menggunakan desain kuesioner yang jelas serta memastikan variabel kontrol (seperti pengalaman pengguna) dikumpulkan dan dipisahkan dalam proses analisis.

---

## Latihan 3 — Ablation Study Planning

Jika sistem memiliki 3 komponen utama, rencanakan ablation study.

> **Panduan jumlah kondisi:** Untuk 3 komponen (A, B, C), kondisi minimal yang direkomendasikan:
> Full + (-A) + (-B) + (-C) = **4 kondisi dasar**. Jika waktu memungkinkan, tambahkan kombinasi ganda: (-A,-B), (-A,-C), (-B,-C) = **7 kondisi**. Sesuaikan dengan *computational cost* dan tenggat waktu penelitian.

| Kondisi | Komponen A | Komponen B | Komponen C | Hasil yang Diharapkan |
|---------|-----------|-----------|-----------|----------------------|
| Full    | ✅ | ✅ | ✅ | Hasil lengkap pengaruh PEOU & PU |
| – A     | ❌ | ✅ | ✅ | Mengetahui pengaruh PU saja      |
| – B     | ✅ | ❌ | ✅ | Mengetahui pengaruh PEOU saja    |
| – C     | ✅ | ✅ | ❌ | Tidak bisa mengukur kepuasan secara valid |

**Komponen mana yang diprediksi paling berkontribusi?** PU (Perceived Usefulness)

**Mengapa?**
> Karena dalam banyak penelitian TAM, persepsi kegunaan biasanya memiliki pengaruh lebih kuat terhadap kepuasan dibanding kemudahan penggunaan.

---

## Refleksi

> Apa risiko jika sistem dibangun seperti produk (monolitik, fitur lengkap) lalu baru dilakukan eksperimen? Mengapa arsitektur modular penting untuk riset?

**Jawaban:**
> Jika sistem dibangun seperti produk (monolitik), maka sulit untuk mengisolasi variabel penelitian karena semua komponen saling terhubung. Hal ini dapat menyebabkan bias dalam eksperimen dan sulit untuk menentukan faktor mana yang benar-benar mempengaruhi hasil. Arsitektur modular penting dalam riset karena memungkinkan setiap variabel diuji secara terpisah, sehingga hasil penelitian lebih valid dan dapat direproduksi.
