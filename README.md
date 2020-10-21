# Pie Sales Linear Regression
## a. Identifikasi Masalah
Diberikan sebuah dataset yang berisikan data penjualan kue pie selama 15 minggu. Data tersebut akan digunakan untuk melakukan evaluasi faktor-faktor yang dianggap mempengaruhi penjualan kue pie. Berikut adalah atribut-atribut yang terdapat pada dataset tersebut.

1. **week**: menunujukkan minggu ke berapa data tersebut
2. **pie_sales**: jumlah kue pie yang terjual pada minggu tersebut merupakan Dependent Variable
3. **price** (dalam $): harga kue pie pada minggu tersebut merupakan Independent Variable
4. **advertising** (dalam $100): biaya iklan dalam minggu tersebut merupakan Independent Variable

### Exploratory Data Analysis
![dataset](/img/dataset.png)

Table tersebut berisikan data-data penjualan kue pie. Setiap atribut menunjukkan faktor-faktor yang dianggap mempengaruhi penjualan kue pie. Untuk atribut week hanya digunakan sebagai penunjuk urutan minggu keberapa untuk atribut pie_sales, price, dan advertising sehingga bisa di drop.
Selanjutnya memvisualisasikan atribut price, advertising serta pie_salses dengan menggunakan scatter plot.

![visualisasi](/img/download.png)

Dari scatter di atas dapat dilihat hubungan antara atribut price dengan pie_sales dan atribut advertising dengan pie_sales. 

- Pada hubungan antara atribut price dengan pie_sales memiliki relasi negatif, berarti jika nilai price semakin tinggi, maka pie_sales akan menurun. 

- Pada hubungan antara atribut advertising dengan pie_sales memiliki relasi positif, berarti jika nilai advertising semakin tinggi, maka pie_sales akan ikut tinggi.

## b. Model Analisis
Data akan dibuat terpisah menjadi dua yakni Independent variables dan Dependent Variable. 

### 1.  Regression dengan Scikit Learn (Model 1)
Pada model 1 digunakan seluruh data tanpa adanya pemisahan antara training data dan testing data. Semua data akan digunakan untuk membuat model prediksi. Data dipisah menjadi 2 yakni X berisi Independent varibles yakni atribut price dan advertising dan Y berisi Dependent varible yakni atribut pie_sales. Prediksi dilakukan dengan memasukkan variabel X.  Berikut merupakan intercept dan koefisien dari model yang dibangun.

![model1](/img/intercept_coeffecient.png)

Pengujian model linear regresi menggunakan MAE, MSE, RMSE, dan R-squared.
- MAE (Mean Absolute Error) mewakili selisih antara nilai sebenarnya dengan nilai prediksi yang didapatkan dengan rata-rata absolut dari selisih data.
- MSE (Mean Squared Error) mewakili perbedaan antara nilai asli dan nilai prediksi yang didapat dengan mengkuadratkan selisih rata-rata dari data
- RMSE (Root Mean Squared Error) adalah tingkat kesalahan menurut akar kuadrat MSE.
- R-squared mewakili tingkat ketepatan dari model yang menunjukkan presentasi variasi dari Dependent variable yang dapat dijelaskan oleh Independent variables. Semakin mendekati 1 maka semakin baik modelnya. 

Pada model yang dibangun mendapatkan hasil sebagai berikut:

- MAE: 34.545

- MSE: 1802.2204

- RMSE: 42.452

- R-squared: 0.521

Nilai RMSE = 42.452 menunjukkan bahwa rata-rata perbedaan antara nilai prediksi dengan nilai asli .

Nilai R-squared = 0.521 menunjukkan bahwa data kurang bervariasi.

Untuk analisis residual menggunakan scatter plot dan histogram.

Data residual antara nilai asli dan nilai prediksi berbentuk linear 

![residu1](/img/scatter_model1.png)

![residu2](/img/histogram_model1.png)

Berdasarkan histogram dengan bentuk yang demikian menandakan bahwa normalitas pada data telah bagus.

### 2.	Regression dengan Scikit Learn (Model 2)
Pada model 2 menggunakan training data dan testing data. Training data sebesar 70% dan testing data sebesar 30% dari total dataset. Training data digunakan untuk membuat model prediksi. Dan Testing data digunakan untuk melakukan uji terhadap model yang dihasilkan dari data training dengan membuat prediksi dari testing data. Hasil prediksi akan dibandingkan dengan nilai sebenarnya dari testing data. 
Berikut meripakan intercept dan koefisien dari model yang dibangun:

![model2](/img/intercept_coeffecient_train_test.png)

Pengujian model linear regresi menggunakan MAE, MSE, RMSE, dan R-squared.
- MAE (Mean Absolute Error) mewakili selisih antara nilai sebenarnya dengan nilai prediksi yang didapatkan dengan rata-rata absolut dari selisih data.
- MSE (Mean Squared Error) mewakili perbedaan antara nilai asli dan nilai prediksi yang didapat dengan mengkuadratkan selisih rata-rata dari data
- RMSE (Root Mean Squared Error) adalah tingkat kesalahan menurut akar kuadrat MSE.
- R-squared mewakili tingkat ketepatan dari model yang menunjukkan presentasi variasi dari Dependent variable yang dapat dijelaskan oleh Independent variables. Semakin mendekati 1 maka semakin baik modelnya. 

Pada model yang dibangun mendapatkan hasil sebagai berikut:

- MAE: 38.506

- MSE: 2326.964

- RMSE: 48.238

- R-squared: 0.501

Nilai RMSE = 48.23 menunjukkan bahwa rata-rata perbedaan antara nilai prediksi dengan nilai asli .

Nilai R-squared = 0.501 menunjukkan bahwa data kurang bervariasi.

Untuk analisis residual menggunakan scatter plot dan histogram.

Data residual antara nilai asli dan nilai prediksi berbentuk linear 

![residu3](/img/scatter.png)

![residu4](/img/histogram.png)

Berdasarkan histogram dengan bentuk yang demikian menandakan bahwa normalitas pada data telah bagus.

### 3.	Regression dengan Statsmodel Model 1
Dengan Statsmodel akan dilakukan eksplorasi lebih lanjut terhadap data. Model yang dimasukkan untuk eksplorasi lebih lanjut adalah model 1 yang menggunakan seluruh data. Model akan melakukan prediksi terhadap Independent variable yang nantinya akan di rangkum menjadi satu kesatuan hasil yang dapat digunakan untuk menganalisis data. Berikut adalah hasil dari model:

![statmodel](/img/statsmodel.png)

Jumlah data (n)= 15

Jumlah Independent variables (k)= 2

### **R-squared**
Dikarenakan jumlah Independent varibels adalah 2 maka digunakan R-squared, karena Adjusted R-squared digunakan untuk regresi dengan lebih dari dua Independent variables. 

Nilai **R-squared = 0.521** menunjukkan bahwa atribut price dan advertising hanya mempengaruhi price_sales sebesar 52.1% dan terdapat 47.9% dipengaruhi oleh atribut lain yang mungkin tidak dimasukkan ke dalam data.


---


### **Autocorrelation dengan Durbin Watson**
H0: tidak terdapat autocorrelation

H1: ada autocorrelation

Nilai **Durbin-Watson (D)=1.683**. Berdasarkan pada tabel Durbin-Watson untuk n=15 dan k=2. 

![tabelDW](/img/dw.png)

dL=0.9455 

dU=1.5432. 

4-dU=2.4568

4-dL=3.0545 

**D > dU dan D < 4-dU**

Sehingga H0 diterima

Membuktikan **tidak ada autocorrelation** pada data.


---



#### **F-Test**

H0: tidak terdapat autocorrelation

H1: ada autocorrelation

![tabelF](/img/Ftest.png)

**Dengan menggunakan F-Test**

Nilai **F-statistic=6.539**.

Tingkat signifikansi menggunakan $\alpha$= 5% atau 0.05.

Dengan n=15, k=2

Maka, 

df1 = 2

df2 = 12

Berdasarkan table distribusi F maka nilai **F=3.89**

**F-statistic > F**, artinya secara signifikan atribut price dan advertising secara bersama-sama berpengaruh terhadap pie_sales. 

---


### **T-Test**

H0: Secara parsial tidak ada pengaruh yang terlalu signifikan

Ha: Secara parsial ada pengaruh yang signifikan

![tabelT](/img/Ttest.png)

**Atribut Price**

Tingkat signifikansi menggunakan $\alpha$ = 5% atau 0.05.

Dengan t=-2.306

Dengan alpha = 5%/2 = 2.5% (uji 2 sisi)

df = 12

maka berdasarkan table distribusi T maka nilai T = 2.17881.

**-t < -T**, H0 ditolak dan artinya secara parsial ada pengaruh signifikan antara Price dengan pie_sales. 

**Atribut Advertising**

Tingkat signifikansi menggunakan $\alpha$ = 5% atau 0.05.

Dengan t=2.855

Dengan alpha = 5%/2 = 2.5% (uji 2 sisi)

df = 12

maka berdasarkan table distribusi T maka nilai T = 2.17881.

**t > T**, H0 ditolak, artinya secara parsial ada pengaruh signifikan antara advertising dengan pie_sales. 

Kesimpulan pada t-Tes menunjukkan bahwa atribut price dan atribut advertising sama-sama memiliki pengaruh yang signifikan terhadap pie_sales

### 4.	Regression dengan Statsmodel Model 2
Dengan Statsmodel akan dilakukan eksplorasi lebih lanjut terhadap data. Model yang dimasukkan untuk eksplorasi lebih lanjut adalah model 2 yang menggunakan training dan testing data. Model akan melakukan prediksi terhadap Independent variable yang nantinya akan di rangkum menjadi satu kesatuan hasil yang dapat digunakan untuk menganalisis data. Berikut adalah hasil dari model:

![statmodel2](/img/statsmodel_model2.png)

Jumlah data (n)= 10

Jumlah Independent variables (k)= 2

### **R-squared**

Nilai **R-squared = 0.465** menunjukkan bahwa atribut price dan advertising hanya mempengaruhi price_sales sebesar 45.6% dan terdapat 64.4% dipengaruhi oleh atribut lain yang mungkin tidak dimasukkan ke dalam data.


---


### **Autocorrelation dengan Durbin Watson**
H0: tidak terdapat autocorrelation

H1: ada autocorrelation

Nilai **Durbin-Watson (D)=2.290**. Berdasarkan pada tabel Durbin-Watson untuk n=10 dan k=2 

![tabelDW2](/img/dw2.png)

dL=0.6972

dU=1.6413

4-dU=2.3587

4-dL=3.3028

**D > dU dan D < 4-dL** 

Sehingga H0 diterima.

Membuktikan **tidak ada autocorrelation** pada data.


---



### **F-Test**
H0: Secara bersamaan tidak ada pengaruh yang terlalu signifikan

Ha: Secara bersamaan ada pengaruh yang signifikan

![tabelF2](/img/Ftest2.png)

**Dengan menggunakan F-Test**

Nilai **F-statistic=3.036**.

Tingkat signifikansi menggunakan $\alpha$= 5% atau 0.05.

Dengan n=10, k=2

Maka, 

df1 = 2

df2 = 7

Berdasarkan table distribusi F maka nilai **F=4.74**

**F-statistic < F**, artinya H0 ditolak dan secara signifikan atribut price dan advertising secara bersama-sama tidak berpengaruh terhadap pie_sales. 


---


### **T-Test**
H0: Secara parsial tidak ada pengaruh yang terlalu signifikan

Ha: Secara parsial ada pengaruh yang signifikan

![tabelT2](/img/Ttest2.png)

**Atribut Price**

Tingkat signifikansi menggunakan $\alpha$ = 5% atau 0.05.

Dengan t=-1.352

Dengan alpha = 5%/2 = 2.5% (uji 2 sisi)

df = 7

maka berdasarkan table distribusi T maka nilai T = -2.36462

**-t > -T**, artinya H0 diterima dan secara parsial tidak ada pengaruh signifikan antara atribut price dengan pie_sales. 

**Atribut Advertising**

Tingkat signifikansi menggunakan $\alpha$ = 5% atau 0.05.

Dengan t=2.274

Dengan alpha = 5%/2 = 2.5% (uji 2 sisi)

df = 7

maka berdasarkan table distribusi T maka nilai T = 2.36462

**t < T**, artinya H0 diterima dan secara parsial tidak ada pengaruh signifikan antara atribut advertising dengan pie_sales. 

Kesimpulan pada t-Tes menunjukkan bahwa atribut price dan atribut advertising sama-sama memiliki pengaruh yang tidak terlalu signifikan terhadap pie_sales

# KESIMPULAN

Model 1 dan Model 2 sama-sama dapat memprediksi bagaimana pie_sales berdasarkan atribut price dan advertising, sama-sama tidak memiliki autocorrelation. 

Untuk model 1 memiliki RMSE=42.245 dan R-squared=0.52. Sedangkankan model 2 memiliki RMSE=48.23 dan R-squared=0.5. Model 1 memiliki tingkat selisih antara data prediksi dan data asli yang lebih sedikit daripada model 2, sehingga dapat memprediksi dengan lebih akurat ketimbang model 2. 

Mesikupun model 1 memiliki performa yang lebih baik daripada model 2, akan tetapi nilainya masih kurang bagus. Selisih rata-rata dari model masih cukup besar dan Dikarenakan dataset hanya berjumlah 15 baris, maka dirasa kurang untuk membuat model linear regresi yang ideal. 

Dilihat dari model statistik berdasarkan model 1, bahwa atribut price dan advertising hanya dapat mempengaruhi 52.1% nilai prediksi, 47.9% dipengaruhi atribut lain yang mungkin tidak dimasukkan dalam dataset.
