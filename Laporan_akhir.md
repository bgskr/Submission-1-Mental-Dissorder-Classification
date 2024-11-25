# Laporan Proyek Machine Learning - Fadly Fajary Bagaskara

## Project Overview

Seiring dengan perkembangan teknologi, jumlah data yang dihasilkan dari berbagai aktivitas manusia seperti komentar, ulasan, peringkat, dan konten digital terus meningkat secara eksponensial. Namun, data dalam jumlah besar ini tidak memiliki nilai intrinsik tanpa diolah menjadi informasi yang bermakna [\[1\]](https://ieeexplore.ieee.org/document/7684166). Pengolahan data yang efektif dapat menghasilkan wawasan yang berguna, baik untuk pengambilan keputusan strategis, peningkatan pengalaman pengguna, maupun pengembangan bisnis.

Salah satu aplikasi utama dari pengolahan data adalah pengembangan **sistem rekomendasi**. Sistem ini memungkinkan penyajian konten atau produk yang sesuai dengan kebutuhan atau preferensi pengguna, sehingga memberikan manfaat bagi konsumen dan meningkatkan efisiensi bisnis. Sebagai contoh, rekomendasi buku dalam platform e-commerce atau aplikasi perpustakaan digital membantu pengguna menemukan buku yang relevan, meningkatkan kepuasan pelanggan, dan mendorong penjualan atau keterlibatan.

Menurut riset, sistem rekomendasi berbasis data telah menjadi salah satu alat utama dalam industri modern, termasuk e-commerce, streaming media, dan layanan pendidikan. Studi yang dilakukan oleh Ricci et al. (2015) [\[2\]](https://link.springer.com/book/10.1007/978-1-4899-7637-6) menunjukkan bahwa sistem rekomendasi berbasis _collaborative filtering_ memiliki efektivitas tinggi dalam meningkatkan pengalaman pengguna dan retensi pelanggan.

Pada proyek ini, pendekatan _item-based collaborative filtering_ diterapkan untuk menghasilkan rekomendasi buku berdasarkan dataset yang tersedia. Pendekatan ini bekerja dengan menganalisis pola rating atau interaksi yang diberikan pengguna terhadap buku tertentu, dan mengukur kemiripan antar buku berdasarkan pola tersebut. Hasil analisis ini memungkinkan sistem untuk merekomendasikan buku yang relevan meskipun pengguna belum pernah berinteraksi dengan item tersebut sebelumnya.

Implementasi proyek ini diharapkan memberikan wawasan praktis tentang cara membangun sistem rekomendasi yang efektif, sekaligus menunjukkan nilai signifikan dari data pengguna yang sering kali kurang dimanfaatkan secara optimal.

Referensi :
 - [1] P. Mathew, B. Kuriakose, and V. Hegde, "Book Recommendation System through Content Based and Collaborative Filtering Method," *Department of Computer Science, Amrita Vishwa Vidyapeetham Mysuru Campus, Mysuru, Karnataka, India*, veenapravi.mathew@gmail.com, bincykarikkattu@gmail.com, vinayakhegde92@gmail.com.  
 - [2] Ricci, F., Rokach, L., & Shapira, B. (2015). _Recommender Systems Handbook_. Springer.  
Available at: https://link.springer.com/book/10.1007/978-1-4899-7637-6

## Business Understanding

### Problem Statement

Proyek ini bertujuan untuk mengembangkan model guna memberikan rekomendasi buku berdasarkan riwayat data buku yang pernah dibaca oleh **user**. Berikut beberapa pernyataan masalah utama:

-   **Masalah 1**: Bagaimana cara memberikan rekomendasi buku yang relevan kepada pengguna yang belum pernah memberikan rating atau review terhadap buku yang ada di sistem?
-   **Masalah 2**: Bagaimana meningkatkan akurasi sistem rekomendasi agar dapat menyesuaikan dengan preferensi individu pengguna meskipun terdapat data yang tidak lengkap atau tidak terstruktur?

### Goals

Tujuan utama dari proyek ini adalah untuk membangun sebuah sistem rekomendasi yang dapat memberikan rekomendasi buku yang sesuai dengan preferensi setiap pengguna. Secara spesifik, tujuan proyek ini meliputi:

-   Mengembangkan sistem rekomendasi berbasis **_item-based collaborative filtering_** untuk buku yang direkomendasikan berdasarkan riwayat pembacaan pengguna lain dengan pola yang serupa.
-   Meningkatkan personalisasi rekomendasi dengan menggunakan pendekatan **_collaborative filtering_** untuk memperkirakan rating atau preferensi pengguna terhadap buku yang belum mereka baca.
-   Menyediakan rekomendasi yang tepat bahkan untuk pengguna baru (cold start problem), dengan mengatasi tantangan terkait data yang tidak lengkap.

### Solution Statement

Solusi untuk masalah ini adalah dengan menggunakan **_collaborative filtering_** yang mengandalkan kemiripan antara buku atau antar pengguna untuk memberikan rekomendasi. Model rekomendasi akan dilatih menggunakan data interaksi pengguna dengan buku, seperti rating yang diberikan. Dengan pendekatan **_item-based_**, sistem ini akan menghitung kemiripan antar buku berdasarkan pola rating dari pengguna lain, dan memberikan rekomendasi buku yang serupa kepada pengguna berdasarkan buku yang sudah mereka baca sebelumnya.

Selain itu, untuk meningkatkan akurasi dan relevansi rekomendasi, model ini akan diuji dan dioptimalkan dengan menggunakan data subset yang sudah diproses dan disaring dari dataset besar yang ada.

## Data Understanding

Dataset yang digunakan pada proyek ini adalah ["Book Recommendation Dataset"](https://www.kaggle.com/datasets/arashnic/book-recommendation-dataset?select=Books.csv) yang bersumber dari [Kaggle](https://www.kaggle.com/). Dataset ini terdiri dari 278,858 user (yang sudah dianonimkan), 1.149.780 rating (eksplisit/implisit) untuk 271.379 buku. Dataset ini juga sudah melewati tahap pra-pemrosesan dan pembersihan data.


Dataset ini terdiri dari tiga file utama, yaitu:

-   **Users**:  
    File ini berisi data pengguna. ID pengguna (`User-ID`) telah dianonimkan dan diubah menjadi bilangan bulat. Informasi demografis seperti lokasi (`Location`) dan usia (`Age`) disediakan jika tersedia; jika tidak, kolom ini akan berisi nilai NULL.
    
-   **Books**:  
    Buku diidentifikasi berdasarkan ISBN masing-masing. ISBN yang tidak valid telah dihapus dari dataset. Selain itu, terdapat informasi berbasis konten seperti judul buku (`Book-Title`), penulis buku (`Book-Author`), tahun terbit (`Year-Of-Publication`), dan penerbit (`Publisher`) yang diperoleh dari Amazon Web Services. Jika terdapat lebih dari satu penulis, hanya penulis pertama yang dicantumkan. URL untuk gambar sampul buku juga disediakan dalam tiga ukuran berbeda (`Image-URL-S`, `Image-URL-M`, `Image-URL-L`) yaitu kecil, sedang, dan besar. URL ini mengarah ke situs Amazon.
    
-   **Ratings**:  
    File ini berisi informasi tentang penilaian buku. Rating (`Book-Rating`) dapat berupa penilaian eksplisit, dengan skala 1-10 (nilai lebih tinggi menunjukkan apresiasi lebih besar), atau penilaian implisit yang ditandai dengan nilai 0.

## Data Preparation

Dikarenakan data ini sudah dilakukan pra-pemrosesan dan pembersihan, maka persiapan yang dilakukan akan mengecualikan hal tersebut, berikut persiapan data yang dilakukan:

1. **Drop Duplicates & Missing Value**
  -   Menghapus data duplicate pada DataFrame `all_data` serta menghapus baris yang memiliki nilai kolom NaN
    
2. **Membuat Dataframe baru untuk seluruh buku**
  -   Pertama buat list dari nilai kolom kolom `ISBN`, `Book_Title`, `Book_Author` . Kemudian buat dataframe baru dari ketiga list tersebut. Dataframe ini yang nantinya akan digunakan untuk ujicoba model

3. **Pemilihan Kolom yang Relevan**
  -   Dari file **Books**, kolom `ISBN`, `Book-Title`, dan `Book-Author` dipertahankan untuk identifikasi buku.
  -   Dari file **Ratings**, kolom `User-ID`, `ISBN`, dan `Book-Rating` digunakan sebagai inti untuk membangun model.
  - Pada proyek ini, file **Users** tidak digunakan.
 
4. **Penamaan Kolom**
  - Mengubah nama kolom **Book-Title, Book-Author, dan User-ID** menjadi **Book_title, Book_Author, User_ID**

5. **Mengubah Nilai Kolom ke Numerik**
  - Melakukan proses encoding untuk kolom **User_ID** dan **ISBN** menjadi tipe numerik agar dapat diproses oleh model. Proses encoding ini dilakukan dengan membuat dictionary dengan nilai key : value berupa _nilai kolom : nilai encoding_. Kemudian menyisipkan ke dalam dataFrame dengan fungsi **map()** , maka value akan disisipkan ke baris yang memiliki nilai sama dengan key.
  - Mengubah tipe data pada kolom **Book-Rating** menjadi float
 
6. **Membatasi Jumlah Baris**
  - Dikarenakan data yang teramat banyak, maka pada proyek ini akan membatasi jumlah data sebanyak 50.000 baris. Dan dengan pengambilan yang dilakukan secara acak.

7. **Persiapan Data Latih**
  - Persiapan data latih dilakukan dengan memisahkan data menjadi dua bagian _training_ dan _test_ set. Perbandingannya adalah 80% _training set_ dan 20% _test set_.
 
8. **Normalisasi Rating**  
  - Nilai rating yang awalnya berada pada rentang 0-10 dinormalisasi ke rentang 0-1 menggunakan rumus:

$$ \text{Rating Normalisasi} = \frac{\text{Rating} - \text{Rating Minimum}}{\text{Rating Maksimum} - \text{Rating Minimum}}$$

Hal ini dilakukan untuk memastikan model dapat belajar lebih efektif dari skala nilai yang seragam.

## Modeling

### Pendekatan Model

Pada proyek ini, digunakan pendekatan _embedding_ untuk membuat sistem rekomendasi. Model memanfaatkan jaringan saraf buatan (_neural network_) yang dirancang untuk mempelajari representasi laten (_latent representation_) dari pengguna dan buku berdasarkan data rating. Berikut penjelasan komponen model:

#### **1. Input Layer**
Model ini dirancang untuk menerima **satu input dengan dua kolom**:
- Kolom pertama mewakili **user ID**.
- Kolom kedua mewakili **book ID**.

```python
input_layer = Input(shape=(2,), name='user_book_input')  # Single input with two columns (user, book)
```

#### **2. Pemisahan Input**
Input dipecah menjadi dua bagian menggunakan **Lambda layer**:
- **User Input**: Mengambil kolom pertama dari input.
- **Book Input**: Mengambil kolom kedua dari input.

```python
user_input = Lambda(lambda x: x[:, 0])(input_layer)  # First column: user IDs
book_input = Lambda(lambda x: x[:, 1])(input_layer)  # Second column: book IDs
```

#### **3. Embedding Layer**
- **User Embedding**: Memberikan representasi terlatih untuk user dengan ukuran vektor embedding 50 dan menambahkan regularisasi L2 (`embeddings_regularizer=l2(1e-5)`).
- **Book Embedding**: Memberikan representasi terlatih untuk book dengan pengaturan yang sama.

```python
user_embedding = Embedding(len_user, 50, name='user_embedding', embeddings_regularizer=l2(1e-5))(user_input)
book_embedding = Embedding(len_book, 50, name='book_embedding', embeddings_regularizer=l2(1e-5))(book_input)
```

Embedding ini kemudian diubah menjadi vektor 1 dimensi menggunakan **Flatten layer**:

```python
user_vec = Flatten()(user_embedding)
book_vec = Flatten()(book_embedding)
```

#### **4. Penggabungan Vektor Embedding**
Vektor embedding untuk user dan book digabungkan menggunakan **Concatenate layer** untuk menghasilkan representasi gabungan.

```python
merged = Concatenate()([user_vec, book_vec])
```

#### **5. Dense Layer**
- **Dense Layer 1**: Terdiri dari 128 unit dengan aktivasi ReLU dan regularisasi L2 (`kernel_regularizer=l2(0.01)`).
- **Dropout**: Menerapkan dropout dengan rate 20% untuk mengurangi risiko overfitting.

```python
dense = Dense(128, activation='relu', kernel_regularizer=l2(0.01))(merged)
dropout = Dropout(0.2)(dense)
```

- **Output Layer**: Menghasilkan 1 output dengan aktivasi sigmoid dan regularisasi L2 pada kernel.

```python
output = Dense(1, activation='sigmoid', kernel_regularizer=l2(0.01))(dropout)
```

#### **6. Kompilasi Model**
Model dikompilasi menggunakan **Adam optimizer** dengan **learning rate 1e-3**, fungsi loss Mean Squared Error (MSE), dan metrik Mean Absolute Error (MAE).

```python
model.compile(optimizer=Adam(learning_rate=1e-3), loss='mse', metrics=['mae'])
```

#### **7. Callback untuk Early Stopping**
**EarlyStopping** digunakan untuk menghentikan pelatihan lebih awal jika tidak ada perbaikan pada **val_loss** selama 3 epoch berturut-turut. Model akan mengembalikan bobot terbaiknya.

```python
early_stopping = EarlyStopping(monitor='val_loss', patience=3, restore_best_weights=True)
```

#### **8. Penggabungan Data Input**
User ID dan Book ID digabungkan ke dalam satu array input dua kolom untuk pelatihan dan validasi.

```python
x_train_combined = np.column_stack((x_train[:, 0], x_train[:, 1]))  # Shape: (num_samples, 2)
x_test_combined = np.column_stack((x_test[:, 0], x_test[:, 1]))
```

#### **9. Pelatihan Model**
Model dilatih dengan **batch size 32** selama maksimum **20 epoch**, dengan validasi dilakukan pada data uji.

```python
history = model.fit(
    x_train_combined, y_train, 
    validation_data=(x_test_combined, y_test), 
    epochs=20, 
    batch_size=32, 
    callbacks=[early_stopping]
)
``` 

### Alasan Pemilihan Model

Model berbasis embedding ini dipilih karena dapat menangkap hubungan kompleks antara pengguna dan buku dengan mempelajari representasi laten yang efektif. Selain itu, jaringan saraf memungkinkan fleksibilitas dalam mengatasi hubungan non-linear dan menghasilkan prediksi yang lebih akurat.

## Evaluation

### Model Performance

Pada tahap evaluasi, metrik **Mean Squared Error (MSE)** dan **Mean Absolute Error (MAE)** digunakan untuk mengukur performa model pada data uji. Berikut hasil evaluasi:

-   **Test Loss (MSE):** 0.14907
-   **Test MAE:** 0.35938

Hasil ini menunjukkan bahwa model mampu memberikan prediksi dengan kesalahan rata-rata sebesar ~0.36 pada skala target yang telah dinormalisasi antara 0 dan 1. Dengan nilai MSE yang rendah, model memiliki kinerja yang baik dalam memprediksi rating pada data uji. Namun, analisis tambahan mungkin diperlukan untuk memastikan kinerja model terhadap data baru atau untuk menangani kemungkinan outlier.

### Learning Curve

Plot berikut menunjukkan perubahan nilai **Loss** (MSE) selama proses pelatihan model pada data pelatihan dan validasi:

![plot_final](https://github.com/user-attachments/assets/9e789952-b8c7-4050-964a-c48a390456f3)


**Observasi:**  
Dari grafik di atas, terlihat bahwa nilai **loss** pada data pelatihan terus menurun seiring bertambahnya epoch, yang menunjukkan bahwa model berhasil belajar dari data pelatihan. Pada data validasi, nilai **loss** cenderung stabil setelah beberapa epoch terakhir, yang menandakan bahwa model mencapai titik optimal dalam generalisasi tanpa mengalami overfitting. Hal ini juga didukung oleh penggunaan **Early Stopping**, yang membantu menghentikan pelatihan sebelum model mulai kehilangan kemampuan generalisasi pada data validasi.

### Evaluasi Dampak Model terhadap Business Understanding  

#### Menjawab Problem Statement  
1. **Masalah 1**: Model yang dikembangkan berhasil memberikan prediksi yang baik untuk rekomendasi buku berdasarkan pola interaksi pengguna, meskipun terdapat pengguna yang belum pernah memberikan rating sebelumnya. Hal ini terlihat dari metrik evaluasi (MSE dan MAE) yang menunjukkan kesalahan prediksi cukup kecil. Dengan menggunakan **_item-based collaborative filtering_**, model mampu memberikan rekomendasi buku yang relevan kepada pengguna, bahkan jika data interaksi mereka terbatas.  

2. **Masalah 2**: Dengan pendekatan **_collaborative filtering_**, model dapat menangani data yang tidak lengkap dan memberikan rekomendasi yang lebih personal. Penggunaan embedding layer untuk representasi pengguna dan buku memungkinkan model menangkap hubungan laten antar entitas, sehingga meningkatkan akurasi rekomendasi.  

#### Mencapai Goals yang Diharapkan  
- **Pencapaian Tujuan 1:** Sistem rekomendasi berhasil dilatih dengan baik untuk mengidentifikasi buku-buku yang relevan berdasarkan interaksi pengguna lain. Hal ini mendukung tujuan memberikan rekomendasi yang sesuai dengan pola pengguna.  
- **Pencapaian Tujuan 2:** Model yang dibangun menggunakan embedding berhasil meningkatkan personalisasi rekomendasi. Berdasarkan metrik MAE sebesar 0.359, model menunjukkan kemampuan prediksi yang cukup baik, mendekati preferensi pengguna terhadap buku yang direkomendasikan.  
- **Pencapaian Tujuan 3:** Model ini memberikan dasar solusi untuk mengatasi cold start problem, meskipun masih memerlukan evaluasi lebih lanjut pada data pengguna baru yang tidak memiliki riwayat pembacaan.  

#### Dampak dari Solusi Statement  
Solusi yang diusulkan, yaitu **_collaborative filtering_**, berdampak signifikan terhadap penyelesaian permasalahan rekomendasi buku. Model ini berhasil:  
- Mengidentifikasi buku-buku yang relevan berdasarkan pola interaksi pengguna.  
- Memberikan rekomendasi yang dapat diandalkan meskipun data pengguna tidak lengkap.  
- Menghadirkan solusi berbasis machine learning yang mampu menangkap hubungan kompleks antar entitas dengan embedding representation.  

Namun, ada beberapa hal yang perlu diperhatikan:  
1. **Evaluasi pada Pengguna Baru:** Model ini perlu diuji lebih lanjut dengan data pengguna baru yang tidak memiliki riwayat pembacaan untuk memastikan pendekatan ini efektif mengatasi cold start problem.  
2. **Feedback Loop:** Model dapat ditingkatkan dengan memanfaatkan feedback pengguna terhadap rekomendasi untuk memperbarui dan meningkatkan kualitas rekomendasi di masa depan.  

Dengan demikian, model yang dikembangkan telah memberikan solusi yang menjawab problem statement dan mencapai sebagian besar goals yang ditetapkan, dengan ruang untuk perbaikan lebih lanjut.  
