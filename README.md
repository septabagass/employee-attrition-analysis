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

Tahapan data preparation dilakukan untuk memastikan data dapat digunakan untuk proses analisis.

Tahapan yang dilakukan meliputi:

1. Memeriksa struktur dan ukuran dataset.
2. Memeriksa tipe data setiap kolom.
3. Memeriksa missing values.
4. Memeriksa data duplikat.
5. Menangani missing values pada kolom `Attrition`.
6. Mengubah beberapa variabel kategorikal menjadi label yang lebih mudah dipahami.
7. Menyiapkan dataset hasil cleaning untuk disimpan ke database.

Data dengan nilai `Attrition` yang kosong tidak digunakan dalam analisis karena variabel tersebut merupakan target utama yang digunakan untuk menghitung tingkat attrition.

Setelah proses cleaning, diperoleh **1.058 data karyawan** yang digunakan dalam analisis.

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
