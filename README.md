## Final Project Data Connector ##

![Data connector](https://github.com/fauzanheryka/Data_Connector/assets/141212116/c63fd5ab-6aec-47f1-b82c-3e9f36814bd3)

Anggota Kelompok:
1. Adri Chairulfatah
2. Egira Adhani K                       
3. Hanum Fazah Aditya K
4. Mohd Fauzan Heryka P
5. Lulu Munira Hanifah
6. Aulia Kindy
7. Rojiat Liqoarobby
8. Qarry Atul Chairunissa

# Health Insurance Cross Sell Prediction
Memprediksi apakah pelanggan akan tertarik untuk membeli Asuransi Kendaraan sehingga perusahaan dapat merencanakan strategi komunikasinya untuk menjangkau pelanggan tersebut dan mengoptimalkan **Business model** dan **Revenue**.

---

## Table of Content
  * [Abstract](#abstract)
  * [Problem Statement](#problem-statement)
  * [Role](#role)
  * [Objective](#objective)
  * [Goal](#goal)
  * [Business Metrics](#business-metrics)
  * [Data Description](#data-description)
  * [Project Outline](#project-outline)
    - 1 [EDA](#eda)
    - 2 [Business Insight](#business-insight)
  * [Reference](#reference)
    

# Abstract
Polis asuransi adalah surat perjanjian atau kontrak sebagai bukti pengalihan risiko dari tertanggung (peserta) kepada penanggung (pihak penyedia layanan asuransi). Perusahaan menyanggupi untuk memberikan jaminan kompensasi atas kerugian, kerusakan, penyakit, atau kematian tertentu sebagai imbalan atas pembayaran premi tertentu. Ada beberapa faktor yang memainkan peran utama dalam menjaring pelanggan untuk setiap polis asuransi. Di sini kami memiliki data tentang demografi seperti usia, jenis kelamin, kode wilayah, dan kerusakan kendaraan, usia kendaraan, premi tahunan, saluran sumber polis.

# Problem Statement
Perusahaan pada dataset merupakan perusahaan asuransi yang telah memberikan layanan asuransi kesehatan kepada pelanggannya. Mereka juga mempunyai produk baru yaitu asuransi kendaraan namun perusahaan belum mengetahui akan dipasarkan ke customer yang mana asuransi kendaraan tersebut, sehingga perusahaan ingin mengetahui customer yang dapat ditargetkan agar bisa menaikan penjualan asuransi kendaraan nya melalui cross selling dengan cara memprediksi apakah pemegang polis asuransi kesehatan dari tahun lalu akan tertarik juga dengan layanan asuransi kendaraan yang disediakan oleh perusahaan.

# Role 
Role kami adalah sebagai Team Data Science yang akan membangun model dan analisis rekomendasi yang dapat memprediksi profile pelanggan asuransi Kesehatan yang akan tertarik juga pada asuransi kendaraan agar perusahaan dapat merencanakan strategi komunikasinya untuk menjangkau pelanggan yang tertarik tersebut dan mengoptimalkan model bisnis dan pendapatannya.


# Objective 
Objective dalam project ini adalah membangun model machine learning dengan cara: menganalisis dataset, melakukan EDA untuk memahami pola dan hubungan dalam data, melakukan data preprocessing, dan melatih beberapa model klasifikasi yang berbeda. Beberapa tahapan objective yang akan dilakukan adalah sebagai berikut: Data Wrangling, Normalization, EDA, Encoding categorical values, Feature Selection, Model Fitting, Hyper-parameter Tuning, dan Metrics Evaluation. Selain menawarkan model Machine Learning, dapat dilakukan juga rekomendasi analisis berdasarkan hasil Exploratory Data Analysis.

# Goal 
Membangun model untuk memprediksi apakah pelanggan akan tertarik pada Asuransi Kendaraan dan membuat analisis rekomendasi, sehingga model dan rekomendasi ini dapat membantu perusahaan untuk dapat merencanakan strategi komunikasinya untuk menjangkau pelanggan yang tertarik tersebut dengan tepat dan pada akhir nya dapat mengoptimalkan model bisnis dan pendapatan perusahaan.
# Business Metrics 
Karena tujuan objective adalah mengoptimalkan model bisnis dan pendapatan perusahaan, maka business metrics yang cocok untuk mengukur ketercapaian objective  tersebut adalah **Total Revenue** atau **Conversion Rate** dari Asuransi Kendaraan.


# Data Description
Kami memiliki dataset yang berisi informasi tentang demografi (jenis kelamin, usia, jenis kode wilayah), Kendaraan (Usia Kendaraan, Kerusakan), Kebijakan (Premium, saluran sumber), dll. Demografi tersebut berhubungan dengan seseorang yang tertarik dengan asuransi kendaraan.
Kami memiliki 381109  baris data.


|Nama fitur|tipe data|Deskripsi|
|:---|:-----|:----------|
|id| (continous) | Unique ID yang sifat nya unik pada setiap customer.|
|Age |(continous)| Umur Customer.|
|Gender |(dichotomous)|Jenis Kelamin Customer|
|Driving_License |(dichotomous)|"0" orang yang tidak memiliki Sim, "1" orang yang memiliki Sim.|
|Region_Code |(nominal)|Kode Unik untuk area customer.|
|Previously_Insured| (dichotomous)| "0" untuk customer yang tidak memiliki asuransi kendaraan , "1" untuk customer yang memiliki asuransi kendaraan.|
|Vehicle_Age| (nominal)| Umur kendaraan.|
|Vehicle_Damage | (dichotomous)| "1" Customer yang pernah mengamalami kerusakan pada kendaraan. "0" untuk customer yang tidak pernah mengalami kerusakan pada kerusakan.|
|Annual_Premium| (continous)| Jumlah yang harus dibayar pelanggan sebagai premi pada tahun tersebut.|
|Policy_Sales_Channel| (nominal)| kode anonim yang menandakan channel untuk menghubungi customer. contohnya : Sales Asuransi, Email, Telephone, In Person, dll.|
|Vintage |(continous)|jumlah hari pelanggan telah berlangganan layanan asuransi dari perusahaan.|
|**Response** (Variabel target)|(dichotomous)| "1" untuk customer yang tertarik , "0" untuk customer yang tidak tertarik.|


----

# Project Outline

## EDA
pada dataset ini memiliki Dalam melakukan Exploratory Data Analysis  pertama kita mencoba me untuk melakukan analisis **univariate** pada kolom numeriik dan kategorik. kita berhasil menemukan beberapa fakta menarik : 
- persebaran Umur Customer
![histogram age](https://github.com/fauzanheryka/Data_Connector/assets/141212116/d6822f71-593e-4670-b8ea-a172800ab012)

grafik diatas menunjukkan bahwa orang-orang yang berusia 25-52 tahun lebih mungkin membeli asuransi kesehatan daripada orang-orang yang lebih muda atau lebih tua. Ini mungkin karena orang-orang dalam kelompok usia ini lebih mungkin memiliki tanggungan, seperti anak-anak atau orang tua yang sakit. Mereka juga lebih mungkin memiliki pekerjaan yang memberi mereka akses ke asuransi kesehatan, tetapi mereka mungkin tidak dapat membeli asuransi kesehatan yang mereka inginkan atau butuhkan.
Referensi yang mendukung data ini salah satunya :
    * Studi oleh Pew Research Center menemukan bahwa 83% orang berusia 18-29 tahun memiliki asuransi kesehatan, dibandingkan dengan 90% orang berusia 30-49 tahun dan 94% orang berusia 50-64 tahun.
- Pie chart previously customer  
![pie chart Previously](https://github.com/fauzanheryka/Data_Connector/assets/141212116/12905489-2115-4022-88ea-8a6d899844ee)

Variabel Previously_Insured menunjukkan bahwa 45,82% orang dalam data pernah memiliki asuransi. Ada beberapa alasan mengapa orang yang pernah memiliki asuransi kesehatan sebelumnya lebih mungkin membeli asuransi kesehatan. orang yang pernah memiliki asuransi kesehatan sebelumnya lebih mungkin memahami manfaat asuransi kesehatan.
Referensi yang mendukung data ini termasuk:
    - Studi oleh Pew Research Center menemukan bahwa 78% orang yang pernah memiliki asuransi kesehatan sebelumnya mengatakan mereka lebih mungkin membeli asuransi kesehatan lagi di masa depan.
    
setelah kita melakukan analisis univariate kita lanjut ke tahap ke berikutnya yaitu analisis **multivariate** : 
- Heatmap
![korelasi health](https://github.com/fauzanheryka/Data_Connector/assets/141212116/84eba541-ec57-491d-b1a7-122b120e9a41)
- Berdasarkan heatmap di atas terlihat bahwa masing-masing feature dan label tidak memiliki korelasi yang cukup kuat. Namun, dapat dilihat pada feature Age, previously insured, dan policy sales channel memiliki nilai korelasi yang lebih tinggi dibandingkan dengan feature yang lainnya, sehingga ke tiga feature tersebut dapat dipertahankan karna cukup relevan untuk digunakan dalam analisis ini. 
- Berdasarkan dari hasil heatmap yang ada, dapat dilihat bahwa feature age dan policy sales channel memiliki pola yang cukup menarik karna berkorelasi negatif yang cukup kuat yakni (-0.58), maka dari itu yang perlu dilakukan terhadap kedua feature tersebut adalah melakukan peninjauan kembali  persebaran data pada masing-masing fitur dengan lebih mendalam.
- Pair plot 
![pair plot healt](https://github.com/fauzanheryka/Data_Connector/assets/141212116/79e7b24c-86be-4bd1-98a5-dbfbbb72086d)
- Berdasarkan pair plot disamping tidak ada korelasi yang menarik terhadap variabel target maka dari itu perlu pertimbangan untuk melakukan feature engineering.
- Dari pair plot disamping sekilas dataset ini memiliki kemungkinan imbalance karena hanya condong di “response = 0”


## Business Insight
dalam EDA kita hanya berfokus untuk mengenali data, persebaran data dan menemukan outlier serta mencari insight, setelah kita melakukan EDA kita akan melakukan bisnis insight untuk perusahaan agar bisa mencapai bisnis metrics yang sudah ditetapkan. 
Berikut beberapa bisnis insight yang sudah ditemukan : 
- Age grup
![age grup](https://github.com/fauzanheryka/Data_Connector/assets/141212116/fb511bc5-52f5-46b9-818a-2a620a8267fd)
distribusi kelompok umur muda lebih banyak membeli asuransi kesehatan atau kendaraan, dikarenakan pada umur yang lebih muda kemungkinan besar mereka cenderung lebih sadar akan pentingnya perlindungan finansial melalui asuransi. Hal ini juga didukung oleh protective.com dalam artikelnya yang berjudul “why you should buy life insurance when you are young” yang mengatakan bahwa kelompok umur muda lebih banyak membeli asuransi karena dua faktor sebagai berikut:
    * Cheaper & Healthier
    Secara umum, semakin muda umur kita maka akan semakin sedikit kita akan membayar premi, karena kelompok umur muda memiliki risiko yang lebih kecil daripada seseorang yang jauh lebih tua secara kondisi kesehatan
- Vehicle age 
![vehicle age grup](https://github.com/fauzanheryka/Data_Connector/assets/141212116/068c75d8-3ba6-4f00-9344-a842aa5d6c85)
Dapat dilihat dari grafik bahwa customer yang memiliki atau tertarik dengan asuransi merupakan customer yang mempunyai usia kendaraan yang kurang dari 2 tahun (1-2 Year dan < 1 Year), karena mereka akan cenderung lebih merawat kendaraan baru yang dimiliki. Hal ini juga didukung oleh forbes.com dalam artikelnya yang berjudul “advisor/car-insurance/new-car-replacement” yang menyatakan bahwa kendaraan baru lebih banyak memiliki asuransi, karena hal sebagai berikut:
    * Penurunan nilai/Depresiasi nilai kendaraan dapat merugikan customer disaat customer mengalami kecelakaan tak lama setelah customer membeli mobil baru. Perusahaan asuransi kemungkinan besar akan mengganti nilai kendaraan dibawah harga beli karena karena depresiasi dan kecelakaan tersebut, sehingga klaim yang dibayarkan tidak cukup untuk mengcover nilai kendaraan customer, sehingga disarankan untuk mempunyai asuransi kendaraan, seperti contoh nya adalah “asuransi penggantian mobil baru”.


**Berikut adalah sekilas beberapa grafik yang menarik, masih banyak lagi di notebook silahkan dilihat :)**

---

# Reference
1. Kaiser Family Foundation - https://www.kff.org/
2. Pew Research Center - https://www.pewresearch.org/
3. U.S. Census Bureau - https://www.census.gov/
