# Laporan Proyek Machine Learning - Fadly Fajary Bagaskara

## Domain Proyek

**Latar Belakang:**
Kesehatan mental menjadi isu yang semakin mendapat perhatian global karena pengaruhnya yang signifikan terhadap kualitas hidup dan produktivitas seseorang. Penyakit mental, seperti depresi, gangguan bipolar, dan kecemasan, seringkali sulit didiagnosis karena gejalanya dapat bervariasi dan tumpang tindih satu sama lain. Akibatnya, diagnosis yang tepat membutuhkan waktu dan ketelitian yang tinggi dari pihak tenaga medis. Dengan teknologi analitik prediktif, diagnosis awal dapat dipermudah dan dipercepatan dengan bantuan model klasifikasi yang dapat mengidentifikasi gangguan mental berdasarkan pola-pola yang terdeteksi dari data gejala pasien.

**Mengapa Masalah Ini Penting Diselesaikan:**
Mendeteksi gangguan mental secara dini berpotensi mencegah perburukan kondisi pasien serta memudahkan intervensi yang lebih cepat dan tepat. Sebuah sistem prediktif berbasis model klasifikasi dapat membantu profesional medis dalam menilai gejala pasien dan memberikan wawasan tambahan untuk diagnosis awal. Hal ini terutama penting di daerah atau fasilitas kesehatan dengan keterbatasan sumber daya, di mana model ini dapat memberikan dukungan praktis dalam penyaringan awal pasien.

**Referensi Riset:**
- World Health Organization (WHO). (2019). *Depression and Other Common Mental Disorders: Global Health Estimates*. [WHO Report](https://www.who.int/news-room/fact-sheets/detail/depression).
  
- National Institute of Mental Health (NIMH). (2021). *Mental Illness*. [NIMH Information](https://www.nimh.nih.gov/health/statistics/mental-illness.shtml).

Dengan pendekatan berbasis data menggunakan *dataset mental disorder classification* dari Kaggle, proyek ini bertujuan untuk mengembangkan model klasifikasi gangguan mental yang dapat membantu dalam memberikan rekomendasi awal kepada tenaga medis, sehingga mereka dapat lebih efisien dalam proses penanganan dan perawatan pasien.

## Business Understanding

### Problem Statements

Proyek ini bertujuan untuk mengembangkan model klasifikasi guna mendeteksi gangguan mental seperti depresi dan gangguan bipolar dengan bantuan data gejala. Berikut adalah beberapa pernyataan masalah yang menjadi fokus:

1. **Pernyataan Masalah 1**: Bagaimana model dapat membantu mengidentifikasi jenis gangguan mental pada pasien berdasarkan data gejala?
   
2. **Pernyataan Masalah 2**: Apa saja fitur atau gejala utama yang paling signifikan dalam menentukan jenis gangguan mental?

3. **Pernyataan Masalah 3**: Bagaimana akurasi model klasifikasi ini dapat dioptimalkan agar hasil prediksinya dapat diandalkan dalam skala besar?

### Goals

Tujuan dari pernyataan masalah di atas adalah sebagai berikut:

- **Jawaban Pernyataan Masalah 1**: Membangun model prediktif yang dapat mengklasifikasikan jenis gangguan mental dengan tingkat akurasi tinggi menggunakan data gejala dari pasien.
  
- **Jawaban Pernyataan Masalah 2**: Mengidentifikasi fitur-fitur yang memiliki kontribusi terbesar dalam diagnosis gangguan mental, sehingga bisa memberikan insight lebih lanjut untuk keperluan medis.
  
- **Jawaban Pernyataan Masalah 3**: Mengoptimalkan performa model melalui teknik augmentasi data untuk memastikan model memiliki akurasi yang tinggi dan dapat digunakan di berbagai kondisi klinis.

### Solution Statements

Untuk mencapai tujuan di atas, langkah-langkah solusi yang diambil meliputi:

1. **Solusi 1**: Menggunakan algoritma K-Nearest Neighbors (KNN) sebagai model utama untuk klasifikasi gangguan mental. Model ini dipilih karena kesederhanaannya dan kemampuannya dalam menangani data dengan banyak fitur.

2. **Solusi 2**: Meningkatkan kualitas data melalui augmentasi menggunakan teknik SMOTE untuk menyeimbangkan data antar kelas. Dengan data yang lebih seimbang, diharapkan model dapat mengenali pola setiap kelas dengan lebih baik.

3. **Solusi 3**: Melakukan evaluasi model dengan menggunakan metrik akurasi, presisi, recall, dan F1-score untuk memastikan bahwa model yang dihasilkan tidak hanya akurat tetapi juga dapat diandalkan dalam konteks medis. Metrik ini akan memberikan gambaran yang jelas tentang performa model dalam melakukan klasifikasi gangguan mental.

Dengan langkah-langkah ini, diharapkan model klasifikasi yang dikembangkan dapat memberikan kontribusi dalam mendeteksi gangguan mental secara lebih efektif dan efisien.

## Data Understanding

Dataset ini berisi data dari **120 pasien psikologi** yang terdiri dari **17 gejala esensial** yang digunakan untuk mendiagnosis beberapa kondisi mental: **Bipolar Mania Disorder**, **Bipolar Depressive Disorder**, **Major Depressive Disorder**, dan individu **Normal**. Dataset ini tersedia dalam format **CSV** dan dapat diakses melalui [Kaggle](https://www.kaggle.com/datasets/cid007/mental-disorder-classification).

### Informasi Data
Dataset ini mencakup gejala perilaku utama yang digunakan oleh psikiater untuk mendiagnosis gangguan yang disebutkan. Gejala-gejala ini meliputi:

1. **Patient Number**: Nomor unik yang berfungsi sebagai identitas untuk setiap pasien. Kolom ini adalah nilai nominal yang tidak akan digunakan dalam analisis prediktif, namun penting untuk identifikasi data.
  
2. **Sadness**: Mengukur tingkat kesedihan yang dirasakan pasien.

3. **Euphoric**: Menggambarkan tingkat perasaan euforia atau kebahagiaan ekstrem. Data ini dapat membantu menganalisis pola suasana hati yang berfluktuasi.

4. **Exhausted**: Mengukur frekuensi pasien merasa kelelahan. Nilai dalam kolom ini menunjukkan tingkat energi fisik atau mental dan bisa menjadi indikasi dari kondisi kesehatan mental.

5. **Sleep Disorder**: Menunjukkan apakah pasien memiliki gangguan tidur, seperti insomnia atau gangguan tidur lainnya. Kondisi ini sangat terkait dengan kesehatan mental.

6. **Mood Swing**: Mencatat ada atau tidaknya perubahan suasana hati yang ekstrim pada pasien, yang mungkin menunjukkan kondisi seperti bipolar atau depresi.

7. **Suicidal Thoughts**: Kolom ini mencatat ada atau tidaknya pikiran bunuh diri pada pasien. Ini merupakan indikator yang sangat penting dalam menilai tingkat risiko pasien terkait masalah kesehatan mental.

8. **Anorexia**: Mencatat apakah pasien menunjukkan tanda-tanda anoreksia atau gangguan makan lainnya, yang seringkali berhubungan dengan kondisi psikologis tertentu.

9. **Authority Respect**: Mengukur apakah pasien memiliki tingkat hormat terhadap otoritas. Ini dapat menjadi indikator dari aspek kepribadian yang mungkin relevan dalam analisis kesehatan mental.

10. **Try-Explanation**: Menunjukkan seberapa sering pasien mencoba memberikan penjelasan atas perilaku atau tindakan mereka, yang bisa memberikan wawasan tentang kecenderungan mereka untuk merefleksikan atau memahami diri mereka sendiri.

11. **Aggressive Response**: Menilai respons agresif yang mungkin ditunjukkan oleh pasien dalam situasi tertentu, yang bisa menjadi tanda dari gangguan emosi atau kontrol impuls.

12. **Ignore & Move-On**: Menunjukkan kecenderungan pasien untuk mengabaikan masalah dan melanjutkan hidup, yang mungkin relevan dalam konteks mekanisme koping (coping mechanisms).

13. **Nervous Break-down**: Mencatat ada atau tidaknya kecenderungan pasien untuk mengalami gangguan saraf atau kepanikan, yang dapat menjadi tanda kondisi kecemasan.

14. **Admit Mistakes**: Menunjukkan apakah pasien cenderung mengakui kesalahan mereka, yang bisa memberikan gambaran tentang aspek-aspek tertentu dari kepribadian atau kesehatan mental mereka.

15. **Overthinking**: Mengukur tingkat kecenderungan untuk berpikir berlebihan yang sering kali dikaitkan dengan kondisi kecemasan dan depresi.

16. **Sexual Activity**: Menunjukkan tingkat aktivitas seksual pasien, yang dapat berfungsi sebagai indikator dari pola perilaku tertentu atau kondisi mental.

17. **Concentration**: Menilai kemampuan pasien untuk berkonsentrasi. Konsentrasi yang rendah dapat menjadi gejala dari gangguan mental seperti depresi atau ADHD.

18. **Optimism**: Menunjukkan tingkat optimisme pasien dalam kehidupan mereka, yang berperan sebagai indikator kesejahteraan mental secara umum.

19. **Expert Diagnose**: Kolom ini adalah diagnosis akhir dari ahli mengenai kondisi mental pasien, seperti Bipolar Type-1, Bipolar Type-2, Depresi, atau Normal. Kolom ini berfungsi sebagai variabel target dalam analisis prediktif kita.  

Untuk kolom 2-5 memiliki data kategorikal dengan nilai:
*   Seldom
*   Sometimes
*   Usually
*   Most-Often


Untuk kolom 6-15 memiliki data dalam bentuk boolean yaitu YES dan NO  
Untuk kolom 16-18 memiliki data dengan bentuk scoring, seperti 4 dari 10  
Dan kolom terakhir merupakan data dengan bentuk kategorikal dengan nilai sebagai berikut:
*   Bipolar Type-1
*   Bipolar Type-2
*   Depression
*   Normal  
  
Setiap fitur ini dirancang untuk memberikan gambaran menyeluruh tentang kondisi mental pasien dan merupakan aspek-aspek penting yang digunakan dalam pemodelan prediksi.
### Kondisi Data
Dataset ini tidak mengandung **nilai hilang** atau **nilai duplikat**, sehingga dapat langsung digunakan dalam analisis. Namun, dengan jumlah yang begitu sedikit,perlu ditambahkan proses augmentasi untuk memperkaya variasi data pelatihan sehingga mampu meningkatkan performa model yang dibuat.

## Data Preparation

Pada bagian ini, beberapa teknik data preparation diterapkan untuk memastikan data siap digunakan dalam model machine learning. Tahapan yang dilakukan meliputi:
1. **Jumlah Nilai Setiap Kolom**
   - Menghitung jumlah nilai pada setiap kolom dengan melakukan perulangan dan memanfaatkan fungsi values_count(). Didapati bahwa terdapat satu value pada kolom "Suicidal Thoughts" yang memiliki nilai sama namun dianggap sebagai nilai yang unik. Dengan asumsi terdapat _whitespace_ pada nilai tersebut,maka akan dilakukan pergantian nilai agar sesuai dan terhitung sebagai satu nilai yang sudah ada (mirip), yaitu nilai YES.

3. **Penghapusan Kolom yang Tidak Relevan**:
   - Menghapus kolom **Patient Number** karena kolom ini tidak memberikan informasi yang relevan untuk analisis dan hanya berfungsi sebagai identifikasi unik. Menghapus fitur yang tidak diperlukan dapat membantu mengurangi kompleksitas model dan meningkatkan performa.

4. **Mengganti Nama Kolom**
   - Nama kolom diubah ke format `snake_case` untuk konsistensi dan mempermudah akses data. Proses penggantian dilakukan dengan menggunakan fungsi `replace` untuk mengganti simbol-simbol atau spasi dengan tanda underscore (`_`). Misalnya, kolom dengan nama `Sleep Disorder` diubah menjadi `sleep_disorder`. Langkah ini meningkatkan keterbacaan dan menjaga format penamaan agar lebih sesuai dengan standar Python.
     
5. **Kategorisasi Variabel Kategorikal**:
   - Mengubah variabel kategorikal menjadi representasi numerik menggunakan **Label Encoding** untuk kolom **Expert Diagnose**. Proses ini diperlukan agar model dapat memahami data dalam bentuk numerik, karena banyak algoritma machine learning hanya dapat bekerja dengan data numerik.

6. **Normalisasi atau Standarisasi**:
   - Menerapkan **StandardScaler** untuk menormalkan fitur numerik. Standarisasi diperlukan agar semua fitur berada pada skala yang sama, yang membantu dalam mempercepat proses pelatihan dan meningkatkan konvergensi model.

7. **Augmentasi Data**:
   - Menerapkan teknik **SMOTE (Synthetic Minority Over-sampling Technique)** untuk menyeimbangkan kelas pada target variabel. Ini penting dilakukan mengingat dataset awal memiliki ketidakseimbangan kelas yang signifikan, yang dapat menyebabkan model bias. Dengan augmentasi, kita mendapatkan dataset yang lebih seimbang yang dapat meningkatkan akurasi model.

8. **PCA (Principal Component Analysis)**:
   - Menggunakan PCA untuk mereduksi dimensi dataset dengan mempertahankan 90% varians. Proses ini membantu mengurangi kompleksitas data dan menghilangkan noise yang tidak perlu, sehingga meningkatkan efisiensi pelatihan model.

9. **Pembagian Data**:
   - Dataset dibagi menjadi dua bagian: training set (80%) dan test set (20%) menggunakan metode **train_test_split**. Pembagian ini penting untuk menguji kinerja model setelah dilatih.
     
### Alasan Perlunya Tahapan Data Preparation

Proses data preparation sangat penting dalam pengembangan model machine learning karena:

- **Meningkatkan Kualitas Data**: Memastikan bahwa data bersih, konsisten, dan relevan, yang sangat mempengaruhi performa model.
- **Menghindari Kesalahan dalam Pelatihan**: Dengan menyiapkan data yang valid, model dapat dilatih dengan baik tanpa risiko mengalami error saat pelatihan.
- **Memudahkan Proses Pelatihan**: Dengan menormalkan data dan mereduksi dimensi, model dapat belajar lebih cepat dan lebih efektif.
- **Meningkatkan Akurasi Model**: Dengan menyeimbangkan kelas dan mempersiapkan data dengan benar, model cenderung memberikan hasil yang lebih akurat dan dapat diandalkan dalam prediksi.

Melalui tahapan ini, kita dapat memastikan bahwa data yang digunakan dalam model machine learning siap untuk dianalisis dan menghasilkan prediksi yang akurat.

## Model Development

Pada tahap ini, model K-Nearest Neighbors (KNN) digunakan untuk klasifikasi data mental illness. KNN bekerja dengan menentukan jarak antara data baru dan titik data yang ada dalam dataset pelatihan, lalu menentukan kelas dari data baru berdasarkan mayoritas kelas dari tetangga terdekatnya. 

Model ini dikonfigurasi dengan parameter `n_neighbors=3`, artinya model mempertimbangkan tiga tetangga terdekat saat menentukan kelas untuk data baru. Setelah pelatihan model pada dataset `X_train` dan `y_train`, model ini dievaluasi pada `X_test`, dan hasil prediksi dibandingkan dengan nilai asli (`y_test`) untuk menghitung akurasi dan laporan klasifikasi yang mencakup metrik seperti precision, recall, dan F1-score.

### Alur Kerja Model KNN

1. **Pengukuran Jarak:** Menghitung jarak antara data uji dan setiap titik data pelatihan.
2. **Pemilihan Tetangga Terdekat:** Memilih tiga titik data terdekat (berdasarkan `n_neighbors=3`).
3. **Klasifikasi Berdasarkan Mayoritas:** Menentukan kelas data baru berdasarkan kelas mayoritas dari tiga tetangga terdekat.

Dengan pendekatan ini, KNN mampu mengklasifikasikan tipe-tipe mental illness pada dataset ini secara efektif, meskipun akurasi dan performa model tetap bergantung pada distribusi dan kualitas data pelatihan yang tersedia.
### Kelebihan dan Kekurangan KNN

**Kelebihan**:
- **Sederhana dan Mudah Dipahami**: KNN adalah algoritma yang mudah untuk diimplementasikan dan diinterpretasikan.
- **Tanpa Pelatihan Terlebih Dahulu**: Model KNN tidak memerlukan pelatihan yang panjang; proses prediksi dilakukan langsung dengan menghitung jarak.
- **Adaptif terhadap Data Baru**: Model KNN dapat dengan cepat beradaptasi terhadap data baru tanpa memerlukan retraining yang mahal.

**Kekurangan**:
- **Waktu Prediksi yang Lambat**: KNN membutuhkan waktu yang lebih lama untuk melakukan prediksi, terutama jika dataset besar, karena harus menghitung jarak ke setiap titik data dalam training set.
- **Sensitif terhadap Skala Data**: KNN memerlukan data yang dinormalisasi atau distandarisasi, karena pengaruh fitur dengan skala yang berbeda bisa mendistorsi hasil.
- **Cenderung Terpengaruh oleh Noise**: Jika terdapat data outlier atau noise dalam dataset, KNN dapat memberikan hasil yang tidak akurat.

### Model Terbaik

Mengingat bahwa hanya satu algoritma yang digunakan dalam proyek ini, yaitu KNN, model ini akan menjadi model terbaik berdasarkan hasil evaluasi yang dilakukan. Model ini dipilih karena performanya yang baik dalam mengklasifikasikan data gangguan mental setelah diterapkan teknik augmentasi dan standarisasi, meskipun mungkin ada potensi untuk peningkatan lebih lanjut melalui teknik tuning yang tidak dilakukan dalam proyek ini.

## Evaluation

Pada tahap evaluasi model K-Nearest Neighbors (KNN), model menghasilkan **akurasi sebesar 93%** dalam mengklasifikasikan kondisi mental **Bipolar Type-1, Bipolar Type-2, Depression,** dan **Normal**. Berikut adalah hasil evaluasi model secara rinci:

| Kelas           | Precision | Recall | F1-score | Support |
|-----------------|-----------|--------|----------|---------|
| Bipolar Type-1  | 0.92      | 0.96   | 0.94     | 24      |
| Bipolar Type-2  | 0.88      | 1.00   | 0.93     | 14      |
| Depression      | 0.94      | 0.91   | 0.92     | 33      |
| Normal          | 0.96      | 0.90   | 0.93     | 29      |

**Accuracy keseluruhan:** 0.93  
**Macro average:** Precision = 0.92, Recall = 0.94, F1-score = 0.93  
**Weighted average:** Precision = 0.93, Recall = 0.93, F1-score = 0.93  

### Analisis Metrik Evaluasi
- **Precision** menunjukkan akurasi model dalam memprediksi tiap kategori dengan benar. Model memberikan nilai precision yang tinggi pada semua kelas, yang berarti kesalahan prediksi pada tiap kelas cukup minim.
- **Recall** mengukur sensitivitas model dalam mendeteksi setiap kelas. Pada kelas **Bipolar Type-2**, recall mencapai 1.00, yang berarti model mampu mengenali setiap instance di kelas tersebut dengan sempurna.
- **F1-score** memberikan keseimbangan antara precision dan recall. Nilai yang tinggi pada semua kelas menunjukkan bahwa model ini efektif dalam mendeteksi kasus dengan tingkat kesalahan yang rendah.

### Dampak
- Model KNN mampu mengidentifikasi dan mengklasifikasikan kondisi mental dengan tingkat akurasi yang tinggi, menjawab kebutuhan untuk membedakan berbagai kondisi mental secara efektif, sehingga problem satement (1) terjawab bahwa model KNN dapat membantu mengidentifikasi jenis gangguan mental pada pasien berdasarkan data gejala.
- Untuk menjawab problem statement dan mencapai tujuan pada goals 2, digunakan **korelasi matriks** (correlation matrix) untuk menganalisis hubungan antar fitur dalam dataset. Korelasi matriks memberikan pemahaman sejauh mana masing-masing fitur saling berhubungan dan memberikan wawasan tentang fitur mana yang berkontribusi signifikan terhadap model klasifikasi gangguan mental.

  Dengan melihat korelasi antar fitur, kita dapat:
  - Mengidentifikasi fitur-fitur yang saling berkaitan kuat (misalnya, memiliki korelasi tinggi) yang bisa memberikan informasi penting untuk model klasifikasi.
  - Menentukan fitur mana yang mungkin redundan, sehingga bisa dihapus tanpa kehilangan informasi penting, sehingga meningkatkan efisiensi model.
  - Memahami hubungan negatif atau positif antara fitur tertentu yang dapat mempengaruhi cara model memprediksi kategori gangguan mental (seperti **Bipolar Type-1**, **Bipolar Type-2**, **Depression**, dan **Normal**).

  Dengan menggunakan korelasi matriks, kita dapat memilih fitur-fitur yang paling relevan dan mengoptimalkan model agar dapat memberikan prediksi yang lebih akurat.
  
-  Model ini berhasil mencapai tujuan utama, yaitu mendukung diagnosis awal dari berbagai tipe gangguan mental dengan akurat. Akurasi dan nilai F1-score yang tinggi menunjukkan bahwa model dapat menjadi alat yang andal dalam memberikan hasil yang konsisten.
- Meskipun model ini sudah memberikan hasil yang baik, tuning parameter lebih lanjut atau penggunaan teknik pemodelan lain di masa mendatang dapat lebih meningkatkan akurasinya, jika diperlukan untuk skala aplikasi yang lebih luas.

