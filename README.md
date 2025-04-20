# Laporan Proyek Sistem Rekomendasi - Jelang Ramadhan

## Project Overview

Anime berasal dari kata "animation" dalam bahasa Inggris dan merujuk pada animasi Jepang. Anime dapat dibuat dengan teknik tradisional atau teknologi komputer (3D, CGI). Umumnya, karakter dalam anime memiliki nama Jepang, seperti Naruto Uzumaki dan Sasuke Uchiha, meskipun beberapa anime menggunakan unsur budaya lain, seperti Attack on Titan dengan nama Jerman atau Magi yang berlatar Timur Tengah.

Sebagian besar anime diadaptasi dari manga, meski ada yang orisinal. Jepang memiliki lebih dari 400 studio anime, termasuk Studio Ghibli, Toei Animation, dan Madhouse Inc. Anime biasanya berbahasa Jepang, tetapi tersedia dalam terjemahan atau dengan subtitle.

Di Indonesia, anime telah lama menjadi tontonan populer, memperkenalkan budaya Jepang seperti bahasa, musik, dan gaya hidup. Di Jepang sendiri, anime merupakan industri besar dengan kawasan khusus yang menjual berbagai produk terkait anime. Popularitasnya terus meningkat, membentuk komunitas penggemar yang tidak hanya menikmati anime, tetapi juga menjadikannya inspirasi dalam gaya berpakaian.

Dalam penelitian yang berjudul **[Perkembangan dan Pengaruh Anime di Indonesia, serta Penggunaan Anime sebagai Media Pemebelajaran](https://eprints2.undip.ac.id/id/eprint/13029/1/TA_Nur%20Cholis%20Khabib.pdf)** oleh **Nur Cholis Khabib** mahasiswa D3 Bahasa Jepang Fakultas Sekolah Vokasi Universitas Diponegoro Tahun 2022. Penelitian tersebut membahas tentang bagaimana perkembangan dan pengaruh anime di Indonesia, serta penerapan anime sebagai media pembelajaran bahasa jepang. Kesimpulan penelitian tersebut sebagi berikut, Mayoritas responden telah menggunakan anime sebagai media
pembelajaran bahasa Jepang. Berdasarkan hasil survei, anime menjadi salah satu referensi unuk tugas-tugas yang membantu bagi para pembelajar bahasa Jepang, dan pembelajaran yang sangat terbantu dalam pembelajaran adalah
Kaiwa dan Chokai

Hal ini menunjukkan bahwa popularitas anime di Indonesia sangat besar dan memiliki pengaruh yang besar dalam melakuakan studi bahasa jepang, maka dari itu menarik untuk membuat terobosan inovasi untuk membantu dalam membantu para pencinta anime dalam mengeksplorasi anime sebanyak mungkin dengan selera masing masing masyarakat, serta untuk membantu perkembangan dunia pendidikan bahasa terutama bahasa jepang. Proyek ini menghasilkan sebuah sistem rekomendasi dalam mencari anime dengan kesamaan genre.

**Referensi**\
Khabib, N. C. (2022) ‘Perkembangan dan Pengaruh Anime di Indonesia, serta Penggunaan Anime sebagai Media Pembelajaran’, Sekolah Vokasi Universitas Diponegoro. Tersedia di: https://eprints2.undip.ac.id/id/eprint/13029/1/TA_Nur%20Cholis%20Khabib.pdf (Diakses: 29 Maret 2025).

## Business Understanding

### Problem Statements

- Berdasarkan data mengenai pengguna, bagaimana membuat sistem rekomendasi yang dipersonalisasi untuk pengguna?
- Dengan data rating yang Anda miliki, bagaimana sistem dapat merekomendasikan anime lain yang mungkin disukai dan belum pernah dilihat oleh pengguna?

### Goals

- Menghasilkan sejumlah rekomendasi anime yang dipersonalisasi untuk pengguna
- Menghasilkan sejumlah rekomendasi anime yang sesuai dengan preferensi pengguna dan belum pernah dilihat sebelumnya.

### Solution statements

- Menggunakan algoritma content based filtering untuk mengahasilkan sistem rekomendasi anime yang dipersonalisasika untuk pengguna
- Menggunakan algoritma collaborative filtering untuk menghasilkan sistem rekomendai yang dapat menampilkan anime lain yang mungkin disukai dan belum pernah dilihat sebelumnya oleh pengguna.

## Data Understanding

Data yang kami gunakan berjudul **"anime-recommendations-database"** yang berisikan database anime dan juga data rating user untuk anime tersebut, dipisahkan menjadi 2 file .csv, yaitu anime.csv dan rating.csv. Didalam anime.csv, mempunyai 7 fitur, yaitu id anime, nama anime, genre, tipe, jumlah episode, rata rata rating, dan jumlah anggota komunitas. Rating.csv mempunyai 3 fitur, yaitu id user, id anime, dan rating.

Dalam proses EDA, didalam dataset mempunyai informasi sebagai berikut :

- Anime.csv

  1. Mempunyai jumlah baris data sebanyak 12.294 baris.
  2. Mempunyai jumlah _missing value_ sebanyak 317 data.
  3. Tidak mempunyai _data duplicated_.
  4. [Tipe anime yang paling banyak banyak di rilis berjenis TV. ](https://github.com/user-attachments/assets/06e9f5d7-9d95-44b8-a351-89f6bfa5a380)
  5. [Death Note, Shingeki no Kyojin (Attack on Titan), dan Sword Art Online adalah anime yang memiliki jumalh anggota komunitas terbesar.](https://github.com/user-attachments/assets/b6c7b3ee-94a4-4151-ac8e-39e2d43afdcd)

- Rating.csv
  1. Memiliki jumlah baris data sebanyak 7.813.737 baris.
  2. Rentang rating dari -1 sampai 10, untuk rating -1 berarti user telah menonton akan tetapi belum memberikan rating.
  3. Tidak memiliki _missing value_.
  4. Mempunyai 1 _data duplicated_.
  5. Mempunyai total 73.515 data user.

Untuk mendowload dataset tesbut: [Kaggle.com](https://www.kaggle.com/datasets/CooperUnion/anime-recommendations-database?select=rating.csv).

### Variabel-variabel pada dataset adalah sebagai berikut:

- Anime.csv

  1. anime_id : ID Anime unik yang berasal dari data [myanimelist.](myanimelist.net)
  2. name : Nama lengkap anime.
  3. genre : Data genre anime, dipisahkan dengan koma(,).
  4. type : Tipe anime (Movie, TV, OVA, Special, ONA, dan Music).
  5. episodes : Jumlah episode anime, jika berjenis movei memiliki direperentasikan dengan 1.
  6. rating : Rata - rata penilian (rating) anime.
  7. members : Jumlah anggota komunitas anime

- Rating.csv
  1. user_id : ID pengguna yang dihasilkan secara acak dan tidak dapat diidentifikasi.
  2. anime_id : ID Anime unik yang berasal dari data [myanimelist.](myanimelist.net)
  3. rating : Rating dari rentang -1 sampai 10 yang diberikan oleh pengguna (-1 jika pengguna telah menonton tetapi tidak memberikan rating).

## Data Preparation

Data preparation merupakan tahapan penting dalam proses pengembangan model machine learning. Ini adalah tahap di mana kita melakukan proses transformasi pada data sehingga menjadi bentuk yang cocok untuk proses pemodelan. Ada beberapa tahapan yang umum dilakukan pada data preparation, antara lain, seleksi fitur, transformasi data, feature engineering, dan dimensionality reduction. Pada kasus kali ini tahapan Data Preparation sebagai berikut:

### Data Preparation - Content-Based Filtering

1. Cek 5 data teratas untuk mengetahui isi dari dataset anime.
2. Cek jumlah dan tipe data pada setiap fitur untuk identifikasi awal kemungkinan _missing value, data duplicated, and inconsistent data_.
3. Menghapus _missing value_ lalu cek lagi jumlah data setelah proses pembersihan data.
4. Menggunakan TF-IDF Vectotizer, teknik tersebut akan digunakan pada sistem rekomendasi untuk menemukan representasi fitur penting dari setiap kategori penulis. tahapanua sebagai berikut:
   - Cek jenis jenis genre dari dataset
   - Tranformasi data kolom genre ke dalam bentuk matriks (tfidf_matrix) dan lihat ukurannya
   - Mengubah vektor tfidf_matrix kedalam bentuk matriks menggunakan todense()
   - Membuat DataFrame untuk melihat tf-idf matrix. Kolom diisi dengan genre anime dan baris diisi dengan nama anime.
   - Matriks tersebut berisikan data anime dengan probabilitasnya untuk masuk kedalam genre tertentu yang digunakan dalam proses rekomendasi.

### Data Preparation - Collaborative Filtering

1. Cek 5 data teratas untuk mengetahui isi dari dataser rating.
2. Menghapus rating '-1' karena informasi tersebut tidak gunakan dalam proses modeling.
3. Encoding user_id untuk menyandikan (encode) fitur ‘user_id’ dan ‘anime_id’ ke dalam indeks integer.
4. Menggunakan fungsi Mapping untuk memetakan user_id dan anime_id ke dataframe yang berkaitan.
5. Mengecek jumlah user, anime, dan mengubah nilai rating menjadi float untuk memudahkan identifikasi awal modeling.
6. Mengacak dataset supaya distribusinya menjadi acak.
7. Memetakan (mapping) data user dan anime menjadi satu value terlebih dahulu. Lalu, buatlah rating dalam skala 0 sampai 1 agar mudah dalam melakukan proses training.
8. Membagi train dan validation set dengan proporsi 80:20 sehingga model tidak hanya menghafal data latih tetapi juga bisa bekerja dengan baik pada data baru

## Modeling and Result

### Model 1 - Content-Based Filtering

Model ini akan digunakan untuk membuat sistem rekomendasi anime yang dipersonalisasi untuk pengguna (sesuai dengan goals 1). Model pertama menggunakan Content-Based Filtering karena pendekatan ini merekomendasikan anime berdasarkan kesamaan fitur dengan anime yang sudah diberikan pengguna. Model tidak bergantung dengan data pengguna lain dan menjaga keunikan selera pengguna. Cara kerjanya sebagai berikut :

1. Cosine Similarity, teknik akan menghitung derajat kesamaan (similarity degree) antar anime. Di sini, kita menggunakan fungsi cosine_similarity dari library sklearn. Untuk cara kerjanya sebagai berikut:

   - Menghitung cosine similarity dataframe tfidf_matrix yang diperoleh pada tahapan sebelumnya. Dengan satu baris kode untuk memanggil fungsi cosine similarity dari library sklearn, kita telah berhasil menghitung kesamaan (similarity) antar restoran. Kode di atas menghasilkan keluaran berupa matriks kesamaan dalam bentuk array.
   - Selanjutnya, membuat dataframe dari variabel cosine_sim dengan baris dan kolom berupa nama anime. Dengan cosine similarity, kita berhasil mengidentifikasi kesamaan antara satu anime dengan anime lainnya. Matriks yang dihasilkan adalah 12.017 x 12.017, artinya kita mengidentifikasi tingkat kesamaan pada 12.017 anime.

2. Sistem rekomendasi, kita telah memiliki data similarity (kesamaan) antar anime. Kini, tibalah saatnya menghasilkan sejumlah anime yang akan direkomendasikan kepada pengguna. Untuk cara kerjanya sebagai berikut,

   - def anime_recommendations(nama_anime similarity_data=cosine_sim_df,items=data[['name','genre','type','rating']], k=10):\
     a. Parameter nama_anime : Nama anime yang dijadikan referensi untuk mencari rekomendasi.\
     b. Parameter similarity_data : Dataframe berisi nilai cosine similarity antar anime.\
     c. Parameter items : Dataframe yang berisi informasi anime (seperti nama, genre, tipe, dan rating)\
     d. Parameter K : Jumlah anime yang akan direkomendasikan

   - index = similarity_data.loc[:, nama_anime].to_numpy().argpartition(range(-1, -k, -1)) -> Untuk mencari anime yang paling mirip\
     a. similarity_data.loc[:, nama_anime] : Mengambil kolom cosine similarity dari anime yang diberikan sebagai referensi.\
     b. .to_numpy() : Mengubah dataframe menjadi array numpy agar lebih cepat diproses.
     c. argpartition(range(-1, -k, -1)) : Mengurutkan indeks berdasarkan nilai similarity terbesar (dari yang paling mirip ke yang paling tidak mirip) tanpa harus melakukan sorting secara keseluruhan (lebih efisien).

   - closest = similarity_data.columns[index[-1:-(k+2):-1]] -> Mengambil k anime dengan nilai cosine similarity terbesar\
     a. index[-1:-(k+2):-1] : Mengambil k+1 anime yang memiliki nilai similarity tertinggi (termasuk anime input).

   - closest = closest.drop(nama_anime, errors='ignore') -> Menghapus nama_resto supaya tidak muncul di rekomendasi.\
     a. drop(nama_anime, errors='ignore') : Menghapus anime pada input data agar tidak muncul pada rekomendasi.

   - return pd.DataFrame(closest).merge(items).head(k) -> Membuat DataFrame k-rekomendasi.\
     a. pd.DataFrame(closest) : Mengubah daftar anime terdekat menjadi dataframe.\
     b. .merge(items) : Menggabungkan daftar anime ini dengan dataset utama (items) untuk mendapatkan informasi seperti genre, tipe, dan rating.\
     c. .head(k) : Mengambil k rekomendasi terbaik.

### Result 1 - Content-Based Filtering

Dengan menjalan fungsi **anime_recommendations** dengan memasukkan parameter nama_anime (contoh:'Dotto Koni-chan') akan menghasilkan 10 (defult) rekomendasi anime yang memiliki kemiripan sesuai dengan cosine similarity yang telah dihasilkan sebelumnya. Rekomendasi anime yang dihasilkan mempunyai informasi nama, genre, tipe, dan rating anime.
Berikut adalah hasil dari model Content-Based Filtering,

Data anime awal untuk sistem rekomendasi Content-Based Filtering:
| Name | Genre |
| -------- | ------- |
| Dotto Koni-chan | Comedy |

Hasil rekoemdasi 10 anime adalah :
| Name | Genre |
| -------- | ------- |
| Sockies: Frontier Quest | Comedy |
| Sugio: Mori de Koi wo Shite | Comedy |
| Sparrow&#039;s Hotel | Comedy |
| Osomatsu-kun | Comedy |
| Atama wa Tsukaiyou. Card mo Tsukaiyou | Comedy |
| Ikeike! Momon-chan | Comedy |
| Barakamon: Mijikamon | Comedy |
| Kaleido Star: Good da yo! Goood!! | Comedy |
| Kipling Jr. | Comedy |
| Ghost in the Shell: Nyuumon Arise | Comedy |

Dengan demikian sistem rekomendasi telah berhasil merekomendasikan 10 anime dengan genre yang mirip dengan anime awal (Dotto Koni-chan)

Kelebihan dan kekurangan pendekatan dengan **Content-Based Filtering**

- Kelebihan

  - Tidak bergantung dengan data pengguna yang lain, sehingga cocok untuk rekomendasi anime yang dipersonalisasi untuk pengguna.
  - Dapat menangani masalah cold start .
  - Interpretable (Mudah Dijelaskan).

- Kekurangan
  - Cenderung untuk mambatasi variasi anime yang direkomendasikan.
  - Bergantung dengan kualitas fitur.
  - Tidak mempertimbangkan popularitas (pada kasus ini hanya kesamaan genre anime)

### Model 2 - Collaborative Filtering

Model ini akan digunakan untuk menghasilkan sejumlah rekomendasi anime yang sesuai dengan preferensi pengguna dan belum pernah dilihat sebelumnya (sesuai dengan goals 2). Model kedua menggunakan Collaborative Filtering karena dapat merekomendasikan berdasarkan rating yang diberikan oleh pengguna lain dengan preferensi serupa. Dengan memanfaatkan data rating ini, model dapat mengidentifikasi pola kesukaan dan merekomendasikan anime yang memiliki skor tinggi di antara pengguna dengan selera yang mirip, sehingga meningkatkan relevansi rekomendasi. Hal ini dapat dimanfaatkan untuk mendapatkan rekomendasi anime yang mungkin disukai dan belum pernah dilihat pengguna. Cara kerja model sebagai berikut,

1. Membuat kelas **RecommenderNet** dengan **Keras Model Class** yang merupakan model rekomendasi berbasis **Collaborative Filtering** dengan pendekatan Matrix Factorization dengan embedding.

   - Dense Layer\
     a. self.user_embedding : Lapisan embedding pengguna.\
     b. self.user_bias : Lapisan embedding untuk menyimpan bias setiap pengguna.\
     c. self.item_embedding : Lapisan embedding untuk setiap anime.\
     d. self.item_bias : Lapisan embedding untuk menyimpan bias individe untuk setiap anime
   - Call\
     a. user_vector = self.user_embedding(inputs[:, 0]) : Mengambil embedding pengguna berdasarkan ID.\
     b. item_vector = self.item_embedding(inputs[:, 1]) : Mengambil embedding anime berdasarkan ID.\
     c. user_bias = self.user_bias(inputs[:, 0]) : Mengambil bias pengguna.\
     d. item_bias = self.item_bias(inputs[:, 1]) : Mengambil bias anime.\
     e. dot_user_item = tf.reduce_sum(user_vector \* item_vector, axis=1, keepdims=True) : Operasi perkalian skalar antara 2 vektor embedding.\
     f. x = dot_user_item + user_bias + item_bias : Menambahkan bias pengguna dan anime.\
     g. return tf.nn.sigmoid(x) : Mengembalikan hasil rekomendasi dengan rentang 0 dan 1 sebagai interpretasikan sebagai probabilitas atau skor kecocokan antara pengguna dan anime.\

2. Inisiasi model --> model = RecommenderNet(num_users, num_anime, 10)
3. Compile model --> Menggunakan loss function **BinaryCrossentropy**, **Adam** sebagai dengan optimizer dengan Learning Rate 0.001, dan metrics RMSE
4. Training Model --> Training model sebanyak 10 epochs dengan ukuran batch_size 1024 serta dengan validation,
5. Membuat variabel **anime_not_visited** untuk memastikan bahwa anime yang direkomendasikan benar benar belum pernah dilihat (belum dirating) oleg user dengan menggunakan operator bitwise(~) pada variable **anime_visted_by_user**(anime yang telah diberikan rating oleh pengguna)
6. Memperoleh rekomendasi dari model.predic()

### Result 2 - Collaborative Filtering

Denagn menjalankan model.predic() akan mengahasilkan output berupa data user acak beserta dengan anime dengan rating teratas yang telah diberikan oleh user tersebut. Kemudian memberikan rekomendaso 10 anime teratas berdasarkan rating kerelevanan dengan rating anime yang diberikan oleh pengguna.
Berikut adalah hasil dari model Collaborative Filtering:

Data user awal untuk sistem rekomendasi Content-Based Filtering:

Menunjukkan anime dengan rating tertinggi yang diberikan oleh user 23005
| Name | Genre |
| -------- | ------- |
| Kuroko no Basket | Comedy, School, Shounen, Sports |
| Mirai Nikki (TV) | Action, Mystery, Psychological, Shounen, Supernatural, Thriller |
| Ao no Exorcist | Action, Demons, Fantasy, Shounen, Supernatural |
| Kuroko no Basket NG-shuu | Comedy, School, Shounen, Sports |
| High School DxD | Comedy, Demons, Ecchi, Harem, Romance, School |

Hasil rekoemdasi 10 anime adalah :
| Name | Genre |
| -------- | ------- |
| Kimi no Na wa. | Drama, Romance, School, Supernatural |
| Fullmetal Alchemist : Brotherhood | Action, Adventure, Drama, Fantasy, Magic, Military, Shounen |
| Gintama° | Action, Comedy, Historical, Parody, Samurai, Sci-Fi, Shounen |
| Steins;Gate | Sci-Fi, Thriller |
| Gintama&#039; | Action, Comedy, Historical, Parody, Samurai, Sci-Fi, Shounen |
| Hunter x Hunter (2011) | Action, Adventure, Shounen, Super Power |
| Ginga Eiyuu Densetsu | Drama, Military, Sci-Fi, Space |
| Gintama Movie : Kanketsu-hen - Yorozuya yo Eien Nare | Action, Comedy, Historical, Parody, Samurai, Sci-Fi, Shounen |
| Gintama&#039; | Enchousen : Action, Comedy, Historical, Parody, Samurai, Sci-Fi, Shounen |
| Gintama | Action, Comedy, Historical, Parody, Samurai, Sci-Fi, Shounen |

Kelebihan dan kekurangan pendekatan dengan **Collaborative Filtering**

- Kelebihan

  - Tidak memerlukan informasi spesifik tentang item yang direkomendasikan, cukup berdasarkan interaksi pengguna sebelumnya.
  - Dapat menemukan pola tersembunyi dalam preferensi pengguna yang mungkin tidak terlihat secara eksplisit.
  - Semakin banyak data interaksi pengguna, semakin baik kualitas rekomendasi yang diberikan.

- Kekurangan
  - Jika jumlah pengguna dan item sangat besar, tetapi interaksi yang tersedia sedikit, sistem kesulitan menemukan pola yang relevan.
  - Cenderung merekomendasikan item populer, sehingga item yang kurang dikenal sulit mendapatkan eksposur.
  - Menggunakan data interaksi pengguna dapat menimbulkan masalah privasi jika tidak dikelola dengan baik.

## Evaluation

### Model 1 - Content-Based Filtering

Metrik evaluasi yang digunakan untuk proyek kali ini adalah **Precision (P)**

- $P=\frac{\text{Jumlah rekomendasi item yang relevan}}{\text{Jumlah item yang direkomendasikan}}$\
  Menghitung seberapa banyak item yang direkomendasikan benar-benar relevan terhadap kebutuhan pengguna. Semakin tinggi nilai precision, semakin baik kualitas rekomendasi yang diberikan oleh sistem.

Setelah melakukan berbagai tahapan ditemukan bahwa :

- $P= \frac{10}{10}=100\%$

### Model 2 - Collaborative Filtering

Metrik evaluasi yang digunakan untuk proyek kali ini adalah **Mean Absolute Error(MAE) dan Root Mean Squared Error(RMSE)**

- MAE = $\frac{1}{n}\sum^{n}_{i=1}|y_i-\hat{y}_i|$\
  Menghitung rata-rata dari selisih absolut antara nilai prediksi dan nilai aktual. Semakin rendah nilai MAE, semakin baik kualitas rekomendasi yang diberikan oleh sistem.
- RMSE = $\sqrt{\frac{1}{n}\sum^{n}_{i=1}(y_i-\hat{y}_i)^2}$\
  Menghitung rata-rata dari selisih kuadrat antara nilai prediksi dan nilai aktual kemudian diambil akar kuadratnya. Semakin rendah nilai RMSE, semakin baik kualitas rekomendasi yang diberikan oleh sistem.

**Keterangan**

- $n$ : Jumlah sampel dalam data
- $y_i$ : Nilai aktual
- $\hat{y}_i$ : Nilai prediksi

Setelah melakukan training dengan model ditemukan bahwa:

- Nilai MAE : 0.09769442971802351
- Nilai RMSE : 0.09769442971802351

### Conclusion

Setelah melakukan berbagai tahapan pada proyek ini, mulai dari tahap Business Understanding, Data Understanding, Data Preparation, Modeling, dan Evaluation untuk membuat sistem rekomendasi anime dengan menggunakan dataset _anime-recommendation-database_ dari Kaggle. Pertanyaan yang dijabarkan pada bagian **Problem Stantments** dapat dijawab semua dengan baik pada akhirnya, dengan menghasilkan **Goals** yang memuaskan, berikut detailnya:

- Menghasilkan sejumlah rekomendasi anime yang dipersonalisasi untuk pengguna
- Menghasilkan sejumlah rekomendasi anime yang sesuai dengan preferensi pengguna dan belum pernah dilihat sebelumnya.
  Hasil yang didapatkan sebagi berikut

  - Model 1 - Content-Based Filtering:\
    Berhasil membuat sistem rekomendasi anime yang dipersonalisasi untuk pengguna.Dengan memasukkan nama anime, sistem dapat merekomendasikan 10 (defult) anime yang memliki kemiripan sesuai genre yang telah dihitung dengan cosine similarity. Mendapatkan hasil

    - Nilai P : 100 %

  - Model 2 - Collaborative Filtering:\
    Berhasil membuat sistem rekomenadi anime ang sesuai dengan preferensi pengguna dan belum pernah dilihat sebelumnya. Sistem dapat memberikan data anime dengan rating teratas yang diberikan oleh pengguna, kemudian merekomendasikan 10 (anisiasi) anime yang mungkin disukai dan belum pernah dilihat oleh pengguna. Mendapatkan hasil
    - Nilai MAE : 0.09769442971802351
    - Nilai RMSE : 0.12904428938684429
    - Dengan kedua nilai tersebut dapat dikatakan model memliki tingkat error yang sangat rendah dan memiliki tingkat akurasi yang tinggi.

Pada setiap **Solution statements** telah memberikan dampak yang baik dalam memaksimalkan pencapaian **Goals**. Berikut dampak yang diberikan:

- Menggunakan algoritma content-based filtering untuk menghasilkan sistem rekomendasi anime yang dipersonalisasi untuk pengguna. Hal ini berdampak pada peningkatan relevansi rekomendasi, karena sistem menyarankan anime berdasarkan preferensi pengguna sebelumnya.

- Menggunakan algoritma collaborative filtering untuk menghasilkan sistem rekomendasi yang dapat menampilkan anime lain yang mungkin disukai dan belum pernah dilihat sebelumnya oleh pengguna. Hal ini berdampak pada peningkatan eksplorasi konten baru, sehingga pengguna dapat menemukan anime yang sesuai dengan selera mereka berdasarkan kesamaan dengan preferensi pengguna lain.
