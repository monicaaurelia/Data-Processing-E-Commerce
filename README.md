# Data-Processing-E-Commerce
## E Commerce Dataset.xlsx adalah Kumpulan data milik perusahaan E-Commerce online terkemuka. Sebuah perusahaan ritel online (E commerce) ingin mengetahui pelanggan yang akan churn, sehingga mereka dapat mendekati pelanggan untuk menawarkan beberapa promo.
### Kolom yang ada pada E Commerce Dataset:
1) CustomerID Unique customer ID
2) Churn Tanda churn
3) Tenure Masa berlangganan
4) PreferredLoginDevice Perangkat login pilihan pelanggan
5) CityTier City tier
6) WarehouseToHome Jarak antara warehouse ke rumah pelanggan
7) PreferredPaymentMode Metode pembayaran pilihan pelanggan
8) Gender Gender Pelanggan
9) HourSpendOnApp Jumlah jam yang dihabiskan untuk aplikasi seluler atau situs web
10) NumberOfDeviceRegistered Jumlah total penipuan terdaftar pada pelanggan tertentu
11) PreferedOrderCat Kategori pesanan pilihan pelanggan bulan lalu
12) SatisfactionScore Skor kepuasan pelanggan pada layanan
13) MaritalStatus Status pernikahan pelanggan
14) NumberOfAddress Jumlah total alamat yang ditambahkan pada pelanggan tertentu
15) Complain Keluhan yang telah diajukan pada bulan lalu
16) OrderAmountHikeFromlastYear Persentase peningkatan pesanan dari tahun lalu
17) CouponUsed Jumlah total kupon yang telah digunakan bulan lalu
18) OrderCount Jumlah total pesanan yang telah sampai di bulan lalu
19) DaySinceLastOrder Jumlah hari sejak pesanan terakhir yang dilakukan oleh pelanggan
20) CashbackAmount Rata-rata cashback di bulan lalu

## Insight Descriptive Analysis

1) Baris data yang ada missing values serta rasionya :
- **Tenure** = 4,9%
- **WareHouseToHome** = 4,7%
- **HourSpendOnApp** = 4,7%
- **OrderAmountHikeFromlastYear** = 4,9%
- **CouponUsed** = 4,8%
- **OrderCount** = 4,8%
- **DaySinceLastOrder** = 5,8%

2) Kolom dengan tipe data kurang sesuai (float64 >> int64)
- Tenure
- HourSpendOnApp
- OrderAmountHikeFromlastYear
- CouponUsed
- OrderCount
- DaySinceLastOrder

3) Tidak ada data duplikat

4) Kolom data numerical yang memiliki nilai min/max terlalu jauh dari mean dan median:
- **Tenure**: min 0, max 61, mean 10, median 9
- **WarehouseToHome**: min 5, max 127, mean 15, median 14
- NumberOfAddress: min 1, max 22, mean 4, median 3
- OrderAmountHikeFromlastYear: min 11, max 26, mean 15, median 15
- CouponUsed: min 0, max 16, mean 1, median 1
- OrderCount: min 1, max 16, mean 3, median 2
- **DaySinceLastOrder**: min 0, max 46, mean 4, median 3
- **CashbackAmount**: min 0, max 324, mean 177, median 163

5) Pada kolom **PreferredLoginDevice** antara **Mobile Phone** dan **Phone** sepertinya jenis yang sama jadi digabung saja

6) Pada kolom **PreferredPaymentMode**:
- **Credit Card** dan **CC** itu sama, jadi akan digabung
- **Cash on Delivery** dan **COD** itu juga sama, jadi akan digabung
- awal ada **7** data unique karena ada yang sama jadi dikurangi tinggal **5** kategori

7) Pada kolom **PreferredOrderCat** antara **Mobile Phone** dan **Mobile** sepertinya jenis yang sama jadi digabung saja

## Insight Univariate Analysis
1) Boxplot
- WarehouseToHome ada outlier satu yang sangat jauh/ekstrem
- CouponUsed, OrderCount, DaySinceLastOrder, dan CashbackAmount memiliki banyak outlier

2) Kdeplot
- **positive skewed (right)**: Tenure, WarehouseToHome, NumerOfAddress, OrderAmountHikeFromlastYear, CouponUsed, DaySinceLastOrder, OrderCount, CashbackAmount
- **bimodal**: Churn, Complain
- **multimodal**: CityTier, HourSpendOnApp, NumberOfDeviceRegistered, SatisfactionScore
- **Unimodal/Simetris**: Churn

3) Countplot

(a) Churn pada Data Categorical
- **PreferredLoginDevice** : pelanggan yang churn mayoritas login melalui **phone** 
- **PreferredPaymentMode** : pelanggan yang melakukan churn paling banyak melakukan pembayaran melalui **debit card**
- **Gender** : pelanggan churn paling banyak dilakukan oleh **laki-laki (male)**
- **PreferedOrderCat** : churn paling banyak dilakukan oleh pelanggan yang membeli **mobile phone**
- **MaritalStatus** : mayoritas pelanggan yang churn berstatus **single**

(b) Churn pada Data Numerical
- **Tenure** : pelanggan yang mayoritas churn memiliki tenure selama **1** (kurang tahu satuannya)
- **CityTier** : pelanggan yang churn paling banyak berada kota tingkat **1**
- **WarehouseToHome** : churn banyak dilakukan oleh pelanggan yang jarak rumahnya dengan gudang sekitar **9** (kilometer)
- **HourSpendOnApp** : pelanggan yang paling banyak churn adalah pelanggan yang menghabiskan waktu sekitar **3 jam** pada mobile phone atau website
- **NumberOfDeviceRegistered** : Jumlah device yang paling banyak terdaftar pada pelanggan yang melakukan churn adalah **4**
- **SatisfactionScore** : Skor kepuasan yang paling banyak diberikan oleh pelanggan yang melakukan churn adalah **3**
- **NumberOfAddress** : jumlah alamat yang paling banyak ditambahkan oleh pelanggan yang melakukan churn yaitu **2**
- **Complain** : dalam sebulan terakhir pelanggan yang melakukan churn banyak **melakukan komplain**
- **OrderAmountHikeFromlastYear** : dalam setahun terakhir, pelanggan yang churn mayoritas terdapat peningkatan persentase order sebesar **12%**
- **CouponUsed** : dalam sebulan terakhir, pelanggan yang churn mayoritas menggunakan kupon sebanyak **1**
- **OrderCount** : dalam sebulan terakhir, pelanggan yang churn mayoritas melakukan order sebanyak **2** kali
- **DaySinceLastOrder** : mayoritas rata2 hari customer melakukan churn sejak terakhir order yaitu **0** dan **1** hari

### Rencana Pre-Processing
1. **Handling missing values with imputation (numeric)**: 
- Tenure = 4,9% =========================> median
- WareHouseToHome = 4,7% ================> median
- HourSpendOnApp = 4,7%  ================> mean
- OrderAmountHikeFromlastYear = 4,9%   ====> median
- CouponUsed = 4,8%  ====================> median
- OrderCount = 4,8%  ====================> median
- DaySinceLastOrder = 5,8%  =============> median


2. **Handling an outliers**
- Using Z score to all positively skewed distribution 


3. **Feature Transformation**
- Using Log Transformation to all positively skewed distribution


4. **Feature Encoding**
- PreferredLoginDevice ====> One Hot Encoding
- PreferredPaymentMode ====> One Hot Encoding
- Gender  =================> One Hot Encoding
- PreferedOrderCat ========> One Hot Encoding
- MaritalStatus ===========> One Hot Encoding


5. **Class Imbalance**
 Apakah frekuensi dari nilai yang paling umum timpang?
- PreferredLoginDevice, top frequency mobile phone = 70,97%    ==========> Undersampling
- PreferredPaymentMode, top frequency Debit Card = 41%        
- Gender, top frequency Gender = 60%                          ============> Undersampling
- PreferedOrderCat, top frequency mobile phone = 36,94 %
- MaritalStatus, top frequency Married = 53,30 %              ============> Undersampling


## Insight Multivariate Analysis

1) Pada **Churn** ditemukan korelasi sebagai berikut:

- korelasi **churn** dengan **tenure** sebesar -0,35 yang artinya **semakin tinggi tenure makan kemungkinan pelanggan untuk churn semakin rendah, sebaliknya semakin kecil tenure maka kemungkinan pelanggan churn semakin tinggi**
- korelasi antara **churn** dengan **complain** sebesar 0,25, artinya **semakin banyak pelanggan melakukan komplain maka kemungkinan pelanggan churn juga semakin tinggi**
- hasil korelasi tersebut mendukung data countplot sebelumnya

2) Terdapat korelasi antara **tenure**  dengan **CashbackAmount** yaitu sebesar 0,48 artinya **jika dalam sebulan terakhir pelanggan semakin banyak mendapatkan cashback maka tenure-nya akan semakin tinggi**

## Business Insight 
1) **Churn, Tenure, dan CashbackAmount**

**Insight**:
Pelanggan dengan tenure rendah cenderung mendapatkan cashback yang tergolong sedikit dan memiliki potensi untuk melakukan churn

**Insight**: 
- Pelanggan yang melakukan churn karena komplain lebih tinggi dibanding yang tidak komplain dan mayoritas membeli mobile phone
- Komplain paling banyak dilakukan oleh pelanggan membeli grocery atau kebutuhan sehari-hari, lalu disusul mobile phone dan fashion

**Business Recommendation**:
- Bagi pelanggan yang baru saja membeli barang elektronik, cross-selling dapat dilakukan dengan menawarkan aksesoris elektronik, seperti keyboard, mouse, dll
- Untuk grocery, menawarkan service pengiriman cepat untuk menjaga kualitas produk
- Untuk fashion dan mobile phone, menawarkan tampilan foto produk yang original atau asli dan deskripsi produk yang jelas

# Pre-Processing
1. **Handling missing values with imputation (numeric)**: 
- Tenure = 4,9% =========================> median
- WareHouseToHome = 4,7% ================> median
- HourSpendOnApp = 4,7%  ================> mean
- OrderAmountHikeFromlastYear = 4,9%   ====> median
- CouponUsed = 4,8%  ====================> median
- OrderCount = 4,8%  ====================> median
- DaySinceLastOrder = 5,8%  =============> median


2. **Handling an outliers**
- Using Z score to all positively skewed distribution 


3. **Feature Transformation**
- Using Log Transformation to all positively skewed distribution


4. **Feature Encoding**
- PreferredLoginDevice ====> One Hot Encoding
- PreferredPaymentMode ====> One Hot Encoding
- Gender  =================> One Hot Encoding
- PreferedOrderCat ========> One Hot Encoding
- MaritalStatus ===========> One Hot Encoding


5. **Class Imbalance** 
<br> Apakah frekuensi masing-masing nilai pada target timpang?
<br> 0 : 4882
<br> 1 : 948
<br> Persentase ketimpangan 16.838 %
<br> Berdasarakan https://developers.google.com/machine-learning/data-prep/construct/sampling-splitting/imbalanced-data ada tiga tingkat ketimpangan yaitu mild, moderate dan extreme. Data ini tergolong pada tingkat ketimpangan moderate.

# 1. **Handling missing values with imputation (numeric)**:
- Tenure = 4,9% =========================> median
- WareHouseToHome = 4,7% ================> median
- HourSpendOnApp = 4,7%  ================> mean
- OrderAmountHikeFromlastYear = 4,9%   ====> median
- CouponUsed = 4,8%  ====================> median
- OrderCount = 4,8%  ====================> median
- DaySinceLastOrder = 5,8%  =============> median

# 2. Feature Selection & Extraction
- Using DaySinceLastOrder or WeekSinceLastOrder
- Drop OrderCount
- New Features: WeekSinceLastOrder, OrderMean, CashbackRate

# 3. **Handling outliers**
- Using Z score

# 4. **Feature Transformation**
- Using Log Transformation to features: WarehouseToHome, NumberOfAddress, OrderAmountHikeFromlastYear
- Using Standardization to features:Tenure, CouponUsed, DaySinceLastOrder, CashbackAmount

# 5. **Feature Encoding**
- PreferredLoginDevice ====> One Hot Encoding
- PreferredPaymentMode ====> One Hot Encoding
- Gender  =================> One Hot Encoding
- PreferedOrderCat ========> One Hot Encoding
- MaritalStatus ===========> One Hot Encoding

# 6. **Class Imbalance**
