# Analisis Employee Attrition - Jaya Jaya Maju

## 📌 Deskripsi Proyek

Proyek ini merupakan proyek analisis data untuk mengidentifikasi faktor-faktor yang berkaitan dengan tingginya tingkat employee attrition pada perusahaan Jaya Jaya Maju.

Jaya Jaya Maju merupakan perusahaan yang memiliki lebih dari 1.000 karyawan. Berdasarkan permasalahan yang diberikan, perusahaan memiliki tingkat attrition yang cukup tinggi sehingga diperlukan analisis untuk membantu departemen Human Resources (HR) memahami faktor-faktor yang berkaitan dengan karyawan yang meninggalkan perusahaan.

Analisis dilakukan menggunakan Python untuk proses data preparation dan exploratory data analysis (EDA), PostgreSQL sebagai database, serta Metabase sebagai business intelligence tool untuk membangun dashboard interaktif.

---

## 🎯 Business Understanding

### Permasalahan

Departemen Human Resources (HR) Jaya Jaya Maju mengalami permasalahan terkait tingginya tingkat employee attrition.

HR membutuhkan informasi yang dapat membantu menjawab pertanyaan berikut:

1. Berapa jumlah karyawan dan berapa banyak karyawan yang meninggalkan perusahaan?
2. Berapa tingkat attrition perusahaan?
3. Departemen mana yang memiliki tingkat attrition paling tinggi?
4. Apakah overtime berkaitan dengan tingkat attrition?
5. Apakah tingkat kepuasan kerja berkaitan dengan attrition?
6. Apakah terdapat job role tertentu yang memiliki tingkat attrition tinggi?
7. Apakah masa kerja karyawan berkaitan dengan tingkat attrition?

### Tujuan

Tujuan dari proyek ini adalah:

- Mengidentifikasi tingkat employee attrition.
- Menganalisis faktor-faktor yang berkaitan dengan employee attrition.
- Menyajikan hasil analisis dalam bentuk dashboard yang mudah dipahami.
- Memberikan insight yang dapat membantu HR dalam menentukan strategi untuk mengurangi tingkat attrition.

---

## 📊 Dataset

Dataset yang digunakan merupakan data employee attrition yang berisi informasi mengenai karakteristik karyawan, pekerjaan, kepuasan kerja, kompensasi, dan status attrition.

Data yang digunakan dalam analisis akhir terdiri dari:

- **1.058 karyawan**
- **35 kolom**

Beberapa variabel yang digunakan dalam analisis antara lain:

| Variabel | Deskripsi |
|---|---|
| EmployeeId | ID karyawan |
| Age | Usia karyawan |
| Attrition | Status karyawan meninggalkan perusahaan atau tidak |
| BusinessTravel | Frekuensi perjalanan bisnis |
| Department | Departemen karyawan |
| DistanceFromHome | Jarak rumah ke tempat kerja |
| JobRole | Jabatan/peran pekerjaan |
| JobSatisfaction | Tingkat kepuasan kerja |
| MonthlyIncome | Pendapatan bulanan |
| OverTime | Status lembur |
| TotalWorkingYears | Total pengalaman kerja |
| YearsAtCompany | Lama bekerja di perusahaan |
| YearsInCurrentRole | Lama berada pada posisi saat ini |
| YearsSinceLastPromotion | Lama sejak promosi terakhir |
| YearsWithCurrManager | Lama bekerja dengan manajer saat ini |

---

## 🔎 Data Preparation

Dataset awal terdiri dari 1.470 baris dan 35 kolom.

Pada tahap awal dilakukan pemeriksaan terhadap struktur data, missing values, dan data duplikat. Hasil pemeriksaan menunjukkan bahwa dataset tidak memiliki data duplikat, namun terdapat missing values pada kolom `Attrition` sebanyak 412 baris.

Karena `Attrition` merupakan variabel utama yang digunakan untuk menentukan apakah seorang karyawan meninggalkan perusahaan atau tidak, baris dengan nilai `Attrition` yang kosong tidak dapat digunakan dalam analisis attrition.

Oleh karena itu, dilakukan penghapusan baris yang memiliki nilai kosong pada kolom `Attrition`.

### Kondisi Data

| Kondisi | Jumlah |
|---|---:|
| Data awal | 1.470 baris |
| Jumlah kolom | 35 |
| Missing value pada `Attrition` | 412 |
| Data duplikat | 0 |
| Data setelah cleaning | 1.058 baris |

Setelah proses cleaning, diperoleh 1.058 data karyawan yang digunakan untuk tahap Exploratory Data Analysis (EDA) dan pembuatan dashboard.

Selain penanganan missing values, beberapa variabel kategorikal juga disesuaikan agar lebih mudah dipahami pada tahap analisis dan visualisasi.

---

## 📈 Exploratory Data Analysis

Exploratory Data Analysis (EDA) dilakukan untuk memahami karakteristik data dan menemukan pola yang berkaitan dengan employee attrition.

Beberapa analisis yang dilakukan meliputi:

### 1. Attrition Rate

Menghitung jumlah karyawan yang meninggalkan perusahaan dan tingkat attrition secara keseluruhan.

### 2. Attrition berdasarkan Department

Menganalisis perbedaan tingkat attrition antar departemen.

### 3. Attrition berdasarkan Overtime

Menganalisis hubungan antara status lembur dengan tingkat attrition.

### 4. Attrition berdasarkan Job Satisfaction

Menganalisis tingkat attrition berdasarkan tingkat kepuasan kerja.

### 5. Attrition berdasarkan Job Role

Mengidentifikasi job role yang memiliki tingkat attrition relatif tinggi.

### 6. Attrition berdasarkan Tenure

Menganalisis tingkat attrition berdasarkan kelompok masa kerja:

- 0–2 Years
- 3–5 Years
- 6–10 Years
- >10 Years

---

## 🗄️ Database

Dataset hasil cleaning disimpan pada database PostgreSQL.

Database digunakan sebagai sumber data untuk dashboard Metabase.

Alur pengolahan data:

```text
Dataset
   ↓
Python / Pandas
   ↓
Data Cleaning & EDA
   ↓
PostgreSQL
   ↓
Metabase
   ↓
Business Dashboard
```

---
## Conclusion

Berdasarkan hasil analisis terhadap 1.058 data karyawan yang telah melalui proses data cleaning, terdapat 179 karyawan yang tercatat meninggalkan perusahaan dengan tingkat employee attrition sebesar **16,92%**.

Hasil exploratory data analysis menunjukkan beberapa pola yang perlu menjadi perhatian departemen Human Resources (HR):

1. **Department Sales** memiliki tingkat attrition paling tinggi, yaitu **20,69%**.
2. Karyawan yang melakukan **overtime** memiliki tingkat attrition sebesar **31,92%**, sedangkan karyawan yang tidak melakukan overtime memiliki tingkat attrition sebesar **10,79%**.
3. Karyawan dengan tingkat **job satisfaction Low** memiliki tingkat attrition sebesar **22,44%**, sedangkan kelompok Very High memiliki tingkat attrition sebesar **11,47%**.
4. **Sales Representative** memiliki tingkat attrition paling tinggi dibandingkan job role lainnya, yaitu **43,10%**.
5. Karyawan dengan masa kerja **0–2 tahun** memiliki tingkat attrition paling tinggi, yaitu **29,96%**. Tingkat attrition kemudian cenderung lebih rendah pada kelompok masa kerja yang lebih panjang.

Secara keseluruhan, hasil analisis menunjukkan bahwa **overtime, job satisfaction, job role, department, dan masa kerja memiliki perbedaan tingkat attrition antar kelompok karyawan**. Faktor-faktor tersebut dapat digunakan sebagai indikator yang perlu diperhatikan HR dalam melakukan monitoring employee attrition.

Perlu diperhatikan bahwa analisis ini menunjukkan **pola dan keterkaitan pada data**, sehingga hasilnya tidak dapat digunakan untuk menyimpulkan hubungan sebab-akibat secara langsung.

### Rekomendasi Action Items

Berdasarkan hasil analisis, beberapa rekomendasi yang dapat dipertimbangkan oleh departemen Human Resources (HR) adalah:

1. **Melakukan evaluasi terhadap karyawan yang sering melakukan overtime**
   
   Tingkat attrition pada karyawan yang melakukan overtime mencapai 31,92%, lebih tinggi dibandingkan karyawan yang tidak melakukan overtime. HR dapat melakukan monitoring terhadap beban kerja, frekuensi overtime, dan keseimbangan beban pekerjaan untuk mengidentifikasi potensi masalah lebih awal.

2. **Meningkatkan employee satisfaction dan engagement**
   
   Kelompok karyawan dengan job satisfaction Low memiliki tingkat attrition yang lebih tinggi. HR dapat melakukan employee survey atau feedback secara berkala untuk mengetahui aspek pekerjaan yang perlu diperbaiki, seperti lingkungan kerja, beban kerja, hubungan dengan atasan, maupun kesempatan pengembangan.

3. **Memberikan perhatian khusus kepada karyawan baru**
   
   Karyawan dengan masa kerja 0–2 tahun memiliki tingkat attrition paling tinggi, yaitu 29,96%. HR dapat memperkuat program onboarding, mentoring, dan evaluasi pada masa awal bekerja agar karyawan lebih mudah beradaptasi dengan lingkungan perusahaan.

4. **Melakukan evaluasi pada job role dengan attrition tinggi**
   
   Sales Representative memiliki tingkat attrition sebesar 43,10%. HR dapat melakukan evaluasi lebih lanjut terhadap karakteristik pekerjaan, beban kerja, target, kompensasi, serta kesempatan pengembangan karier pada job role dengan tingkat attrition tinggi.

5. **Memberikan perhatian lebih pada department dengan attrition tinggi**
   
   Department Sales memiliki tingkat attrition paling tinggi, yaitu 20,69%. HR dapat melakukan analisis lebih lanjut pada department tersebut untuk memahami karakteristik karyawan yang memiliki risiko attrition lebih tinggi dan menentukan intervensi yang sesuai.

6. **Menggunakan dashboard sebagai alat monitoring HR**
   
   Dashboard employee attrition dapat digunakan secara berkala untuk memonitor perubahan tingkat attrition berdasarkan department, overtime, job satisfaction, job role, dan masa kerja. Monitoring secara berkala dapat membantu HR mengidentifikasi perubahan pola attrition dan menentukan prioritas tindak lanjut.
