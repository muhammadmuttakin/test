# Laporan Proyek Machine Learning - Muhammad Muttakin

## Domain Proyek
Penyakit jantung merupakan penyebab kematian utama di dunia, dengan lebih dari 20 juta jiwa meninggal akibat penyakit kardiovaskular (CVD) pada tahun 2021. Angka ini setara dengan hampir sepertiga dari seluruh kematian global. Penyakit jantung iskemik dan stroke menjadi penyumbang terbesar, mencakup sekitar 85% dari seluruh kematian akibat CVD. Meskipun tingkat kematian berdasarkan usia menurun di beberapa negara maju, jumlah kasus secara keseluruhan terus meningkat, terutama di negara berkembang [1].

Penyebab utama penyakit jantung sangat berkaitan dengan gaya hidup yang tidak sehat, seperti konsumsi makanan tinggi lemak dan gula, kurangnya aktivitas fisik, kebiasaan merokok, konsumsi alkohol, dan stres berkepanjangan. Padahal, sebagian besar kasus penyakit jantung dapat dicegah melalui deteksi dini dan pengendalian faktor risiko. Deteksi awal sangat penting, terutama bagi individu dengan riwayat keluarga, untuk mencegah komplikasi serius hingga kematian yang sebenarnya dapat dicegah [2].

Kurangnya pemahaman gejala awal penyakit jantung dan minimnya gaya hidup sehat membuat banyak orang tidak menyadari risikonya. Deteksi ini berperan sebagai dukungan dalam pengambilan keputusan untuk menjaga kesehatan. Dengan pemeriksaan rutin, risiko penyakit jantung dapat diketahui sejak dini sehingga penanganan lebih tepat dan biaya pengobatan lebih efisien [3]. Oleh sebab itu, diperlukan sistem deteksi penyakit jantung yang dapat memberikan hasil yang akurat sekaligus lebih efisien secara biaya bagi masyarakat agar terhindar dari kondisi yang lebih buruk di masa depan [4].

Dalam mendeteksi penyakit jantung, digunakan berbagai metode seperti stress echocardiography, cardiac CT scan, myocardial perfusion imaging, dan coronary CT angiography (CCTA) untuk menilai fungsi jantung, aliran darah, serta kelainan struktural dan penyumbatan arteri koroner. Studi oleh Costantino et al. (2025) menekankan bahwa kombinasi berbagai modalitas ini penting dalam evaluasi penyakit jantung iskemik, karena meningkatkan akurasi diagnosis dan membantu menentukan perlunya angiografi koroner [5].

Penelitian sebelumnya menunjukkan bahwa algoritma K-Nearest Neighbor (K-NN) digunakan dalam sistem pendukung keputusan medis, khususnya untuk deteksi penyakit jantung. Studi oleh Ningsih & Zakaria (2023) membuktikan bahwa K-NN mampu mengklasifikasikan data pasien dengan akurasi tinggi menggunakan parameter seperti name, age, sex, cp, trestbps, chol, fbs, restecg, thalac, exang, oldpeak, slope, ca, thal [6].

Berdasarkan temuan-temuan tersebut, penelitian ini menggunakan empat algoritma klasifikasi yaitu Decision Tree, Random Forest, K-Nearest Neighbors (KNN), dan Support Vector Machine (SVM) untuk membangun model prediksi risiko penyakit jantung. Tujuannya adalah untuk mengevaluasi performa masing-masing algoritma dalam mendeteksi penyakit jantung secara dini dan akurat, sehingga dapat mendukung proses diagnosis yang lebih efisien dan mudah diimplementasikan dalam sistem layanan kesehatan.

---

### Referensi

[1] World Heart Federation, “World Heart Report 2023: Confronting the world’s number one killer,” pp. 1–52, 2023.  
[2] E. M. Marwali, Y. Purnama, P. S. Roebiono, K. : Eva, M. Marwali, and T. Pustaka, “Modalitas Deteksi Dini Penyakit Jantung Bawaan di Pelayanan Kesehatan Primer.”  
[3] Y. Amelia, “PERBANDINGAN METODE MACHINE LEARNING UNTUK MENDETEKSI PENYAKIT JANTUNG,” 2023. [Online]. Available: http://jom.fti.budiluhur.ac.id/index.php/IDEALIS/index  
[4] A. B. Wibisono and A. Fahrurozi, “PERBANDINGAN ALGORITMA KLASIFIKASI DALAM PENGKLASIFIKASIAN DATA PENYAKIT JANTUNG KORONER,” Jurnal Ilmiah Teknologi dan Rekayasa, vol. 24, no. 3, pp. 161–170, 2019, doi: 10.35760/tr.2019.v24i3.2393.  
[5] M. F. Costantino, F. Cortese, G. D’Addeo, A. Nicoletti, S. Mancino, and L. Stolfi, “Diagnostic modalities for ischemic heart disease: evaluating the role of stress echocardiography, cardiac CT, and myocardial perfusion scintigraphy in guiding coronary angiography,” Exploration of Cardiology, Jan. 2025, doi: 10.37349/ec.2025.101243.  
[6] T. K. Ningsih and H. Zakaria, “Implementasi Algoritma K-Nearest Neighbor Pada Sistem Deteksi Penyakit Jantung (Studi Kasus : Klinik Makmur Jaya).” [Online]. Available: https://journal.mediapublikasi.id/index.php/logic  




# Business Understanding

## Problem Statements

1. **Pernyataan Masalah 1:**  
   Penyakit jantung merupakan penyebab kematian terbesar di dunia, dan jumlah kasusnya terus meningkat, terutama di negara berkembang. Deteksi dini masih menjadi tantangan karena minimnya kesadaran masyarakat terhadap gejala awal serta kurangnya sistem deteksi yang efisien dan akurat.

2. **Pernyataan Masalah 2:**  
   Metode diagnosis penyakit jantung konvensional seperti CCTA atau myocardial perfusion imaging membutuhkan biaya tinggi dan tidak selalu mudah diakses, terutama di daerah dengan fasilitas medis terbatas.

3. **Pernyataan Masalah 3:**  
   Belum diketahui algoritma machine learning mana yang paling optimal dalam mendeteksi risiko penyakit jantung secara dini dengan akurasi tinggi dan efisiensi waktu serta sumber daya.

---

## Goals

1. **Jawaban Pernyataan Masalah 1:**  
   Mengembangkan model deteksi dini penyakit jantung berbasis machine learning yang mampu memanfaatkan data klinis umum (seperti usia, tekanan darah, kolesterol) untuk mengidentifikasi risiko penyakit jantung secara akurat dan tepat waktu.

2. **Jawaban Pernyataan Masalah 2:**  
   Menyediakan solusi diagnosis alternatif berbasis AI yang lebih murah dan mudah diimplementasikan dibandingkan metode konvensional, sehingga dapat menjangkau lebih banyak lapisan masyarakat.

3. **Jawaban Pernyataan Masalah 3:**  
   Mengevaluasi dan membandingkan performa beberapa algoritma klasifikasi (Decision Tree, Random Forest, K-Nearest Neighbors, dan SVM) dalam mendeteksi penyakit jantung untuk menentukan algoritma terbaik berdasarkan metrik seperti akurasi, presisi, recall, dan F1-score.

---

## Solution Statements

1. **Solusi 1:**  
   Membangun dan melatih model klasifikasi menggunakan empat algoritma berbeda — **Decision Tree, Random Forest, K-Nearest Neighbors (KNN), dan Support Vector Machine (SVM)** — untuk mendeteksi risiko penyakit jantung berdasarkan dataset dari Kaggle. Kinerja masing-masing algoritma akan diukur menggunakan **confusion matrix** dan metrik evaluasi: **akurasi, presisi, recall, dan F1-score**.

2. **Solusi 2:**  
   Menggunakan teknik **cross-validation** untuk memvalidasi kestabilan dan generalisasi model terhadap variasi data pelatihan dan pengujian. Ini penting untuk menghindari overfitting dan memastikan model bekerja baik pada data baru.

3. **Solusi 3:**  
   Melakukan **data preprocessing** termasuk normalisasi dan transformasi variabel kategorikal menjadi numerik, serta pemilihan fitur berdasarkan korelasi tertinggi agar model lebih fokus pada fitur yang relevan terhadap penyakit jantung.


## Data Understanding
# Data Understanding

## Sumber Dataset

Dataset yang digunakan dalam proyek ini diperoleh dari situs [Kaggle - Heart Disease Dataset](https://www.kaggle.com/datasets/johnsmith88/heart-disease-dataset/data). Dataset ini berisi informasi klinis dari 1025 pasien dengan variabel-variabel yang digunakan untuk memprediksi kemungkinan adanya penyakit jantung. Variabel target terdiri dari dua kelas:
- **0**: Pasien *tidak* menderita penyakit jantung
- **1**: Pasien *menderita* penyakit jantung

---

## Variabel-variabel pada Dataset Penyakit Jantung

Berikut adalah penjelasan dari masing-masing fitur yang terdapat dalam dataset:

1. **age**: Usia pasien
2. **sex**: Jenis kelamin (0 = perempuan, 1 = laki-laki)
3. **cp**: Tipe nyeri dada (indikasi kemungkinan penyakit jantung)
4. **trestbps**: Tekanan darah saat istirahat (dalam mm Hg)
5. **chol**: Kadar kolesterol total dalam darah (dalam mg/dl)
6. **fbs**: Gula darah puasa > 120 mg/dl (1 = ya, 0 = tidak)
7. **restecg**: Hasil EKG saat istirahat (elektrokardiografi)
8. **thalach**: Denyut jantung maksimum yang dicapai
9. **exang**: Angina (nyeri dada) yang dipicu oleh olahraga (1 = ya, 0 = tidak)
10. **oldpeak**: Tingkat depresi segmen ST dibandingkan saat istirahat
11. **slope**: Kemiringan segmen ST saat latihan fisik
12. **ca**: Jumlah pembuluh darah besar yang terlihat melalui fluoroskopi
13. **thal**: Jenis thalasemia (kelainan darah bawaan)
14. **target**: Status penyakit jantung (0 = tidak, 1 = ya)

---

## Eksplorasi dan Transformasi Data

### Eksplorasi Awal

- Dataset terdiri dari 1025 baris dan 14 kolom.
- Tidak ditemukan nilai hilang dalam dataset.
- Statistik deskriptif dan struktur data diperiksa menggunakan fungsi `info()` dan `describe()`.

### Penggantian Nama Kolom

Untuk meningkatkan keterbacaan, beberapa nama kolom diubah ke Bahasa Indonesia, seperti:
- `age` menjadi `usia`
- `sex` menjadi `jenis_kelamin`
- `cp` menjadi `tipe_nyeri_dada`
- `trestbps` menjadi `tekanan_darah_istirahat`
- `chol` menjadi `kolesterol`
- `fbs` menjadi `gula_darah_puasa`
- `restecg` menjadi `hasil_ekg_istirahat`
- `thalach` menjadi `denyut_jantung_maks`
- `exang` menjadi `angina_terinduksi_olahraga`
- `oldpeak` menjadi `depresi_st`
- `slope` menjadi `kemiringan_st`
- `ca` menjadi `jumlah_pembuluh_berwarna`
- `thal` menjadi `jenis_thalasemia`

### Analisis Korelasi
![image](https://github.com/user-attachments/assets/c00a61d9-fd99-4366-a7b5-5b26ca83999b)

Dilakukan analisis korelasi antara fitur dan variabel target. Hasilnya:

| Fitur                       | Korelasi dengan Target |
|----------------------------|------------------------|
| Tipe nyeri dada            | 0.43                   |
| Denyut jantung maks        | 0.42                   |
| Kemiringan ST              | 0.35                   |
| Usia                       | -0.23                  |
| Jenis kelamin              | -0.28                  |
| Jumlah pembuluh berwarna   | -0.38                  |
| Jenis thalasemia           | -0.34                  |
| Angina terinduksi olahraga | -0.44                  |
| Depresi ST                 | -0.44                  |

Fitur-fitur dengan korelasi tinggi dipilih untuk pelatihan model:  
**tipe nyeri dada, angina terinduksi olahraga, depresi ST, jenis thalasemia, denyut jantung maksimum, jumlah pembuluh berwarna, dan usia.**

---
## Data Preparation

Tahapan data preparation bertujuan untuk mempersiapkan data sebelum masuk ke proses pemodelan. Langkah-langkah yang diterapkan dalam proyek ini meliputi:

### 1. Seleksi Fitur

Langkah awal adalah memilih subset dari fitur yang paling relevan terhadap prediksi penyakit jantung berdasarkan analisis korelasi sebelumnya. Fitur-fitur yang dipilih antara lain:

- `tipe_nyeri_dada`
- `angina_terinduksi_olahraga`
- `depresi_st`
- `jenis_thalasemia`
- `denyut_jantung_maks`
- `jumlah_pembuluh_berwarna`
- `usia`
- `jenis_kelamin`
- `target`

Seleksi fitur ini penting untuk:
- Mengurangi kompleksitas model
- Meningkatkan akurasi dan efisiensi algoritma
- Menghindari fitur yang redundan atau kurang informatif

---

### 2. One-Hot Encoding Fitur Kategorikal

Fitur kategorikal `tipe_nyeri_dada` dan `jenis_thalasemia` diubah menjadi representasi numerik menggunakan teknik **One-Hot Encoding**. Fungsi `pd.get_dummies()` digunakan untuk mengubah kategori menjadi kolom biner (0 atau 1), dan `drop_first=True` digunakan untuk menghindari multikolinearitas.

Setelah proses encoding, kolom hasil diubah ke tipe integer agar dapat digunakan dalam model pembelajaran mesin.

Tujuan tahap ini:
- Mengonversi data kategorikal menjadi bentuk numerik yang bisa digunakan oleh algoritma ML
- Memastikan model tidak mengasumsikan urutan atau hubungan antara kategori

---

### 3. Normalisasi Fitur Numerik

Fitur numerik seperti `usia`, `depresi_st`, dan `denyut_jantung_maks` dinormalisasi menggunakan **StandardScaler** dari `sklearn.preprocessing`. Normalisasi ini mengubah nilai-nilai menjadi distribusi dengan:

- Rata-rata (mean) = 0
- Standar deviasi = 1

Proses ini penting untuk model berbasis jarak seperti **K-Nearest Neighbors (KNN)** dan **Support Vector Machine (SVM)**, agar:
- Setiap fitur memiliki kontribusi yang seimbang dalam perhitungan jarak
- Mempercepat proses pelatihan dan meningkatkan stabilitas model

---

### 4. Finalisasi Data

Setelah semua tahap selesai:
- Dataset akhir (`df_new`) terdiri dari fitur-fitur numerik yang sudah dinormalisasi
- Fitur kategorikal yang sudah di-encode ke dalam bentuk biner
- Kolom target (`target`) tetap dipertahankan sebagai label

Contoh lima data teratas (4 pertama + 1 terakhir) dari dataset hasil preprocessing ditampilkan menggunakan `pd.concat()` untuk memastikan struktur data akhir sudah sesuai.

---

## Modeling

Pada tahap ini, dilakukan pemodelan menggunakan empat algoritma machine learning yang berbeda. Tujuan dari penggunaan beberapa model adalah untuk membandingkan performa masing-masing dan memilih model terbaik untuk klasifikasi penyakit jantung.

### Model yang Digunakan

Empat algoritma supervised learning yang digunakan adalah:

1. **Decision Tree**
   - Implementasi: `DecisionTreeClassifier()`
   - Merupakan model berbasis pohon keputusan yang membagi data ke dalam cabang berdasarkan fitur yang paling berpengaruh.
   - **Kelebihan**:
     - Mudah diinterpretasikan.
     - Dapat menangani data kategorikal dan numerik.
     - Tidak memerlukan normalisasi data.
   - **Kekurangan**:
     - Rentan terhadap overfitting, terutama pada data dengan banyak noise.
     - Kurang stabil terhadap perubahan kecil pada data.

2. **Random Forest**
   - Implementasi: `RandomForestClassifier()`
   - Merupakan ensemble dari banyak decision tree, yang digabung menggunakan metode voting untuk meningkatkan akurasi dan mengurangi overfitting.
   - **Kelebihan**:
     - Lebih akurat dan stabil dibandingkan decision tree tunggal.
     - Dapat menangani missing value dan data tidak linear.
   - **Kekurangan**:
     - Lebih kompleks dan membutuhkan lebih banyak sumber daya komputasi.
     - Sulit diinterpretasikan secara individual.

3. **K-Nearest Neighbors (KNN)**
   - Implementasi: `KNeighborsClassifier()`
   - Model ini mengklasifikasikan data baru berdasarkan kemiripan (jarak) ke data-data terdekat (tetangga).
   - **Kelebihan**:
     - Sederhana dan efektif untuk dataset kecil.
     - Tidak ada asumsi distribusi data.
   - **Kekurangan**:
     - Sensitif terhadap fitur yang tidak dinormalisasi (itulah mengapa dilakukan **StandardScaler** sebelumnya).
     - Kurang efisien untuk dataset besar karena proses pencarian tetangga.

4. **Support Vector Machine (SVM)**
   - Implementasi: `SVC()`
   - Mencari hyperplane optimal yang memisahkan dua kelas dengan margin maksimal.
   - **Kelebihan**:
     - Efektif dalam ruang dimensi tinggi.
     - Bekerja baik untuk data yang tidak linear dengan kernel trick.
   - **Kekurangan**:
     - Proses training bisa lama untuk dataset besar.
     - Perlu tuning parameter seperti `C` dan `kernel` untuk hasil optimal.

---

### Proses Pemodelan

1. Dataset hasil **preprocessing** digunakan sebagai input.
2. Empat model dimasukkan ke dalam dictionary `models` untuk dilakukan training dan evaluasi secara terpisah.
3. Selanjutnya dilakukan **evaluasi performa masing-masing model**, biasanya menggunakan metrik seperti:
   - Akurasi
   - Precision
   - Recall
   - F1-score
   - Confusion matrix
4. Model dengan performa terbaik dipilih sebagai model final.

---

### Pemilihan Model Terbaik

Setelah seluruh model dievaluasi, akan dipilih **model dengan metrik performa tertinggi**, terutama berdasarkan akurasi dan F1-score karena ini adalah kasus klasifikasi biner dan melalui cross validation untuk melihat model yang memiliki kemungkinan overfitting. Model terbaik kemudian akan digunakan sebagai dasar untuk prediksi dan analisis lebih lanjut.

---

## Kesimpulan

Pendekatan menggunakan beberapa algoritma memberikan gambaran yang lebih komprehensif terhadap kemampuan klasifikasi dataset penyakit jantung. Dengan mengevaluasi performa masing-masing model, kita dapat memilih model yang paling optimal dalam memberikan prediksi akurat terhadap kemungkinan seseorang menderita penyakit jantung.


## Evaluation

Pada proyek klasifikasi ini, digunakan beberapa metrik evaluasi untuk mengukur kinerja model machine learning, yaitu:

- **Accuracy**: Mengukur seberapa banyak prediksi yang benar dari seluruh data. Formula:  
  \[
  \text{Accuracy} = \frac{TP + TN}{TP + TN + FP + FN}
  \]
  Di mana TP (True Positive), TN (True Negative), FP (False Positive), dan FN (False Negative).

- **Precision**: Mengukur ketepatan prediksi positif. Artinya, dari seluruh data yang diprediksi positif, berapa banyak yang benar-benar positif.  
  \[
  \text{Precision} = \frac{TP}{TP + FP}
  \]

- **Recall**: Mengukur sensitivitas model dalam menangkap data positif. Artinya, dari seluruh data positif, berapa banyak yang berhasil ditangkap model.  
  \[
  \text{Recall} = \frac{TP}{TP + FN}
  \]

- **F1-score**: Merupakan harmonic mean dari precision dan recall, memberikan gambaran keseimbangan antara keduanya.  
  \[
  \text{F1-score} = 2 \times \frac{Precision \times Recall}{Precision + Recall}
  \]

### Hasil Evaluasi Model
Confusion Matrix Decision Tree
![image](https://github.com/user-attachments/assets/4a2f26f0-4867-4161-9ba0-43f946078425)
Confusion Matrix Random Forest
![image](https://github.com/user-attachments/assets/b3f9d527-cbe9-4438-b719-970eccfb7eee)
Confusion Matrix KNN
![image](https://github.com/user-attachments/assets/66ccfe62-3f9a-4cfa-8472-466dd85cb843)
Confusion Matrix SVM
![image](https://github.com/user-attachments/assets/7b2f29d9-fce0-4605-ad88-3e31a0f3d1bd)

Empat algoritma telah digunakan untuk menyelesaikan tugas klasifikasi penyakit jantung:

| Model             | Accuracy | Precision (Class 1) | Recall (Class 1) | F1-score (Class 1) |
|-------------------|----------|----------------------|------------------|--------------------|
| Decision Tree     | 0.99     | 1.00                 | 0.97             | 0.99               |
| Random Forest     | 0.99     | 1.00                 | 0.97             | 0.99               |
| K-Nearest Neighbor| 0.84     | 0.84                 | 0.85             | 0.85               |
| Support Vector Machine (SVM) | 0.88 | 0.85           | 0.91             | 0.88               |

### Analisis Confusion Matrix
- **Decision Tree & Random Forest** memiliki hasil yang sangat tinggi, dengan hanya 3 kesalahan klasifikasi pada kelas 1. Tidak ada kesalahan pada kelas 0.
- **KNN** memiliki lebih banyak kesalahan dibanding dua model di atas, yaitu 17 kesalahan untuk kelas 0 dan 15 kesalahan untuk kelas 1.
- **SVM** membuat 16 kesalahan pada kelas 0 dan 9 kesalahan pada kelas 1, namun menunjukkan keseimbangan precision-recall yang baik.

### Evaluasi Tambahan: Cross-Validation

| Model             | Mean Accuracy | Standard Deviation |
|-------------------|----------------|---------------------|
| Decision Tree     | 1.0000         | 0.0000              |
| Random Forest     | 1.0000         | 0.0000              |
| KNN               | 0.8478         | 0.0221              |
| SVM               | 0.9063         | 0.0217              |

Hasil evaluasi menggunakan 5-Fold Cross-Validation menunjukkan bahwa:
- **Decision Tree dan Random Forest** memiliki akurasi sempurna pada seluruh fold. Namun, ini menunjukkan potensi **overfitting**, karena model terlalu menyesuaikan diri dengan data pelatihan.
- **KNN dan SVM** menunjukkan akurasi yang lebih realistis dan kemampuan generalisasi yang baik. Di antaranya, **SVM** memiliki **akurasi rata-rata tertinggi** (90,63%) dan variasi antar fold yang rendah, menunjukkan kestabilan model yang lebih baik di data nyata.

---

### Kesimpulan Evaluasi

Meskipun model Decision Tree dan Random Forest menunjukkan akurasi tinggi pada data pelatihan, hasil cross-validation mengindikasikan potensi **overfitting**. Sebaliknya, model **Support Vector Machine (SVM)** menunjukkan keseimbangan terbaik antara akurasi dan kemampuan generalisasi berdasarkan metrik evaluasi dan validasi silang.

> **Dengan demikian, SVM dipilih sebagai model terbaik untuk kasus klasifikasi ini, karena memberikan performa yang tinggi dan stabil tanpa indikasi overfitting.**



