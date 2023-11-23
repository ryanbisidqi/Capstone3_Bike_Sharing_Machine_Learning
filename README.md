# Capstone Project Module 3 - Bike Sharing

## **Contents**

1. Business Problem Understanding
2. Data Understanding
3. Data Preprocessing
4. Modeling
5. Conclusion
6. Recommendation

## **1. Business Problem Understanding**

### **Context**

Bike Sharing is a shared transportation service where conetional bicycles or electric bicycles are made availabel for shared use by individuals on a short-term basis for a price or for free.

Users can pick up bicycles around the city from multiple docked or dockless stations and return them at the same system. Docks are special bike racks that lock the bike, and can only be released by computer control, while dock-less bike share does not require a docking station, bikes can be parked inside designated bike racks or along sidewalks. Bike sharing provides an easy, cheap, and efficient means of transportation for locals and tourists to get around the city.

Bike sharing systems are often facilitated through mobile apps or membership cards, which allow users to locate and unlock bikes, track their usage, and make payments. 

Bike sharing market statistics have witnessed significant growth in recent years, driven by increasing urbanization, focus on sustainable transportation options, and popularity of shared mobility services.

### **Problem Statement**

Salah satu tantangan bagi perusahaan bike sharing adalah pemecahan  masalah untuk dapat memiliki model bisnis yang menguntungkan secara finansial bagi perusahaan, serta bisa memberikan pengalaman positif terhadap penyewa sepeda.

Mengingat bisnis bike sharing ini sangat tergantung pada kualiatas sepeda dan ketersediaan sepeda di lapangan yang digunakan oleh penyewa sepeda setiap harinya, Namun keputusan yang tidak tepat bisa menimbulkan masalah serius terhadap perusahaan, menyediakan sepeda yang terlalu banyak bisa mengakibatkan penurunan revenue dan tingginya biaya maintenance, begitu pula jika kebutuhan sepeda tidak terpenuhi bisa menurunkan kepuasan penyewa dan hilangnya pengguna mengingat bahwa persaingan ketat dengan perusahaan lain sangat tinggi.

### **Goal**

oleh karena itu untuk meminimalisir biaya maintance dan bisa meningkatkan revenue perusahaan ingin memprediksi penggunaan sepeda yang produktif dan tidak, sehingga mengurangi pembengkakan biaya akibat sepeda yang berlebih dan kekurangan sepeda ketika penyewa sedang banyak. 

Maka perusahaan memerlukan tools yang bisa membantu perusahaan untuk menentukan unit yang harus disediakan sesuai dengan jumlah customer yang membutuhkan, sehingga bisa meningkatkan revenue dan menurunkan biaya maintenance akibat penumpukan unit yang tidak digunakan

### **Analytical Approach**

Untuk memenuhi kebutuhan tersebut, perlu dilakukan analisis data yang tersedia agar menemukan pola dari setiap fitur yang ada, sehingga bisa membuat pemodelan prediksi yang sesuai dengan kebutuhan perusahaan untuk menentukan unit yang disediakan berdasarkan kondisi yang terjadi. 

Selanjutnya, kita akan membangun suatu model regresi yang akan membantu perusahaan untuk dapat menyediakan 'tool' prediksi Kebutuhan Unit , yang mana akan berguna untuk perusahaan dalam menentukan jumlah unit yang dibutuhkan sesuai tingkat permintaan customer.

### **Metric Evaluation**

Evaluasi metrik yang akan digunakan adalah RMSE, MAE, dan MAPE, di mana RMSE adalah nilai rataan akar kuadrat dari error, MAE adalah rataan nilai absolut dari error, sedangkan MAPE adalah rataan persentase error yang dihasilkan oleh model regresi. Semakin kecil nilai RMSE, MAE, dan MAPE yang dihasilkan, berarti model semakin akurat dalam memprediksi kebutuhan unit sesuai dengan limitasi fitur yang digunakan. 

Selain itu, kita juga bisa menggunakan nilai R-squared atau adj. R-squared jika model yang nanti terpilih sebagai final model adalah model linear. Nilai R-squared digunakan untuk mengetahui seberapa baik model dapat merepresentasikan varians keseluruhan data. Semakin mendekati 1, maka semakin fit pula modelnya terhadap data observasi. Namun, metrik ini tidak valid untuk model non-linear.

## **2. Data Understanding**

### **Attributes Information**

| **Attribute** | **Data Type** | **Description** |
| --- | --- | --- |
| dteday | Object | Date  |
| hum | Float | Normalized humidity (the values are divided to 100) |
| weathersit | Integer | 1: Clear, Few clouds, Partly cloudy, Partly cloudy 2: Mist + Cloudy, Mist + Broken clouds, Mist + Few clouds, Mist, 3: Light Snow, Light Rain + Thunderstorm + Scattered clouds, Light Rain + Scattered clouds 4: Heavy Rain + Ice Pallets + Thunderstorm + Mist, Snow + Fog|
| holiday | integer | holiday or not |
| season | integer | season 1: winter 2: spring 3: summer 4: fall |
| atemp | Float | Normalized feeling temperature in Celsius. The values are derived via (t-tmin)/(tmax-tmin), tmin=-16, t_max=+50 (only in hourly scale) |
| temp | Float | normalized temperature in Celsius. The values are derived via (t-tmin)/(tmax-tmin), tmin=-8, t_max=+39 (only in hourly scale) |
| hr | Integer |hour (0 to 23) |
| casual | Integer | count of casual users |
| registered | Integer | registered users |
| cnt | Integer | count of total rental bikes including both casual and registered |

<br>

## **3. Exploratory Data Analysis (EDA)**

## **4. Data Prepocessing**

At this stage, we will perform data cleaning to ensure that the dataset to be used in further analysis is clean and ready for use. Some of the steps that need to be taken are:
- Check Missing Value
- Check Data Duplicates
- Replace Value
- Generate New Features
- Remove Irrelevant Feature
- Rename Features
- Handling Outliers

## **5. Data Analysis**

Based on the graph above, we can interpret that :

- At low temperatures, the number of bicycle rentals tends to be low. This is because at low temperatures, people tend to do less outdoor activities.
- At high temperatures, the number of bicycle rentals tends to be high. This is because at high temperatures, people tend to be more active outdoors, and bicycles are one of the efficient and environmentally friendly means of transportation.
- Humidity (x-axis) does not have a strong relationship with the number of bicycle rentals (y-axis). This means that changes in humidity have no significant effect on the number of bicycle rentals.
- This can be explained by the theory that humidity does not really affect people's desire for outdoor activities. People can still do outdoor activities, even with high humidity levels.
- Next, let's look at the correlation between the features.

It can be seen that the relationship between the features `Humidity`, `Temperature`, and `Count`, where the relationship between the features `Humidity` and `Count` has a moderate negative correlation, meaning that the more humidity decreases, the average bicycle rental will increase. 

And the `Temperature` feature has a moderate positive correlation, meaning that the higher the temperature, the higher the bike rental. However, we need to look at other features to make the analysis results more specific. Next, we will look at the relationship between categorical features and the `Count` feature.

Based on the graph above, it can be concluded that there is a significant relationship between weather and average bike rentals. We can see that:

- Sunny weather has the highest average bike rentals at 152 units.
- Cloudy weather has a lower average bike rental of 124 units.
- Drizzly weather has an average bike rental of 68 units.
- Heavy rainy weather has an average bicycle rental of 36 units.

In general, weather features have a high influence on bicycle rentals.
## **6. Modeling**

There is a significant difference between the RMSE and MAE values, where the RMSE value is higher because the residuals or error values are squared first before averaging. This causes RMSE to give a higher 'weight' to large error values, in other words, there are large error values generated by all algorithms used, so there is a significant difference between RMSE and MAR values.

- Based on the RMSE, MAE and MAPE values, SGBoost is the best model. and the lowest value is the Linear Regression model.

## **7. Conclusion and Recomendations**

### **a. Conclusion**

Dari hasil Benchmark Model dan Hyperparameter Tuning yang dilakukan, diperoleh model XGBoost Regressor sebagai model terbaik dengan parameter terbaik sebagai berikut :

- n_estimators : 300
- max_depth : 7
- learning_rate : 0.1

Metrik yang digunakan pada model ini adalah nilai RMSE, MAE dan MAPE. Jika dilihat dari nilai MAPE-nya sebesar 24%, model XGBoost Tuning bisa melakukan prediksi dengan kesalahan error berdasarkan MAPE sebesar 24%. maka ini berarti bahwa nilai prediksi untuk jumlah kebutuhan bike sharing akan berkisar kurang lebih 40 unit dari nilai prediksi dari model (dengan nilai yang dilatih dalam pemodelan sebesar 645). Namun tidak menutup kemungkinan juga bahwa prediksi bisa melest lebih jauh karena masih terdapat beberapa data yang nilai prediksi dan aktualnya masih menghasilkan errod yang lebih besar dari nilai RMSE.

### **b. Recomendation**

Rekomendasi untuk memperbaiki model serta meningkatkan model :
- Melakukan Hyperparameter Tuning dengan GridSearch dan mencobe berbagai kombinasi dari berbagai parameter yang ada pada model lebih banyak lagi.
- Mencoba lebih banyak model yang termasuk metode Ensemble seperti Voting Regressor dan Stacking Regressor.
- Penambahan fitur yang lebih memiliki korelasi dengan target('Count') seperti adanya event tertentu dan jarak lokasi station dengan lokasi perkantoran , sekolah atau tempat wisata, biaya per sewa untuk menghitung keuntungan dari setiap perjalanan.
- Penambahan jumlah data, dilihat dair efektif kinerja modeling yang sampi 600 data, menunjukan masih kurangnya data yang digunakan untuk pemodelan, karena ML akan semakin bagus hasil prediksinya jika semakin banyak ML mempelajari sebuah data.
