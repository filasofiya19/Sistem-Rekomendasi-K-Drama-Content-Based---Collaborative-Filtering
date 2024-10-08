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
- Seberapa efektif sistem rekomendasi saat ini dalam memberikan saran K-Drama yang relevan dan memuaskan bagi penonton?

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


Pada Dataset tersebut berisikan informasi sebanyak 250 judul k-drama dengan 17 fitur serta terdapat ?? missing values dan 0 data duplikat, untuk data yang duplikat di hapus sehingga hanya tersisa 12.205 sampel, kemudian pada dataset ini ada sekitar 17,9% outlier, karena outlier ini cukup besar, jadi tidak dihilangkan.

### Berikut rangkuman `statistik deskriptif` dari fitur dalam dataset: <br>


| **Fitur**                    | **count**   | **mean**   | **std**    | **min**    | **25%**    | **50%**    | **75%**    | **max**    |
|------------------------------|-------------|------------|------------|------------|------------|------------|------------|------------|
| **Administrative**            | 12205.0000  | 2.3389     | 3.3304     | 0.0000     | 0.0000     | 1.0000     | 4.0000     | 27.0000    |
| **Administrative_Duration**   | 12205.0000  | 81.6463    | 177.4918   | 0.0000     | 0.0000     | 9.0000     | 94.7000    | 3398.7500  |
| **Informational**             | 12205.0000  | 0.5087     | 1.2756     | 0.0000     | 0.0000     | 0.0000     | 0.0000     | 24.0000    |
| **Informational_Duration**    | 12205.0000  | 34.8255    | 141.4248   | 0.0000     | 0.0000     | 0.0000     | 0.0000     | 2549.3750  |
| **ProductRelated**            | 12205.0000  | 32.0456    | 44.5936    | 0.0000     | 8.0000     | 18.0000    | 38.0000    | 705.0000   |
| **ProductRelated_Duration**   | 12205.0000  | 1206.9825  | 1919.6014  | 0.0000     | 193.0000   | 608.9429   | 1477.1548  | 63973.5222 |
| **BounceRates**               | 12205.0000  | 0.0204     | 0.0453     | 0.0000     | 0.0000     | 0.0029     | 0.0167     | 0.2000     |
| **ExitRates**                 | 12205.0000  | 0.0415     | 0.0462     | 0.0000     | 0.0142     | 0.0250     | 0.0485     | 0.2000     |
| **PageValues**                | 12205.0000  | 5.9496     | 18.6537    | 0.0000     | 0.0000     | 0.0000     | 0.0000     | 361.7637   |
| **SpecialDay**                | 12205.0000  | 0.0619     | 0.1997     | 0.0000     | 0.0000     | 0.0000     | 0.0000     | 1.0000     |
| **OperatingSystems**          | 12205.0000  | 2.1242     | 0.9068     | 1.0000     | 2.0000     | 2.0000     | 3.0000     | 8.0000     |
| **Browser**                   | 12205.0000  | 2.3578     | 1.7101     | 1.0000     | 2.0000     | 2.0000     | 2.0000     | 13.0000    |
| **Region**                    | 12205.0000  | 3.1533     | 2.4023     | 1.0000     | 1.0000     | 3.0000     | 4.0000     | 9.0000     |
| **TrafficType**               | 12205.0000  | 4.0739     | 4.0167     | 1.0000     | 2.0000     | 2.0000     | 4.0000     | 20.0000    |

#### Interpretasi Statistika Deskriptif Data data 
- Mayoritas dataset memiliki angka **Mean < Median** , artinya distribusi data cenderung positively skewed.
- Pada fitur yang menunjukkan **traffic website** seperti 'Administrative', 'Administrative_Duration', 'Informational', 'Informational_Duration', 'ProductRelated', 'ProductRelated_Duration', dan 'PageValues mayoritas memiliki nilai yang menumpuk di angka 0. Sehingga dilakukan Feature Transformation menggunakan PowerTransformer Yeo-Johnson untuk membuat distribusi lebih mendekati normal (Guassian) dan mendukung value data memiliki nilai positif atau negatif.

## Analisis Univariat dan Visualisasi Data
### Analisis Univariat Visitor Type dengan Revenue
![Persentase Revenue dengan Visitor Type](https://github.com/user-attachments/assets/df1c7aa4-94cb-4b56-8b06-e470c7d02aa3)
Dapat dilihat bahwa pada setahun terakhir jumlah kunjungan dan revenue pengunjung dari new visitor memiliki perbandingan yang cukup rendah di banding dengan returning visitor.

### Analisis Univariat Month dengan Revenue
![plt.title(Total Visitor per Month vs Revenue](https://github.com/user-attachments/assets/2741bed9-ffe4-482a-937a-e2de615723f1)
Dapat dilihat bahwa trafik jumlah kunjungan pelanggan setiap bulan memiliki jumlah yang paling tinggi pada bulan Mei dan di susul pada bulan November. Namun pada bulan Mei tingginya trafik tidak diikuti dengan tingginya angka Revenue yang hanya menghasilkan 11%. Sedangkan pada bulan November merupakan bulan yang memiliki cukup banyak pengunjung dengan nilai Revenue bulanan yang paling tinggi, yaitu mencapai 25%.

### Analisis Univariat Region dengan Revenue
![plt.title('Visitor Region vs Revenue', fontweight='bold')
](https://github.com/user-attachments/assets/2f26f158-48bc-471f-9491-ddd17201b2b0)
Kunjungan pelanggan didominasi pada region "1" dengan Revenue Rate yang cukup tinggi.

### Analisis Univariat Weekend dengan Revenue
![Persentase Revenue Coversion Rate saat Weekend'](https://github.com/user-attachments/assets/ae29a14b-2cc5-4a7d-86ed-f13a3afe0fbe)
Pada dasarnya presentase kunjungan Weekend dan Weekday tidak terlalu berbeda signifikan. Namun Weekday memiliki nilai yang lebih tinggi. Namun hal ini bisa terjadi dikarenakan memang jumlah hari di Weekday lebih banyak daripada Weekend atau memang pengunjung memang lebih sering mengunjungi website di hari-hari weekday.


## Analisis Multivariat dan Visualisasi Data
### Hubungan Antar Fitur Numerikal
![Heatmap Hubungan antar Fitur Numerikal](https://github.com/user-attachments/assets/41e9098d-2ea8-42e2-8c0c-2285665f6bae)

- Fitur ExitRates dan BounceRates memiliki nilai multikolinieritas yang tinggi 0.9, kedua kolom ini pun berhubungan satu sama lain sehingga dapat di drop salah satunya.
- Terdapat beberapa fitur-fitur yang kemungkinan redundan karena memiliki korelasi yang cukup tinggi diantaranya ProductRelated dengan - ProductRelated_Duration, Adminisitrative dengan Adminisitrative_Duration, Informational dengan Informational_Duration, dan begitu pula BounceRates dengan ExitRates. Dalam tahap data prepocessing feature-feature tersebut dapat di drop ataupun dipilih salah satu.
- Kolom PageValues ternyata memiliki korelasi tinggi dengan Revenue (0.49).
- Kolom BounceRates dengan beberapa kolom lain, ExitRates dengan beberapa kolom lain, dan page values dengan beberapa kolom lain berkumpul di bawah dan samping kiri cenderung membentuk pola logaritmik. Itu artinya, Apabila kolom BounceRates dan kolom Informational_Duration berhubungan secara logaritmik, semakin besar nilai BounceRates, nilai Informational_Duration semakin kecil secara logaritmik.

### Hubungan Antara Fitur Kategorikal
![Heatmap Hubungan antar Fitur Kategorikal](https://github.com/user-attachments/assets/cd0ae6e0-b86d-4e4f-98ba-df9cb6e86e87)
- Browser dan OperatingSystems memiliki korelasi yang cukup tinggi.
- Browser dan TrafficType juga memiliki korelasi yang tinggi. Nilai korelasi antar kolom dengan kolom Revenue cenderung rendah.

### Hubungan Antara Fitur Numerikal dan Kategorikal (Semua Fitur)

![Heatmap Hubungan Semua Fitur](https://github.com/user-attachments/assets/55076bf9-d8c3-4546-ac94-7f4d2cfa7cbc)

- Fitur ExitRates dan BounceRates memiliki nilai multikolinieritas yang tinggi 0.9, kedua kolom ini pun berhubungan satu sama lain sehingga dapat di drop salah satunya.
- Terdapat beberapa fitur-fitur yang redundan karena memiliki korelasi yang cukup tinggi diantaranya ProductRelated dengan ProductRelated_Duration, Adminisitrativedengan Adminisitrative_Duration, Informational dengan Informational_Duration, dan begitu pula BounceRates dengan ExitRates. Dalam tahap data prepocessing feature-feature tersebut dapat di drop ataupun dipilih salah satu.
- Kolom PageValues memiliki korelasi tinggi dengan Revenue (0.49)
- Browser dan OperatingSystems memiliki korelasi yang cukup tinggi.
- Browser dan TrafficType juga memiliki korelasi yang tinggi. Nilai korelasi antar kolom dengan kolom Revenue cenderung rendah.
  
## Data Preparation
### Mengatasi Missing Values
Semua fitur dalam dataset ini tidak memiliki missing value, dengan rincian sebagai berikut:

| Fitur                    | Missing Value |
|--------------------------|---------------|
| Administrative            | 0             |
| Administrative_Duration   | 0             |
| Informational             | 0             |
| Informational_Duration    | 0             |
| ProductRelated            | 0             |
| ProductRelated_Duration   | 0             |
| BounceRates               | 0             |
| ExitRates                 | 0             |
| PageValues                | 0             |
| SpecialDay                | 0             |
| Month                     | 0             |
| OperatingSystems          | 0             |
| Browser                   | 0             |
| Region                    | 0             |
| TrafficType               | 0             |
| VisitorType               | 0             |
| Weekend                   | 0             |
| Revenue                   | 0             |

Dari tabel di atas, dapat disimpulkan bahwa tidak ada missing value di dalam dataset.

### Mengatasi Data Duplicate
![Data Duplikat](https://github.com/user-attachments/assets/97f0e66b-9f0d-4f66-9d17-b6d5228fd6e4)

Pada data ini terdapat 125 data duplikat, kemudian data duplikat tersebut dihapus.

### Cek Outlier Data
![Outlier](https://github.com/user-attachments/assets/1b5d97fb-74e2-4cbc-9698-bf4529be3afb)
Presentase outlier dalam data ini 17.90%, nilai tersebut cukup besar, maka outlier tidak dihilangkan. Tidak dilakukan handle juga karena outlier ini bukan dari kesalahan dalam pengambilan data.

### Feature Encoding
Beberapa fitur yang di encoding dengan one hot encoding yaitu 
- VisitorType dengan other dianggap sebagai returning visitor (modus). Jadi Returning Visitor: 1 dan New Visitor: 0.
- Revenue, dengan True: 1 dan False: 0.
- Weekend, dengan True: 1 dan False: 0.

Kemudian Fitur Month, disini akan dilakukan label encoding berdasarkan indeks terbanyak.
| Bulan | Angka |
|-------|-------|
| May   | 1     |
| Nov   | 2     |
| Mar   | 3     |
| Dec   | 4     |
| Oct   | 5     |
| Sep   | 6     |
| Aug   | 7     |
| Jul   | 8     |
| June  | 9     |
| Feb   | 10    |

Berikut tampilan data sample setelah fitur tersebut di encoding:

| Administrative | Administrative_Duration | Informational | Informational_Duration | ProductRelated | ProductRelated_Duration | BounceRates | ExitRates | PageValues | SpecialDay | Month | OperatingSystems | Browser | Region | TrafficType | VisitorType | Weekend | Revenue |
|----------------|--------------------------|---------------|------------------------|----------------|-------------------------|-------------|-----------|------------|------------|-------|-------------------|---------|--------|-------------|-------------|---------|---------|
| -0.998474      | -1.005468                | -0.523851      | -0.494799              | 0.309362       | 0.323600                | -0.802948    | -0.241701 | 1.954765   | -0.33763   | 2     | 2                 | 2       | 3      | 11          | 1           | 0       | 1       |
| 0.834177       | 0.691681                 | -0.523851      | -0.494799              | 0.992655       | 1.947720                | -0.415908    | -1.004383 | 1.974870   | -0.33763   | 2     | 2                 | 6       | 1      | 3           | 1           | 0       | 1       |
| -0.998474      | -1.005468                | -0.523851      | -0.494799              | -1.007465      | -1.321258               | 2.209050     | 1.941751  | -0.532801  | -0.33763   | 3     | 3                 | 2       | 3      | 1           | 1           | 0       | 0       |
| -0.998474      | -1.005468                | 1.807721       | 2.033464               | 2.732505       | 2.394185                | -0.610252    | -1.230481 | 1.898881   | -0.33763   | 2     | 2                 | 2       | 1      | 2           | 1           | 0       | 1       |
| 1.171179       | 1.290641                 | -0.523851      | -0.494799              | -0.316462      | 0.706921                | -0.395957    | -0.081143 | 1.973952   | -0.33763   | 4     | 2                 | 2       | 1      | 8           | 1           | 0       | 0       |


### Data Transformation
Berdasarkan stastika deskriptif data tadi banyak value dengan nilai 0, jadi Transformasi feature tidak menggunakan log karena data memiliki banyak value dengan nilai 0. PowerTransformer Yeo-Johnson dipilih untuk membuat distribusi lebih mendekati normal (Guassian) dan mendukung value data memiliki nilai positif atau negatif.

![Distribusi setelah dilakukan transformasi](https://github.com/user-attachments/assets/4f8dd2df-d776-468f-95ea-78665055cf38)

### Feature Selection
Memilih fitur dengan korelasi tinggi dengan Revenue
| **Fitur**                 | **Korelasi dengan Revenue** |
|---------------------------|-----------------------------|
| Administrative            | 0.164376                    |
| Administrative_Duration   | 0.164306                    |
| Informational             | 0.110966                    |
| Informational_Duration    | 0.107878                    |
| ProductRelated            | 0.196981                    |
| ProductRelated_Duration   | 0.211123                    |
| BounceRates               | -0.172585                   |
| ExitRates                 | -0.249863                   |
| PageValues                | 0.611599                    |
| SpecialDay                | -0.088071                   |
| VisitorType               | -0.102694                   |
| Revenue                   | 1.000000                    |

Berdasar, nilai korelasi variabel dengan label revenue, maka fitur yang dipilih adalah Administrative, Administrative_Duration, Informational, Informational_Duratiom, ProductRelated, ProductRelated_Duration, BounceRates, ExitRates, PageValues, SpecialDay, VisitorType.

Tetapi beberapa variabel diatas ada yang redundan yaitu

Administrative, Administrative_Duration dipilih Administrative_Duration,
Informational, Informational_Duratiom, dipilih Informational_Duration,
ProductRelated, ProductRelated_Duration, dipilih ProductRelated_Duration
Kemudian ada variabel yang multikolinearitas nya tinggi yaitu BounceRates, ExitRates jadi dipilih salah satu yaitu ExitRates.

### Splitting Data
- Fitur Revenue merupakan label data.
- Digunakan random state 42 untuk memastikan reprodusibilitas hasil pembagian data.
- test_size menentukan proporsi data yang akan dialokasikan untuk set pengujian. Dalam kasus ini, nilai 0.2 berarti 20% dari data akan digunakan untuk pengujian, sementara 80% akan digunakan untuk pelatihan.
- Pembagian data dilakukan dengan stratifikasi, untuk memastikan distribusi kelas pada set pelatihan dan set pengujian tetap seimbang. Hal ini penting karena kelas Revenue tidak seimbang dalam dataset.
- fungsi StandarScaler untuk melakukan normalisasi (scaling) pada data. Normalisasi adalah proses mengubah fitur-fitur data sehingga memiliki rata-rata 0 dan standar deviasi 1.

## Model Development
BeberapaModel machine learning yang akan digunakan yaitu algoritma Decision Tree, Gradient Boosting Machines (GBM), Random Forest dan XgBoost.

- Decision Tree (Pohon Keputusan) merupakan salah satu cara data processing dalam memprediksi masa depan dengan cara membangun klasifikasi atau regresi model dalam bentuk struktur pohon. Hal tersebut dilakukan dengan cara memecah terus ke dalam himpunan bagian yang lebih kecil lalu pada saat itu juga sebuah pohon keputusan secara bertahap dikembangkan. Hasil akhir dari proses tersebut adalah pohon dengan node keputusan dan node daun. [BINUS](https://sis.binus.ac.id/2022/01/21/decision-tree-algoritma-beserta-contohnya-pada-data-mining/#:~:text=Sebuah%20node%20keputusan%20(misalnya,%20Cuaca/%20Outlook)%20memiliki%20dua%20atau%20lebih)
- Random Forest adalah algoritma supervised learning yang digunakan untuk klasifikasi dan regresi. Ini termasuk dalam kategori ensemble learning, di mana sekelompok model (dalam hal ini, decision trees) bekerja bersama untuk meningkatkan akurasi prediksi. Setiap model dalam Random Forest dilatih pada subset acak dari data dan fitur, lalu hasil prediksi dari semua model digabungkan untuk menghasilkan prediksi akhir. Random Forest menggunakan teknik bagging (bootstrap aggregating) yang melibatkan pelatihan beberapa decision trees pada sampel data yang berbeda untuk mengurangi overfitting dan meningkatkan stabilitas model. [Dicoding](https://www.dicoding.com/academies/319/tutorials/18585?from=18580)
- Gradient Boosting Machine (GBM) adalah metode ensemble learning yang menggabungkan beberapa model sederhana untuk meningkatkan performa prediksi. GBM bekerja dengan cara membangun model secara bertahap, di mana setiap model baru memperbaiki kesalahan prediksi model sebelumnya. Pada setiap iterasi, model baru ditambahkan untuk memperbaiki hasil prediksi, sehingga secara bertahap meningkatkan akurasi model secara keseluruhan. Pendekatan GBM bersifat "greedy" karena terus menyesuaikan prediksi hingga mencapai performa optimal. [Medium](https://medium.com/@ichlasulamal12/gradient-boosting-machine-konsep-implementasi-dan-aplikasi-f33be4f68052#:~:text=Gradient%20Boosting%20Machine%20(GBM)%20merupakan%20salah%20satu%20metode%20dalam%20machine)
- XGBoost (Extreme Gradient Boosting) adalah algoritma supervised learning yang sangat efektif dan populer untuk tugas klasifikasi dan regresi. XGBoost merupakan implementasi dari teknik gradient boosting yang mengoptimalkan dan mempercepat proses boosting model.
### Feature Important
![Feature Important](https://github.com/user-attachments/assets/4cc10501-25f8-4f71-8a61-fb2cf3c00d7d)

Setelah menerapkan ke empat model yaitu Decision Tree, Gradient Boosting Machines (GBM), Random Forest dan XgBoost, Terlihat 3 fitur teratas yang paling mempengaruhi revenue dari pelanggan yaitu PageValues, ProductRelated_Duration, dan ExitRates

- PageValues: Fitur ini sangat penting karena mencerminkan nilai rata-rata halaman yang dikunjungi oleh pelanggan. Semakin tinggi nilai ini, semakin besar kemungkinan pelanggan akan melakukan pembelian (revenue). Hal ini karena PageValues menunjukkan kontribusi halaman tertentu terhadap transaksi.

- ProductRelated_Duration: Durasi yang dihabiskan oleh pengguna pada halaman-halaman terkait produk. Semakin lama seorang pelanggan menghabiskan waktu untuk melihat produk, semakin besar kemungkinan mereka tertarik untuk membeli, yang akhirnya berdampak positif terhadap revenue.

- ExitRates: Persentase pengunjung yang meninggalkan situs dari halaman tertentu. ExitRates yang lebih tinggi bisa menjadi indikator negatif, di mana pelanggan cenderung meninggalkan situs tanpa melakukan pembelian. Namun, ExitRates yang lebih rendah pada halaman penting menunjukkan potensi yang lebih besar untuk menghasilkan revenue.

## Evaluasi
Beberapa Evaluasi model yang digunakan yaitu menggunakan:
* ROC AUC (Receiver Operating Characteristic Area Under the Curve): Nilai ini menunjukkan seberapa baik model dapat membedakan antara kelas positif dan negatif. Semakin mendekati 1, semakin baik model.
Visualisasi ROC Curve: Membandingkan dua model dalam hal trade-off antara True Positive Rate (TPR) dan False Positive Rate (FPR).

* Confusion Matrix:
   * True Positives (TP): Kasus positif yang benar-benar diprediksi sebagai positif.
   * False Positives (FP): Kasus negatif yang salah diprediksi sebagai positif.
   * True Negatives (TN): Kasus negatif yang benar-benar diprediksi sebagai negatif.
   * False Negatives (FN): Kasus positif yang salah diprediksi sebagai negatif.

* Classification Report: 
  * Akurasi : mengukur sejauh mana model berhasil memprediksi dengan benar secara keseluruhan. TP+TN/(TP+TN+FP+FN).
  * Presisi : mengukur seberapa akurat model dalam memprediksi kelas positif. TP/(TP+FP).
  * Recall : mengukur sejauh mana model klasifikasi dapat mengidentifikasi semua kasus positif yang sebenarnya. TP/(TP+FP)

### Perbandingan ROC AUC Curve
![ROC AUC Curve](https://github.com/user-attachments/assets/29dac46b-b3b9-4e6e-9e3a-d129ce17cfad)
Berdasarkan ROC AUC Curve dimana semakin mendekati nilai 1, maka model semakin baik terlihat bahwa Gradient Boosting Machines adalah algoritma yang paling baik dalam membedakan antara kelas True Positive dan Fale Positive dengan nilai 0,914.

### Perbandingan Confussion Matrix 
![Confussion Matrix](https://github.com/user-attachments/assets/7740c6af-6a4c-43c0-8d57-b17de4f25b92)

### Perbandingan Classification Report
#### Decision Tree
| Class | Precision | Recall | F1-Score | Support |
|-------|-----------|--------|----------|---------|
| 0     | 0.915     | 0.913  | 0.914    | 2059    |
| 1     | 0.536     | 0.542  | 0.539    | 382     |
| **Accuracy** | | | 0.855 | 2441 |
| **Macro Avg** | 0.726     | 0.727  | 0.727    | 2441    |
| **Weighted Avg** | 0.856     | 0.855  | 0.855    | 2441    |

#### Random Forest
| Class | Precision | Recall | F1-Score | Support |
|-------|-----------|--------|----------|---------|
| 0     | 0.919     | 0.949  | 0.934    | 2059    |
| 1     | 0.667     | 0.550  | 0.603    | 382     |
| **Accuracy** | | | 0.887 | 2441 |
| **Macro Avg** | 0.793     | 0.749  | 0.768    | 2441    |
| **Weighted Avg** | 0.880     | 0.887  | 0.882    | 2441    |

#### Gradient Boosting
| Class | Precision | Recall | F1-Score | Support |
|-------|-----------|--------|----------|---------|
| 0     | 0.927     | 0.955  | 0.941    | 2059    |
| 1     | 0.709     | 0.594  | 0.647    | 382     |
| **Accuracy** | | | 0.898 | 2441 |
| **Macro Avg** | 0.818     | 0.775  | 0.794    | 2441    |
| **Weighted Avg** | 0.893     | 0.898  | 0.895    | 2441    |

#### XGBoost
| Class | Precision | Recall | F1-Score | Support |
|-------|-----------|--------|----------|---------|
| 0     | 0.924     | 0.951  | 0.937    | 2059    |
| 1     | 0.686     | 0.579  | 0.628    | 382     |
| **Accuracy** | | | 0.893 | 2441 |
| **Macro Avg** | 0.805     | 0.765  | 0.783    | 2441    |
| **Weighted Avg** | 0.887     | 0.893  | 0.889    | 2441    |

* Decision Tree memiliki akurasi yang cukup baik (85.5%), namun performa untuk kelas 1 (dengan precision 53,6% dan recall 54,2%) menunjukkan bahwa model ini kesulitan mengidentifikasi kasus positif (kelas 1). F1-Score yang rendah untuk kelas 1 juga menunjukkan ketidakseimbangan dalam prediksi.

* Random Forest memberikan peningkatan akurasi (88.7%) dibandingkan Decision Tree. Precision dan F1-Score untuk kelas 1 meningkat signifikan (precision 66,7% dan F1-Score 60,3%), menunjukkan bahwa model ini lebih baik dalam mengidentifikasi kasus positif (kelas 1). Namun, recall untuk kelas 1 (55%) masih rendah, artinya model ini tidak dapat mendeteksi semua kasus positif.

* Gradient Boosting memberikan hasil terbaik dari segi accuracy (89.8%) dan precision untuk kelas 1 (70,9%). Namun, recall untuk kelas 1 masih lebih rendah (59,4%), meskipun sedikit lebih baik daripada Random Forest. F1-Score untuk kelas 1 juga meningkat menjadi 64,7%, menunjukkan kemampuan model yang lebih baik dalam mengidentifikasi kasus positif secara keseluruhan.

* XGBoost menunjukkan performa yang mendekati Gradient Boosting, dengan accuracy yang tinggi (89.3%). Precision untuk kelas 1 (68,6%) dan recall (57,9%) masih lebih baik dibandingkan Random Forest, tetapi sedikit lebih rendah dibandingkan Gradient Boosting. Namun, secara keseluruhan model ini juga memberikan keseimbangan yang cukup baik dalam memprediksi kedua kelas.

## Interpretasi:
- **Berdasarkan analisis dan model machine learning 3 fitur yang paling berpengaruh dalam menghasilkan Revenue oleh Pelanggan yaitu PageValues, ProductRelated_Duration, dan ExitRates.**

- **Kemudan Algoritma Machine Learning terbaik untuk memprediksi revenue oleh pelanggan yaitu Gradien Boosting Machines (GBM) dengan nilai ROC AUC: 0,914 ini berarti model sangat baik dalam membedakan kelas positif dan negatif. Akurasi dari GBM paling tinggi dari model lainyya yaitu 89,8%.**

## Referensi

1. [Dicoding](https://www.dicoding.com/academies/319/tutorials/17116) (2024). *Content Based Filtering*
2. [AWS Amazon](https://aws.amazon.com/id/what-is/deep-learning/#:~:text=Deep%20learning%20adalah%20metode%20dalam%20kecerdasan%20buatan%20(AI)%20yang%20mengajarkan). *Apa itu Deep Learning*
3. [Badan Pusat Statistika Indonesia](https://web-api.bps.go.id/download.php?f=5g3vWbrA+R3h1GRyjNFOdHcxNW1QNmZVS1BvK0hRdEQ3VjRLT1NZYVFOa25qb1hscXBlbWxzU3prSzJWNUpXeGJwMHY1L3lNY1V5QXZmOW11TlBSQUlhVEFjNFNScjh2aS9xL1NEZVpvRlhiV3RNT2JPU3VCQnpndkEvYmlZdHpHaGNKV0N4enNYaEpaTHB2cDdqVE13a0pYVmdETmVFeVZFN0pBU2ZNUTQwRU1UQS81MkhwMXBYd2l0dFhYS2JzY2Frd1RjNU1LYkJRZGVtQWkzcW1lR041SnVwVU02a2VCNlBwbmwyWGFmMXJhbHZpbzF5U08wdEJPWHdMMjNvY0lRdy9IOHhPeXhYalJlRmc=&_gl=1*1xp0dwg*_ga*MjAzMjcyMjU2Ni4xNjk1MzA3OTIx*_ga_XXTTVXWHDB*MTcyNzI0OTAxOS4xOC4xLjE3MjcyNTAyNzkuMC4wLjA) . *Statistik E-Commerce 2022/2023)*
4. [BINUS](https://sis.binus.ac.id/2022/01/21/decision-tree-algoritma-beserta-contohnya-pada-data-mining/#:~:text=Sebuah%20node%20keputusan%20(misalnya,%20Cuaca/%20Outlook)%20memiliki%20dua%20atau%20lebih) *DECISION TREE ALGORITMA BESERTA CONTOHNYA PADA DATA MINING*
5. [Medium](https://medium.com/@ichlasulamal12/gradient-boosting-machine-konsep-implementasi-dan-aplikasi-f33be4f68052#:~:text=Gradient%20Boosting%20Machine%20(GBM)%20merupakan%20salah%20satu%20metode%20dalam%20machine)  *Gradient Boosting Machine: Konsep, Implementasi, dan Aplikasi*



