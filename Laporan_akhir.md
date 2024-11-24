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
Proyek ini bertujuan untuk mengembangkan model guna memberikan rekomendasi buku berdasarkan riwayat data buku  yang pernah dibaca oleh _user_. Berikut beberapa pernyataan masalah utama:  
 - Bagaimana cara memberikan rekomendasi buku yang relevan kepada pengguna yang belum pernah memberikan rating atau review terhadap buku yang ada di sistem?
 - Bagaimana meningkatkan akurasi sistem rekomendasi agar dapat menyesuaikan dengan preferensi individu pengguna meskipun terdapat data yang tidak lengkap atau tidak terstruktur?

### Goals
 1. Mengembangkan sistem rekomendasi menggunakan teknik _collaborative filtering_ dengan pendekatan _item-based_ untuk merekomendasikan buku berdasarkan riwayat pembacaan dari pengguna lain dengan pola yang serupa.
 2. Meningkatkan personalisasi rekomendasi dengan menggunakan teknik _collaborative filtering_ untuk memperkirakan rating atau preferensi pengguna terhadap buku yang belum pernah mereka baca.
 3. Menyediakan rekomendasi yang tepat bahkan untuk pengguna baru _(cold start problem)_, dengan mengatasi tantangan terkait data yang tidak lengkap.
 
### Solution Statement
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

1. **Pemilihan Kolom yang Relevan**
  -   Dari file **Books**, kolom `ISBN`, `Book-Title`, dan `Book-Author` dipertahankan untuk identifikasi buku.
  -   Dari file **Ratings**, kolom `User-ID`, `ISBN`, dan `Book-Rating` digunakan sebagai inti untuk membangun model.
  - Pada proyek ini, file **Users** tidak digunakan.
 
2. **Penamaan Kolom**
  - Mengubah nama kolom **Book-Title, Book-Author, dan User-ID** menjadi **Book_title, Book_Author, User_ID**
  
3. **Mengubah Nilai Kolom ke Numerik**
  - Melakukan proses encoding untuk kolom **User_ID** dan **ISBN** menjadi tipe numerik agar dapat diproses oleh model. Proses encoding ini dilakukan dengan membuat dictionary dengan nilai key : value berupa _nilai kolom : nilai encoding_. Kemudian menyisipkan ke dalam dataFrame dengan fungsi **map()** , maka value akan disisipkan ke baris yang memiliki nilai sama dengan key.
  - Mengubah tipe data pada kolom **Book-Rating** menjadi float
 
4. **Membatasi Jumlah Baris**
  - Dikarenakan data yang teramat banyak, maka pada proyek ini akan membatasi jumlah data sebanyak 50.000 baris. Dan dengan pengambilan yang dilakukan secara acak.

5. **Persiapan Data Latih**
  - Persiapan data latih dilakukan dengan memisahkan data menjadi dua bagian _training_ dan _test_ set. Perbandingannya adalah 80% _training set_ dan 20% _test set_.
 
 6. **Normalisasi Rating**  
Nilai rating yang awalnya berada pada rentang 0-10 dinormalisasi ke rentang 0-1 menggunakan rumus:

$$ \text{Rating Normalisasi} = \frac{\text{Rating} - \text{Rating Minimum}}{\text{Rating Maksimum} - \text{Rating Minimum}}$$

Hal ini dilakukan untuk memastikan model dapat belajar lebih efektif dari skala nilai yang seragam.

## Modeling

### Pendekatan Model

Pada proyek ini, digunakan pendekatan _embedding_ untuk membuat sistem rekomendasi. Model memanfaatkan jaringan saraf buatan (_neural network_) yang dirancang untuk mempelajari representasi laten (_latent representation_) dari pengguna dan buku berdasarkan data rating. Berikut penjelasan komponen model:

1.  **Input Layer**  
    Model memiliki satu _input layer_ dengan dua kolom:
    
    -   Kolom pertama adalah ID pengguna (user).
    -   Kolom kedua adalah ID buku (book).  
        Input layer diberi nama `user_book_input` dengan ukuran `(2,)`, yang berarti model menerima array berdimensi dua (user dan book) dalam satu input.
    
    ```python
    input_layer = Input(shape=(2,), name='user_book_input')
    
    ```
    
2.  **Split Input**  
    Input digabungkan menjadi satu array, sehingga perlu dipisahkan kembali menjadi kolom `user` dan `book` menggunakan lapisan `Lambda`.
    
    -   `user_input` mengambil kolom pertama dari array.
    -   `book_input` mengambil kolom kedua dari array.
    
    ```python
    user_input = Lambda(lambda x: x[:, 0])(input_layer)
    book_input = Lambda(lambda x: x[:, 1])(input_layer)
    
    ```
    
3.  **Embedding Layer**
    
    -   **User Embedding**: Lapisan `Embedding` digunakan untuk mempelajari representasi vektor laten dari ID pengguna. Dimensi embedding diatur menjadi 50, yang berarti setiap pengguna akan direpresentasikan oleh vektor berdimensi 50.
    -   **Book Embedding**: Lapisan `Embedding` lain digunakan untuk mempelajari representasi vektor laten dari ID buku dengan dimensi embedding yang sama.  
        Representasi ini bertujuan untuk menangkap hubungan antar pengguna dan buku dalam ruang laten.
    
    ```python
    user_embedding = Embedding(len_user, 50, name='user_embedding')(user_input)
    book_embedding = Embedding(len_book, 50, name='book_embedding')(book_input)
    
    ```
    
4.  **Flatten Layer**  
    Hasil dari embedding diubah menjadi vektor 1D menggunakan lapisan `Flatten` agar bisa digabungkan dan diproses lebih lanjut dalam model.
    
    ```python
    user_vec = Flatten()(user_embedding)
    book_vec = Flatten()(book_embedding)
    
    ```
    
5.  **Concatenate Layer**  
    Representasi laten dari pengguna dan buku digabungkan menjadi satu vektor menggunakan lapisan `Concatenate`. Ini memungkinkan model untuk mempelajari hubungan antara pengguna dan buku secara simultan.
    
    ```python
    merged = Concatenate()([user_vec, book_vec])
    
    ```
    
6.  **Dense Layers**
    
    -   Lapisan `Dense` dengan 128 unit dan fungsi aktivasi `relu` digunakan untuk memproses representasi gabungan. Lapisan ini membantu model belajar hubungan non-linear antara pengguna dan buku.
    -   Lapisan output dengan satu unit dan aktivasi `sigmoid` digunakan untuk menghasilkan prediksi nilai rating yang telah dinormalisasi (0 hingga 1).
    
    ```python
    dense = Dense(128, activation='relu')(merged)
    output = Dense(1, activation='sigmoid')(dense)
    
    ```
    
7.  **Model Compilation**  
    Model dikompilasi dengan menggunakan optimizer `adam`, _loss function_ `mean squared error (MSE)`, dan metrik `mean absolute error (MAE)` untuk mengevaluasi performa.
    
    ```python
    model.compile(optimizer='adam', loss='mse', metrics=['mae'])
    
    ```
    
8.  **Early Stopping**  
    Digunakan teknik _early stopping_ untuk mencegah overfitting. Model akan berhenti dilatih jika tidak ada peningkatan pada metrik validasi selama 3 epoch berturut-turut.
    
    ```python
    early_stopping = EarlyStopping(monitor='val_loss', patience=3, restore_best_weights=True)
    
    ```
    
9.  **Data Input untuk Training**  
    Input data pengguna dan buku digabungkan menjadi satu array 2D sebelum diberikan ke model. Proses pelatihan dilakukan dengan membagi data menjadi 80% untuk pelatihan dan 20% untuk validasi.
    
    ```python
    x_train_combined = np.column_stack((x_train[:, 0], x_train[:, 1]))
    history = model.fit(x_train_combined, y_train, validation_split=0.2, epochs=20, batch_size=32, callbacks=[early_stopping])
    
    ```
    

### Alasan Pemilihan Model

Model berbasis embedding ini dipilih karena dapat menangkap hubungan kompleks antara pengguna dan buku dengan mempelajari representasi laten yang efektif. Selain itu, jaringan saraf memungkinkan fleksibilitas dalam mengatasi hubungan non-linear dan menghasilkan prediksi yang lebih akurat.

## Evaluation

### Model Performance

Pada tahap evaluasi, metrik **Mean Squared Error (MSE)** dan **Mean Absolute Error (MAE)** digunakan untuk mengukur performa model pada data uji. Berikut hasil evaluasi:

-   **Test Loss (MSE):** 0.00856
-   **Test MAE:** 0.02482

Hasil ini menunjukkan bahwa model mampu memberikan prediksi yang cukup baik dengan rata-rata kesalahan prediksi sebesar ~0.025 pada skala rating yang telah dinormalisasi.

### Learning Curve

Plot berikut menunjukkan perubahan nilai **Loss** (MSE) selama proses pelatihan model pada data pelatihan dan validasi:

![Model loss](https://github.com/bgskr/Submission-1-Mental-Dissorder-Classification/blob/main/plot_eval.png)

**Observasi:**  
Dari grafik di atas, terlihat bahwa nilai loss pada data pelatihan terus menurun seiring bertambahnya epoch. Namun, pada data validasi, nilai loss cenderung stabil setelah beberapa epoch terakhir, menunjukkan bahwa model tidak mengalami overfitting.
