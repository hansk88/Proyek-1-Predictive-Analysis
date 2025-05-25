# Laporan Proyek Machine Learning - Hans Kristiandi

## Domain Proyek

### Latar Belakang
Saat ini Indonesia tengah memasuki musim kemarau basah. Fenomena ini merupakan istilah yang merujuk pada kondisi musim kemarau tetapi masih disertai dengan masih tingginya intensitas hujan. Badan Meteorologi, Klimatologi, dan Geofisika (BMKG) memperkirakan kemarau basah akan berlangsung hingga akhir Agustus 2025. Kondisi cuaca yang tidak menentu ini membuat kita sulit beraktivitas dan menggangu jadwal yang telah direncanakan. Misalnya di kota Jakarta, hujan deras dapat terjadi sewaktu-waktu entah di pagi saat ingin berangkat kuliah, siang saat ingin pergi membeli makan, ataupun malam setelah pulang dari kerja. Berangkat dari masalah tersebut, saya tertarik untuk membuat sebuah program untuk memprediksi cuaca dengan mempertimbangkan berbagai variabel seperti suhu, kecepatan angin, dan sebagainya. Dengan demikian, seseorang bisa mengetahui apa yang akan terjadi selanjutnya sehingga dapat bersiap-siap terlebih dahulu.
 
### Mengapa dan bagaimana masalah tersebut harus diselesaikan
Prediksi cuaca merupakan salah satu hal yang penting dilakukan, mengingat kondisi cuaca yang tidak selalu pasti dan cenderung berubah-ubah. Dalam konteks kehidupan sehari-hari, cuaca yang tidak menentu dapat menggangu aktivitas seseorang dan mempengaruhi kesehatan kita. Dalam konteks yang lebih luas, ketidakpastian akan cuaca memberikan pengaruh yang lebih signifikan, misalnya dalam pertanian, ekonomi, lalu lintas, dan bencana alam. Informasi yang akurat akan membantu dalam pengambilan keputusan yang lebih baik dan cepat sehingga dapat mencegah atau setidaknya mengurangi kerusakan/kerugian yang dapat ditimbulkan dari hal-hal tersebut.

Prediksi cuaca bukanlah sesuatu yang mudah dilakukan mengingat adanya berbagai variabel yang turut berpengaruh terhadap kondisi akhirnya. Variabel-variabel seperti tekanan udara, suhu, kelembaban, dan sebagainya menjadikan prediksi cuaca sesuatu yang rumit jika dilakukan tanpa metode yang tepat. Untungnya, setelah mempelajari machine learning, saya mendapatkan ide dan pengetahuan baru untuk solusi atas permasalahan tersebut. Dengan adanya model-model seperti K Nearest Neighbour, Support Vector Machine, Random Forest, dsb maka kita dimungkinkan untuk menghasilkan prediksi yang lebih akurat. 

### Hasil riset terkait atau referensi
- M. Holmstrom, D. Liu, and C. Vo, “Machine learning applied to weather forecasting,” in _Stanford CS229_, Dec. 2016. [Online]. Available: https://cs229.stanford.edu/proj2016/report/HolmstromLiuVo-MachineLearningAppliedToWeatherForecasting-report.
- D. Watson-Paris, “Machine learning for weather and climate are worlds apart,” in _Philosophical Transactions of the Royal Society A Mathematical, Physical and Engineering Sciences_, vol. 379, no. 2194, pp. 1–19, Aug. 2021. [Online]. Available: https://royalsocietypublishing.org/doi/pdf/10.1098/rsta.2020.0098.

## Business Understanding

### Problem Statements

Pernyataan masalah yang dimiliki yaitu:
- Bagaimana membangun model prediksi cuaca yang akurat dengan memanfaatkan machine learning?
- Apakah model yang telah dibangun dapat digunakan untuk memprediksi cuaca dalam kehidupan sehari-hari?

### Goals

Berdasarkan pernyataan masalah yang telah dibuat, tujuannya yaitu:
- Membuat model sederhana yang dapat memprediksi cuaca dengan akurat dengan memanfaatkan machine learning
- Membuat model yang dapat digunakan untuk memprediksi cuaca dalam kehidupan sehari-hari

### Solution Statements

Agar tujuan yang telah dibuat dapat tercapai, solusi dasar yang ditawarkan yaitu:
- Melatih model menggunakan tiga algoritma, yaitu K Nearest Neighbour, Random Forest, dan Boosting Algorithm
- Model yang telah dibuat wajib dievaluasi dan memiliki nilai akurasi dan F1 score minimal 80% supaya dapat menghasilkan data prediksi yang akurat

## Data Understanding
Data yang digunakan pada proyek ini diunduh dari Kaggle, dengan alamat URL yaitu https://www.kaggle.com/datasets/cornflake15/denpasarbalihistoricalweatherdata. Dataset ini berisi tentang data historis cuaca di kota Denpasar, Bali dalam kurun waktu 20 tahun, sejak 1 Januari 1990 hingga 7 Januari 2020 dan dicatat dalam satuan jam. Pemilik dari dataset ini adalah Rudy Hendrawan dan penting untuk diketahui bahwa dataset tersebut dibeli dari Open Weather App sehingga sumber dataset tersebut adalah kredibel dan dapat dipertanggungjawabkan. Adapun dataset berupa file csv dan memiliki jumlah baris sebanyak 264924 yang terdiri atas 32 kolom, dengan rincian sebagai berikut:
- dt: Unix timestamp yang menunjukkan tanggal dan waktu menurut jumlah detik sejak tanggal 1 Januari 1970
- dt_iso: Tanggal dan waktu
- timezone: Perbedaan waktu dari UTC dalam satuan detik
- city_name: Nama kota
- lat: Garis lintang
- lon: Garis kota
- temp: Suhu (dalam satuan Celcius)
- temp_min: Suhu minimum
- temp_max: Suhu maksimum
- pressure: Tekanan udara (dalam satuan hPa)
- sea_level: Tekanan udara di permukaan laut
- grnd_level: Tekanan udara di permukaan tanah
- humidity: Kelembapan (dalam persentase)
- wind_speed: Kecepatan angin (dalam satuan m/s)
- wind_deg: Arah angin (dalam derajat)
- rain_1h: Volume hujan selama 1 jam terakhir (dalam satuan mm)
- rain_3h: Volume hujan selama 3 jam terakhir
- rain_6h: Volume hujan selama 6 jam terakhir
- rain_12h: Volume hujan selama 12 jam terakhir
- rain_24h: Volume hujan selama 24 jam terakhir
- rain_today: Volume hujan pada hari tersebut
- snow_1h: Volume salju selama 1 jam terakhir (dalam satuan mm)
- snow_3h: Volume salju selama 3 jam terakhir
- snow_6h: Volume salju selama 6 jam terakhir
- snow_12h: Volume salju selama 12 jam terakhir
- snow_24h: Volume salju selama 24 jam terakhir
- snow_today: Volume salju pada hari tersebut
- clouds_all: Volume awan (dalam persentase)
- weather_id: Kode unik untuk masing-masing cuaca
- weather_main: Cuaca
- weather_description: Deskripsi detail tentang cuaca
- weather_icon: Kode ikon untuk masing-masing cuaca

### Variabel-variabel pada Dataset

Meski dataset memiliki 32 kolom, namun saat dilakukan EDA didapati bahwa beberapa kolom tidak memiliki nilai sama sekali dan kolom lainnya tidak relevan dengan kolom target (label). Adapun variabel/fitur yang digunakan pada dataset yaitu:
- temp
- temp_min
- temp_max
- pressure
- humidity
- wind_speed
- wind_deg
- clouds_all
Sementara itu kolom target atau label yang digunakan yaitu:
- weather_description

Alasan dari dipilihnya **weather_description** dibandingkan **weather_main** dikarenakan kolom ini lebih lengkap. Misalnya entri pada **weather_main** adalah rain, namun pada **weather_description** entri yang diberikan adalah light rain, heavy rain, dsb sehingga dapat memberikan gambaran yang lebih jelas kepada pengguna.

### Tahapan untuk Memahami Data

Seperti yang telah dijelaskan, variabel/fitur akhir yang dipilih telah melalui berbagai penghapusan kolom yang tidak relevan. Adapun tahapan-tahapan yang dilakukan yaitu:
- dataset.head() -> Bertujuan untuk menampilkan data yang telah dimuat. Dari tahapan ini, dapat dilihat berbagai entri dari semua kolom yang ada
- dataset.info() -> Bertujuan untuk melihat tipe data (float, integer, string, object, datetime, dsb) pada setiap kolom dan berapa banyak baris data yang dimiliki
- dataset.isna().sum() -> Bertujuan untuk melihat kolom mana yang memiliki nilai null dan berapa jumlah null yang dimilikinya
- dataset.duplicated().sum() -> Bertujuan untuk melihat berapa banyak data duplikat yang ada
- dataset.shape() -> Bertujuan untuk melihat jumlah baris dan jumlah kolom pada dataset
- dataset.describe() -> Bertujuan untuk melihat statistik deskriptif (mean, median, Q1, Q3, dsb) dari masing-masing kolom pada dataset

Selain berbagai tahapan EDA di atas, juga dilakukan berbagai visualisasi data untuk mempermudah pemahaman terhadap data yang dimiliki seperti membuat boxplot dan matriks korelasi.
![download (1)](https://github.com/user-attachments/assets/4d8dd1ba-108c-439e-a841-ba7b3164d44f)
Boxplot ini bertujuan untuk melihat outlier pada masing-masing variabel/fitur
![download](https://github.com/user-attachments/assets/ac016ad7-a8c3-409e-aeef-49c97a23d835)
Matriks korelasi ini bertujuan untuk mempermudah pemahaman terhadap hubungan antar variabel dengan label (**weather_desciption**) yang dilengkapi dengan warna dimana merah gelap artinya hubungan korelasi antar variabel sangat kuat dan biru muda artinya hubungan korelasi antar variabel sangat lemah

## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

## Modeling
Tahapan ini membahas mengenai model machine learning yang digunakan untuk menyelesaikan permasalahan. Anda perlu menjelaskan tahapan dan parameter yang digunakan pada proses pemodelan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan kelebihan dan kekurangan dari setiap algoritma yang digunakan.
- Jika menggunakan satu algoritma pada solution statement, lakukan proses improvement terhadap model dengan hyperparameter tuning. **Jelaskan proses improvement yang dilakukan**.
- Jika menggunakan dua atau lebih algoritma pada solution statement, maka pilih model terbaik sebagai solusi. **Jelaskan mengapa memilih model tersebut sebagai model terbaik**.

## Evaluation
Pada bagian ini anda perlu menyebutkan metrik evaluasi yang digunakan. Lalu anda perlu menjelaskan hasil proyek berdasarkan metrik evaluasi yang digunakan.

Sebagai contoh, Anda memiih kasus klasifikasi dan menggunakan metrik **akurasi, precision, recall, dan F1 score**. Jelaskan mengenai beberapa hal berikut:
- Penjelasan mengenai metrik yang digunakan
- Menjelaskan hasil proyek berdasarkan metrik evaluasi

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.

