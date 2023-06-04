# Final Project Rakamin Data Science Bootcamp Batch 32
## Kelompok 4 : Data Traveller

## Insight Summary
### Univariate Analysis
1. Distribusi kolom Age cenderung mendekati distribusi normal, menunjukkan penyebaran nilai yang seimbang.
2. kolom DurationOfPitch, NumberOfTrips, dan MonthlyIncome memiliki skewness positif, menunjukkan adanya pencilan atau outlier dalam data. Pencilan ini dapat memiliki pengaruh yang signifikan terhadap hasil analisis.
3. Untuk kolom lainnya, dapat diabaikan karena umumnya mengandung data diskrit atau ordinal, yang tidak memerlukan pertimbangan yang sama dengan variabel kontinu.
4. Pada kolom TypeofContact distribusi Self Enquiry lebih banyak daripada COmpany Visited
5. Pada kolom Occupation distribusi Salaried dan Small Business paling banyak dibanding yang lainnya, dan pada Free Lancer nantinya akan dihapus karena tidak ada nilainya
6. Pada kolom Gender jenis kelamin laki-laki lebih banyak dibandingkan perempuan. Dan ada kesalahan penulisan Fe Male yang dimana seharusnya Female.
7. Pada kolom ProductPitched basic dan Deluxe memiliki penjualan tertinggi
8. Pada kolom MaritalStatus Customer yang sudah menikah memiliki jumlah paling banyak
9. Pada kolom Designation customer dengan jabatan Executive dan Manager memiliki jumlah paling banyak

### Multivariate Analysis
1. Kolom MonthlyIncome, Passport dan Age memiliki korelasi kuat terhadap kolom target (ProdTaken)
2. Mayoritas yang tidak membeli produk adalah laki-laki yang sudah menikah dan bekerja sebagai karyawan, sedangkan mayoritas yang membeli produk adalah laki-laki yang sudah menikah dan seorang wiraswasta.
3. Pembeli produk rata-rata berumur 26-50
4. Kebanyakan pembeli tinggal dilingkungan kota yang sudah maju atau juga tinggal di kota satelit
5. Kebanyakan transaksi dilakukan oleh orang yang memiliki passport.

## Data Preprocessing
### Handling Missing Value
Opsi yang kami ambil untuk handle missing value adalah menggunakan metode MICE karena imputasi dilakukan menggunakan model regresi.
Setelah dilakukan proses imputasi untuk missing values menggunakan metode MICE, dataset sudah tidak ada kolom yang kosong.

### Handling Invalid Value
Berdasarkan hasil pengamatan EDA:
1. Terdapat kesalahan pada penulisan kolom Gender dimana "Fe Male" bermakna sama dengan "Female". Maka "Female" akan direplace menjadi "Female"
2. Terdapat penggunaan istilah yang berbeda pada kolom Marital status yaitu "Unmarried" dan "Single" dimana kedua status tersebut bermakna sama. Maka "Unmarried" akan direplace menjadi "Single"

### Handling Duplicated Data
Setelah dilakukan pengecekan ulang dengan menghapus kolom CustomerID (drop CustomerID) ditemukan beberapa data yang duplikat. Kemudian dilakukan penghapusan data duplikat.

### Handling Outlier
Karena keterbatasan data, metode yang kami pakai untuk handling outlier adalah Z-Score.

### Feature Extraction
Pada feature extraction kita akan menggabungkan kolom NumberOfPersonVisiting dan NumberOfChildrenVisting menjadi kolom baru yaitu TotalVisiting.

### Feature Tambahan
Berikut adalah beberapa fitur tambahan selain yang ada di dataset namun tidak diimplementasikan : 
1. Recurring Transaction (Boolean)
2. Preferred Property Type
3. Region of Destination
4. Preferred Duration of Trip

### Feature Transformation
Berdasarkan insight yang kita dapat dari EDA, ada beberapa fitur yang berkorelasi dengan target tapi belum berdistribusi normal atau skew positif. Maka kita lakukan log Transformasi dan Standarisasi agar distribusi nya normal/ mendekati normal.

### Feature Encoding
Pada Feature Encoding categorical dibagi menjadi dua metode yaitu encoding yang bertipe data ordinal dan encoding yang bertipe data selain ordinal dan menggunakan librari LabelEncoder dan OneHotEncoder dari sklearn

### Feature Selection
Pada feature selection kita memakai 2 metode yang digunakan untuk menentukan fitur-fitur apa saja yang digunakan pada pemodelan dan mempunyai korelasi terhadap target yaitu metode ANOVA dan metode RandomForest.
Karena dari dua metode tersebut semua fitur relatif terdistribusi maka kami menggunakan semua kolom sebagai fitur.

### Handling Data Imbalance
Karena adanya ketimpangan atau ketidakseimbangan dalam jumlah data pada kolom target maka perlu dilakukan oversampling. Oversampling akan dilakukan menggunakan metode SMOTE.