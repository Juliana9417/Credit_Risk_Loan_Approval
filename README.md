# Credit_Risk_Loan_Approvall
Predicting Credit Risk Using Machine Learning for Loan Decision-Making

# 🛒 **Predicting Credit Risk Using Machine Learning for Loan Decision-Making** 🛒
---
## 📂 **Stage 0 : Problem Statement**
### Problem Statement
- In the multifinance industry, effective credit risk management is essential to prevent financial losses and enhance profitability. High Non-Performing Loan (NPL) rates can disrupt financial stability and impact business decisions. By leveraging seven years of historical loan data, companies can improve the accuracy of credit risk assessments and predict default probabilities more effectively.

- The available data indicates that approximately 89.07% of loans are classified as good loans, while 10.93% fall into the bad loan category. Although the percentage of bad loans is relatively small, it still poses significant risks, warranting deeper analysis.

- The Probability of Default (PD) is a powerful method for accurately predicting credit risk. Utilizing PD allows companies to identify risk factors, optimize credit decisions, mitigate potential losses, and increase profitability.- 


### Goals
- Develop a Probability of Default (PD) model to predict loan defaults and support more accurate credit decision-making.


### Objectives
- Build a reliable and accurate machine learning-based PD model.
- Identify key factors influencing loan defaults to facilitate better decision-making.

### Business Matrics
-  Probability of Default (PD)
<br>

---
<br>
## 📂 **Stage 1 : Data Understanding**
### Dataset
Dataset Loan 2007-2014
Rows : 466285
Columns : 75
Columns-Null : 40 Columns
Duplicates Data : 0
</p>
<br>

## 📂 **Stage 2 : Feature Engineering**
<p align="center">
<img src="https://github.com/user-attachments/assets/886250d9-6221-458f-90e0-e0fa18128d66"
 alt="Proportionloan">
</p>
<br>

### Data Preprocessing Summary:

1. Feature Removal:
- Drop columns with >70% missing values.
- Exclude identifiers (e.g., id, id anggota, url, etc.).
- Remove sub_grade (duplicates information from grade).
- Exclude future-related features (e.g., next_pymnt_d, recovery, etc.).

2. Loan Status Classification:
- Bad Loans (1): Charged Off, Default, Late (31-120 days), Late (16-30 days), Does not meet the credit policy. Status: Charged Off.
- Good Loans (0): Fully Paid, Current, In Grace Period, Does not meet the credit policy. Status: Fully Paid.

3. Target Variable Creation:
- Create a binary variable: good (0) and bad (1) loans.
<br>

## 📂 **Stage 3 : Exploratory Data Analysis**
<p align="center">
<img src="https://github.com/user-attachments/assets/6fcab117-4c78-4587-bccd-ab6a5f1dabca"
 alt="MultivariateAnalysis">
</p>

The heatmap highlights significant correlations among payment variables, such as total_rec_int with total_pymnt (0.60) and last_pymnt_amnt with total_pymnt (0.64). Weak correlations exist between loan_bad and variables like annual_inc (0.04, positive), dti (-0.06), and int_rate (-0.17, both negative), suggesting minimal influence on default risk. Most other features show low, likely insignificant correlations.

Data distribution is imbalanced, with most features highly skewed and concentrated in specific ranges, alongside notable outliers. The target variable, loan_bad, also shows class imbalance, requiring adjustments for effective classification modeling.
<br>

## 📂 **Stage 4 : Data Preparation**
<br>
1. Data Preparation
- Data transformation
- Handling missing value
- Feature encoding : OHE
- Feature selection : Teknik WoE dan IV
- Feature Extraction

2. New Features Based WoE and IV
- Spliting Data : Train & Test
- Class Imbalance : RandomOverSampler
- Modelling

<p align="center">
<img src="https://github.com/user-attachments/assets/d528b2c7-b2ed-4699-9968-56384d4ba2ae"
 alt="JumlahData">

## 📂 **Stage 4 : Data Modeling**

<p align="center">
<img src="https://github.com/user-attachments/assets/26c4db70-addd-41d5-9fe5-2fbc55f347f4"
 alt="DataModeling">

## 📂 **Stage 3 : Modelling**

**Recall (cross validation)** digunakan sebagai matrix evaluasi dengan fokus terhadap nilai **False Negative** dalam membandingkan performa antar algoritma model klasifikasi mechine learning (Supervised Learning). <br>

Menurut Powers, **recall (sensitivitas atau true positive rate)** merupakan metrik evaluasi yang penting, terutama dalam kasus di mana deteksi positif benar (**true positives**) lebih kritis dibandingkan dengan deteksi negatif salah (false negatives). Powers juga menjelaskan bahwa kesalahan tipe II (**false negatives**) memiliki konsekuensi yang lebih serius dibandingkan dengan kesalahan tipe I (false positives). <br>

**Cross-validation** digunakan sebagai teknik evaluasi recall dari model machine learning untuk memastikan model tidak hanya dioptimalkan untuk dataset tertentu, tetapi memiliki generalisasi yang baik pada dataset lainnya (Caruana & Niculescu-Mizil, 2006). <br>

Kasus dalam dataset ini dimana perusahaan ingin meningkatkan revenue. Maka dari itu, recall (cross validation) menjadi fokus utama untuk menghindari model gagal mengidentifikasi pelanggan yang benar-benar menghasilkan revenue. Dengan nilai false negatives rendah, diharapkan lebih banyak peluang revenue yang tidak terlewatkan oleh perusahaan. Model dengan nilai recall (cross validation) mendekati 1 menunjukkan performa yang lebih baik dalam mendeteksi semua kejadian positif. <br>

### **Logistic Regression : Modeling and Evaluation**

Setelah uji coba beberapa algoritma model klasifikasi yaitu Logistic Regression, Decission Tree, Random Forest, AdaBoost, dan XGBoost. Model algoritma **Logistic Regression** dengan Hyperparameter Tuning dipilih karena menunjukkan performa terbaik. Dengan mempertimbangkan recall yang tinggi dan hasil cross-validation yang baik, Logistic Regression memberikan keseimbangan optimal antara deteksi kasus positif dan penghindaran dari false negatives, sehingga mendukung tujuan akhir peningkatan revenue secara efektif.<br>

Berikut hasil evaluasi dari prediksi model Logistic Regression setelah dilakukan Hyperparameter Tuning.
<p align="center">
  <img src="https://github.com/user-attachments/assets/637a0ed5-5f1a-40bf-bf42-37825c5120b7">
   </p>
<p align="center">
  Gambar 18 – Hasil Evaluasi Matriks Logistic Regression dengan Hyperparameter Tuning  <br>

Nilai Recall (cross-validation) dari model Logistic Regression dengan Hyperparameter Tuning pada train sekitar 0.83 dan test 0.81 yang berarti model memiliki performa yang sudah cukup baik.
<p align="center">
  <img src="https://github.com/user-attachments/assets/58c460d5-4508-4ca4-b57d-2fdf50db6a74">
   </p>  
<p align="center">
  Gambar 19 – Confussion Matrix Logistic Regression dengan Hyperparameter Tuning <br>
<br>
</p>
best_model (Logistic Regression dengan Hyperparameter Tuning terbaik) lebih moderat dan lebih seimbang dalam hal recall dengan ukuran/metrik evaluasi lainnya. Dalam konteks bisnis, model ini merupakan pilihan yang lebih baik karena tetap menjaga keseimbangan antara revenue (tujuan utama) dan cost (bukan tujuan utama namun perlu dipertimbangkan juga).

### **Logistic Regression : Feature Importances**
Langkah berikutnya dilakukan pengukuran pengaruh fitur terhadap model berdasarkan nilai absolut dari koefisien fitur dalam model. Dengan kata lain, fitur dengan koefisien yang lebih besar (baik positif maupun negatif) dianggap lebih penting, karena perubahan dalam fitur tersebut akan berdampak lebih signifikan terhadap output model. <br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/acf3cae7-a1a1-4bc3-896b-03279affef92">
   </p>  
<p align="center">
  Gambar 20 – Feature Importances by the absolute value of their coefficients <br>
<br>

Fitur PageValues memiliki koefisien positif (0.02854369)menunjukkan bahwa PageValues berdampak positif terhadap target variabel, tetapi pengaruhnya tidak besar.<br>
Fitur lainnya (Month_encoded, VisitorType_isNew_Visitor, SpecialDay, dan Page_Count) memiliki koefisien 0, menunjukkan bahwa fitur fitur tsb tidak berpengaruh signifikan dalam model ini.
<br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/1beee733-23fb-40db-becd-e8c386b46a0c">
   </p>  
<p align="center">
  Gambar 21 – Feature Importances by the SHAP value (impact on model output) <br>
<br>
  
PageValues memiliki nilai SHAP yang tinggi, berarti fitur ini memiliki pengaruh besar pada prediksi model. Nilai SHAP untuk PageValues cenderung positif yang artinya peningkatan PageValues berdampak pada peningkatan variabel target.
<br>
Fitur lainnya (Month_encoded, VisitorType_isNew_Visitor, SpecialDay, dan Page_Count) memiliki nilai SHAP rendah yang menunjukkan bahwa fitur-fitur tersebut tidak berpengaruh signifikan dalam model ini.

**Business Insight :** <br>
1. Pentingnya Pengalaman Pengguna: <br>
'Page values' yang tinggi menunjukkan bahwa pengunjung yang terlibat secara aktif dengan halaman-halaman situs cenderung lebih mungkin untuk membeli. Ini menekankan pentingnya pengalaman pengguna yang baik dan menarik untuk meningkatkan kemungkinan konversi.<br>
2. Relevansi Konten: <br>
Halaman-halaman dengan 'page values' tinggi mungkin memiliki konten yang lebih relevan dan informatif bagi pengunjung. Konten ini dapat mencakup deskripsi produk yang jelas, testimoni pelanggan, ulasan produk, dan informasi lain yang membantu pengunjung membuat keputusan pembelian. <br>
3. Perilaku Pembelian: <br>
Insight ini menunjukkan bahwa pengunjung yang lebih terlibat dengan konten situs web cenderung lebih cenderung untuk membeli. Ini bisa mencerminkan tahap perjalanan pembelian pengunjung dan faktor-faktor psikologis yang mempengaruhi keputusan pembelian. <br>

**Rekomendasi Bisnis :**
<br>
1. Optimalkan Halaman Produk: <br>
Pastikan deskripsi produk, gambar, dan ulasan pelanggan disajikan dengan baik dan mudah diakses. Gunakan tata letak yang menarik dan intuitif untuk meningkatkan 'page values'. <br>
2. Personalisasi Konten:<br>
Gunakan data pengunjung untuk menyesuaikan rekomendasi produk dan konten yang ditampilkan di halaman. Personalisasi dapat membantu meningkatkan relevansi konten dan minat pengunjung. <br>
3. Uji A/B dan Analisis:<br>
Lakukan uji A/B untuk halaman-halaman kunci dan analisis lanjutan terhadap data 'page values' untuk memahami faktor apa yang paling mempengaruhi konversi. Ini dapat membantu mengidentifikasi perbaikan yang dapat dilakukan dengan cepat. <br>
4. Peningkatan Pengalaman Pengguna: <br>
Fokus pada pengalaman pengguna yang responsif dan intuitif. Pastikan situs web mudah dinavigasi, cepat dimuat, dan menawarkan pengalaman yang menyenangkan bagi pengunjung. <br>
5. Monitoring dan Optimasi Terus-menerus: <br>
Terus pantau metrik 'page values' dan konversi untuk melihat bagaimana perubahan yang diterapkan memengaruhi perilaku pengunjung. Optimalkan strategi berdasarkan temuan dari analisis ini secara berkala.

<br>

---

#### Sumber
Caruana, R. & Niculescu-Mizil, A., 2006. An empirical comparison of supervised learning algorithms. Proceedings of the 23rd International Conference on Machine Learning, pp.161-168. doi: 10.1145/1143844.1143865. <br>
Powers, D. M., 2011. Evaluation: From Precision, Recall and F-Measure to ROC, Informedness, Markedness & Correlation. [online] Available at: https://doi.org/10.48550/arXiv.2010.16061 [Accessed 16 July 2024].
