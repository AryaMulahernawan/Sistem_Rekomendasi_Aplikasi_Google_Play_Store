# Laporan Proyek Machine Learning - Nama Anda

## Project Overview

Kemajuan teknologi serta meningkatnya penggunaan smartphone secara global telah memicu lonjakan besar dalam jumlah aplikasi mobile, khususnya di platform Android melalui Google Play Store. Berdasarkan laporan dari Statista (2024), lebih dari 3 juta aplikasi tersedia di platform tersebut pada awal tahun 2024 [9Statista 20240](https://www.statista.com/statistics/276623/number-of-apps-available-in-leading-app-stores/). Namun, banyaknya pilihan ini justru bisa menjadi hambatan bagi pengguna yang ingin menemukan aplikasi yang benar-benar sesuai dengan kebutuhan dan preferensi mereka.

Untuk menjawab tantangan tersebut, proyek ini dirancang untuk mengembangkan sebuah sistem rekomendasi aplikasi di Google Play Store. Tujuan utamanya adalah membantu pengguna menemukan aplikasi yang relevan dan berkualitas dengan lebih mudah. Sistem ini akan memanfaatkan data historis aplikasi seperti kategori, rating, jumlah unduhan, ukuran, harga, dan fitur lainnya. Melalui pendekatan tersebut, rekomendasi yang dihasilkan diharapkan lebih akurat dan sesuai dengan karakteristik pengguna.

Urgensi dari proyek ini terlihat dari beberapa hal. Pertama, sistem ini mampu mengurangi waktu yang dibutuhkan pengguna dalam mencari aplikasi yang tepat. Kedua, rekomendasi yang personal bisa meningkatkan kepuasan dan keterlibatan pengguna terhadap aplikasi yang dipilih. Ketiga, dari sisi pengembang, sistem ini dapat menjadi sarana untuk memperluas jangkauan dan meningkatkan visibilitas aplikasi mereka di tengah persaingan yang ketat.

Dari perspektif ilmiah, sistem rekomendasi telah menjadi fokus banyak penelitian. Aggarwal (2016), dalam bukunya Recommender Systems: The Textbook, membahas secara komprehensif berbagai metode yang umum digunakan dalam sistem rekomendasi, seperti content-based filtering dan collaborative filtering [Aggarwal, 2016](https://doi.org/10.1007/978-3-319-29659-3). Sementara itu, Ricci dan rekan-rekannya dalam Recommender Systems Handbook menjelaskan pentingnya peran sistem rekomendasi dalam menyaring informasi dan membantu pengguna dalam pengambilan keputusan di era digital [Ricci et al., 2015](https://doi.org/10.1007/978-1-4899-7637-6).

Referensi
Aggarwal, C. C. (2016). Recommender Systems: The Textbook. Springer. https://doi.org/10.1007/978-3-319-29659-3
Ricci, F., Rokach, L., & Shapira, B. (2015). Recommender Systems Handbook (2nd ed.). Springer. https://doi.org/10.1007/978-1-4899-7637-6
Statista. (2024). Number of apps available in leading app stores as of 1st quarter 2024. https://www.statista.com/statistics/276623/number-of-apps-available-in-leading-app-stores/

## Business Understanding

Pada bagian ini, Anda perlu menjelaskan proses klarifikasi masalah.

Bagian laporan ini mencakup:

### Problem Statements

Menjelaskan pernyataan masalah:
- Pernyataan Masalah 1
- Pernyataan Masalah 2
- Pernyataan Masalah n

### Goals

Menjelaskan tujuan proyek yang menjawab pernyataan masalah:
- Jawaban pernyataan masalah 1
- Jawaban pernyataan masalah 2
- Jawaban pernyataan masalah n

Semua poin di atas harus diuraikan dengan jelas. Anda bebas menuliskan berapa pernyataan masalah dan juga goals yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**:
- Menambahkan bagian “Solution Approach” yang menguraikan cara untuk meraih goals. Bagian ini dibuat dengan ketentuan sebagai berikut: 

    ### Solution statements
    - Mengajukan 2 atau lebih solution approach (algoritma atau pendekatan sistem rekomendasi).

## Data Understanding
Paragraf awal bagian ini menjelaskan informasi mengenai jumlah data, kondisi data, dan informasi mengenai data yang digunakan. Sertakan juga sumber atau tautan untuk mengunduh dataset. Contoh: [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Restaurant+%26+consumer+data).

Selanjutnya, uraikanlah seluruh variabel atau fitur pada data. Sebagai contoh:  

Variabel-variabel pada Restaurant UCI dataset adalah sebagai berikut:
- accepts : merupakan jenis pembayaran yang diterima pada restoran tertentu.
- cuisine : merupakan jenis masakan yang disajikan pada restoran.
- dst

**Rubrik/Kriteria Tambahan (Opsional)**:
- Melakukan beberapa tahapan yang diperlukan untuk memahami data, contohnya teknik visualisasi data beserta insight atau exploratory data analysis.

## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

## Modeling
Tahapan ini membahas mengenai model sisten rekomendasi yang Anda buat untuk menyelesaikan permasalahan. Sajikan top-N recommendation sebagai output.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menyajikan dua solusi rekomendasi dengan algoritma yang berbeda.
- Menjelaskan kelebihan dan kekurangan dari solusi/pendekatan yang dipilih.

## Evaluation
Pada bagian ini Anda perlu menyebutkan metrik evaluasi yang digunakan. Kemudian, jelaskan hasil proyek berdasarkan metrik evaluasi tersebut.

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.
