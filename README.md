# Laporan Proyek Machine Learning - Fila Sofiyati

## Project Overview

K-Drama (Korean Drama) telah menjadi salah satu bentuk hiburan yang paling populer di seluruh dunia, dengan basis penggemar yang terus berkembang pesat. Popularitas K-Drama tidak hanya terbatas di Korea Selatan, tetapi juga menyebar ke berbagai negara, terutama di Asia, Eropa, dan Amerika. Menurut laporan dari Statista, jumlah pemirsa K-Drama global diperkirakan mencapai lebih dari 50 juta orang, menunjukkan peningkatan signifikan dalam permintaan akan konten K-Drama.
Seiring dengan bertambahnya jumlah judul K-Drama yang tersedia, penonton sering kali mengalami kesulitan dalam menemukan judul baru yang sesuai dengan selera mereka. Sebuah studi oleh Yoon et al. (2021) menunjukkan bahwa sistem rekomendasi dapat meningkatkan kepuasan pengguna dengan memberikan saran konten yang relevan berdasarkan preferensi individu. Dalam konteks K-Drama, rekomendasi yang akurat dapat membantu penonton mengeksplorasi judul yang mungkin mereka nikmati tetapi tidak mereka ketahui.
Dalam pengembangan sistem rekomendasi K-Drama ini, terdapat dua pendekatan utama yang dapat dipertimbangkan: Content-based Filtering dan Collaborative Filtering. Content-based Filtering merekomendasikan K-Drama kepada pengguna berdasarkan fitur-fitur spesifik dari judul yang telah mereka tonton sebelumnya, seperti genre, aktor, dan sinopsis. Pendekatan ini memungkinkan sistem untuk memberikan rekomendasi yang personal dan relevan, meskipun masih memiliki tantangan seperti kesulitan dalam merekomendasikan judul baru.
Di sisi lain, Collaborative Filtering merekomendasikan K-Drama berdasarkan perilaku dan preferensi pengguna lain yang memiliki kesamaan. Meskipun pendekatan ini dapat menawarkan variasi yang lebih besar dalam rekomendasi, ia juga menghadapi masalah seperti cold start, di mana sistem memerlukan data pengguna yang cukup untuk memberikan saran yang akurat. Oleh karena itu, pendekatan Content-based Filtering dipilih untuk proyek ini, terutama mengingat keterbatasan dataset yang digunakan, yang mencakup 250 sampel dari K-Drama teratas di MyDramaList.
Dengan memanfaatkan data dari MyDramaList, proyek ini bertujuan untuk mengembangkan sistem rekomendasi K-Drama yang dapat menyajikan saran judul berdasarkan fitur-fitur penting, sehingga meningkatkan pengalaman menonton pengguna.


## Business Understanding
Berikut beberapa pernyataan masalah yang akan di selesaikan berdasarkan pemaparan latar belakang, sebagai berikut:
- Bagaimana cara penonton K-Drama menemukan judul baru yang sesuai dengan preferensi mereka di tengah banyaknya pilihan yang tersedia?
- Apa faktor utama yang mempengaruhi preferensi penonton dalam memilih K-Drama yang akan ditonton?

### Goals
- Mengembangkan sistem rekomendasi K-Drama yang mampu memberikan saran judul yang sesuai dengan preferensi penonton.
- Meningkatkan pengalaman menonton penonton dengan membantu mereka menemukan konten baru yang relevan dan menarik, sehingga mengurangi kesulitan dalam memilih K-Drama di tengah banyaknya pilihan yang tersedia.
- Meningkatkan akurasi dan relevansi rekomendasi dengan memanfaatkan data dari MyDramaList.

### Solution statements
Proyek ini akan menciptakan sistem rekomendasi K-Drama berbasis Content-based Filtering, yang menggunakan data dari MyDramaList yang mencakup 250 judul K-Drama teratas. Sistem ini akan menganalisis fitur-fitur kunci dari K-Drama yang telah ditonton oleh pengguna, untuk menghasilkan rekomendasi yang personal dan relevan. Dengan cara ini, pengguna akan lebih mudah menemukan K-Drama yang sesuai dengan preferensi mereka, meskipun mereka adalah pengguna baru atau ketika ada judul baru yang ditambahkan.

## Data Understanding 
Dataset yang digunakan yaitu  [Top 250 Korean Dramas (KDrama) Dataset](https://www.kaggle.com/datasets/ahbab911/top-250-korean-dramas-kdrama-dataset) berisi csv data top 250 kdrama di website [MyDramaList](https://mydramalist.com)
Dataset ini bertujuan untuk memberikan rekomendasi k-drama yang sesuai baik Content Based Recommender System maupun Collaborative Filtering.
Dataset ini terdiri dari 1 file csv, 17 fitur dan 250 sampel judul k-drama.

### Informasi data:
| **Fitur**             | **Deskripsi**                                                                                           |
|-----------------------|---------------------------------------------------------------------------------------------------------|
| **Name**              | Judul dari K-drama.                                                                                     |
| **Aired Date**        | Tanggal pertama kali K-drama ditayangkan.                                                               |
| **Year of Release**   | Tahun di mana K-drama ini pertama kali dirilis.                                                         |
| **Original Network**  | Channel televisi atau platform OTT tempat K-drama ini pertama kali ditayangkan.                         |
| **Number of Episodes**| Jumlah total episode dari K-drama tersebut.                                                             |
| **Duration**          | Durasi setiap episode dalam jam dan menit.                                                              |
| **Content Rating**    | Rating usia yang sesuai untuk penonton K-drama ini.                                                     |
| **Rating**            | Peringkat atau rating berdasarkan vote pengguna MyDramaList pada saat dataset dibuat.                   |
| **Synopsis**          | Ringkasan atau plot cerita K-drama.                                                                     |
| **Genre**             | Genre atau kategori utama yang menggambarkan tema K-drama, seperti romansa, aksi, komedi, dll.          |
| **Tags**              | Elemen-elemen unik dari K-drama, misalnya "time travel," "revenge," atau "school life."                 |
| **Director**          | Nama sutradara yang bertanggung jawab atas K-drama ini.                                                 |
| **Screenwriter**      | Nama penulis skenario yang menulis cerita K-drama.                                                      |
| **Cast**              | Daftar aktor dan aktris yang membintangi K-drama ini.                                                   |
| **Production Companies** | Perusahaan yang memproduksi K-drama tersebut.                                                       |
| **Rank**              | Peringkat K-drama dalam daftar top 250, berdasarkan popularitas dan rating.                             |


Pada Dataset tersebut berisikan informasi sebanyak 250 judul k-drama dengan 17 fitur serta terdapat 9 missing values pada 8 baris judul K-Drama dan 0 data duplikat. Untuk 8 baris yang memiliki missing value, baris tersebut dihapus saja, karena presentasinya yang kecil.


## Analisis Univariat dan Visualisasi Data
### Analisis Univariat Tahun Rilis
![Visualisasi Tahun Rilis](https://github.com/user-attachments/assets/d6ff50a9-2159-477c-aec8-54d484cce0b6)
Pada Dataset ini paling banyak K-Drama yang rilis tahun 2019 dan 2021.

### Analisis Univariat Saluran Penyiaran K-Drama
![Visualisasi Original Network](https://github.com/user-attachments/assets/3d199085-104e-4782-b29a-2049cdc5f763)
Terlihat pada dataset ini, k-darama yang ada terbanyak dari saluran tvN.

### Analisis Univariat Hari penyiaran K-Drama
![Visualisasi Aired On](https://github.com/user-attachments/assets/c289574d-0543-46c1-893d-98267d1532b2)
Terlihat pada dataset ini, k-drama yang ada terbanyak di siarkan pada Wednesday, Thursday.

### Analisis Univariat Jumlah Episode K-Drama
![Episode](https://github.com/user-attachments/assets/1e65fe96-1e6d-40e5-b5c4-b8e12afe03a8)
Rentang episode 0 -20 mendominasi kebanyakan k-darama dalam dataset ini.

###  Analisis Univariat Waktu Durasi Tayang K-Drama per episode
![Duration](https://github.com/user-attachments/assets/a7fa88ca-fffa-416e-8a75-d0f8a1e116ff)
Kebanyakan K-Drama dalam dataset ini berdurasi 60 - 70 menit.

### Analisis Univariat kategori Content Rating usia
![Content Rating](https://github.com/user-attachments/assets/a53c4a8f-7951-4e50-99f4-72d3a2a82b1b)
Kebanayakan K-Drama dataset ini diperuntukkan untuk penonton dengan usia 15 tahun ke atas.

### Analisis Univariat Rating K-Drama
![Rating](https://github.com/user-attachments/assets/44138e46-9f7b-41ff-8147-3c3adb564382)
Kebanykana K-Drama dalam dataset ini memiliki rating 8,3 - 8,4.

## Analisis Multivariat dan Visualisasi Data
### Analsis Multivariat Rating dengan Jumlah Episode
![rating episode](https://github.com/user-attachments/assets/38d1b11b-1c70-43ec-bf11-7610dad86283)
K-Drama dengan Rating Tinggi kebanyakan rentang episodenya antara 0 - 40.

### Analsis Multivariat Rating, Content Rating dengan Jumlah Episode
![Rating content rating episode](https://github.com/user-attachments/assets/5cc3fd30-bfd9-4513-a4b2-8a1e5e22f674)
Tidak terlalu berpengaruh anatara Rating, Content Rating dengan Jumlah Episode.

### Analsis Multivariat Rating dengan Genre
![Rating Genre](https://github.com/user-attachments/assets/3f7e403e-d429-4891-90d3-503b97527a39)
Rating Tinggi K-Drama didominasi Genre Drama, Romance, dan Thriller.
  
## Data Preparation
### Mengatasi Missing Values
Semua fitur dalam dataset ini tidak memiliki missing value, dengan rincian sebagai berikut:
![missing value](https://github.com/user-attachments/assets/18fc5015-68c8-4737-aacb-3f9f3193a9a3)

| Name                      | Aired Date                   | Year of Release | Original Network | Aired On         | Number of Episodes | Duration    | Content Rating       | Rating | Synopsis                                                                                         | Genre                              | Tags                                         | Director        | Screenwriter              | Cast                                                | Production Companies | Rank |
|---------------------------|------------------------------|-----------------|------------------|------------------|--------------------|-------------|-----------------------|--------|-------------------------------------------------------------------------------------------------|-------------------------------------|----------------------------------------------|----------------|---------------------------|-----------------------------------------------------|-----------------------|------|
| One Dollar Lawyer         | Sep 23, 2022 - Nov 11, 2022  | 2022            | SBS              | Friday, Saturday | 12                 | 1 hr. 10 min. | NaN                   | 8.4    | Cheon Ji Hun is a lawyer with unusual flair...                                                 | Comedy, Law, Drama                 | Lawyer Male Lead, Former Prosecutor Male Lead | Kim Jae Hyun    | Choi Soo Jin, Choi Chang Hwan | Namkoong Min, Kim Ji Eun, Choi Dae Hoon, Lee Deok Hwa | Studio S             | #141 |
| Duel                      | Jun 3, 2017 - Jul 23, 2017   | 2017            | OCN              | Saturday, Sunday | 16                 | 1 hr. 3 min.  | NaN                   | 8.4    | Jang Deuk Cheon, a hardened detective cop...                                                    | Thriller, Mystery, Sci-Fi          | Amnesia, Human Experimentation, Kidnapping    | Lee Jong Jae    | Kim Yoon Joo              | Jung Jae Young, Kim Jung Eun, Yang Se Jong, Seo Eun Soo | Chorokbaem Media     | #147 |
| Player                    | Sep 29, 2018 - Nov 11, 2018  | 2018            | OCN              | Saturday, Sunday | 14                 | 1 hr. 5 min.  | NaN                   | 8.4    | A police redemption team consisting of a swind...                                             | Action, Thriller, Mystery, Comedy  | Strong Female Lead, Corruption, Hidden Identity | Go Jae Hyun     | Shin Jae Hyung            | Song Seung Heon, Krystal Jung, Lee Si Eon, Tae Won Suk | iWill Media          | #172 |
| The Mysterious Class      | Nov 12, 2021 - Dec 31, 2021  | 2021            | YouTube          | Friday           | 8                  | 20 min.      | NaN                   | 8.3    | "There are 21 students in our class." "What are you...                                        | Mystery, Horror, Youth, Supernatural | Student, Ghost, Investigation, High School     | Ha Han Me       | Han Song-yi               | Choi Hyun Suk, Park Ji Hoon, Yoshi, Kim Jun Kyu       | YG Entertainment      | #191 |
| It's Okay, That's Friendship | Mar 5, 2021              | 2021            | YouTube          | Friday           | 1                  | 20 min.      | G - All Ages          | 8.3    | The 12 members of TREASURE take on acting for...                                               | Comedy, Life                       | Idol Male Lead, Multiple Mains, Transfer Student | NaN            | NaN                       | Choi Hyun Suk, Park Ji Hoon, Kim Jun Kyu, Yoshi       | YG Entertainment      | #193 |
| Angry Mom                 | Mar 18, 2015 - May 7, 2015   | 2015            | MBC              | Wednesday, Thursday | 16              | 1 hr. 10 min. | 15+ - Teens 15 or older | 8.3    | The protagonist, Jo Kang Ja was once legendary...                                             | Comedy, Drama, Melodrama           | Independent Female Lead, Mother-Daughter Relationship | Ashbun         | Kim Ban Di                | Kim Hee Sun, Kim Yoo Jung, Ji Hyun Woo, Kim Ji Soo    | NaN                   | #219 |
| Liar Game                 | Oct 20, 2014 - Nov 25, 2014  | 2014            | tvN              | Monday, Tuesday  | 12                 | 1 hr. 3 min.  | NaN                   | 8.3    | Various contestants take part in a game show w...                                           | Thriller, Mystery, Psychological, Drama | Naive Female Lead, Debt, Game Show, Swindler Male Lead | Kim Hong Seon   | Ryu Yong Jae             | Lee Sang Yoon, Kim So Eun, Shin Sung Rok, Cha Soo Yeon | Apollo Pictures, Fantagio | #231 |
| Coffee Prince            | Jul 2, 2007 - Aug 28, 2007   | 2007            | MBC              | Monday, Tuesday  | 17                 | 60 min.      | 15+ - Teens 15 or older | 8.3    | Choi Han Gyul is the grandson of chairwoman Ba...                                           | Food, Comedy, Romance, Drama       | Cross-Dressing, Hidden Identity, Boss-Employee Relationship | Lee Yoon Jung  | Jang Hyun Joo, Lee Jung Ah | Gong Yoo, Yoon Eun Hye, Lee Sun Kyun, Chae Jung Ahn   | NaN                   | #241 |



Terlihat beberapa fitur yang memiliki 9 missing value yaitu Content Rating, Director, Screenwriter dan Production companies yang tersebar dalam 8 baris. karena 8 baris ini presentasinya kecil jadi baris yg ada missing valuenya dihapus saja.
Sekarang tidak ada missing value lagi, data yang semula memiliki 250 data judul film, sekarang hanya ada 242 judul film.


### Mengatasi Data Duplicate
![duplikat](https://github.com/user-attachments/assets/c8597427-70d5-4fe0-97ea-eeeec075820f)
Pada dataset ini tidak ada data duplikat.

## Model Development dengan Content Based Filtering
Feature Engineering merupakan  teknik rekayasa fitur untuk representasi teks. Teknik ini mengubah teks pada data masukan ke dalam bentuk numerik sehingga dapat digunakan untuk pemodelan. [Feature Engginering](https://www.dicoding.com/academies/319/tutorials/18804).

TF-IDF (Term Frequency-Inverse Document Frequency) adalah teknik yang digunakan untuk menilai seberapa penting sebuah kata dalam konteks dokumen atau korpus. Pendekatan ini mengatasi kelemahan metode frekuensi kata sederhana dengan melakukan skala ulang berdasarkan seberapa sering kata tersebut muncul di keseluruhan dokumen.

Teknik ini mengubah teks pada data masukan ke dalam bentuk numerik sehingga dapat digunakan untuk pemodelan. Pada Feature Engineering ini menggunakan metode Basic vectorization approaches yaitu TF-IDF.

TF-IDF (Term Frequency-Inverse Document Frequency) adalah teknik yang digunakan untuk menilai seberapa penting sebuah kata dalam konteks dokumen atau korpus. Pendekatan ini mengatasi kelemahan metode frekuensi kata sederhana dengan melakukan skala ulang berdasarkan seberapa sering kata tersebut muncul di keseluruhan dokumen.

Pendekatan ini menggunakan dua komponen utama:

* TF (Term Frequency): Mengukur seberapa sering kata muncul dalam teks, dinormalisasi berdasarkan panjang dokumen.
* DF (Inverse Document Frequency): Mengukur seberapa unik kata tersebut dalam seluruh dokumen, sehingga kata yang umum di seluruh korpus diberi bobot lebih rendah.

Skor TF-IDF dihitung dengan mengalikan nilai TF dan IDF dari suatu kata. Hasilnya digunakan untuk mengenali istilah-istilah yang penting dalam teks tertentu. [TF-IDF](https://www.dicoding.com/academies/319/tutorials/18804)

Disini digunakan data Genre Karena penonton biasanya cenderung menyukai konten K-Drama yang meiliki tema Genre yang hampir mirip.

![image](https://github.com/user-attachments/assets/15cdcbbb-e7b5-491a-9198-9221ac427ef8)

Terlihat beberapa Genre yang ada dalam dataset.
Disini dilakukan fit lalu ditransformasikan ke bentuk matrix.
matriks yang di miliki berukuran (242, 30). Nilai 242 merupakan ukuran data dan 30 merupakan matrik kategori Genre.
selanjutnya vektor tf-idf dalam bentuk matriks.

Sampai di sini, telah berhasil diidentifikasi representasi fitur penting dari setiap kategori Genre dengan fungsi tfidfvectorizer, juga telah dihasilkan matriks yang menunjukkan korelasi antara Genre dengan Name (Judul K-Drama). Selanjutnya, akan dihitung derajat kesamaan antara satu judul K-Drama dengan K-Drama lainnya untuk menghasilkan kandidat Judul K-Drama yang akan direkomendasikan.


### Similarity Measure (Derajat Kesamaan)
Dalam sistem rekomendasi, tingkat kesamaan atau degree of similarity adalah ukuran seberapa mirip dua item. Disebut juga sebagai similarity function, fungsi ini menghitung kesamaan antara dua item
* Semakin besar jarak, kesamaan semakin kecil (menuju nol).
* Semakin kecil jarak, kesamaan semakin besar (menuju satu).

Kesamaan berbanding terbalik dengan jarak: semakin kecil jarak antar item, semakin tinggi tingkat kesamaannya. [Similarity Measure](https://www.dicoding.com/academies/319/tutorials/17128).

Untuk tingkat kesamaan ini digunakan Cosine Similarity.
Cosine Similarity mengukur kesamaan antara dua vektor dan menentukan apakah kedua vektor tersebut menunjuk ke arah yang sama. Ia menghitung sudut cosinus antara dua vektor. Semakin kecil sudut cosinus, semakin besar nilai cosine similarity. [Cosine Similarity](https://www.dicoding.com/academies/319/tutorials/17128).

Pada tahapan ini, dihitunh cosine similarity dataframe tfidf_matrix yang diperoleh pada tahapan sebelumnya. Dengan satu baris kode untuk memanggil fungsi cosine similarity dari library sklearn, kita telah berhasil menghitung kesamaan (similarity) antar restoran. Kode di atas menghasilkan keluaran berupa matriks kesamaan dalam bentuk array.

Selanjutnya, akan di lihat matriks kesamaan setiap Name (Judul K-Drama) dengan menampilkan Judul K-Drama (Name) dalam 5 sampel kolom (axis = 1) dan 10 sampel baris (axis=0).

Dengan cosine similarity, telah berhasil diidentifikasi kesamaan antara satu Judul K-Drama dengan K-Drama lainnya. Shape (242, 242) merupakan ukuran matriks similarity dari data yang kita miliki. Berdasarkan data yang ada, matriks di atas sebenarnya berukuran 242 K-Drama X 242 K-Drama (masing-masing dalam sumbu X dan Y). Artinya, kita mengidentifikasi tingkat kesamaan pada 242 Judul K-Drama, dengan dipilih contoh 10 restoran pada baris vertikal dan 5 restoran pada sumbu horizontal.

### Mendapatkan Rekomendasi
Disini Rekomendasi K-Drama diambil K-Drama yang Genrenya berkaitan.

```python
def kdrama_recommendations(Name, similarity_data=cosine_sim_df, items=data[['Name', 'Genre']], k=5):
    """
    Rekomendasi Resto berdasarkan kemiripan dataframe

    Parameter:
    ---
    Name : Tipe data string (str)
           Judul K-Drama (index kemiripan dataframe)
    similarity_data : tipe data pd.DataFrame (object)
                      Kesamaan dataframe, simetrik, dengan Name (Judul K-Drama) sebagai
                      indeks dan kolom
    items : tipe data pd.DataFrame (object)
            Mengandung kedua nama dan fitur lainnya yang digunakan untuk mendefinisikan kemiripan
    k : tipe data integer (int)
        Banyaknya jumlah rekomendasi yang diberikan
    ---

    Pada index ini, kita mengambil k dengan nilai similarity terbesar
    pada index matrix yang diberikan (i).
    """

    # Mengambil data dengan menggunakan argpartition untuk melakukan partisi secara tidak langsung sepanjang sumbu yang diberikan
    # Dataframe diubah menjadi numpy
    # Range(start, stop, step)
    index = similarity_data.loc[:,Name].to_numpy().argpartition(
        range(-1, -k, -1))

    # Mengambil data dengan similarity terbesar dari index yang ada
    closest = similarity_data.columns[index[-1:-(k+2):-1]]

    # Drop nama_resto agar nama resto yang dicari tidak muncul dalam daftar rekomendasi
    closest = closest.drop(Name, errors='ignore')

    return pd.DataFrame(closest).merge(items).head(k)

Dengan menggunakan argpartition,di ambil sejumlah nilai k tertinggi dari similarity data (dalam kasus ini: dataframe cosine_sim_df). Kemudian, kita mengambil data dari bobot (tingkat kesamaan) tertinggi ke terendah. Data ini dimasukkan ke dalam variabel closest. Berikutnya, kita perlu menghapus nama_resto yang yang dicari agar tidak muncul dalam daftar rekomendasi.

Dalam contoh ini, akan dicari K-Drama yang mirip dengan Mr. Queen, sehingga perlu drop Name Mr. Queen agar tidak muncul dalam daftar rekomendasi yang diberikan nanti.

| Name       | Aired Date             | Year of Release | Original Network | Aired On           | Number of Episodes | Duration     | Content Rating            | Rating | Synopsis                                                                | Genre                       | Tags                                            | Director      | Screenwriter           | Cast                                         | Production Companies     | Rank |
|------------|------------------------|-----------------|------------------|--------------------|--------------------|--------------|---------------------------|--------|------------------------------------------------------------------------|-----------------------------|------------------------------------------------|---------------|------------------------|----------------------------------------------|--------------------------|------|
| Mr. Queen  | Dec 12, 2020 - Feb 14, 2021 | 2020            | tvN              | Saturday, Sunday   | 20                 | 1 hr. 20 min. | 15+ - Teens 15 or older    | 9.0    | Jang Bong Hwan is a South Korean chef who has ... | Historical, Mystery, Comedy, Romance | Smart Male Lead, Transmigration, Calm Male Lead, ... | Yoon Sung Shik | Park Kye Ok, Choi Ah Il | Shin Hye Sun, Kim Jung Hyun, Bae Jong Ok, Kim ... | Crave Works, YG Entertainment | #11  |

Mr. Queen merupakan K- Drama dengan kategori Historical, Mystery, Comedy, Romance. Tentu penonton berharap rekomendasi yang diberikan adalah K-Drama dengan genre yang mirip.

Berikut Rekomendasi yang dihasilkan
| Name                       | Genre                            |
|----------------------------|-----------------------------------|
| 100 Days My Prince         | Historical, Comedy, Romance, Drama |
| Rookie Historian Goo Hae Ryung | Historical, Comedy, Romance, Drama |
| The Tale of Nokdu          | Action, Historical, Comedy, Romance |
| Queen In Hyun's Man        | Historical, Comedy, Romance, Fantasy |
| The King's Affection       | Historical, Romance, Drama         |


## Interpretasi:
- **Jadi dengan menggunakan Content Based Filtering penonton K-Drama dapat menemukan judul baru yang sesuai dengan preferensi genre mereka di tengah banyaknya pilihan yang tersedia.**

- **Genre sangat memengaruhi preferensi k-drama yang di tonton oleh penonton, penonton biasnaya lebih suka dengan K-Drama yang memiliki tema Genre yang hampir mirip.**


## Referensi

1. [Dicoding](https://www.dicoding.com/academies/319/tutorials/17116) (2024). *Content Based Filtering*
2. [Dicoding](https://www.dicoding.com/academies/319/tutorials/18804). *FeaturebEngineering*
3. [Dicoding](https://www.dicoding.com/academies/319/tutorials/18804) *TF-IDF*
4. [Dicoding](https://www.dicoding.com/academies/319/tutorials/17128). *Similarity Measure*
5. [Dicoding](https://www.dicoding.com/academies/319/tutorials/17128). *Cosine Similarity*
6. [Science Direct](https://www.sciencedirect.com/science/article/abs/pii/S0306457321001436) *How You Like That?: Development of a Korean Drama Recommendation System Through Sentiment Analysis]*



