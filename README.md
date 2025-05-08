**Proyek Pertama Prediksi Harga Sewa Rumah**

### **Informasi Diri**

* **Nama:** Khamdan Annas Fakhryza
* **Email:** [Khamdan@std.unissul.ac.id](mailto:Khamdan@std.unissul.ac.id)
* **ID Dicoding:** khamdan-fakhryza

Proyek ini adalah proyek pertama dalam bidang predictive analytics untuk memenuhi persyaratan submission dicoding. Proyek ini bertujuan membangun model machine learning yang dapat memprediksi harga sewa rumah dan apartemen di India.

### **Latar Belakang Proyek**

Tempat tinggal seperti rumah atau apartemen adalah kebutuhan dasar bagi setiap orang untuk berlindung. Nilai dari tempat tinggal ini ditentukan oleh berbagai faktor seperti lokasi, ukuran, jumlah kamar tidur, jumlah kamar mandi, furnitur, dan elemen lainnya.

Harga sewa rumah sering kali sulit diprediksi secara manual karena adanya banyak faktor yang mempengaruhi harga. Oleh karena itu, penting untuk mengurangi ketidakpastian ini dengan membangun sistem prediksi yang dapat menentukan harga sewa berdasarkan karakteristik tertentu.

Dalam proyek ini, tujuan utama adalah membangun model prediksi harga sewa rumah yang dapat memberikan harga yang sesuai dengan pasar. Model ini nantinya akan menjadi acuan untuk perusahaan dalam menyewakan rumah dengan harga yang optimal.

**Referensi:** [Analisis Prediksi Harga Rumah Sesuai Spesifikasi Menggunakan Multiple Linear Regression](https://ejournal.upnvj.ac.id/index.php/informatik/article/download/3635/1498)

### **Pemahaman Bisnis**

Proyek ini ditujukan untuk perusahaan yang menjalankan bisnis di bidang penyewaan rumah dan apartemen. Karakteristik bisnis perusahaan adalah:

* Perusahaan memiliki rumah atau apartemen yang disewakan kepada konsumen.
* Perusahaan juga memberikan layanan konsultasi mengenai harga sewa rumah dan apartemen.

#### **Permasalahan yang Dihadapi**

1. Apa fitur yang paling mempengaruhi harga sewa rumah atau apartemen?
2. Bagaimana cara mempersiapkan data agar model dapat dilatih dengan baik?
3. Bagaimana cara memprediksi harga sewa rumah berdasarkan karakteristik tertentu?

#### **Tujuan Proyek**

1. Mengetahui fitur yang paling berpengaruh terhadap harga sewa rumah atau apartemen.
2. Menyiapkan data yang sesuai untuk dilatih dalam model.
3. Membangun model machine learning yang dapat memprediksi harga sewa rumah secara akurat.

#### **Solusi yang Diberikan**

1. Melakukan analisis univariat dan multivariat serta visualisasi data untuk memahami kolerasi antar fitur dan mendeteksi adanya outlier.
2. Menyiapkan data sehingga dapat digunakan untuk membangun model prediksi harga sewa.
3. Melakukan pencarian hyperparameter menggunakan grid search untuk mendapatkan model yang optimal. Algoritma yang digunakan adalah K-Nearest Neighbour (KNN), Random Forest, dan AdaBoost.

### **Pemahaman Data & Penghapusan Outlier**

Dataset yang digunakan dalam proyek ini berisi data harga sewa rumah dengan berbagai karakteristik di India. Dataset ini tersedia di [Kaggle : House Rent Prediction Dataset](https://www.kaggle.com/datasets/iamsouravbanerjee/house-rent-prediction-dataset).

#### **Deskripsi Dataset**

* Format dataset adalah CSV (Comma-Separated Values).
* Dataset terdiri dari 4746 sampel dengan 12 fitur.
* Terdapat 4 fitur bertipe numerik dan 8 fitur kategorikal.
* Tidak ada missing value dalam dataset.

#### **Variabel-variabel dalam Dataset**

* **Posted On:** Tanggal posting data.
* **BHK:** Jumlah kamar tidur, ruang tamu, dan dapur.
* **Rent:** Harga sewa rumah/apartemen.
* **Size:** Luas rumah/apartemen dalam satuan sqft.
* **Floor:** Letak dan jumlah lantai rumah/apartemen.
* **Area Type:** Kategori ukuran rumah (Super Area, Carpet Area, atau Built Area).
* **Area Locality:** Lokasi rumah/apartemen.
* **City:** Kota tempat rumah/apartemen berada.
* **Furnishing Status:** Status furnitur (Furnished, Semi-Furnished, atau Unfurnished).
* **Tenant Preferred:** Jenis penyewa yang diutamakan.
* **Bathroom:** Jumlah kamar mandi.
* **Point of Contact:** Kontak yang dihubungi untuk informasi lebih lanjut.

Fitur **Point of Contact** dan **Posted On** tidak berpengaruh terhadap harga sewa dan akan dihapus dari dataset.

### **Analisis Univariat**

Analisis univariat dilakukan untuk menganalisis fitur secara terpisah.

#### **Analisis Fitur Kategorikal**

Beberapa fitur kategorikal seperti **City**, **Furnishing Status**, dan **Tenant Preferred** menunjukkan distribusi sampel yang cukup merata, sementara fitur **Area Type** memiliki distribusi yang tidak merata, sehingga beberapa kategori akan dihapus untuk menghindari data dimensionalitas tinggi.

#### **Analisis Fitur Numerik**

* Sebagian besar rumah memiliki ukuran antara 1 hingga 3 BHK dan 1 hingga 3 kamar mandi.
* Sebagian besar rumah memiliki ukuran di bawah 2000 sqft.
* Harga sewa memiliki distribusi yang sangat bervariasi, dengan harga terendah sekitar 1200 dan tertinggi mencapai 3.5 juta.

### **Analisis Multivariat**

Multivariat analysis menunjukkan hubungan antar fitur numerik dan kategorikal dengan fitur target (Rent).

#### **Fitur yang Mempengaruhi Harga Sewa**

* **City:** Kota tempat rumah/apartemen berada memiliki pengaruh yang besar terhadap harga sewa. Kota Mumbai, misalnya, memiliki harga sewa yang lebih tinggi dibandingkan kota lainnya.
* **Furnishing Status:** Rumah yang memiliki furnitur lengkap cenderung memiliki harga sewa lebih tinggi dibandingkan yang tidak terfurnish.
* **Tenant Preferred:** Rumah yang disarankan untuk keluarga cenderung memiliki harga sewa yang lebih tinggi.

### **Persiapan Data**

* **One Hot Encoding:** Mengubah fitur kategorikal menjadi numerik untuk memudahkan pemodelan.
* **Train-Test Split:** Data dibagi menjadi data latih dan data uji, dengan proporsi 95% untuk latih dan 5% untuk uji.
* **Normalisasi:** Data dinormalisasi menggunakan StandardScaler untuk memastikan bahwa semua fitur memiliki skala yang sama.

### **Pemodelan**

Model dibangun menggunakan tiga algoritma: K-Nearest Neighbour (KNN), Random Forest, dan AdaBoost.

#### **Algoritma yang Digunakan**

* **K-Nearest Neighbour (KNN):** Algoritma ini bekerja dengan menghitung jarak antara sampel dan memilih k tetangga terdekat untuk menentukan prediksi harga sewa.
* **Random Forest:** Model ensemble yang menggunakan banyak pohon keputusan untuk meningkatkan akurasi prediksi.
* **AdaBoost:** Teknik boosting yang menggabungkan beberapa model lemah untuk menghasilkan model yang lebih kuat.

#### **Pencarian Hyperparameter (Grid Search)**

Grid search digunakan untuk menemukan parameter terbaik untuk setiap algoritma. Berikut adalah hasil hyperparameter tuning:

| Model         | Best Params                                                  |
| ------------- | ------------------------------------------------------------ |
| KNN           | `n_neighbors = 7`                                            |
| Boosting      | `learning_rate = 0.1, n_estimators = 100, random_state = 11` |
| Random Forest | `max_depth = 8, n_estimators = 25, random_state = 11`        |

### **Evaluasi Model**

Evaluasi dilakukan dengan menggunakan akurasi dan Mean Squared Error (MSE) sebagai metrik.

#### **Hasil Evaluasi**

* **Akurasi:**

  * KNN: 72.68%
  * Boosting: 89.86%
  * Random Forest: 93.21%

* **Mean Squared Error (MSE):**
  Hasil menunjukkan bahwa **Random Forest** memiliki akurasi terbaik dan MSE yang lebih rendah dibandingkan dengan algoritma lainnya.

Dengan demikian, Random Forest menjadi model yang paling optimal untuk memprediksi harga sewa rumah dalam proyek ini.
