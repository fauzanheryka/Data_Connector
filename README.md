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
    - 3 [Data Pre-Processing](#data-pre-processing)
    - 4 [Feature Engineering](#feature-engineering)
    - 5 [Feature Selection](#feature-selection)
    - 6 [Machine Learning Evaluation & Supervised Learning](#machine-learning-evaluation--supervised-learning)
    - 7 [Business Recommendation](#business-recommendation)
    
  * [Conclusion](#conclusion)
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
![age grup](https://github.com/fauzanheryka/Data_Connector/assets/141212116/1e93e7f8-5cbb-45d9-afa8-1b1100b2c2fb)
distribusi kelompok umur muda lebih banyak membeli asuransi kesehatan atau kendaraan, dikarenakan pada umur yang lebih muda kemungkinan besar mereka cenderung lebih sadar akan pentingnya perlindungan finansial melalui asuransi. Hal ini juga didukung oleh protective.com dalam artikelnya yang berjudul “why you should buy life insurance when you are young” yang mengatakan bahwa kelompok umur muda lebih banyak membeli asuransi karena dua faktor sebagai berikut:
    * Cheaper & Healthier
    Secara umum, semakin muda umur kita maka akan semakin sedikit kita akan membayar premi, karena kelompok umur muda memiliki risiko yang lebih kecil daripada seseorang yang jauh lebih tua secara kondisi kesehatan
- Vehicle age 
![vehicle age grup](https://github.com/fauzanheryka/Data_Connector/assets/141212116/75551920-b1a6-4b0d-b634-6b0dad6f2368)
Dapat dilihat dari grafik bahwa customer yang memiliki atau tertarik dengan asuransi merupakan customer yang mempunyai usia kendaraan yang kurang dari 2 tahun (1-2 Year dan < 1 Year), karena mereka akan cenderung lebih merawat kendaraan baru yang dimiliki. Hal ini juga didukung oleh forbes.com dalam artikelnya yang berjudul “advisor/car-insurance/new-car-replacement” yang menyatakan bahwa kendaraan baru lebih banyak memiliki asuransi, karena hal sebagai berikut:
    * Penurunan nilai/Depresiasi nilai kendaraan dapat merugikan customer disaat customer mengalami kecelakaan tak lama setelah customer membeli mobil baru. Perusahaan asuransi kemungkinan besar akan mengganti nilai kendaraan dibawah harga beli karena karena depresiasi dan kecelakaan tersebut, sehingga klaim yang dibayarkan tidak cukup untuk mengcover nilai kendaraan customer, sehingga disarankan untuk mempunyai asuransi kendaraan, seperti contoh nya adalah “asuransi penggantian mobil baru”.


- **Berikut adalah sekilas beberapa grafik yang menarik, masih banyak lagi di notebook silahkan dilihat**

## Data Pre-Processing
- ## Data cleansing 
  1a.  **Handle missing value**
  dari hasil function isnull().sum(), tidak ada data yang memiliki missing values. Sehingga tidak perlu dilakukan handling terhadap missing value pada bagian ini.

  2a. **Handle Duplicated Data**
  dari hasil function duplicated().sum(), tidak ada data yang memiliki data duplikat. Sehingga tidak perlu dilakukan handling terhadap duplicated data pada bagian ini.

  3a. **Handle Outlier** Sesuai informasi dan insight yang didapatkan pada EDA, kami akan mencoba melakukan Handling Outliers dengan menggunakan IQR dan QQ Plot pada feature Annual_Premium 
  ![outlier](https://github.com/fauzanheryka/Data_Connector/assets/141212116/59130b0f-b029-4dc3-b185-aa0627727c9f)
  ![outlier 2](https://github.com/fauzanheryka/Data_Connector/assets/141212116/6cb2c827-3fc0-4c54-8d36-f9229ccd50d6)
  - Dari observasi dan analisis IQR dan QQ plot diatas, dapat disimpulkan bahwa outlier Annual_Premium merupakan collective outlier. Collective outlier merupakan kelompok titik data yang secara kolektif menyimpang secara signifikan dari keseluruhan distribusi kumpulan data (Dalam hal ini distribusi dari feature Annual_Premium).
  - Dalam kasus pada dataset ini outlier yang ada pada Annual_Premium masih wajar terjadi di dunia nyata, karena Annual Premium tiap nasabah yang berbeda-beda dipengaruhi banyak sekali variabel lainnya seperti Loan (apakah nasabah memiliki pinjaman atau tidak), Jumlah tanggungan keluarga,Jenis Pekerjaan, Jenis Kendaraan, Merk Kendaraan,Jumlah mobil yang dimiliki nasabah dan lain lain.
  - Sehingga berdasarkan alasan diatas, tidak akan dilakukan handling outliers lebih lanjut pada project ini.
- ## Feature Engineering
  1. kita menambahkan fitur baru yaitu mengelompokan umur dengan berdsarkan young Age, Middle Age, Old Age.
  2. setelah kita menemukan fitur baru maka kita akan melakukan encoding pada fitur gender, Vehicle Damage, Vehicle Age, Age Group.
  3. memili fitur - fitur mana yang relevan maka kita melakukan **Heatmap** dan **Multikolinearitas**
  ---
  ![Heatmap final](https://github.com/fauzanheryka/Data_Connector/assets/141212116/e932bd54-da28-4c3c-8ac9-984ae2ba97e7)
  ---
  ![multikolon Final](https://github.com/fauzanheryka/Data_Connector/assets/141212116/9cf66e85-ac83-4393-9bf1-c772c679e361)
  ---
- ## feature selection 
  Pada bagian feature selection ini, kami menentukan feature yang akan dipilih berdasarkan uji statistik, EDA, heatmap terbaru yang sudah dilakukan encoding, dan multicollinearity. Sehingga kami hanya akan mengambil fitur fitur yang memiliki korelasi yang penting dengan target dan membuang fitur yang kurang relevan. Hal-hal yang dilakukan pada feature selection adalah sebagai berikut:
     - Tidak memilih/Drop feature "id" di feature selection karena feature ini hanya merepresentasikan id dari customer dan tidak mempengaruhi prediksi dari model machine learning
     - Tidak memilih/Drop feature "Age" dan "Driving_License"di feature selection karena feature ini mempunyai Multicollinearity yang tinggi sehingga tidak lulus uji multikolinearitas dan kami akan drop pada project ini.
     - Tidak memilih/Drop feature "Policy_Sales_Channel" dan "Region_Code" di feature selection karena feature ini memiliki terlalu banyak nilai unik/kategori sehingga tidak dapat terlalu diambil insight atau informasi nya, 
     - Tidak memilih/Drop feature "Vintage" di feature selection .karena berdasarkan heatmap, sebelum dan sesudah menggunakan feature engineering, tidak relevan terhadap fitur-fitur lain. Feature Vintage bisa sangat berguna pada dunia nyata jika usia polis asuransi memiliki nilai lebih dari setahun sebagai perbandingan. Namun pada case ini, karena feature Vintage mempunyai usia dibawah 1 tahun, sehingga feature ini tidak terlalu berguna dan akan kami drop juga pada bagian feature selection ini
     - Memilih fitur yang sudah di encode atau di kategorikan seperti age_group.

   **Kesimpulan** dari feature selection yang diatas, feature selection yang kami pilih untuk project ini adalah:

      - Gender
      - Previously_Insured
      - Vehicle_Age
      - Vehicle_Damage
      - Annual_Premium
      - Age_Group
      - Response (*Feature Target)
- ## Handle Imbalance ##
  - karena pada dataset ini memiliki imbalance yang cukup ekstrim maka kita memutuskan untuk menggunakan random under sampling, alasan kita memakai sampling menggunakan **random under sampling** yaitu :
    
    - untuk mengurangi jumlah sampel dari kelas mayoritas sehingga seimbang dengan jumlah sampel dari kelas minoritas. Ini dilakukan dengan menghapus sejumlah sampel acak dari kelas mayoritas hingga proporsi kelas menjadi lebih seimbang.
    - Ketidakseimbangan kelas dapat menyebabkan model cenderung memprediksi kelas mayoritas sepanjang waktu, yang mengurangi kemampuan model untuk mengklasifikasikan kelas minoritas. Dengan melakukan Random Under Sampling, model memiliki kesempatan yang lebih baik untuk mempelajari fitur-fitur kelas minoritas agar tidak merubah insight.
- ## Normalization 
  pada modeling kali ini kita memilih untuk melakukan **Standart Scaler**
- ## Feature Tambahan 
    1. Feature "Loan"
        Feature Loan dapat ditambahkan untuk melihat apakah nasabah memiliki pinjaman atau tidak. Feature ini dapat bermanfaat untuk melihat pengaruh Loan terhadap keputusan customer apakah mereka akan tertarik menggunakan Asuransi Kendaraan atau tidak. Feature Loan menjadi bermanfaat, karena pertimbangan bahwa nasabah yang sudah memiliki loan, akan cenderung tidak tertarik mengambil asuransi kendaraan karena akan ada biaya tambahan yang harus dikeluarkan untuk menggunakan Asuransi Kendaraan, dan vice versa.

    2. Feature "Dependent"
        Feature "Dependent" atau Jumlah Tanggungan Keluarga dapat ditambahkan, karena feature ini bisa menjadi pertimbangan bagi customer apakah akan memutuskan menggunakan Asuransi Kendaraan atau tidak karena akan ada biaya tambahan yang harus dikeluarkan apabila memiliki tanggungan keluarga, dibandingkan customer yang belum memiliki tanggungan.

  3. Feature "Occupation"
      Feature Occupation atau Jenis Pekerjaan, dapat juga ditambahkan sebagai feature tambahan, karena feature ini akan melihat pengaruh jenis pekerjaan terhadap keputusan customer untuk menggunakan Asuransi Kendaraan atau tidak. Nanti nya feature ini dapat melihat, jenis pekerjaan apa yang memiliki kecenderungan yang tinggi dan tidak untuk jumlah customer yang tertarik menggunakan Asuransi Kendaraan.

  4. Feature "Vehicle_Type"
      Feature Vehicle_Type atau Jenis Kendaraan, dapat ditambahkan sebagai feature tambahan karena featur ini akan berguna untuk melihat pengaruh jenis kendaraan yang dimiliki oleh customer terhadap keputusan customer yang akan menggunakan Asuransi Kendaraan atau tidak. Pada dunia nyata, biasa nya tipe kendaraan saat berpengaruh terhadap polis asuransi yang akan dibayar. Biasa nya semakin besar size kendaraan akan semakin besar polis asuransi yang dibayarkan, karena resiko kendaraan besar (Seperti jenis kendaraan Hatchback, Truck, MPV, SUV, dll) mengalami kecelakaan/kerusakan lebih besar dibandingkan kendaraan kecil (Seperti jenis kendaraan Sedan, Lowrider, Muscle car, dll). Nantinya akan diliat jenis kendaraan apa yang memiliki kecenderungan yang tinggi dan tidak untuk jumlah customer yang tertarik menggunakan Asuransi Kendaraan.

  5. Feature "Vehicle_Brand"
      Feature Vehicle_Brand atau Merk Kendaraan dapat ditambahkan sebagai feature tambahan karena feature ini akan berguna untuk melihat pengaruh merk kendaraan yang dimiliki oleh customer terhadap keputusan customer yang akan menggunakan Asuransi Kendaraan atau tidak. Feature ini dapat bermanfaat karena customer yang mempunyai merk kendaraan mewah, cenderung lebih tertarik untuk menggunakan asuransi kendaraan karena asuransi kendaraan dapat meningkatkan rasa aman dan nyaman mengingat merk kendaraan yang mahal tentu nya harga kendaraannya dan pajak nya juga akan bernilai tinggi, daripada kendaraan yang mempunyai merk dibawah merek mahal. Nantinya akan diliat jenis kendaraan apa yang memiliki kecenderungan yang tinggi dan tidak untuk jumlah customer yang tertarik menggunakan Asuransi Kendaraan.

  6. Feature "Number_Vehicle_Owned"
      Feature "Number_Vehicle_Owned" atau Jumlah Mobil yang Dimiliki oleh Customer dapat ditambahkan sebagai feature tambahan karena feature ini akan berguna untuk melihat pengaruh jumlah kendaraan yang dimiliki oleh customer terhadap keputusan customer yang akan menggunakan Asuransi Kendaraan atau tidak. Hal ini disebabkan karena ketika customer memiliki banyak kendaraan, tentunya ada biaya lain yang perlu dikeluarkan dan menggunakan Asuransi Kendaraan akan menambah biaya. Oleh karena itu feature ini cukup penting untuk melihat pengaruhnya terhadap keputusan customer untuk menggunakan Asuransi Kendaraan atau tidak

    7. Feature "Net_Income"
        Feature "Net_Income" atau Besar Pendapatan yang dimiliki customer dapat dijadikan feature tambahan karena feature ini akan berguna untuk melihat pengaruh besar kecilnya pendapatan individu terhadap keputusan customer apakah akan menggunakan Asuransi Kendaraan atau tidak. Hal ini disebabkan kemampuan customer untuk membeli produk asuransi dapat dipengaruhi oleh berapa banyak pendapatan yang mereka peroleh per bulan karena tentunya semakin tinggi pendapatan yang dihasilkan per bulannya semakin leluasa customer menggunakan uangnya membeli produk asuransi kendaraan

    8. Feature "Payment_Method"
        Feature "Payment_Method" atau Metode Pembayaran saat customer membeli kendaraan dapat dijadikan feature tambahan karena feature ini akan berguna untuk melihat seberapa besar pengaruh cara bayar customer saat membeli kendaraan terhadap keputusan customer apakah akan menggunakan Asuransi Kendaraan atau tidak. Hal ini disebabkan ketika customer memiliki kendaraan yang belum lunas pembayarannya, mereka cenderung untuk menjaga kendaraan nya agar tidak mengalami kerusakan, yang disebabkan karena ketika kendaraan rusak, maka akan ada biaya tambahan lagi yang dikeluarkan. Akan menjadi lebih menarik lagi jika kita dapat melihat bagaimana kecenderungan customer yang masih memiliki cicilan kendaraan terhadap ketertarikan mereka untuk membayar asuransi kendaraan tiap bulan.

## Machine Learning Evaluation & Supervised Learning

- ## Referensi Modeling Machine Learning dan Hyperparameter Tuning
  Untuk mempermudah pemilihan model machine learning dan hyperparameter tuning yang akan digunakan pada project ini, kami melakukan riset dan pada akhir nya mengacu pada dua penelitian sebagai berikut untuk penentuan model dan hyperparameter tuning yang akan dilakukan:
     - Paper "A Classification Problem: Health Insurance Cross Sell Prediction" - University of San Diego
     - Journal "Comparative Analysis of Building Insurance Prediction Using Some Machine Learning Algorithms" - University of Electronic Science and Technology of China

- ##  Modeling Machine Learning
  Berdasarkan referensi diatas dan pembelajaran yang telah kami lakukan pada bootcamp, kami akan mencoba berbagai model pembelajaran ML pada kumpulan data untuk melihat kinerja masing-masing model:
     - Logistic Regression
     - XGBoost
     - Decision Tree
     - Random Forest
     - Naive Bayes
     - KNN
     - Precision : Precision adalah rasio prediksi True Positive terhadap jumlah total prediksi Positive.
     - Recall : Recall adalah rasio prediksi True positif terhadap jumlah total kasus positif sebenarnya
     - F1-Score : menghitung keseimbangan mean dari precision dan recall
     - Confusion Matrix : Matriks konfusi menunjukkan jumlah prediksi True Positive, False positive, True Negative, dan False Negative yang dibuat oleh model.
     - ROC Curve: Kurva karakteristik pengoperasian penerima, atau kurva ROC, adalah plot grafis yang menggambarkan kemampuan diagnostik sistem pengklasifikasi binary karena ambang diskriminasinya bervariasi. Kurva ROC dibuat dengan memplot True Positive Rate (TPR) terhadap False Positive Rate (FPR) pada berbagai pengaturan threshold. true positive Rate (TPR) juga dikenal sebagai sensitivitas, perolehan, atau probabilitas deteksi dalam pembelajaran mesin. False positive Rate juga dikenal sebagai probabilitas alarm palsu dan dapat dihitung sebagai (1 − spesifisitas).
     - Classification report : Visualisasi laporan klasifikasi menampilkan score precision, recall, F1, dan dukungan untuk model. Untuk mendukung interpretasi dan deteksi masalah yang lebih mudah, laporan ini mengintegrasikan skor numerik dengan heatmap.
     - Untuk dataset ini kita memfokuskan metric evaluasi recall score, karena ingin meningkatkan conversion rate sebanyak mungkin untuk mendapatkan potensial user

![Eval Classification Models](https://github.com/fauzanheryka/Data_Connector/assets/141822563/cbcc0200-e6dc-4c51-8c2f-c8c396fc43eb)

Dari modeling diatas kita bisa mengetahui bahwa model Logistic Regression dan naive bayes memiliki score recall yang baguss sesuai dengan tujuan bisnis yang sudah ditentukan yaitu mencari true positive sebanyak - banyaknya. maka pilihan model logistic regression dan naive bayes adalah opsi terbaik dengan score yang hampir mirip yaitu 97% dengan score auc roc yang stabil juga, sehingga memiliki kecenderungan overfit/underfit yang sangat kecil sekali. meskipun begitu kita akan mencoba mengoptimasi kedua model tersebut menggunakan hyperparameter tuning.

- ##  Hyperparameter Logistic Regression

![Hyperparam Logistic Regression](https://github.com/fauzanheryka/Data_Connector/assets/141822563/5fe73b12-5f15-4926-934a-bb9ea47ede02)
![Logistic Regression ROC Curve](https://github.com/fauzanheryka/Data_Connector/assets/141822563/e3ca1264-83ae-4c10-b05f-2995c366ae82)

     - Setelah melakukan tuning kita berhasil menaikan recall score dari 97% meskipun tidak terlalu signifikan menggunakan randomized search karena pada saat menggunakan metode tersebut memiliki compute time yang relatif cepat
     -Setelah melakukan tuning kita berhasil mengurangi false negative yang lumayan, sehingga hal ini bisa membuat model untuk memprediksi customer yang memang benar - benar tidak berminat untuk membeli asuransi lebih akurat dan dapat mencegah cost loss perusahaan.
     - Dan setelah tuning pada data test memiliki kenaikan true postive yang bisa menjadi peningkatan conversion rate sesuai dengan tujuan bisnis
<br>

- ## Analisis menggunakan lift curve dan gain curve
  - Cumulative Gain Curve
  ![cumulative curve](https://github.com/fauzanheryka/Data_Connector/assets/141212116/75821367-8e27-401d-93ba-befe0a074b38)
<br>

- Cumulative Gain Curve
  ![gain curve](https://github.com/fauzanheryka/Data_Connector/assets/141212116/9f9bb2c5-227c-464e-8b0d-fe5f762ab88c)
  - - Bisa dilihat pada cumulative gain curve mengalami peningkatan yang signifikan setelah melakukan prediksi dengan sampel 30% data model dapat mengcapture 80% customer yang interest, dan Model logistic regression juga berhasil melampaui baseline yang bearti logistic regression bisa melakukan prediksi dengan baik daripada menggunakan prediksi acak secara manual **(Baseline)**
  - - pada lift curve jika kita memakai 30% sample maka performa machine learning akan meningkat 2.4X lebih baik daripada melakukan prediksi random/manual

- ##  Hyperparameter Tuning GNB

![Hyperparam GNB](https://github.com/fauzanheryka/Data_Connector/assets/141822563/f4a6c56c-d9d6-4d4d-85f0-a63aaea1d3bd)
![GNB ROC Curve](https://github.com/fauzanheryka/Data_Connector/assets/141822563/ebd201dc-15ca-4ee3-8729-c1dc92664f37)

     - Dari hasil hyper parameter diatas sepertinya naive bayes sudah berada di batas max dan sudah tidak memiliki kenaikan yang signifikan pada saat dilakukan hyperparameter tuning maka dari itu bisa disimpulkan bahwa logistic regresion adalah best model untuk dataset ini

- ## Feature Importance
![Feature Importance](https://github.com/fauzanheryka/Data_Connector/assets/141822563/10adbb3b-f52d-46b1-b968-3dda42eea1e2)

  Pada dataset ini memiliki beberapa fitur yang penting, sesuai dari grafik diatas ada 2 fitur yang dominan yaitu vehicle damage dan vehicle age.Fitur vehicle damage memiliki importance score yang tinggi, maka fitur tersebut memiliki hubungan yang kuat pada conversion rate hal ini didukung dengan artikel dari analyticsvidhya.com dalam artikelnya yang berjudul “Cross-Sell Prediction Using Machine Learning in Python” yang menyatakan bahwa:
- Customer yang kendaraan nya pernah rusak cenderung lebih memiliki pengalaman dan pengetahuan dari segi cost yang harus dikeluarkan untuk memperbaiki kendaraan nya. Dari segi pengalaman customer, apabila menggunakan asuransi, cost yang dikeluarkan jauh lebih murah daripada saat tidak menggunakan asuransi, karena saat menggunakan asuransi kendaraan, customer dapat mendapatkan klaim dari asuransi disaat kendaraan mereka rusak, sedangkan apabila tidak menggunakan asuransi, customer akan menanggung biaya perbaikan nya sendiri (yang jauh lebih mahal).
 
Untuk vehicle age juga memiliki score tertinggi kedua yang bearti usia kendaraan juga memiliki kemungkinan tinggi untuk customer membeli asuransi kendaraan.Dari EDA yang sudah ditampilkan usia kendaraan kurang dari 2 tahun akan membeli asuransi kendaraan, karena untuk beberapa customer dengan memiliki mobil baru mereka akan merawat kendaraan yang baru dimiliki. Hal ini juga didukung oleh forbes.com dalam artikelnya yang berjudul “advisor/car-insurance/new-car-replacement” yang menyatakan bahwa kendaraan baru lebih banyak memiliki asuransi, karena hal sebagai berikut:
- Penurunan nilai/Depresiasi nilai kendaraan dapat merugikan customer disaat customer mengalami kecelakaan tak lama setelah customer membeli mobil baru. Perusahaan asuransi kemungkinan besar akan mengganti nilai kendaraan dibawah harga beli karena karena depresiasi dan kecelakaan tersebut, sehingga klaim yang dibayarkan tidak cukup untuk mengcover nilai kendaraan customer, sehingga disarankan untuk mempunyai asuransi kendaraan, seperti contoh nya adalah “asuransi penggantian mobil baru”.

![Shap Values](https://github.com/fauzanheryka/Data_Connector/assets/141822563/e2aba29a-2a7b-40f0-bbb2-4a67d6a59146)

- ## Business Insight
     - Bisa dilihat pada fitur previously insured sangat tidak membantu dalam pemodelan, karena sudah pasti jika customer sudah memiliki asuransi maka tidak akan berlanggan asuransi lagi kecuali perusahaan bisa mengadakan event,promo menarik yang bisa menggaet customer yang sudah memiliki asuransi pada perusahaan lain .
     - Pada fitur vehicle damage, jika customer pernah mengalami kerusakan pada kendaraan maka customer memiliki kemungkinan yang tinggi untuk melakukan pembelian asuransi, dikarenan biaya yang mahal pada saat melakukan perbaikan apabila tidak dicover oleh asuransi.
     - Fitur vehicle age juga memiliki kontribusi untuk customer membeli asuransi, karena ketika kendaaran baru customer cenderung melakukan perawatan maksimal dengan salah satu cara yaitu membeli asuransi agar lebih aman.
 
- ## Business Recommendation
Jika ingin menarik customer yang sudah memiliki asuransi maka sangat disarankan untuk melakukan pendekatan customer secara detail, dengan cara melakukan penyebaran kuisioner atau mengadakan event yang menarik supaya customer bisa beralih yang sebelumnya dari perusahaan competitor menjadi memiliki minat untuk membeli asuransi di perusahaan. Selain itu perusahaan juga dapat memberikan diskon untuk calon customer yang sudah memiliki asuransi sebelumnya dengan skema sebagai berikut:

- Safety Driver Discount - Memberikan diskon 25% untuk customer yang tidak memiliki catatan kecelakaan kendaraan sebelumnya.
- Young Driver Discount - Memberikan diskon 20% untuk customer yang berusia dibawah 25 tahun
- Mature Driver Discount - Memberikan diskon 15% untuk customer yang berusia diatas 50 tahun
  
Melakukan campaign yang berfokus pada customer yang sudah pernah mengalami kerusakan pada kendaraan. Selain itu perusahaan juga dapat menawarkan layanan add-on gratis khusus kepada customer yang sudah pernah mengalami kerusakaan pada kendaraan dengan opsi layanan sebagai berikut:

- Zero-Depreciation - Biasanya dalam kasus klaim asuransi kendaraan, perusahaan asuransi membayar penggantian suku cadang setelah dikurangi penyusutan, namun dalam hal ini untuk menarik customer, perusahaan dapat menawarkan pembayaran full untuk suku cadang nya dengan tidak dikurangi biaya penyusutan.
- Engine Protection - Layanan Add-on ini akan mengcover biaya penggantian khusus apabila terjadi kerusakan pada mesin kendaraan. Perusahaan akan menanggung biaya perbaikan mesin seperti jika ada kerusakan mesin akibat cuaca buruk, seperti banjir yang mengakibatkan masuknya air pada mesin kendaraan yang menyebabkan kendaraan rusak.
- 24x7 Roadside Assistance - Kerusakan kendaraan paling sering terjadi saat di jalanan. Customer mungkin terjebak saat hujan terus-menerus karena kendaraan tidak dapat dihidupkan atau ketika ban customer pecah saat sedang berkendara di jalan. Untuk mendapatkanmenarik customer dan membantu customer mendapatkan bantuan dalam keadaan seperti ini, perusahaan dapat memberikan layanan Add-on bantuan pinggir jalan (Roadside Assistance) kapan pun dan dimanapun (24x7). Dengan layanan ini customer bisa mendapatkan bantuan antara lain memperbaiki roda atau derek mobil. Dengan layanan ini perusahaan akan mencegah customer terdampar tanpa bantuan apa pun selama beberapa jam. Paket-paket yang dapat ditawarkan oleh perusahaan lewat Add-on ini seperti Derek Mobil, Menyalakan Baterai, Perbaikan Ban Kempes. Layanan ini akan sangat berguna bagi individu/calon customer yang sering melakukan perjalanan jarak jauh melalui jalan darat, karena dapat membantu jika terjadi kerusakan mekanis, ban bocor, atau keadaan darurat lainnya.

Mengadakan campaign pada saat customer membeli kendaraan baru, karena pada saat customer membeli kendaraan baru, pasti akan sangat memperhatikan kendaraanya. maka dari itu perusahaan harus menyusun strategi campaign yang tepat. Selain itu perusahaan juga disarankan untuk bekerja sama dengan dealer/showroom kendaraan seperti berikut:

- Melakukan bundling asuransi kendaraan dengan customer yang membeli kendaraan, terutama pada usia kendaraan yang baru atau berusia 1-2 tahun untuk memaksimalkan konversi asuransi dari penjualan kendaraan yang berasal dari dealer/showroom.

- ## Best Model
![Best Model](https://github.com/fauzanheryka/Data_Connector/assets/141822563/b0a27b07-201b-4008-aeef-3499c2fa7f31)

## Conclusion
- Mulai dari dataset ,awalnya kami memeriksa nilai null dan duplikat. Tidak ada nilai nol dan duplikat sehingga tidak perlu handle missing value/duplicate terhadap hal tersebut tidak diperlukan.pada saat data preprocessing , kami menerapkan teknik standarize fitur untuk menormalkan data agar mempermudah pemrosesan dengan algoritma ML. pada dataset ini karena ingin meningkatkan conversion rate maka kita memfokuskan recall score yang berfokus pada true positive sebanyak - banyaknya.
- Melalui EDA, kami mengkategorikan Usia, kami mengamati bahwa pelanggan yang termasuk dalam kelompok youngAge lebih tertarik pada respons kendaraan. Kami mengamati bahwa pelanggan yang memiliki kendaraan berusia kurang dari 2 tahun cenderung lebih tertarik pada asuransi kendaraan. Demikian pula, pelanggan yang memiliki kendaraan rusak cenderung lebih tertarik pada asuransi kendaraan.
- Untuk Seleksi Fitur, kami menggunakan heatmap dan uji multikolonieritas untuk fitur numerik dan untuk fitur kategorikal, kami menerapkan encoding. Di sini kami mengamati berdasarkan dua hal tersebut lalu mengambil fitur yang memiliki korelasi dan lolos uji VIF
- Selanjutnya, kami menerapkan Algoritma machine learning untuk menentukan apakah pelanggan tertarik dengan Asuransi Kendaraan. Untuk algoritma kita memakai :Logistic Regression, XGBoost, Decision Tree, Random Forest, Naive Bayes, dan KNN
- Setelah mengetahui hasil dari beberapa logaritma ML kita melihat bahwa pada score logistic regression mendapatkan skor recall sebesar 97% setelah melakukan hyperparameter, mengalami peningkatan meskipun tidak terlalu signifikan. Begitu pula untuk Naive bayes Classifier yang memiliki recall score 97%. maka kita dapat mengambil kesimpulan bahwa dua model tersebut merupakan best fit untuk pemodelan kali ini.
- Untuk Business Recommendation kami memfokuskan pada 3 feature yaitu Previously_Insured, Previously_Damaged dan Vehicle_Age sebagai berikut
- Previously_Insured - Perusahaan disarankan untuk melakukan pendekatan customer secara detail, dengan cara melakukan penyebaran kuisioner atau mengadakan event yang menarik untuk customer dan perusahaan juga disarankan untuk memberikan diskon untuk customer seperti diskon untuk "Safety Driver", "Young Driver" dan "Mature Driver".
- Previously_Damaged - Perusahaan disarankan melakukan campaign yang berfokus pada customer yang sudah pernah mengalami kerusakan pada kendaraan dan perusahaan juga disarankan untuk dapat menawarkan layanan add-on gratis khusus kepada customer yang sudah pernah mengalami kerusakaan pada kendaraan dengan opsi layanan add on seperti "Zero-Depreciation", "Engine Protection", dan "24x7 Roadside Assistance".
- Vehicle_Age - Perusahaan disarankan untuk mengadakan campaign pada saat customer membeli kendaraan baru, dan bekerja sama dengan dealer/showroom kendaraan dengan cara melakukan bundling asuransi kendaraan dengan customer yang membeli kendaraan, terutama pada usia kendaraan yang baru atau berusia 1-2 tahun untuk memaksimalkan konversi asuransi dari penjualan kendaraan yang berasal dari dealer/showroom.
---

# Reference
1. Kaiser Family Foundation - https://www.kff.org/
2. Pew Research Center - https://www.pewresearch.org/
3. U.S. Census Bureau - https://www.census.gov/
4. Paper - https://github.com/minsu0816/ADS505-HealthCareCrossSelling/blob/main/ADS-505-Team6-JupyterNotebook-WrittenReport.pdf
5. Journal - https://www.academia.edu/80341307/Comparative_Analysis_of_Building_Insurance_Prediction_Using_Some_Machine_Learning_Algorithms


[def]: #machine-learning-evaluation-&-supervised-learning
[(#machine-learning-evaluation-&-supervised-learning)]: #machine-learning-evaluation-&-supervised-learning
