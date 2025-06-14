# Laporan Proyek Machine Learning - Muhammad Muttakin

## Domain Proyek

Dalam era digital yang terus berkembang, jumlah buku yang tersedia secara daring meningkat secara signifikan setiap tahunnya. Hal ini diperkuat oleh data dari International Publishers Association (IPA, 2022) yang mencatat pertumbuhan signifikan dalam penerbitan buku, baik dalam format cetak maupun digital. Pertumbuhan ini memberikan tantangan tersendiri bagi pembaca, yaitu kesulitan dalam menemukan buku yang sesuai dengan minat, kebutuhan, atau preferensi mereka secara efisien dan tepat sasaran.

Untuk menjawab tantangan tersebut, sistem rekomendasi buku menjadi salah satu solusi yang semakin relevan dan penting. Sistem ini bekerja dengan menganalisis data pengguna dan menawarkan rekomendasi bacaan yang dipersonalisasi. Platform besar seperti Amazon dan Goodreads telah lama mengandalkan sistem rekomendasi untuk meningkatkan pengalaman pengguna dan mendorong keterlibatan yang lebih besar (Zhang et al., 2021). Dalam konteks literasi digital dan pembelajaran, sistem ini juga terbukti mampu meningkatkan minat baca dan akses terhadap sumber informasi yang lebih luas (Lee & Chen, 2020).

Berbagai pendekatan dalam pengembangan sistem rekomendasi telah diperkenalkan, mulai dari content-based filtering yang menganalisis karakteristik buku, hingga collaborative filtering yang memanfaatkan perilaku pengguna lain sebagai dasar rekomendasi. Pendekatan hibrida yang menggabungkan keduanya juga menunjukkan hasil yang lebih akurat dalam berbagai studi terkini (Khan et al., 2021). Dengan berkembangnya teknologi machine learning dan kecerdasan buatan, sistem rekomendasi kini mampu belajar dan menyesuaikan 
diri dengan pola dan preferensi pengguna yang kompleks.

Oleh karena itu, proyek ini bertujuan untuk merancang dan mengimplementasikan sistem rekomendasi buku yang adaptif dan cerdas, guna membantu pengguna dalam menemukan buku yang relevan secara efisien. Pengembangan sistem ini diharapkan tidak hanya meningkatkan pengalaman pengguna, tetapi juga berkontribusi pada peningkatan budaya literasi di era digital.

## Business Understanding

Dalam era digital yang dipenuhi oleh limpahan informasi, pengguna dihadapkan pada tantangan dalam memilih buku yang sesuai dengan preferensi mereka. Banyaknya pilihan buku di platform digital membuat proses pencarian menjadi tidak efisien dan terkadang membuat pengguna melewatkan buku yang sebenarnya relevan atau menarik. Selain itu, pengguna 
baru yang belum memiliki riwayat interaksi di platform akan kesulitan mendapatkan rekomendasi yang sesuai karena tidak adanya data awal yang bisa digunakan sistem.

Penyedia layanan digital seperti toko buku online, perpustakaan digital, dan aplikasi pembaca membutuhkan sistem yang mampu merekomendasikan buku secara otomatis, akurat, dan personal. Untuk itu, diperlukan pendekatan sistematis untuk membangun sistem rekomendasi buku yang mampu mengatasi keterbatasan dalam pencarian manual serta meningkatkan pengalaman pengguna secara keseluruhan.

---

### Problem Statements

1. Bagaimana cara membantu pengguna menemukan buku yang relevan dengan minat mereka tanpa harus menelusuri seluruh katalog secara manual?
2. Bagaimana membangun sistem rekomendasi yang tetap efektif meskipun pengguna baru belum memiliki riwayat aktivitas?

---

## Goals (Tujuan)

1. Membangun sistem rekomendasi buku yang mampu memberikan rekomendasi yang relevan dan dipersonalisasi berdasarkan preferensi pengguna.
2. Meningkatkan efisiensi pencarian buku dan kepuasan pengguna dalam memilih bacaan.

---

## Solution Approach

Untuk mencapai tujuan tersebut, proyek ini mengusulkan dua pendekatan solusi berikut:

### 1. Content-Based Filtering

Pendekatan ini merekomendasikan buku berdasarkan kemiripan konten antara buku-buku yang pernah disukai pengguna dengan buku-buku lainnya. Fitur yang digunakan bisa berupa genre, penulis, sinopsis, atau kata kunci. Sistem ini membangun profil pengguna berdasarkan karakteristik buku yang pernah mereka beri rating tinggi atau sukai.

**Keunggulan:**
- Tidak tergantung pada aktivitas pengguna lain.
- Tetap efektif meskipun pengguna masih baru.

**Kelemahan:**
- Rekomendasi cenderung terbatas pada jenis buku yang serupa (terjebak dalam "filter bubble").

### 2. Collaborative Filtering

Pendekatan ini memberikan rekomendasi berdasarkan perilaku pengguna lain yang memiliki preferensi serupa. Jika dua pengguna menyukai buku yang sama, maka sistem akan merekomendasikan buku lain yang dibaca oleh salah satu dari mereka.

**Keunggulan:**
- Mampu menemukan buku baru di luar preferensi awal pengguna.
- Cocok untuk menemukan pola dari komunitas pengguna.

**Kelemahan:**
- Memerlukan data interaksi yang cukup banyak (ratings, ulasan, histori pembelian).
- Mengalami masalah cold-start untuk pengguna baru atau buku baru.

---

# Data Understanding

Dataset yang digunakan dalam proyek ini diambil dari platform Kaggle dan berjudul **“Best Books 10k - Multi-Genre Data”**. Dataset ini bersumber dari Goodreads dan berisi informasi seputar lebih dari 10.000 buku yang mencakup berbagai genre. Dataset ini dapat diakses melalui tautan berikut:  
[Kaggle - Best Books 10k Dataset](https://www.kaggle.com/datasets/ishikajohari/best-books-10k-multi-genre-data)

Dataset ini sangat relevan untuk membangun sistem rekomendasi karena memuat data deskriptif, kategori (genre), serta penilaian pengguna yang dapat dimanfaatkan dalam pendekatan **content-based filtering**, **collaborative filtering**, maupun pendekatan hibrida.

---

## Variabel-variabel dalam Dataset:

Berikut adalah penjelasan setiap fitur atau kolom dalam dataset `goodreads_data.csv`:

- **Unnamed: 0**  
  Merupakan indeks baris yang secara otomatis tersimpan saat dataset diekspor ke CSV dari pandas dengan parameter `index=True`. Kolom ini berisi urutan angka (biasanya dari 0 atau 1 ke atas) dan tidak membawa informasi penting terkait data buku. Urutan ini nantinya akan digunakan sebagai user_id.

- **Book**  
  Nama buku. Dalam beberapa kasus, nama ini juga mencakup informasi tentang seri buku di dalam tanda kurung. Informasi ini dapat diekstrak lebih lanjut untuk analisis seri buku.

- **Author**  
  Nama penulis dari buku yang bersangkutan.

- **Description**  
  Deskripsi buku sebagaimana tercantum di Goodreads. Kolom ini merupakan fitur penting untuk analisis berbasis konten (*content-based filtering*) karena berisi kata kunci dan ringkasan isi buku.

- **Genres**  
  Daftar genre yang diklasifikasikan oleh pengguna Goodreads. Genre bersifat multikategori (multi-label), sehingga cocok digunakan untuk klasifikasi multi-label, rekomendasi berbasis konten, atau klasterisasi.

- **Average Rating**  
  Nilai rata-rata (dari skala 5) yang diberikan oleh pengguna Goodreads terhadap buku tersebut. Nilai ini dapat dimanfaatkan sebagai indikator popularitas atau kualitas dalam pendekatan rekomendasi.

- **Number of Ratings**  
  Jumlah pengguna yang memberikan rating. Perlu dicatat bahwa ini berbeda dari jumlah ulasan (*reviews*). Fitur ini bisa digunakan sebagai bobot atau skor kepercayaan dalam model kolaboratif.

- **URL**  
  Tautan menuju halaman detail buku di Goodreads. Meskipun tidak digunakan dalam proses pemodelan, URL ini berguna untuk validasi manual dan penyajian hasil.


# Exploratory Data Analysis (EDA)

Tahapan EDA bertujuan untuk memahami struktur, kualitas, dan karakteristik dari dataset yang akan digunakan untuk membangun sistem rekomendasi buku.

---

## 1. Struktur Dataset

- **Jumlah baris (entri)**: 10.000
- **Jumlah kolom (fitur)**: 8

Setelah menghapus baris dengan nilai kosong di kolom `Description`, jumlah baris menjadi:

- **Shape setelah penghapusan missing values**: 9.923 baris × 8 kolom

---

## 2. Cek Nilai Kosong (Missing Values)

| Kolom        | Missing Values |
|--------------|----------------|
| Unnamed: 0   | 0              |
| Book         | 0              |
| Author       | 0              |
| Description  | 77             |
| Genres       | 0              |
| Avg_Rating   | 0              |
| Num_Ratings  | 0              |
| URL          | 0              |

> Sebanyak **77** entri tidak memiliki deskripsi buku. Karena `Description` merupakan fitur penting dalam analisis berbasis konten, baris-baris ini dihapus agar tidak memengaruhi hasil model.

---

## 3. Duplikasi

- **Jumlah baris duplikat**: 0  
  Dataset tidak mengandung baris yang terduplikasi.

---

## 4. Statistik Deskriptif Kolom Numerik

| Statistik     | Unnamed: 0 | Avg_Rating |
|---------------|-------------|------------|
| count         | 9.923       | 9.923      |
| mean          | 4.985       | 4.067      |
| std (deviasi) | 2.883       | 0.332      |
| min           | 0           | 0.0        |
| 25%           | 2.487       | 3.88       |
| 50% (median)  | 4.983       | 4.07       |
| 75%           | 7.481       | 4.26       |
| max           | 9.999       | 5.0        |

> Distribusi `Avg_Rating` memperlihatkan bahwa sebagian besar buku memiliki rating antara 3.8–4.3, yang mengindikasikan **bias positif** dari pengguna Goodreads.

---

## 5. Visualisasi Distribusi Rating

![image](https://github.com/user-attachments/assets/1df5600d-18d9-48bd-8063-b7e542df31e2)


- Rating rata-rata buku menunjukkan **distribusi normal miring ke kiri**, dengan puncaknya antara 4.0 dan 4.3.
- Sangat sedikit buku yang diberi rating di bawah 3.0, menegaskan adanya preferensi pengguna terhadap memberikan rating tinggi.

---

## 6. Visualisasi Genre Populer

![image](https://github.com/user-attachments/assets/dd8dbf50-0e75-44f7-ba8a-1333de09ebad)


- Genre terbanyak dalam dataset adalah:
  1. Fiction
  2. Nonfiction
  3. Fantasy
  4. Classics
  5. Romance

- Distribusi genre menunjukkan **dominasi genre fiksi**, namun juga mencakup variasi genre seperti `Biography`, `Self Help`, dan `Science Fiction`, yang penting untuk segmentasi pengguna dan personalisasi rekomendasi.

---

## 7. Insight Penting dari EDA

- Dataset relatif bersih dan tidak memerlukan banyak pembersihan.
- Rating rata-rata cenderung tinggi; model perlu memperhatikan potensi **skew**.
- Genre dan deskripsi memberikan informasi penting untuk digunakan dalam pendekatan **content-based filtering**.
- Variasi genre mendukung pengembangan sistem rekomendasi yang adaptif terhadap berbagai minat pembaca.

## 📦 Data Preparation

Tahapan persiapan data dilakukan untuk memastikan bahwa data bersih, relevan, dan siap digunakan dalam proses pemodelan. Beberapa langkah tambahan yang penting namun belum dijelaskan secara eksplisit sebelumnya juga ditambahkan di sini.

---

### 0. Pengolahan Awal Dataset

- **Menghapus Nilai Kosong**  
  Baris dengan nilai kosong, khususnya pada kolom deskripsi, dihapus menggunakan `dropna()` untuk menjaga kualitas data input, terutama pada model berbasis konten.

- **Mengganti Nama Kolom Unnamed: 0**  
  Kolom ini merupakan indeks lama yang tersimpan saat ekspor dari pandas. Diubah namanya menjadi `'userid'` agar lebih deskriptif dan memudahkan dalam pengolahan selanjutnya.

---

### 1. Handling Missing Values

Data dengan nilai kosong pada kolom penting seperti `description`, `userid`, atau `rating` dihapus untuk memastikan kualitas data tetap terjaga.

---

### 2. Inisialisasi Stopwords dan Stemming

Langkah awal dilakukan dengan menyiapkan daftar stopwords dan alat untuk stemming:

- **Stopwords**: Menggunakan daftar stopwords Bahasa Inggris dari NLTK, serta menambahkan stopwords khusus seperti *book*, *author*, *read*, dll.
- **Stemming**: Menggunakan `PorterStemmer` dari NLTK untuk mengubah kata ke bentuk dasarnya.

---

### 3. Preprocessing Teks

Proses pembersihan teks dilakukan melalui beberapa tahapan berikut:

1. **Lowercasing**: Mengubah semua huruf menjadi huruf kecil.
2. **Pembersihan tanda baca dan angka**: Menghapus karakter non-alfabet seperti tanda baca dan angka.
3. **Tokenisasi**: Memecah teks menjadi kata-kata individual.
4. **Stopword removal**: Menghapus kata-kata umum yang tidak memiliki makna khusus.
5. **Stemming**: Mengubah kata ke bentuk dasar menggunakan `PorterStemmer`.
6. **Whitespace cleaning**: Menghapus spasi ganda atau tidak diperlukan.

> Tujuan preprocessing adalah menyederhanakan dan menstandarkan data teks agar lebih relevan dan informatif dalam analisis selanjutnya.

---

### 4. Pembentukan dan Visualisasi N-Gram

Setelah data dibersihkan, dilakukan pembentukan **n-gram** menggunakan `TfidfVectorizer`:

- **Bigram** (`ngram_range=(2,2)`): Kombinasi dua kata berurutan.
- **Trigram** (`ngram_range=(3,3)`): Kombinasi tiga kata berurutan.

![Bigram](https://github.com/user-attachments/assets/4fb29dad-dabb-4749-a663-9e0f33cbe4c4)

Hasil bigram dan trigram dengan skor tertinggi divisualisasikan menggunakan barplot. Beberapa temuan populer:

- **Bigram**: *new york*, *york time*, *best friend*
- **Trigram**: *new york time*, *york time bestsel*, *altern cover edit*

![Trigram](https://github.com/user-attachments/assets/6b86cc63-3e39-40ad-adcb-34f457048a52)

> Visualisasi ini membantu mengidentifikasi frasa penting yang sering muncul dalam deskripsi buku.

---

### 5. Penanganan Duplikat Rating

Data rating diperiksa untuk mendeteksi pasangan `userid` dan `Book` yang duplikat:

- Jika ditemukan duplikat, rating untuk pasangan tersebut dirata-ratakan menggunakan `groupby` dan `mean`.
- Hal ini penting untuk menjaga kualitas data sebelum digunakan dalam model rekomendasi.

---

### 6. Word Cloud

Untuk memberikan gambaran umum tentang kata-kata yang sering digunakan dalam deskripsi, dibuat **word cloud** dari seluruh `cleaned_description`.

- Kata-kata seperti: *life*, *love*, *world*, *power*, *make*, dan *one* menjadi dominan.
- Ini menunjukkan tema umum yang muncul dalam koleksi buku.

![Word Cloud](https://github.com/user-attachments/assets/d7f22986-2d23-4056-b716-ca4b213afac2)

---

### 7. Persiapan Data untuk Surprise

Data untuk model Collaborative Filtering disiapkan menggunakan `Reader` dan `Dataset.load_from_df` dari library Surprise, yang membutuhkan format khusus: `(user, item, rating)`.

---

### 8. Split Data Latih dan Uji

Data rating dibagi menjadi data latih dan data uji menggunakan `train_test_split` dari Surprise untuk keperluan evaluasi model.


## 📊 Modeling

Tahapan ini menjelaskan model machine learning yang digunakan, parameter, kelebihan, kekurangan, serta evaluasi untuk memilih model terbaik.

---

### 1. 🔁 User-Based Collaborative Filtering (UBCF)

#### 📌 Deskripsi
Model ini menggunakan pendekatan Collaborative Filtering berbasis pengguna (user-based) dengan algoritma K-Nearest Neighbors (KNN) dari pustaka Surprise. Sistem akan merekomendasikan buku kepada pengguna berdasarkan kesamaan preferensi pengguna lain yang mirip.

#### ⚙️ Parameter Utama
- `user_based=True` dalam `sim_options`, yang mengarahkan KNN untuk menghitung kemiripan antar pengguna.
- Skala rating: 1–5.

#### ✅ Kelebihan
- Rekomendasi menjadi personal karena mempertimbangkan kesamaan antar pengguna.
- Tidak membutuhkan data konten buku (metadata).

#### ❌ Kekurangan
- Rentan terhadap masalah cold-start, khususnya bagi pengguna baru yang belum memberikan rating.
- Performa menurun jika data terlalu sparse (banyak nilai kosong).

---

### 🔎 Result (Hasil Rekomendasi dan Evaluasi Model)

#### User-Based Recommendations for user 3835:
Berikut adalah daftar rekomendasi buku untuk pengguna dengan ID 3835 berdasarkan User-Based Collaborative Filtering:

1. **To Kill a Mockingbird** (predicted rating: 4.07)  
2. **Harry Potter and the Philosopher’s Stone (Harry Potter, #1)** (predicted rating: 4.07)  
3. **Pride and Prejudice** (predicted rating: 4.07)  
4. **The Diary of a Young Girl** (predicted rating: 4.07)  
5. **Animal Farm** (predicted rating: 4.07)  

Model memprediksi rating pengguna terhadap buku-buku tersebut cukup tinggi, menandakan potensi minat yang besar.

---

## Evaluasi Model Sistem Rekomendasi

### Evaluasi Collaborative Filtering (User-Based)

Model Collaborative Filtering yang digunakan adalah User-Based Collaborative Filtering dengan algoritma KNN. Evaluasi model ini menggunakan metrik kuantitatif sebagai berikut:

- **Root Mean Squared Error (RMSE):** 0.3542  
  RMSE mengukur rata-rata selisih kuadrat antara rating asli dan rating prediksi. Nilai yang lebih kecil menunjukkan prediksi yang lebih akurat.

- **Mean Absolute Error (MAE):** 0.2463  
  MAE mengukur rata-rata selisih absolut antara rating asli dan rating prediksi, memberikan gambaran kesalahan prediksi secara langsung.

**Kesimpulan:**  
Nilai RMSE dan MAE yang rendah menunjukkan model User-Based Collaborative Filtering dapat memprediksi rating pengguna dengan cukup baik, sehingga dapat memberikan rekomendasi yang relevan berdasarkan pola rating pengguna lain yang mirip.

---

### Kesimpulan Evaluasi

- **Collaborative Filtering** unggul dalam memberikan rekomendasi berdasarkan pola rating pengguna lain yang mirip, dengan bukti numerik akurasi prediksi yang baik melalui RMSE dan MAE.
- Kombinasi metode berbasis pengguna dan pendekatan lainnya dapat meningkatkan kualitas rekomendasi, terutama untuk kasus pengguna baru atau data sparsity.




### References:

International Publishers Association. (2022). Global publishing statistics. https://www.internationalpublishers.org

Khan, M. A., Nazir, M., & Bashir, A. K. (2021). A hybrid recommendation system for books using machine learning. Expert Systems with Applications, 168, 114481. https://doi.org/10.1016/j.eswa.2020.114481 

Lee, C.-Y., & Chen, Y.-L. (2020). Personalized book recommendation using a deep learning approach. Information Processing & Management, 57(5), 102321. https://doi.org/10.1016/j.ipm.2020.102321

Zhang, Y., Zhao, H., & Zheng, Y. (2021). A survey on recommendation systems in the book domain. Artificial Intelligence Review, 54, 243–273. https://doi.org/10.1007/s10462-020-09827-9
