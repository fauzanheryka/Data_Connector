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
    - 3 [Data Pre-Processing](#data-pre-processing)
    - 4 [Feature Engineering](#feature-engineering)
    - 5 [Feature selection](#feature-selection)
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

---

# Reference
1. Kaiser Family Foundation - https://www.kff.org/
2. Pew Research Center - https://www.pewresearch.org/
3. U.S. Census Bureau - https://www.census.gov/
