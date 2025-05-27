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
- Memilih parameter default dari masing-masing algoritma dengan asumsi parameter-parameter tersebut telah diatur sedemikian rupa berdasarkan berbagai eksperimen oleh ahli
- Model yang telah dibuat wajib dievaluasi dan memiliki nilai akurasi dan F1-score minimal 80% supaya dapat menghasilkan data prediksi yang akurat. Pemilihan kedua metrik tersebut dikarenakan akurasi paling mudah dipahami dan menunjukkan persentase prediksi yang benar, sementara F1-score menunjukkan keseimbangan antara precision dan recall. Melalui kedua metrik tersebut, kita dimungkinkan untuk mendapatkan gambaran evaluasi yang menyeluruh terhadap performa model yang telah dibuat

## Data Understanding
Data yang digunakan pada proyek ini diunduh dari Kaggle, dengan alamat URL yaitu https://www.kaggle.com/datasets/cornflake15/denpasarbalihistoricalweatherdata. Dataset ini berisi tentang data historis cuaca di kota Denpasar, Bali dalam kurun waktu 20 tahun, sejak 1 Januari 1990 hingga 7 Januari 2020 dan dicatat dalam satuan jam. Pemilik dari dataset ini adalah Rudy Hendrawan dan penting untuk diketahui bahwa dataset tersebut dibeli dari Open Weather App sehingga sumber dataset tersebut adalah kredibel dan dapat dipertanggungjawabkan. Adapun dataset berupa file csv dan memiliki jumlah baris sebanyak 264924 yang terdiri atas 32 kolom, dengan rincian sebagai berikut:
- dt: Unix timestamp yang menunjukkan tanggal dan waktu menurut jumlah detik sejak tanggal 1 Januari 1970
- dt_iso: Tanggal dan waktu
- timezone: Perbedaan waktu dari UTC dalam satuan detik
- city_name: Nama kota
- lat: Koordinat garis lintang
- lon: Koordinat garis bujur
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

Meski dataset memiliki 32 kolom, namun saat dilakukan EDA didapati bahwa beberapa kolom memiliki entri yang mayoritas berupa nilai null (yaitu kolom **sea_level**, **grnd_level**, **rain_today**, **snow_1h**, **snow_3h**, **snow_6h**, **snow_12h**, **snow_24h**, **snow_today**, **rain_1h**, **rain_3h** **rain_6h** **rain_12h** **rain_24h**) dan kolom lainnya tidak relevan dengan kolom target (kolom yang entrinya tidak informatif dan berpotensi menambah noise/menyebabkan overfitting seperti kolom **dt**, **dt_iso**, **timezone**, **city_name**, **lat**, **lon**, **weather_id**, **weather_main**, **weather_icon**). Adapun variabel/fitur yang digunakan pada dataset yaitu:
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

Seperti yang telah dijelaskan, variabel/fitur akhir yang dipilih telah melalui berbagai tahapan EDA. Adapun tahapan-tahapan yang dilakukan yaitu:
- dataset.head() -> Bertujuan untuk menampilkan data yang telah dimuat. Dari tahapan ini, dapat dilihat berbagai entri dari semua kolom yang ada
- dataset.info() -> Bertujuan untuk melihat tipe data (float, integer, string, object, datetime, dsb) pada setiap kolom dan berapa banyak baris data yang dimiliki
- dataset.isna().sum() -> Bertujuan untuk melihat kolom mana yang memiliki nilai null dan berapa jumlah null yang dimilikinya
- dataset.duplicated().sum() -> Bertujuan untuk melihat berapa banyak data duplikat yang ada
- dataset.shape() -> Bertujuan untuk melihat jumlah baris dan jumlah kolom pada dataset
- dataset.describe() -> Bertujuan untuk melihat statistik deskriptif (mean, median, Q1, Q3, dsb) dari masing-masing kolom pada dataset

Selain berbagai tahapan EDA di atas, juga dilakukan berbagai visualisasi data untuk mempermudah pemahaman terhadap data yang dimiliki seperti membuat boxplot dan matriks korelasi.
![download (1)](https://github.com/user-attachments/assets/4d8dd1ba-108c-439e-a841-ba7b3164d44f)
Boxplot di atas bertujuan untuk melihat outlier pada masing-masing variabel/fitur
![download](https://github.com/user-attachments/assets/ac016ad7-a8c3-409e-aeef-49c97a23d835)
Matriks korelasi di atas bertujuan untuk mempermudah pemahaman terhadap hubungan antar variabel dengan label (**weather_desciption**) yang dilengkapi dengan warna dimana merah gelap artinya hubungan korelasi antar variabel sangat kuat dan biru muda artinya hubungan korelasi antar variabel sangat lemah.

## Data Preparation

Sebelum data digunakan untuk melatih model, data-data tersebut dibersihkan terlebih dahulu dan melewati serangkaian tahapan seperti:

```ruby
dataset.drop(['dt', 'dt_iso', 'timezone', 'city_name', 'lat', 'lon', 'weather_id', 'weather_main', 'weather_icon'], inplace=True, axis=1)
```
Karena kolom seperti tanggal, waktu, lokasi, dsb tidak relevan dengan kolom target (label) maka kolom-kolom tersebut dihapus.

```ruby
dataset.drop(['sea_level', 'grnd_level', 'rain_today', 'snow_1h', 'snow_3h', 'snow_6h', 'snow_12h', 'snow_24h', 'snow_today'], inplace=True, axis=1)
dataset.drop(['rain_1h', 'rain_3h', 'rain_6h', 'rain_12h', 'rain_24h'], inplace=True, axis=1)
```
Karena entri dari kolom ini semuanya atau mayoritas berupa nilai null maka kolom-kolom tersebut juga akan dihapus.

```ruby
check_diff = ((dataset["temp"] != dataset["temp_min"]) & 
              (dataset["temp"] != dataset["temp_max"])).sum()
```
Berdasarkan pengamatan awal, entri dari kolom **temp**, **temp_min**, dan **temp_max** terlihat sama semua. Oleh karena itu kode ini bertujuan untuk mengecek apakah ada entri dari ketiga kolom tersebut yang berbeda. Setelah diperiksa, ditemukan bahwa terdapat beberapa baris dimana entri ketiga kolom berbeda sehingga kolom **temp_min** dan **temp_max** tidak jadi dihapus.

```ruby
dataset.drop_duplicates(inplace=True)
```
Karena adanya data duplikat pada saat EDA maka kode di atas ditulis untuk menghapus nilai duplikat pada dataset. Kode inplace=True berarti perubahan langsung diterapkan pada dataset.

```ruby
filter_outliers = ~((dataset[num_features] < (Q1 - 1.5 * IQR)) |
                    (dataset[num_features] > (Q3 + 1.5 * IQR))).any(axis=1)
```
Berdasarkan pengamatan dari boxplot, ditemukan berbagai variabel/fitur yang mengadung outlier. Kode ini bertujuan untuk menghapus entri-entri yang nilainya berada di luar dari batasan yang telah ditentukan

```ruby
for column in categorical_columns:
    le = LabelEncoder()
    dataset[column] = le.fit_transform(dataset[column])
    label_encoders[column] = le
```
Bertujuan untuk melakukan encoding kolom yang bertipe object (dalam hal ini yaitu kolom target (label) alias **weather_description**) sehingga untuk sementara waktu menjadi angka. Tujuannya adalah untuk melihat korelasi setiap variabel dengan label.

```ruby
for column, encoder in label_encoders.items():
    dataset[column] = encoder.inverse_transform(dataset[column])
```
Karena nantinya akan dilakukan inferensi model, maka kolom target dikembalikan ke bentuk semula untuk memudahkan pengguna saat ingin menggunakan program

```ruby
X = dataset.drop(["weather_description"],axis =1)
y = dataset["weather_description"]
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size = 0.2, random_state = 42)
```
Bertujuan untuk memisahkan kolom variabel dalam X dan kolom target dalam y. Selanjutnya data dipisah dengan komposisi 80% untuk latihan dan 20% untuk diuji. Data yang telah dipisah telah siap untuk dimasukkan ke pelatihan model.

## Modeling
Untuk proyek kali ini, algoritma pelatihan yang digunakan ada 3 yaitu KNN, Random Forest, dan Algorithm Boosting. Penjelasan lengkap untuk masing-masing algoritma yaitu:

### K Nearest Neighbour (KNN)

```ruby
knn = KNeighborsClassifier().fit(X_train, y_train)
```
Sesuai namanya, algoritma ini bekerja berdasarkan kedekatan antar data. KNN kemudian menghitung jarak Euclidean antara data tersebut dengan seluruh data pada dataset pelatihan. Selanjutnya, KNN akan memilih sejumlah tetangga terdekat sebanyak K, sesuai nilai parameter yang ditentukan. Algoritma ini akan menentukan kelas mayoritas dari tetangga terdekat tersebut sebagai hasil prediksi. Adapun parameter yang digunakan adalah default yaitu:
- n_neighbors=5 -> Bertujuan untuk memilih 5 tetangga terdekat
- weights='uniform' -> Bertujuan untuk menetapkan bobot semua tetangga adalah sama
- algorithm='auto' -> Bertujuan untuk mMemilh algoritma pencarian tetangga secara otomatis
- p=2 -> Bertujuan untuk memilih jarak yang digunakan yaitu jarak Euclidean
- metric='minkowski' -> Bertujuan untuk memilih fungsi jarak Minkowski

Kelebihan:
- Proses pelatihan yang ringan, terlihat dari proses running time yang lebih cepat dibandingkan algoritma lainnya
- Bekerja baik pada dataset yang berukuran kecil hingga sedang

Kekurangan:
- Sensitif terhadap skala data (biasanya membutuhkan standardisasi/normalisasi data terlebih dahulu untuk mengatasi hal ini)
- Sensitif terhadap outlier sehingga jika dataset mengandung outlier maka hasil prediksi berpotensi menjadi bias

### Random Forest

```ruby
rf = RandomForestClassifier().fit(X_train, y_train)
```
Sesuai namanya, Random Forest adalah algoritma ML yang terdiri dari banyak pohon keputusan. Algoritma ini merupakan pengembangan atau tingkat lanjut dari algoritma Decision Tree. Cara kerjanya dimulai dengan membuat sejumlah pohon keputusan. Setiap pohon dilatih secara independen dan menghasilkan prediksi masing-masing. Random Forest kemudian menggabungkan hasil dari semua pohon, dimana kelas yang paling banyak dipilih oleh pohon-pohon tersebut menjadi prediksi akhir. Adapun parameter dari snippet code di atas adalah default dengan rincian sebagai berikut:
- n_estimators=100 -> Berarti jumlah pohon yang dibuat ada 100
- max_depth=None -> Berarti kedalaman pohon tidak dibatasi
- min_samples_split=2 -> Berarti jumlah minimum sampel adalah 2
- min_samples_leaf=1 -> Berarti jumlah minimum sampel pada setiap daun adalah 1
- max_features='sqrt' -> Berarti jumlah fitur maksimal adalah akar kudarat dari jumlah fitur
- bootstrap=True -> Berarti pohon dibuat dari sampel acak yang berasal dari data pelatihan
- random_state=None -> Berarti sampel data dipilih secara acak
- n_jobs=None -> Berarti model hanya memakai satu CPU untuk proses pelatihan

Kelebihan:
- Akurasi pada model ini biasanya lebih baik
- Karena data dan fitur dipilih secara acak, maka model lebih baik dalam mengatasi overfitting

Kekurangan:
- Lebih lambat dan membutuhkan memori yang lebih besar, terlihat dari running time yang lebih lama
- Kurang ideal untuk penggunaan real-time

### Boosting Algorithm

```ruby
boosting = AdaBoostClassifier().fit(X_train, y_train)
```
Algoritma ini menggunakan teknik boosting yang bekerja dengan membangun model dari data latih. Kemudian ia membuat model kedua yang bertugas memperbaiki kesalahan dari model pertama. Model ditambahkan sampai data latih terprediksi dengan baik atau telah mencapai jumlah maksimum model untuk ditambahkan. Caranya adalah dengan menggabungkan beberapa model sederhana dan dianggap lemah (weak learners) sehingga membentuk suatu model yang kuat (strong ensemble learner). Adapun parameter yang digunakan adalah default yaitu:
- n_estimators=50 -> Weak learners yang dibangun sejumlah 50
- learning_rate=1 -> Bobot yang diterapkan pada masing-masing proses iterasi boosting
- base_estimator=DecisionTreeClassifier(max_depth=1) ->	Algoritma dasar yang digunakan berupa Decision Tree
- random_state=None: Digunakan untuk mengontrol random number generator yang digunakan

Kelebihan:
- Akurasi yang lebih tinggi karena belajar dari kesalahan sebelumnya
- Sering mengungguli model yang lebih sederhana seperti logistic regression dan random forest

Kekurangan:
- Performa yang cenderung menurun jika menggunakan base learner yang terlalu kompleks

Dari ketiga algoritma di atas, model **Algorithm Boosting** dapat dikatakan sebagai solusi terbaik untuk proyek ini. Sebabnya, dataset cenderung berukuran terlalu besar untuk model KNN. Di sisi lain, model Algorithm Boosting lebih cepat dibandingkan RF saat menjalani proses running (Boosting 13 detik vs RF 25 detik) sehingga lebih mendukung dalam penggunaan real-time.

## Evaluation

Proyek ini menggunakan penyelesaian klasifikasi sehingga metrik evaluasi yang tepat untuk proyek ini yaitu accuracy, F1-score, precision dan recall. Adapun penjelasan lebih lanjut untuk masing-masing metrik yaitu:
- Accuracy: Ukuran yang menyatakan berapa banyak prediksi yang benar dari seluruh data yang diuji. Metrik ini sering digunakan untuk menggambarkan tingkat keberhasilan keseluruhan model. Meski begitu, accuracy bisa memberikan gambaran yang salah jika data tidak seimbang sehingga diperlukan metrik lainnya.
- F1-score: Rata-rata antara precision dan recall, memberikan gambaran yang lebih seimbang untuk menilai performa model terutama saat kelas tidak seimbang
- Precision: Mengukur perbandingan prediksi positif yang benar-benar positif
- Recall: Mengukur perbandingan data positif yang berhasil dideteksi oleh model

Metrik di atas didasarkan pada perhitungan matematis dengan formula untuk tiap-tiap metrik yaitu:
- Accuracy = (TP + TN) / (TP + TN + FP + FN)
- F1 Score = 2 × (Precision × Recall) / (Precision + Recall)
- Precision= TP / (TP + FP)  
- Recall = TP / (TP + FN)

_dimana TP = True Positive (prediksi positif dan realitanya memang positif), FN = False Negative (prediksi negatif padahal realitanya positif), FP = False Positive (prediksi positif padahal realitanya negatif), TN = True Negative (prediksi negatif dan realitanya memang negatif)_

Berdasarkan pernyataan masalah, tujuan, dan solusi yang telah dibuat, metrik akurasi dan F1-score setiap model pada proyek ini telah memenuhi standar yaitu di atas 80%. Untuk model Algorithm Boosting, diperoleh nilai:
- Accuracy 85.62%
- F1-score 81.14%
- Precision 77.31%
- Recall 85.62%


### Tambahan
```ruby
results = {
    'Accuracy': accuracy_score(y_test, y_pred),
    'Precision': precision_score(y_test, y_pred, average='weighted'),
    'Recall': recall_score(y_test, y_pred, average='weighted'),
    'F1-Score': f1_score(y_test, y_pred, average='weighted')
```
Penting untuk diperhatikan potongan kode di atas. Pada kode precision, recall, dan F1-score, parameter average yang digunakan yaitu 'weighted' bukan 'macro'. Hal ini dikarenakan dataset berupa cuaca di Bali dimana cuaca yang paling dominan adalah berawan sehingga ada peristiwa imbalance dataset. Namun karena proyek ini bertujuan untuk memprediksi cuaca secara umum dan bukan untuk memperhatikan kejadian langka (misal bencana alam atau deteksi penyakit) maka parameter yang digunakan akan average='weighted'.
![download (2)](https://github.com/user-attachments/assets/f28a11ce-853e-45d4-8252-9b23e72ef476)

```ruby
predicted_label = boosting.predict(input_data)[0]
print("Predicted weather: ", predicted_label)
```
Sesuai dengan tujuan yang telah ditetapkan sebelumnya, untuk dapat membuat model sederhana yang dapat memprediksi keadaan cuaca, maka kode di atas ditulis dengan harapan untuk menggambarkan hasil akhir dari model yang telah dibuat.

**---Ini adalah bagian akhir laporan---**
