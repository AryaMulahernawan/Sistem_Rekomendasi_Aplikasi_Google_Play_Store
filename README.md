# Laporan Proyek Machine Learning - Nama Anda

## Project Overview

Kemajuan teknologi serta meningkatnya penggunaan smartphone secara global telah memicu lonjakan besar dalam jumlah aplikasi mobile, khususnya di platform Android melalui Google Play Store. Berdasarkan laporan dari Statista (2024), lebih dari 3 juta aplikasi tersedia di platform tersebut pada awal tahun 2024 [(Statista 2024)](https://www.statista.com/statistics/276623/number-of-apps-available-in-leading-app-stores/). Namun, banyaknya pilihan ini justru bisa menjadi hambatan bagi pengguna yang ingin menemukan aplikasi yang benar-benar sesuai dengan kebutuhan dan preferensi mereka.

Untuk menjawab tantangan tersebut, proyek ini dirancang untuk mengembangkan sebuah sistem rekomendasi aplikasi di Google Play Store. Tujuan utamanya adalah membantu pengguna menemukan aplikasi yang relevan dan berkualitas dengan lebih mudah. Sistem ini akan memanfaatkan data historis aplikasi seperti kategori, rating, jumlah unduhan, ukuran, harga, dan fitur lainnya. Melalui pendekatan tersebut, rekomendasi yang dihasilkan diharapkan lebih akurat dan sesuai dengan karakteristik pengguna.

Urgensi dari proyek ini terlihat dari beberapa hal. Pertama, sistem ini mampu mengurangi waktu yang dibutuhkan pengguna dalam mencari aplikasi yang tepat. Kedua, rekomendasi yang personal bisa meningkatkan kepuasan dan keterlibatan pengguna terhadap aplikasi yang dipilih. Ketiga, dari sisi pengembang, sistem ini dapat menjadi sarana untuk memperluas jangkauan dan meningkatkan visibilitas aplikasi mereka di tengah persaingan yang ketat.

Dari perspektif ilmiah, sistem rekomendasi telah menjadi fokus banyak penelitian. Aggarwal (2016), dalam bukunya Recommender Systems: The Textbook, membahas secara komprehensif berbagai metode yang umum digunakan dalam sistem rekomendasi, seperti content-based filtering dan collaborative filtering [Aggarwal, 2016](https://doi.org/10.1007/978-3-319-29659-3). Sementara itu, Ricci dan rekan-rekannya dalam Recommender Systems Handbook menjelaskan pentingnya peran sistem rekomendasi dalam menyaring informasi dan membantu pengguna dalam pengambilan keputusan di era digital [Ricci et al., 2015](https://doi.org/10.1007/978-1-4899-7637-6).

Referensi
Aggarwal, C. C. (2016). Recommender Systems: The Textbook. Springer. https://doi.org/10.1007/978-3-319-29659-3
Ricci, F., Rokach, L., & Shapira, B. (2015). Recommender Systems Handbook (2nd ed.). Springer. https://doi.org/10.1007/978-1-4899-7637-6
Statista. (2024). Number of apps available in leading app stores as of 1st quarter 2024. https://www.statista.com/statistics/276623/number-of-apps-available-in-leading-app-stores/

## Business Understanding
Sistem rekomendasi merupakan salah satu teknologi penting dalam industri digital, termasuk pada platform distribusi aplikasi seperti Google Play Store. Dengan jumlah aplikasi yang sangat besar dan beragam kategori, pengguna kerap mengalami kesulitan dalam menemukan aplikasi yang sesuai dengan preferensi mereka. Hal ini mendorong perlunya sistem rekomendasi yang cerdas dan relevan untuk meningkatkan pengalaman pengguna sekaligus memperbesar peluang unduhan aplikasi.

Proyek ini bertujuan untuk membangun sistem rekomendasi aplikasi berbasis data yang tersedia, tanpa data eksplisit dari pengguna. Dengan memanfaatkan informasi fitur dari aplikasi seperti kategori, rating, jumlah unduhan, status gratis/berbayar, dan lainnya, sistem akan memberikan saran aplikasi yang mirip dengan aplikasi tertentu atau aplikasi populer secara umum.

### Problem Statements
1. Bagaimana cara membuat sistem rekomendasi aplikasi yang memberikan saran kepada pengguna berdasarkan kemiripan fitur aplikasi (seperti kategori)?

2. Bagaimana cara mengukur performa model sistem rekomendasi aplikasi secara kuantitatif?

### Goals
Menghasilkan rekomendasi aplikasi sebanyak Top-N rekomendasi yang relevan untuk pengguna berdasarkan kemiripan fitur aplikasi.

Mengukur performa model sistem rekomendasi menggunakan metrik evaluasi seperti cosine similarity, precision@k, atau diversity score untuk menilai relevansi dan keberagaman rekomendasi.


 ### Solution statements
Solution Approach
Untuk mencapai tujuan yang telah ditetapkan, digunakan dua pendekatan sistem rekomendasi berikut:

1. Content-Based Filtering
Pendekatan ini merekomendasikan aplikasi berdasarkan kemiripan fitur konten antar aplikasi. Fitur-fitur yang digunakan antara lain: Category (kategori aplikasi), Rating dan Rating Count, Installs, Free atau Price, Size, Content Rating

Fitur-fitur tersebut diolah menjadi vektor fitur aplikasi, lalu dihitung tingkat kemiripannya menggunakan metode seperti cosine similarity. Sistem ini akan menyarankan aplikasi yang mirip dengan aplikasi yang sudah populer atau telah dipilih pengguna sebelumnya.

2. Popularity-Based Filtering (Sebagai Alternatif Collaborative Filtering)
Karena tidak tersedia data interaksi pengguna (seperti ID pengguna, histori klik, atau rating per pengguna), maka pendekatan collaborative filtering klasik tidak dapat diterapkan. Sebagai gantinya, digunakan pendekatan berbasis popularitas sebagai baseline:

Menampilkan aplikasi dengan jumlah instalasi, rating count, atau rating tertinggi sebagai rekomendasi umum.


## Data Understanding
Pada tahap ini, dilakukan pemahaman awal terhadap dataset yang digunakan dalam proyek sistem rekomendasi aplikasi. Informasi yang disampaikan mencakup jumlah data, kondisi data, serta penjelasan setiap fitur dalam dataset.

Dataset yang digunakan diperoleh dari sumber berikut: [Kaggle](https://www.kaggle.com/datasets/gauthamp10/google-playstore-apps)

Dataset ini terdiri dari 2.312.944 baris dan 24 kolom. Setiap baris merepresentasikan satu aplikasi yang tersedia di Google Play Store, sementara kolom-kolomnya berisi informasi terkait atribut aplikasi tersebut.

Berikut adalah penjelasan singkat mengenai fitur/variabel dalam dataset:
- App Name	       : Nama aplikasi seperti yang ditampilkan di Play Store.
- App Id	       : ID unik aplikasi di Play Store (biasanya berupa nama paket, seperti com.example.app).
- Category	       : Kategori aplikasi, seperti Games, Education, Shopping, dll.
- Rating	       : Nilai rata-rata penilaian pengguna (biasanya dari 1.0 hingga 5.0).
- Rating Count     : Jumlah total penilaian atau rating yang diberikan oleh pengguna.
- Installs	       : Jumlah pemasangan aplikasi (dalam format seperti "1,000+").
- Minimum Installs : Estimasi jumlah minimum instalasi berdasarkan data.
- Maximum Installs : Estimasi jumlah maksimum instalasi berdasarkan data.
- Free	           : Apakah aplikasi gratis (True) atau berbayar (False).
- Price	           : Harga aplikasi jika tidak gratis.
- Currency         : Mata uang yang digunakan untuk harga (misalnya USD, IDR).
- Size	           : Ukuran file aplikasi.
- Minimum Android  : Versi minimum Android yang dibutuhkan untuk menjalankan aplikasi.
- Developer Id     : ID unik pengembang di Play Store.
- Developer Website : Situs web resmi dari pengembang aplikasi (jika tersedia).
- Developer Email	: Alamat email kontak pengembang.
- Released	        : Tanggal pertama kali aplikasi dirilis di Play Store.
- Last Updated	    : Tanggal terakhir aplikasi diperbarui.
- Content Rating	: Rating konten aplikasi berdasarkan umur pengguna (seperti "Everyone", "Teen", dll).
- Privacy Policy	: URL ke kebijakan privasi aplikasi.
- Ad Supported	    : Menunjukkan apakah aplikasi mendukung iklan (True/False).
- In App Purchases	: Menunjukkan apakah aplikasi memiliki pembelian dalam aplikasi (True/False).
- Editors Choice	: Apakah aplikasi mendapat label “Pilihan Editor” dari Google Play.
- Scraped Time      : Waktu saat data aplikasi ini dikumpulkan/scraped.

  Tetapi karena beberapa pertimbangan sebagai berikut:

1. Kolom-kolom tersebut memiliki nilai informatif yang tinggi dalam merepresentasikan popularitas, kualitas, serta segmentasi aplikasi.
2. Kolom yang dipilih cenderung memiliki data yang lebih lengkap dan bersih, sehingga dapat meminimalkan risiko ketidaksesuaian atau missing value pada tahap pemrosesan data.
3. Fitur-fitur tersebut lebih mudah untuk diolah dan dianalisis, baik dalam analisis statistik deskriptif maupun dalam proses modeling seperti sistem rekomendasi

maka Dalam proses pemilihan fitur, dipilih 11 kolom utama dari dataset
- App Name	       : Nama aplikasi seperti yang ditampilkan di Play Store.
- App Id	       : ID unik aplikasi di Play Store (biasanya berupa nama paket, seperti com.example.app).
- Category	       : Kategori aplikasi, seperti Games, Education, Shopping, dll.
- Rating	       : Nilai rata-rata penilaian pengguna (biasanya dari 1.0 hingga 5.0).
- Rating Count     : Jumlah total penilaian atau rating yang diberikan oleh pengguna.
- Installs	       : Jumlah pemasangan aplikasi (dalam format seperti "1,000+").
- Free	           : Apakah aplikasi gratis (True) atau berbayar (False).
- Price	           : Harga aplikasi jika tidak gratis.
- Size	           : Ukuran file aplikasi.
- Minimum Android  : Versi minimum Android yang dibutuhkan untuk menjalankan aplikasi.
jadi Dataset nya terdiri dari 2.312.944 baris dan 11 kolom.


**Rubrik/Kriteria Tambahan (Opsional)**:
- Melakukan beberapa tahapan yang diperlukan untuk memahami data, contohnya teknik visualisasi data beserta insight atau exploratory data analysis.
![Image](https://github.com/user-attachments/assets/7c2dbb9c-4d9e-4edf-b9d9-82bb318bf7d0)
![Image](https://github.com/user-attachments/assets/bbcf301d-754b-45a9-a809-fd2c1ce7e5c4)
## Data Preparation
1. Feature Selection
**Proses:** Memilih 11 kolom penting dari dataset asli Google-Playstore.csv yang relevan untuk analisis dan sistem rekomendasi, antara lain App Name, App Id, Category, Rating, Rating Count, Installs, Free, Price, Size, dan Minimum Android.

Alasan: Kolom-kolom ini dipilih karena memiliki nilai informatif tinggi terhadap popularitas dan segmentasi aplikasi, serta tersedia secara konsisten dan mudah diolah untuk modeling.

3. Missing Value Handling
**Proses:**
- Menghapus baris dengan nilai 0 pada kolom Rating dan Rating Count, karena dianggap sebagai data tidak valid.
- Menghapus baris yang memiliki nilai null pada kolom-kolom kunci seperti App Name, Rating, Rating Count, Size, dan Minimum Android.
**Alasan:** Data kosong atau nol pada kolom penting dapat menyebabkan bias atau kesalahan pada analisis dan model, sehingga perlu dihapus untuk meningkatkan kualitas data.

4. Duplicate Handling
**Proses:** Mengecek jumlah data duplikat pada dataset dan di data tidak ditemukan data yang duplikat.
**Alasan:** Mencegah model terpengaruh oleh entri ganda yang bisa menyebabkan informasi berulang.

5. Outlier Handling (Winsorizing)
**Proses:** Menggunakan teknik winsorizing pada kolom Rating dan Rating Count dengan menggantikan nilai ekstrem di luar batas IQR dengan nilai batas atas/bawah.
**Alasan:** Mengurangi pengaruh outlier ekstrem yang dapat merusak distribusi data dan menyebabkan model bias.

6. Data Visualization & Exploratory Analysis
**Proses:**
Visualisasi boxplot untuk kolom numerik guna melihat sebaran dan outlier.
Visualisasi histogram dan pairplot untuk melihat distribusi data.
Matriks korelasi untuk mengetahui hubungan antar fitur numerik.
**Alasan:** Untuk memahami pola data, mendeteksi potensi masalah, dan menyesuaikan strategi pemodelan.

7. Sampling
**Proses:** Mengambil sampel acak sebanyak 10.000 baris dari dataset bersih.
**Alasan:** Untuk mempercepat proses komputasi, terutama saat menghitung similarity matrix dan pelatihan model.

8. Text Vectorization
**Proses:** Menggunakan TF-IDF Vectorizer pada kolom Category untuk mengubah data teks menjadi representasi numerik.
**Alasan:** Karena sistem rekomendasi ini berbasis content-based filtering, diperlukan representasi numerik dari kategori aplikasi agar kemiripan antar aplikasi dapat dihitung.

9. Cosine Similarity
**Proses:**: Menghitung kemiripan antar aplikasi berdasarkan hasil vektorisasi TF-IDF.
**Alasan:** Cosine similarity digunakan untuk mengukur seberapa mirip dua aplikasi berdasarkan kategori mereka, yang menjadi dasar sistem rekomendasi.

## Modeling
Tahapan ini membahas pembangunan model sistem rekomendasi yang dirancang untuk membantu pengguna menemukan aplikasi yang relevan berdasarkan preferensi atau kesamaan konten.

1. Pendekatan 1: Content-Based Filtering dengan TF-IDF + Cosine Similarity
Pada pendekatan pertama, digunakan teknik content-based filtering yang memanfaatkan informasi dari fitur kategori (Category) setiap aplikasi. Pendekatan ini didasarkan pada asumsi bahwa aplikasi yang mirip dari segi kategori akan relevan satu sama lain.

**Langkah-Langkah:**
- Representasi kategori diubah menjadi vektor numerik menggunakan TF-IDF Vectorizer.

- Kemudian dihitung cosine similarity antar aplikasi berdasarkan hasil vektorisasi.

- Untuk setiap aplikasi yang dimasukkan, sistem akan merekomendasikan Top-10 aplikasi serupa berdasarkan skor kemiripan tertinggi.

a. Kelebihan:
- Tidak bergantung pada data pengguna atau interaksi historis.

- Bisa merekomendasikan item baru (cold-start friendly, selama deskripsinya tersedia).

- Mudah diimplementasikan dan ditafsirkan.

b. Kekurangan:
- Rekomendasi terbatas hanya pada konten yang tersedia (hanya berdasarkan kategori).

- Tidak bisa menangkap preferensi pengguna secara personal.

2. Pendekatan 2: Popularity-Based Filtering
Sebagai pembanding, juga dibuat pendekatan berbasis popularitas. Pendekatan ini menyarankan aplikasi dengan jumlah pemasangan (Installs), rating tertinggi (Rating), dan jumlah rating (Rating Count) terbanyak.

**Langkah-Langkah:**
- Aplikasi diurutkan berdasarkan gabungan tiga metrik: Installs, Rating Count, dan Rating.
- Diambil Top-10 aplikasi terpopuler sebagai rekomendasi universal untuk semua pengguna.

a. Kelebihan:
- Sederhana dan efektif dalam banyak kasus.

- Relevan bagi pengguna baru yang belum memiliki preferensi khusus.

b. Kekurangan:
- Tidak personalisasi (semua pengguna mendapat rekomendasi yang sama).

- Rentan bias terhadap aplikasi lama dan terkenal.
**Top-N Recommendation Output**
Berikut adalah contoh hasil rekomendasi untuk beberapa aplikasi:
![Image](https://github.com/user-attachments/assets/4051d424-ad3e-48da-b72d-16d69360f044)

Sistem merekomendasikan beberapa aplikasi lain yang berada dalam kategori Shopping dan memiliki kemiripan fitur dengan Supermarket Deal Calculator. Beberapa aplikasi yang direkomendasikan antara lain Shopping List Barcode Scanner, FidMe Loyalty Cards & Deals at Grocery Supermarkets, hingga Toy Store App. Rekomendasi ini relevan karena memiliki fungsi serupa dalam membantu aktivitas berbelanja dan pengelolaan produk.

Rekomendasi untuk aplikasi Happy birth:
Untuk aplikasi bertema hiburan seperti Happy birth, sistem menghasilkan rekomendasi dari kategori Entertainment seperti LAVA TV, Pelet Online Prank, dan Among us mod MCPE 2021. Aplikasi-aplikasi ini memiliki konten hiburan yang bervariasi, dari video lucu hingga mod game, yang dinilai sesuai dengan selera pengguna aplikasi Happy birth.

Rekomendasi untuk aplikasi Fire Truck Simulator 3D:
Aplikasi ini termasuk dalam kategori Simulation, sehingga sistem memberikan rekomendasi aplikasi simulasi lainnya seperti Car Driving, Armed Air Forces, dan Real Sports Car Game. Aplikasi-aplikasi ini menawarkan pengalaman interaktif dan simulasi kendaraan atau aktivitas serupa yang sesuai dengan konsep dari Fire Truck Simulator 3D.

![Image](https://github.com/user-attachments/assets/78d826c6-6a7f-41e8-864b-9d1337b788b5)

Hasil yang ditampilkan menunjukkan 10 aplikasi yang dianggap paling populer, seperti:
- Contacts dari Google, dengan lebih dari 500 juta pemasangan.
- Книга Вслух. Аудиокниги, aplikasi audiobook dengan rating tinggi (4.9).
- Lose Belly Fat Workouts dan Taiwan Drivers License Test, yang meskipun jumlah installs lebih kecil, tetap masuk karena rating dan jumlah ratingnya tinggi.
Aplikasi-aplikasi ini berasal dari berbagai kategori, menunjukkan bahwa popularitas tidak hanya bergantung pada satu jenis aplikasi, tetapi juga kualitas.

## Evaluation
Evaluasi sistem rekomendasi dilakukan untuk mengukur sejauh mana hasil rekomendasi yang dihasilkan oleh model dapat dianggap relevan, bervariasi, dan tidak terlalu seragam. Dalam proyek ini, digunakan tiga metrik evaluasi utama yang umum digunakan dalam sistem rekomendasi:

### 1. Precision@K
**Definisi:**
Precision@K mengukur proporsi item yang relevan dari total item yang direkomendasikan sebanyak K.
**Formula:**


**Implementasi:**
Sebuah rekomendasi dianggap relevan jika aplikasi yang direkomendasikan memiliki kategori yang sama dengan aplikasi input.

**Hasil:**
Untuk beberapa aplikasi seperti:
- Supermarket Deal Calculator: Precision@10 = 0.80

- Happy birth: Precision@10 = 0.70

- 40 Hadist Peristiwa Akhir Zaman: Precision@10 = 0.60

Rata-rata precision menunjukkan bahwa sistem dapat memberikan rekomendasi yang cukup relevan dengan kategori aplikasi awal.

### 2. Diversity Score
**Definisi:**
Diversity score mengukur seberapa beragam kategori dari aplikasi yang direkomendasikan. Semakin banyak kategori berbeda dalam daftar rekomendasi, semakin tinggi nilai diversitas.

**Formula:**

**Hasil:**
Skor diversitas berkisar antara 0.6 hingga 0.8.

Ini menunjukkan bahwa sistem mampu memberikan variasi kategori dalam rekomendasinya, tidak hanya fokus pada satu kategori saja.


### 3. Intra-list Similarity (ILS)
**Definisi:**
ILS mengukur seberapa mirip aplikasi-aplikasi dalam daftar rekomendasi satu sama lain. Semakin rendah ILS, maka semakin beragam dan tidak terlalu seragam item rekomendasinya.
**Formula:**
![Image](https://github.com/user-attachments/assets/3f821a9b-69bd-459e-9494-b27e886af4bc)
![Image](https://github.com/user-attachments/assets/8ec0e5e9-c8f1-448e-9cd0-00e71d81c62f)
![Image](https://github.com/user-attachments/assets/2a2ad68d-20c5-4378-acce-bad03219cbf4)
Dengan sim(i, j) adalah cosine similarity antar dua aplikasi yang direkomendasikan.

**Hasil:**
![Image](https://github.com/user-attachments/assets/a8e5f961-5e37-4078-af5c-d5c174854d95)
![Image](https://github.com/user-attachments/assets/6fe5e789-ed14-4981-b3cb-b27a2248ec5f)
![Image](https://github.com/user-attachments/assets/fbd9b68e-3c29-4e7b-a0a5-3ba546bf076d)
Nilai ILS berkisar 0.55 - 0.70, yang berarti masih terdapat kemiripan antar aplikasi dalam rekomendasi, namun tidak terlalu identik.

Kesimpulan Evaluasi
Sistem rekomendasi berbasis content-based filtering memberikan hasil yang memuaskan berdasarkan:

Relevansi (Precision@10 tinggi)

Keragaman (Diversity Score baik)

Keseimbangan seragam vs beragam (ILS cukup rendah)

Metrik-metrik tersebut dipilih karena sesuai dengan konteks problem dan tujuan sistem, yaitu memberikan rekomendasi aplikasi yang relevan namun tetap bervariasi, khususnya untuk pengguna yang tidak memiliki riwayat interaksi.


**---Ini adalah bagian akhir laporan---**

