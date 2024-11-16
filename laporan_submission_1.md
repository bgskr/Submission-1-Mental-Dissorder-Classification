# Laporan Proyek Machine Learning - Fadly Fajary Bagaskara

## Domain Proyek

**Latar Belakang:**  
Diagnosis penyakit berbasis gejala merupakan aspek penting dalam pelayanan kesehatan yang bertujuan untuk mendeteksi dini berbagai kondisi medis. Namun, pendekatan tradisional sering kali bergantung pada pengalaman dokter atau akses ke sumber daya kesehatan yang memadai, yang dapat menjadi tantangan di daerah dengan keterbatasan layanan kesehatan.

Salah satu upaya modern untuk mendukung diagnosis berbasis gejala adalah penggunaan teknologi kecerdasan buatan (AI), khususnya dalam bentuk model prediktif berbasis *machine learning*. Dengan data gejala yang terstruktur, model AI dapat membantu dalam mengidentifikasi potensi penyakit dengan cepat dan akurat, memberikan rekomendasi berbasis data kepada tenaga medis [\[1\]](https://link.springer.com/article/10.1007/s12652-021-03612-z). 

Dataset *"Disease and Symptoms"* yang digunakan dalam proyek ini mencakup data gejala berbagai penyakit dan memungkinkan pengembangan model klasifikasi yang mampu memberikan prediksi penyakit berdasarkan data gejala pasien. Pendekatan ini mendukung diagnosis lebih cepat dan berpotensi mengurangi risiko kesalahan diagnosis [\[1\]](https://link.springer.com/article/10.1007/s12652-021-03612-z).

**Mengapa Masalah Ini Penting Diselesaikan:**  
Keterbatasan akses terhadap layanan medis yang memadai dan meningkatnya kebutuhan diagnosis dini merupakan tantangan yang signifikan dalam bidang kesehatan. Dengan solusi berbasis AI, model prediktif dapat:  
1. **Meningkatkan Efisiensi:** Membantu tenaga medis mendiagnosis penyakit dengan lebih cepat [\[1\]](https://link.springer.com/article/10.1007/s12652-021-03612-z).  
2. **Meningkatkan Aksesibilitas:** Memberikan dukungan diagnosis di daerah dengan akses terbatas terhadap dokter spesialis.  
3. **Meningkatkan Akurasi:** Mengurangi risiko kesalahan dalam diagnosis berbasis gejala [\[1\]](https://link.springer.com/article/10.1007/s12652-021-03612-z).

Pendekatan ini memberikan manfaat langsung baik untuk pasien maupun tenaga medis, serta membantu dalam pengembangan sistem kesehatan yang lebih responsif dan berbasis data.

**Referensi Riset:**  
[1] Y. Kumar, A. Koul, R. Singla, dan M. F. Ijaz, "Artificial intelligence in disease diagnosis: a systematic literature review, synthesizing framework and future research agenda," *Journal of Ambient Intelligence and Humanized Computing*, 2021. [\[Online\]](https://link.springer.com/article/10.1007/s12652-021-03612-z). Tersedia: https://link.springer.com/article/10.1007/s12652-021-03612-z

Dengan penggunaan *Disease and Symptoms Dataset*, proyek ini bertujuan untuk mengembangkan model klasifikasi yang mampu mengidentifikasi berbagai penyakit berdasarkan data gejala pasien, sehingga mendukung diagnosis dini dan pengambilan keputusan medis yang lebih baik.  

## Business Understanding

### Problem Statements

Proyek ini bertujuan untuk mengembangkan model prediktif guna mengidentifikasi penyakit berdasarkan data gejala pasien. Berikut adalah beberapa pernyataan masalah utama:

1. **Pernyataan Masalah 1**: Bagaimana model prediktif dapat membantu mengidentifikasi jenis penyakit berdasarkan data gejala yang tersedia secara akurat?  
   
2. **Pernyataan Masalah 2**: Model mana yang terbaik diantara model berikut, KNN, XGBoost, dan RandomForest dalam mengidentifikasi jenis penyakit berdasarkan data gejala yang tersedia?

### Goals
1. Mengembangkan model prediktif yang dapat mengidentifikasi jenis penyakit berdasarkan data gejala pasien secara akurat. Model ini akan digunakan untuk membantu proses diagnosis awal dengan hasil yang dapat diandalkan.  
2. Membandingkan performa model **KNN**, **XGBoost**, dan **Random Forest** untuk menentukan model terbaik dalam mengklasifikasikan jenis penyakit berdasarkan data gejala pasien.  

### Solution Statement
Untuk mencapai tujuan proyek, dilakukan langkah-langkah berikut:  
1. Menggunakan dataset **Diagnosis and Symptoms Dataset** yang berisi data gejala pasien untuk membangun model prediktif. Dataset ini akan dibersihkan dan diproses untuk memastikan kualitas data yang baik sebelum digunakan untuk pemodelan.  
2. Melakukan eksplorasi awal data untuk memahami pola hubungan antar fitur dan kontribusinya terhadap klasifikasi jenis penyakit. Analisis ini melibatkan penggunaan korelasi matriks untuk mengidentifikasi fitur penting dan mengeliminasi fitur yang tidak relevan.  
3. Mengimplementasikan tiga algoritma pembelajaran mesin, yaitu **KNN**, **XGBoost**, dan **Random Forest**, untuk membangun model prediktif.  
4. Melakukan evaluasi performa setiap model menggunakan metrik **akurasi, precision, recall,** dan **F1-score** untuk menentukan model terbaik.  
5. Menggunakan teknik **hyperparameter tuning** untuk meningkatkan kinerja model yang dipilih, sehingga dapat memberikan hasil yang lebih akurat dalam mengidentifikasi jenis penyakit berdasarkan data gejala.  
6. Berdasarkan hasil evaluasi, memilih model dengan performa terbaik yang akan dijadikan solusi utama untuk membantu proses diagnosis penyakit.  
Dengan pendekatan ini, diharapkan model prediktif dapat memberikan hasil yang lebih akurat dan bermanfaat dalam mendukung proses diagnosis dini penyakit berdasarkan gejala pasien, serta memberikan wawasan tambahan bagi tenaga medis.  

## Data Understanding  

Dataset yang digunakan adalah [**Disease and Symptoms Dataset**](https://www.kaggle.com/datasets/choongqianzheng/disease-and-symptoms-dataset) yang bersumber dari [Kaggle](https://www.kaggle.com/datasets/choongqianzheng/disease-and-symptoms-dataset), yang terdiri dari **800+ penyakit unik** dengan **600 gejala berbeda** yang dikelompokkan dalam **18 kolom**. Setiap penyakit memiliki jumlah gejala yang bervariasi, dengan kolom kosong (null) jika suatu gejala tidak relevan untuk penyakit tertentu. Dataset ini tersedia dalam format **CSV** dan dirancang untuk membantu mengidentifikasi dan mengklasifikasi penyakit berdasarkan gejala yang diamati.  

### Informasi Data  

Dataset terdiri dari kolom-kolom berikut:  

1. **Disease**: Nama penyakit yang menjadi target analisis dan prediksi.  
2. **Symptom_1 hingga Symptom_17**:  
   - Kolom ini mewakili gejala-gejala terkait setiap penyakit, dengan gejala pertama hingga gejala ketujuh belas diurutkan berdasarkan relevansi.  
   - Jika suatu penyakit memiliki jumlah gejala lebih sedikit, kolom yang tersisa akan berisi nilai kosong (null).  

### Kondisi Data  

1. **Jumlah Data**:  
   - Dataset ini berisi total **800+ observasi** dan **18 kolom**, termasuk kolom gejala dan label target (Disease).  
   - Terdapat nilai kosong di kolom **Symptom_4 hingga Symptom_17** dengan tren peningkatan jumlah nilai kosong tersebut

## Data Preparation

Pada bagian ini, beberapa teknik *data preparation* diterapkan untuk memastikan data siap digunakan dalam proses pelatihan model *machine learning*. Tahapan yang dilakukan meliputi:

### 1. **Pemilihan Kolom yang Relevan**  
Dataset awal memiliki **18 kolom**, yang mencakup label target (*Disease*) dan 17 kolom gejala (*Symptom_1* hingga *Symptom_17*). Namun, untuk menyederhanakan analisis dan mengurangi kompleksitas model, hanya **3 kolom gejala pertama** (*Symptom_1*, *Symptom_2*, *Symptom_3*) beserta kolom **Disease** yang dipilih untuk digunakan pada tahap berikutnya.  

Alasan memilih hanya kolom tersebut:  
- Gejala awal biasanya lebih dominan dalam mendiagnosis penyakit.  
- Mengurangi dimensi data untuk mempercepat pelatihan model.  

### 2. **Encoding Label untuk Kolom Kategorikal**  
Kolom **Disease** (label target) serta kolom gejala (*Symptom_1*, *Symptom_2*, *Symptom_3*) merupakan data berbentuk teks (*categorical*). Data ini perlu diubah menjadi bentuk numerik menggunakan **Label Encoding**, sehingga model dapat memprosesnya dengan baik.  

Prosesnya adalah sebagai berikut:  
- **Disease**: Setiap nama penyakit diberi representasi numerik unik.  
- **Symptom_1 hingga Symptom_3**: Setiap gejala juga diberi nilai numerik berdasarkan kategori unik yang dimiliki.  

Contoh hasil encoding:  
| Disease     | Symptom_1       | Symptom_2       | Symptom_3       |  
|-------------|-----------------|-----------------|-----------------|  
| Disease_A   | Fever           | Headache        | Nausea          |  
| Disease_B   | Fatigue         | Chills          | None            |  

Setelah encoding:  
| Disease | Symptom_1 | Symptom_2 | Symptom_3 |  
|---------|-----------|-----------|-----------|  
| 0       | 1         | 2         | 3         |  
| 1       | 4         | 5         | 0         |  

### 3. **Imputasi untuk Mengisi Nilai Kosong**  
Nilai kosong (*null*) ditemukan pada beberapa kolom gejala, terutama jika suatu penyakit hanya memiliki sedikit gejala. Nilai kosong ini diisi menggunakan metode **KNN Imputation**, yang memperkirakan nilai berdasarkan kedekatan data lain yang serupa.  

Langkah-langkah imputasi:  
- Mengidentifikasi kolom dengan nilai kosong menggunakan `.isnull().sum()`.  
- Menggunakan algoritma KNN untuk mengisi nilai kosong berdasarkan pola pada data tetangga terdekat.  

### 4. **Pembagian Data**  
Setelah proses *data preparation*, dataset dibagi menjadi dua bagian:  
- **Training set (80%)**: Digunakan untuk melatih model.  
- **Test set (20%)**: Digunakan untuk menguji performa model.  

Metode **train_test_split** dari pustaka Scikit-learn digunakan untuk membagi data secara acak, memastikan distribusi label yang seimbang pada kedua bagian.

### Alasan Perlunya Tahapan Data Preparation  

Proses *data preparation* sangat penting karena:  
1. **Meningkatkan Kualitas Data**: Memastikan data relevan, konsisten, dan bebas dari nilai kosong.  
2. **Memudahkan Proses Pelatihan**: Dengan mengurangi kompleksitas dan mengatur skala data, pelatihan model menjadi lebih cepat.  
3. **Menghindari Kesalahan dalam Pelatihan**: Data yang tidak bersih dapat menyebabkan error selama proses pelatihan.  
4. **Meningkatkan Akurasi Model**: Data yang diproses dengan baik akan membantu model memberikan hasil prediksi yang lebih akurat dan andal.

Melalui tahapan ini, dataset yang digunakan telah disiapkan untuk diolah oleh model *machine learning*, memastikan prediksi yang lebih baik dan akurat.  

## Pengembangan Model

Pada fase ini, tiga model dikembangkan dan dibandingkan untuk mengklasifikasikan data penyakit mental berdasarkan gejala yang tersedia: **K-Nearest Neighbors (KNN)**, **XGBoost Classifier (XGBClassifier)**, dan **Random Forest Classifier (RFC)**. Setiap model disetel menggunakan **GridSearchCV** untuk menemukan hiperparameter yang optimal.

### Tinjauan Model dan Penyelarasan Hyperparameter

1. **KNN (K-Nearest Neighbors)**  
   - **Deskripsi**: KNN mengklasifikasikan data dengan menghitung jarak antara titik data baru dan data pelatihan, kemudian menetapkan kelas berdasarkan kelas mayoritas dari tetangga terdekat.
   - **Penyelarasan Parameter**: Parameter `n_neighbors` disetel dengan nilai [3, 5, 7, 9].

2. **XGBoost Classifier**  
   - **Deskripsi**: XGBoost adalah algoritma boosting yang membangun ensemble dari pohon keputusan untuk meningkatkan kinerja model.
   - **Penyelarasan Parameter**: Parameter berikut disetel:
     - `learning_rate`: [0.01, 0.1, 0.2]
     - `n_estimators`: [100, 200, 300]
     - `max_depth`: [3, 4, 5]

3. **Random Forest Classifier**  
   - **Deskripsi**: RFC adalah metode ensemble yang membangun beberapa pohon keputusan dan merata-rata prediksinya untuk meningkatkan akurasi dan mengurangi overfitting.
   - **Penyelarasan Parameter**: Parameter berikut disetel:
     - `n_estimators`: [100, 200, 300]
     - `max_depth`: [None, 5, 10]
     - `min_samples_split`: [2, 5, 10]

### Pemilihan Model Terbaik

Berdasarkan hasil evaluasi, baik **XGBoost** dan **Random Forest** mencapai akurasi tertinggi (94.92%), presisi (96.98%), recall (94.92%), dan F1-score (94.17%). Namun, **XGBoost** memiliki keunggulan dalam hal penyelarasan parameter, karena membutuhkan lebih sedikit pohon (100) dibandingkan dengan Random Forest (yang juga menggunakan 100 pohon tetapi dengan konfigurasi yang berbeda).

Oleh karena itu, **XGBoost Classifier** dipilih sebagai model terbaik karena kinerjanya yang sedikit lebih tinggi dan konfigurasi parameter yang lebih efisien.

### Kesimpulan

Melalui penggunaan **GridSearchCV**, tiga model dievaluasi dan dibandingkan kemampuannya untuk mengklasifikasikan penyakit berdasarkan dataset yang tersedia. **XGBoost Classifier** berkinerja terbaik, menawarkan akurasi, presisi, recall, dan F1-score tertinggi. Model ini dipilih sebagai model akhir untuk diterapkan, memberikan solusi yang andal untuk mengklasifikasikan penyakit berdasarkan data gejala.

## Evaluation

Setelah mengevaluasi ketiga model, berikut adalah ringkasan kinerjanya:

| Model                | Akurasi  | Presisi  | Recall  | F1-Score | Parameter Terbaik                                                                |
|----------------------|----------|----------|---------|----------|----------------------------------------------------------------------------------|
| **KNN**              | 94.41%   | 96.63%   | 94.41%  | 93.68%   | `{'n_neighbors': 3}`                                                             |
| **XGBoost**          | 94.92%   | 96.98%   | 94.92%  | 94.17%   | `{'learning_rate': 0.1, 'max_depth': 3, 'n_estimators': 100}`                   |
| **Random Forest**    | 94.92%   | 96.98%   | 94.92%  | 94.17%   | `{'max_depth': None, 'min_samples_split': 10, 'n_estimators': 100}`             |

### Analisis Metrik Evaluasi
- **Precision** menunjukkan akurasi model dalam memprediksi tiap kategori dengan benar. Model memberikan nilai precision yang tinggi pada semua kelas, yang berarti kesalahan prediksi pada tiap kelas cukup minim.
- **Recall** mengukur sensitivitas model dalam mendeteksi setiap kelas.
- **F1-score** memberikan keseimbangan antara precision dan recall. Nilai yang tinggi pada semua kelas menunjukkan bahwa model ini efektif dalam mendeteksi kasus dengan tingkat kesalahan yang rendah.

### Dampak  
Hasil dari proyek ini memberikan dampak yang signifikan, terutama dalam meningkatkan efisiensi dan akurasi diagnosis penyakit berdasarkan data gejala pasien. Berikut adalah dampaknya:  

1. **Mendukung proses diagnosis awal yang lebih akurat**  
   - Dengan model prediktif yang dibangun, proses diagnosis dapat dilakukan dengan lebih cepat dan akurat. Hal ini membantu tenaga medis untuk mengidentifikasi jenis penyakit pasien berdasarkan data gejala awal yang tersedia.  
   - Untuk **Pernyataan Masalah 1**, model prediktif yang dihasilkan mampu mengolah data gejala pasien dan memberikan prediksi dengan tingkat akurasi yang tinggi. Hal ini memberikan nilai tambah pada sistem kesehatan dalam memanfaatkan teknologi prediktif.  

2. **Pemilihan model terbaik untuk membantu pengambilan keputusan**  
   - Dalam menjawab **Pernyataan Masalah 2**, evaluasi model menunjukkan bahwa model **XGBoost** memberikan performa terbaik dengan nilai **akurasi, precision, recall,** dan **F1-score** tertinggi. Pemilihan model ini sebagai solusi utama memberikan keyakinan bahwa hasil prediksi yang dihasilkan dapat diandalkan.  
   - Dengan membandingkan tiga model (KNN, XGBoost, dan Random Forest), hasil proyek juga memberikan wawasan bagi pengembang atau pengguna sistem tentang kekuatan dan kelemahan masing-masing algoritma, yang dapat menjadi dasar untuk pengembangan lebih lanjut.  

3. **Peningkatan efisiensi dalam analisis data gejala pasien**  
   - Penggunaan korelasi matriks dalam proses eksplorasi data memberikan pemahaman lebih mendalam tentang hubungan antar fitur gejala. Hasil ini memungkinkan pengurangan dimensi data tanpa kehilangan informasi penting, sehingga proses analisis menjadi lebih cepat dan efisien.  

4. **Kontribusi terhadap sistem kesehatan berbasis data**  
   - Model ini dapat diintegrasikan ke dalam sistem kesehatan berbasis data untuk mendukung tenaga medis dalam pengambilan keputusan. Dampaknya mencakup peningkatan kepercayaan terhadap teknologi prediktif dalam bidang kesehatan, terutama dalam membantu diagnosis penyakit secara efisien.  

5. **Dasar untuk pengembangan di masa depan**  
   - Meskipun model saat ini sudah memberikan hasil yang baik, proyek ini membuka peluang untuk pengembangan lebih lanjut, seperti menambahkan data baru, menggunakan algoritma lain, atau mengaplikasikan model ini ke dataset yang lebih luas dan beragam untuk mendukung aplikasi di skala yang lebih besar.  
