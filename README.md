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

![image](https://github.com/user-attachments/assets/3af239c1-0e25-4577-8735-7e50e161a32a)
Pada Dataset ini paling banyak K-Drama yang rilis tahun 2021.

### Analisis Univariat Saluran Penyiaran K-Drama

![image](https://github.com/user-attachments/assets/3e6c72e8-e6c4-463c-a0ae-5e1db2824e14)
Terlihat pada dataset ini, k-darama yang ada terbanyak dari saluran tvN.

### Analisis Univariat Hari penyiaran K-Drama

![image](https://github.com/user-attachments/assets/68776329-d94e-4f56-8995-bdbcd83e5cf9)
Terlihat pada dataset ini, k-drama yang ada terbanyak di siarkan pada Wednesday, Thursday.

### Analisis Univariat Jumlah Episode K-Drama

![image](https://github.com/user-attachments/assets/94c42bcb-8874-4e94-8b98-5d80e1b959ca)
Rentang episode 10-30 mendominasi kebanyakan k-darama dalam dataset ini.

###  Analisis Univariat Waktu Durasi Tayang K-Drama per episode

![image](https://github.com/user-attachments/assets/fe421fbc-64de-45a1-b044-f1e59c7954ce)
Kebanyakan K-Drama dalam dataset ini berdurasi 60 - 70 menit.

### Analisis Univariat kategori Content Rating usia

![image](https://github.com/user-attachments/assets/a05a0bf4-cef9-4363-ac52-424289d04da7)
Kebanayakan K-Drama dataset ini diperuntukkan untuk penonton dengan usia 15 tahun ke atas.

### Analisis Univariat Rating K-Drama

![image](https://github.com/user-attachments/assets/42e92657-ceab-466f-83ce-7c5aaa6b5629)
Kebanykana K-Drama dalam dataset ini memiliki rating 8,3 - 8,4.

## Analisis Multivariat dan Visualisasi Data
### Analsis Multivariat Rating dengan Jumlah Episode

![image](https://github.com/user-attachments/assets/5e694a23-7a3f-4635-99e4-35a348ad2ae6)
K-Drama dengan Rating Tinggi kebanyakan rentang episodenya antara 0 - 40.

### Analsis Multivariat Rating, Content Rating dengan Jumlah Episode

![image](https://github.com/user-attachments/assets/624263cb-6a9f-4e47-8373-de81ddce97b1)
Tidak terlalu berpengaruh anatara Rating, Content Rating dengan Jumlah Episode.

### Analsis Multivariat Rating dengan Genre

![image](https://github.com/user-attachments/assets/1326730b-fce8-4274-8b87-88ea382dbb6a)
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

Content Based Filtering, Teknik ini merekomendasikan item yang mirip dengan preferensi pengguna di masa lalu. Content-Based Filtering merekomendasikan item berdasarkan kemiripan fitur  preferensi item yang sudah disukai atau dipilih oleh pengguna di masa a. Dalam kasus ini, fitur yang digunakan adalah genre K-Drama.
Teknik yang Digunakan: Biasanya menggunakan similarity measures (salah satunya, cosine similarity) untuk menghitung kemiripan antar item. Rekomendasi dihasilkan dengan memilih item yang memiliki skor kemiripan tertinggi dengan item yang diberikan.

Pada tahap ini akan di bangun sistem rekomendasi sederhana Judul K-drama berdasarkan Genre.

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
```

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

## Evaluasi
Untuk Evaluasi disini digunakan Precision@K, Mean Reciprocal Rank (MRR), dan Mean Average Precision (MAP).

### Precision at K
Precision@K mengukur ketepatan model dalam merekomendasikan item yang relevan di antara K rekomendasi teratas yang dihasilkan.

Precision@K merupakan rasio dari jumlah item relevan yang ditemukan dalam K rekomendasi teratas, dibagi dengan K. Dengan kata lain, Precision@K menunjukkan persentase rekomendasi yang relevan di antara K rekomendasi teratas.

Rumus

![image](https://github.com/user-attachments/assets/2f8628d5-5bec-4d34-b9f0-39acd18235ad)

Hasil Evaluasi Precisision@5

![image](https://github.com/user-attachments/assets/181e5156-14fb-4c19-9157-58a83c449ce4)
Nilai 1.0 berarti bahwa semua K item (rekomendasi K-Drama) teratas adalah relevan.

### Mean Reciprocal Rank (MRR)
Mean Reciprocal Rank (MRR) menilai seberapa cepat item relevan pertama muncul dalam daftar rekomendasi. MRR mengukur Reciprocal Rank dari item relevan pertama untuk beberapa query atau pengguna, lalu menghitung rata-ratanya.

Reciprocal Rank adalah kebalikan dari posisi item relevan pertama dalam daftar rekomendasi. MRR adalah rata-rata dari Reciprocal Rank untuk semua query atau pengguna

Rumus

![image](https://github.com/user-attachments/assets/a3826045-46b6-46c0-b5f6-feaba007de57)

Di mana rank_𝑖 adalah posisi item relevan pertama untuk query ke-𝑖 i, dan 𝑁 adalah jumlah query.

Hasil Evaluasi MRR

![image](https://github.com/user-attachments/assets/68d3d309-d008-47f2-a9fb-85ed601ee2ff)
Nilai 1.0 berarti item relevan (Rekomendasi K-Drama) pertama selalu ada di posisi teratas.

Semakin tinggi nilai MRR, semakin cepat item relevan ditemukan di dalam daftar rekomendasi.

### Mean Average Precision (MAP)
Mean Average Precision (MAP) mengukur akurasi rata-rata dari semua posisi relevan dalam daftar rekomendasi dan kemudian menghitung rata-ratanya untuk semua query atau pengguna. Dimana Untuk setiap query atau pengguna, kita menghitung Average Precision (AP), yang merupakan rata-rata Precision pada setiap posisi di mana item relevan muncul. MAP adalah rata-rata dari AP untuk seluruh query.

![image](https://github.com/user-attachments/assets/904657db-bd3c-4ccc-88f2-cda7df66b51f)
Di mana AP𝑖 adalah Average Precision untuk query ke-𝑖, dan 𝑁 adalah jumlah query.

Untuk menghitung AP, kita menggunakan

![image](https://github.com/user-attachments/assets/a2e55285-8d8a-47da-82bd-e60b8bb61b0b)
Di mana 𝑛 adalah jumlah item yang direkomendasikan, dan relevance (𝑘) adalah 1 jika item pada posisi 𝑘 relevan, dan 0 jika tidak relevan.

Haisl Evaluasi

![image](https://github.com/user-attachments/assets/4e884f14-069b-4e2a-8710-66839e2868d5)
Nilai 1.0 menunjukkan bahwa semua item relevan berada di posisi paling atas dan semuanya relevan.

**Jadi Berdasarkan Evaluasi menggunakan Precision@K, Mean Reciprocal Rank (MRR), dan Mean Average Precision (MAP) didapatkan nilai 1.0 yang berarti item yang di rekomendasikan relevan.**

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




