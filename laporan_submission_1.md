# Laporan Proyek Machine Learning - Fadly Fajary Bagaskara

## Domain Proyek

**Latar Belakang:**
Lower back pain (LBP) atau nyeri punggung bawah adalah masalah kesehatan yang umum dan signifikan secara global. Diperkirakan bahwa hingga 80% orang akan mengalami LBP setidaknya sekali dalam hidup mereka, dan nyeri ini sering kali menyebabkan penurunan kualitas hidup serta berdampak pada ekonomi. Menurut laporan dari Organisasi Kesehatan Dunia (WHO), LBP adalah salah satu penyebab utama disabilitas di seluruh dunia dan menjadi alasan utama kehilangan waktu kerja bagi banyak orang dewasa (WHO, 2021). Penelitian lebih lanjut dari National Institutes of Health (NIH) juga menunjukkan bahwa LBP sering dikaitkan dengan kondisi kronis yang membutuhkan pengobatan jangka panjang (NIH, 2022).

Dengan adanya prediksi dini dan penanganan yang tepat, risiko perkembangan LBP menjadi kondisi kronis dapat dikurangi. Teknologi kecerdasan buatan, seperti model prediktif dalam machine learning, berpotensi membantu dalam identifikasi awal faktor risiko dan prediksi LBP berdasarkan gejala pasien dan data kesehatan lainnya.

**Mengapa Masalah Ini Penting Diselesaikan:**
Biaya kesehatan dan ketidakhadiran di tempat kerja yang diakibatkan oleh LBP sangat besar, tidak hanya bagi individu tetapi juga bagi perusahaan dan sistem kesehatan. Mengingat tingginya prevalensi LBP, alat prediksi yang dapat mengidentifikasi risiko LBP pada tahap awal akan memberikan manfaat besar. Ini tidak hanya meningkatkan kualitas hidup pasien tetapi juga mengurangi biaya perawatan kesehatan. Selain itu, pendekatan prediktif dapat membantu dalam menyediakan perawatan preventif yang lebih tepat sasaran, seperti program latihan punggung atau terapi fisik, yang dapat mengurangi insiden LBP secara keseluruhan.

**Referensi Riset:**
- World Health Organization (WHO). (2021). Low back pain fact sheet. Diakses dari [WHO official website](https://www.who.int/news-room/fact-sheets/detail/depression](https://www.who.int/news-room/fact-sheets/detail/low-back-pain)).
  
- National Institutes of Health (NIH). (2022). Low back pain and its chronic implications. Diakses dari [NIMH Information](https://www.nimh.nih.gov/health/statistics/mental-illness.shtml](https://www.nih.gov/news-events/news-releases/low-back-pain-its-chronic-implications)).
- 
Dengan pendekatan berbasis data menggunakan *dataset Lower Back Pain Symptoms* dari Kaggle, proyek ini bertujuan untuk mengembangkan model klasifikasi yang mampu mengidentifikasi jenis gangguan terkait nyeri punggung bawah berdasarkan data gejala pasien.

## Business Understanding

### Problem Statements

Proyek ini bertujuan untuk mengembangkan model prediktif guna mendeteksi risiko Lower Back Pain (LBP) pada pasien berdasarkan data gejala. Berikut adalah beberapa pernyataan masalah utama:

1. **Pernyataan Masalah 1**: Bagaimana model dapat membantu mengidentifikasi pasien yang berisiko mengalami LBP berdasarkan data gejala yang tersedia?
   
2. **Pernyataan Masalah 2**: Apa saja faktor atau gejala utama yang paling signifikan dalam menentukan risiko LBP pada pasien?

### Goals

Tujuan dari pernyataan masalah di atas adalah sebagai berikut:

- **Jawaban Pernyataan Masalah 1**: Membangun model prediktif yang dapat mendeteksi risiko LBP dengan tingkat akurasi tinggi menggunakan data gejala dari pasien.
  
- **Jawaban Pernyataan Masalah 2**: Mengidentifikasi faktor-faktor atau gejala yang memiliki pengaruh terbesar dalam penentuan risiko LBP, sehingga dapat memberikan wawasan tambahan bagi tenaga medis.

### Solution Statements

Untuk mencapai tujuan di atas, langkah-langkah solusi yang diambil meliputi:

1. **Solusi 1**: Menggunakan algoritma K-Nearest Neighbors (KNN) dengan n_neighbors=3 sebagai model utama untuk klasifikasi risiko LBP. Algoritma ini dipilih karena kemampuannya dalam menangani data dengan berbagai fitur dan kesederhanaannya dalam implementasi.

2. **Solusi 2**: Meningkatkan kualitas dan representasi data melalui augmentasi dan teknik SMOTE untuk menyeimbangkan distribusi data antar kelas. Dengan data yang lebih seimbang, diharapkan model dapat mengenali pola pada masing-masing kelas secara lebih akurat.

Dengan langkah-langkah ini, diharapkan model prediktif yang dikembangkan dapat membantu mendeteksi risiko LBP secara lebih efektif, mendukung pengambilan keputusan klinis, dan memberikan kontribusi yang berarti dalam pencegahan LBP bagi masyarakat luas.

## Data Understanding

Dataset ini berisi data dari **310 observasi** yang terdiri dari **13 gejala esensial** dengan **12 Gejala, bertipe Numerik** dan **1 Label bertipe Obect** kemudian menentukan k data ini akan mengidentifikasi seseorang yang abnormal atau normal menggunakan data/detail tulang belakang fisik yang dikumpulkan. Dataset ini tersedia dalam format **CSV** dan dapat diakses melalui [Kaggle](https://www.kaggle.com/datasets/sammy123/lower-back-pain-symptoms-dataset).

Nyeri punggung bawah dapat disebabkan oleh berbagai masalah pada bagian mana pun dari jaringan otot, saraf, tulang, cakram, atau tendon tulang belakang yang kompleks dan saling berhubungan di tulang belakang lumbar. Sumber nyeri punggung bawah yang umum meliputi:

*   Akar saraf besar di punggung bawah yang menuju ke kaki mungkin teriritasi
*   Saraf yang lebih kecil yang mensuplai punggung bawah mungkin teriritasi
*   Otot punggung bawah berpasangan yang besar (erector spinae) mungkin tegang
*   Tulang, ligamen, atau sendi mungkin rusak
*   Cakram intervertebralis mungkin mengalami degenerasi

Iritasi atau masalah pada salah satu struktur ini dapat menyebabkan nyeri punggung bawah dan/atau nyeri yang menjalar atau dirujuk ke bagian tubuh lainnya. Banyak masalah punggung bawah juga menyebabkan kejang otot punggung, yang kedengarannya tidak terlalu parah tetapi dapat menyebabkan nyeri parah dan kecacatan.

Meskipun nyeri punggung bawah sangat umum, gejala dan tingkat keparahan nyeri punggung bawah sangat bervariasi. Ketegangan otot punggung bawah yang sederhana mungkin cukup menyiksa hingga memerlukan kunjungan ke ruang gawat darurat, sementara degenerasi diskus mungkin hanya menyebabkan ketidaknyamanan ringan dan berkala.

### Informasi Data

1. **Pelvic Incidence**: Ukuran sudut yang terbentuk antara garis vertikal tubuh dengan garis yang menghubungkan pusat panggul dan dasar tulang belakang. Sudut ini penting dalam memahami keseimbangan postural seseorang.

2. **Pelvic Tilt**: Menggambarkan sudut kemiringan panggul terhadap sumbu tubuh. Sudut ini bisa memberikan indikasi tentang postur tubuh dan potensi masalah pada tulang belakang bagian bawah.

3. **Lumbar Lordosis Angle**: Mengukur sudut lordosis (lengkungan alami ke dalam) pada tulang belakang lumbar atau bagian bawah punggung. Sudut yang tidak normal dapat menjadi indikasi adanya masalah postur atau kondisi kesehatan lainnya.

4. **Sacral Slope**: Menggambarkan sudut kemiringan sakrum (tulang di dasar tulang belakang). Nilai dari sakral slope berhubungan erat dengan sudut lain pada panggul dan berperan dalam postur tubuh secara keseluruhan.

5. **Pelvic Radius**: Jarak atau radius dari panggul yang dapat memberikan informasi tentang anatomi panggul seseorang. Ukuran ini bisa digunakan dalam analisis keseimbangan panggul.

6. **Degree Spondylolisthesis**: Menunjukkan derajat perpindahan vertebra (tulang belakang) akibat kondisi spondylolisthesis. Ini adalah kondisi di mana salah satu vertebra tergelincir ke depan dari vertebra di bawahnya, yang dapat menyebabkan nyeri dan masalah pada punggung.

7. **Pelvic Slope**: Menggambarkan sudut kemiringan panggul. Ini adalah ukuran tambahan yang mendukung analisis sudut lainnya pada panggul dan sakrum.

8. **Direct Tilt**: Menunjukkan sudut kemiringan langsung dari panggul, yang juga berguna dalam penilaian postural secara keseluruhan.

9. **Thoracic Slope**: Mengukur kemiringan pada tulang belakang bagian atas atau toraks. Ini dapat memberikan gambaran tentang postur dan potensi kelainan pada area punggung atas.

10. **Cervical Tilt**: Menggambarkan sudut kemiringan pada tulang belakang serviks atau leher. Sudut ini dapat berhubungan dengan postur leher dan potensi ketegangan atau ketidakseimbangan di daerah leher.

11. **Sacrum Angle**: Menunjukkan sudut sakrum, yang penting dalam analisis keseimbangan postural serta hubungan antara panggul dan tulang belakang.

12. **Scoliosis Slope**: Mengukur kemiringan pada tulang belakang yang terkait dengan skoliosis, yaitu kelainan pada tulang belakang yang ditandai dengan lengkungan lateral.

13. **Normality**: Kolom ini adalah variabel target yang menunjukkan apakah kondisi tulang belakang pasien dalam keadaan normal atau mengalami abnormalitas. Nilai dari kolom ini akan digunakan dalam analisis prediktif untuk menentukan klasifikasi kesehatan tulang belakang pasien.

Kolom 1-12 memiliki tipe data float dengan masing-masing kolom memiliki nilai minimum dan maximumnya. Kemudian kolom 'Normality' merupakan label dengan dua nilai yaitu 'Abnormal' dan 'Normal'

Setiap fitur ini dirancang untuk memberikan informasi detail tentang struktur dan keseimbangan tulang belakang dan panggul, yang merupakan faktor penting dalam penilaian kesehatan punggung serta postur pasien.

### Kondisi Data
Dataset ini tidak mengandung **nilai hilang** atau **nilai duplikat**, sehingga dapat langsung digunakan dalam analisis. Namun, dengan jumlah yang begitu sedikit,perlu ditambahkan proses augmentasi untuk memperkaya variasi data pelatihan sehingga mampu meningkatkan performa model yang dibuat.

## Data Preparation

Pada bagian ini, beberapa teknik data preparation diterapkan untuk memastikan data siap digunakan dalam model machine learning. Tahapan yang dilakukan meliputi:

1. **Penghapusan Kolom yang Tidak Relevan**:
   - Menghapus kolom **Unnamed: 13** karena kolom ini tidak memberikan informasi yang relevan untuk analisis dan hanya berfungsi sebagai identifikasi unik. Menghapus fitur yang tidak diperlukan dapat membantu mengurangi kompleksitas model dan meningkatkan performa.

2. **Mengganti Nama Kolom**
   - Nama kolom diubah ke format `snake_case` untuk konsistensi dan mempermudah akses data. Proses penggantian dilakukan dengan menggunakan fungsi `replace` untuk mengganti simbol-simbol atau spasi dengan tanda underscore (`_`). Misalnya, kolom dengan nama `Sleep Disorder` diubah menjadi `sleep_disorder`. Langkah ini meningkatkan keterbacaan dan menjaga format penamaan agar lebih sesuai dengan standar Python.

3. **Validasi Nilai kolom hilang atau Null**
   - Memanfaatkan fungsi .isnull().sum() untuk menghitung nilai kolom yang kosong pada masing-masing kolom. Hasil menunjukkan bahwa tidak ada nilai yang hilang sehingga data dianggap sudah lengkap dan tidak perlu dilakukan pemberihan lagi.

4. **Mengubah kolom 'Normality' menjadi Numerik**:
   - Mengubah variabel 'Normality' yang merupakan label dengan nilai 'Abnormal' dan 'Normal' menjadi nilai numerik dengan keterangan berikut. 0 => **Abnormal** || 1 => **Normal**

5. **Normalisasi atau Standarisasi**:
   - Menerapkan **StandardScaler** untuk menormalkan fitur numerik. Standarisasi diperlukan agar semua fitur berada pada skala yang sama, yang membantu dalam mempercepat proses pelatihan dan meningkatkan konvergensi model.

6. **Augmentasi Data**:
   - Menerapkan teknik **SMOTE (Synthetic Minority Over-sampling Technique)** untuk menyeimbangkan kelas pada target variabel. Ini penting dilakukan mengingat dataset awal memiliki ketidakseimbangan kelas yang signifikan, yang dapat menyebabkan model bias. Dengan augmentasi, kita mendapatkan dataset yang lebih seimbang yang dapat meningkatkan akurasi model
    
7. **Pembagian Data**:
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

Model ini dikonfigurasi dengan parameter `n_neighbors=1`, artinya model mempertimbangkan tiga tetangga terdekat saat menentukan kelas untuk data baru. Setelah pelatihan model pada dataset `X_train` dan `y_train`, model ini dievaluasi pada `X_test`, dan hasil prediksi dibandingkan dengan nilai asli (`y_test`) untuk menghitung akurasi dan laporan klasifikasi yang mencakup metrik seperti precision, recall, dan F1-score.

### Alur Kerja Model KNN

1. **Pengukuran Jarak:** Menghitung jarak antara data uji dan setiap titik data pelatihan.
2. **Pemilihan Tetangga Terdekat:** Memilih tiga titik data terdekat (berdasarkan `n_neighbors=1`).
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

Pada tahap evaluasi model K-Nearest Neighbors (KNN), model menghasilkan **akurasi sebesar 93%** dalam mengklasifikasikan kondisi seseorang **Abnormal** atau **Normal** menggunakan data/detail tulang belakang fisik. Berikut adalah hasil evaluasi model secara rinci:

| Kelas           | Precision | Recall | F1-score | Support |
|-----------------|-----------|--------|----------|---------|
| Abnormal        | 1.00      | 0.87   | 0.93     | 55      |
| Normal          | 0.87      | 1.00   | 0.93     | 45      |

**Accuracy keseluruhan:** 0.93  
**Macro average:** Precision = 0.93, Recall = 0.94, F1-score = 0.93  
**Weighted average:** Precision = 0.94, Recall = 0.93, F1-score = 0.93  

### Analisis Metrik Evaluasi
- **Precision** menunjukkan akurasi model dalam memprediksi tiap kategori dengan benar. Model memberikan nilai precision yang tinggi pada semua kelas, yang berarti kesalahan prediksi pada tiap kelas cukup minim.
- **Recall** mengukur sensitivitas model dalam mendeteksi setiap kelas. Pada kelas **Abnormal**, recall mencapai 1.00, yang berarti model mampu mengenali setiap instance di kelas tersebut dengan sempurna.
- **F1-score** memberikan keseimbangan antara precision dan recall. Nilai yang tinggi pada semua kelas menunjukkan bahwa model ini efektif dalam mendeteksi kasus dengan tingkat kesalahan yang rendah.

### Dampak
- Model KNN mampu mengidentifikasi dan mengklasifikasikan kondisi fisik tulang belakang dengan tingkat akurasi yang tinggi, menjawab kebutuhan untuk membedakan apakah kondisi tulang belakang orang tersebut normal atau tidak secara efektif, sehingga problem satement (1) terjawab bahwa model KNN dapat membantu mengidentifikasi resiko gangguan LBP berdasarkan data gejala yang tersedia
- Untuk menjawab problem statement dan mencapai tujuan pada goals 2, digunakan **korelasi matriks** (correlation matrix) untuk menganalisis hubungan antar fitur dalam dataset. Korelasi matriks memberikan pemahaman sejauh mana masing-masing fitur saling berhubungan dan memberikan wawasan tentang fitur mana yang berkontribusi signifikan terhadap model klasifikasi resiko LBP.

  Dengan melihat korelasi antar fitur, kita dapat:
  - Mengidentifikasi fitur-fitur yang saling berkaitan kuat (misalnya, memiliki korelasi tinggi) yang bisa memberikan informasi penting untuk model klasifikasi.
  - Menentukan fitur mana yang mungkin redundan, sehingga bisa dihapus tanpa kehilangan informasi penting, sehingga meningkatkan efisiensi model.
  - Memahami hubungan negatif atau positif antara fitur tertentu yang dapat mempengaruhi cara model memprediksi kategori yang tersedia.
  Dengan menggunakan korelasi matriks, kita dapat memilih fitur-fitur yang paling relevan dan mengoptimalkan model agar dapat memberikan prediksi yang lebih akurat.
  
-  Model ini berhasil mencapai tujuan utama, yaitu mendukung identifikasi resiko seseorang mengalami *Lower Back Pain* secara akurat. Akurasi dan nilai F1-score yang tinggi menunjukkan bahwa model dapat menjadi alat yang andal dalam memberikan hasil yang konsisten.
- Meskipun model ini sudah memberikan hasil yang baik, tuning parameter lebih lanjut atau penggunaan teknik pemodelan lain di masa mendatang dapat lebih meningkatkan akurasinya, jika diperlukan untuk skala aplikasi yang lebih luas.

