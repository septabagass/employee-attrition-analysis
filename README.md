# Proyek Akhir: Menyelesaikan Permasalahan Human Resources

## Business Understanding

Jaya Jaya Maju merupakan perusahaan yang memiliki lebih dari 1.000 karyawan. Perusahaan menghadapi permasalahan employee attrition yang cukup tinggi. Tingginya jumlah karyawan yang meninggalkan perusahaan dapat meningkatkan biaya rekrutmen dan pelatihan, mengganggu produktivitas, serta menyebabkan hilangnya pengalaman dan pengetahuan yang dimiliki karyawan.

Proyek ini dilakukan untuk membantu departemen Human Resources (HR) memahami karakteristik karyawan yang melakukan attrition serta faktor-faktor yang berkaitan dengan employee attrition. Hasil analisis kemudian disajikan dalam business dashboard menggunakan Metabase sehingga dapat digunakan sebagai alat monitoring dan pendukung pengambilan keputusan berbasis data.

Analisis dilakukan menggunakan Python dan Pandas untuk data preparation serta Exploratory Data Analysis (EDA), PostgreSQL sebagai database hasil pengolahan data, dan Metabase sebagai business intelligence tool untuk membangun dashboard.

### Permasalahan Bisnis

1. Berapa jumlah karyawan yang keluar dan berapa tingkat employee attrition perusahaan?
2. Departemen mana yang memiliki tingkat attrition paling tinggi?
3. Apakah status overtime berkaitan dengan tingkat attrition?
4. Apakah tingkat job satisfaction berkaitan dengan attrition?
5. Apakah terdapat job role tertentu yang memiliki tingkat attrition tinggi?
6. Apakah masa kerja karyawan berkaitan dengan tingkat attrition?

### Cakupan Proyek

Cakupan proyek meliputi:

- Memahami struktur dan karakteristik dataset employee attrition.
- Melakukan pemeriksaan kualitas data, termasuk missing value dan data duplikat.
- Melakukan data cleaning dengan menghapus baris yang tidak memiliki nilai pada kolom `Attrition`.
- Melakukan perubahan tipe data pada `EmployeeId`.
- Melakukan labeling pada beberapa variabel kategorikal agar hasil analisis lebih mudah dipahami.
- Melakukan Exploratory Data Analysis (EDA) untuk menganalisis employee attrition berdasarkan:
  - Attrition secara keseluruhan.
  - Department.
  - OverTime.
  - Job Satisfaction.
  - YearsAtCompany.
  - MonthlyIncome.
  - Age.
  - Work-Life Balance.
  - Korelasi variabel numerik.
- Menyimpan hasil data cleaning sebagai `employee_data_clean.csv`.
- Menyimpan data hasil pengolahan pada PostgreSQL sebagai sumber data dashboard.
- Membuat business dashboard menggunakan Metabase.
- Menyusun insight dan rekomendasi action items untuk membantu HR mengurangi employee attrition.

### Persiapan

Sumber data: [employee_data.csv](https://github.com/dicodingacademy/dicoding_dataset/tree/main/employee)

Dataset yang digunakan merupakan Employee Data yang disediakan oleh Dicoding. Dataset ini berisi data demografis, informasi pekerjaan, serta atribut Attrition yang menunjukkan apakah seorang karyawan mengalami attrition atau tidak. Dataset terdiri dari 1.470 data karyawan dengan 35 atribut.

Setup environment:

**Versi Python:** Python 3.11.x

1. Clone atau download repository proyek, kemudian masuk ke folder proyek.

2. Buat virtual environment:

```bash
python -m venv venv
```

3. Aktifkan virtual environment.

Windows:

```bash
venv\Scripts\activate
```

macOS/Linux:

```bash
source venv/bin/activate
```

4. Install seluruh dependency dari `requirements.txt`:

```bash
pip install -r requirements.txt
```

5. Siapkan dataset:

```text
proyek-hr-jaya-jaya-maju/
├── employee_data.csv
├── notebook.ipynb
├── requirements.txt
├── README.md
├── metabase.db.mv.db
└── septabagass_dicoding-dashboard.png
```

6. Buka dan jalankan `notebook.ipynb` secara berurutan dari bagian **Persiapan**, **Data Understanding**, **Data Preparation / Preprocessing**, **Exploratory Data Analysis (EDA)**, hingga **Conclusion**.

Jika menjalankan notebook secara lokal, ubah kode pembacaan dataset dari path Google Colab:

```python
df = pd.read_csv('/content/employee_data.csv')
```

menjadi:

```python
df = pd.read_csv('employee_data.csv')
```

7. Setelah seluruh proses notebook selesai, file `employee_data_clean.csv` akan dihasilkan sebagai data hasil cleaning.

8. Data hasil cleaning kemudian digunakan sebagai sumber data untuk PostgreSQL dan dashboard Metabase.

## Business Dashboard

Business dashboard dibuat menggunakan **Metabase v0.46.4**. Dashboard digunakan untuk memantau employee attrition berdasarkan beberapa dimensi, seperti department, overtime, job satisfaction, job role, dan masa kerja.

Screenshot dashboard tersedia pada file:

`septabagass_dicoding-dashboard.png`

### Menjalankan Metabase dengan Docker

Pastikan Docker Desktop sudah terpasang dan sedang berjalan.

1. Pastikan file berikut berada pada folder proyek:

```text
metabase.db.mv.db
```

2. Download image Metabase versi yang digunakan:

```bash
docker pull metabase/metabase:v0.46.4
```

3. Jalankan container Metabase:

```bash
docker run -d -p 3000:3000 --name metabase metabase/metabase:v0.46.4
```

4. Tunggu beberapa saat sampai container selesai melakukan proses startup. Periksa status dengan:

```bash
docker logs -f metabase
```

Tekan `Ctrl + C` untuk keluar dari tampilan log tanpa menghentikan container.

5. Hentikan container sebelum mengganti database aplikasi Metabase:

```bash
docker stop metabase
```

6. Salin file `metabase.db.mv.db` dari folder proyek ke lokasi database Metabase di dalam container:

```bash
docker cp metabase.db.mv.db metabase:/metabase.db/metabase.db.mv.db
```

Lokasi `/metabase.db/metabase.db.mv.db` merupakan lokasi default application database H2 pada container Metabase. Setelah database diganti, jalankan kembali container:

```bash
docker start metabase
```

7. Periksa apakah Metabase sudah berjalan:

```bash
docker ps
```

Kemudian buka:

[http://localhost:3000](http://localhost:3000)

### Kredensial Metabase

Database Metabase yang disertakan dalam submission telah memiliki akun yang digunakan saat dashboard dibuat.

- **Email:** `septabagass@gmail.com`
- **Password:** **sety4metabase**

Jika container sebelumnya sudah pernah dibuat dengan nama `metabase`, gunakan:

```bash
docker rm -f metabase
```

kemudian ulangi proses pembuatan container dari langkah nomor 2 agar database H2 yang dilampirkan dapat digunakan sejak awal.

### Alur Dashboard

Alur data yang digunakan dalam proyek:

```text
employee_data.csv
       ↓
Python / Pandas
       ↓
Data Cleaning & Labeling
       ↓
Exploratory Data Analysis (EDA)
       ↓
employee_data_clean.csv
       ↓
PostgreSQL
       ↓
Metabase
       ↓
Business Dashboard
```

Dashboard digunakan untuk membantu HR memonitor:

- Total karyawan.
- Jumlah karyawan yang melakukan attrition.
- Attrition rate.
- Attrition berdasarkan department.
- Attrition berdasarkan job role.
- Attrition berdasarkan overtime.
- Attrition berdasarkan job satisfaction.
- Attrition berdasarkan kelompok masa kerja.

## Conclusion

Berdasarkan hasil analisis terhadap 1.058 data karyawan yang memiliki label `Attrition`, terdapat 179 karyawan yang melakukan attrition dan 879 karyawan yang masih bertahan. Dengan demikian, tingkat attrition keseluruhan adalah sekitar **16,92%**.

Beberapa pola penting yang ditemukan dari hasil Exploratory Data Analysis adalah:

1. **OverTime**

   Karyawan yang melakukan overtime memiliki tingkat attrition sebesar **31,92%**, sedangkan karyawan yang tidak melakukan overtime memiliki tingkat attrition sebesar **10,79%**. Perbedaan ini menunjukkan bahwa overtime merupakan salah satu karakteristik yang perlu menjadi perhatian HR.

2. **Department**

   Department **Sales** memiliki tingkat attrition paling tinggi, yaitu **20,69%**, dibandingkan department lainnya.

3. **Job Role**

   **Sales Representative** memiliki tingkat attrition paling tinggi, yaitu **43,10%**. Kondisi ini perlu dianalisis lebih lanjut dari sisi beban kerja, target, kompensasi, dan peluang pengembangan karier.

4. **Job Satisfaction**

   Karyawan dengan tingkat job satisfaction **Low** memiliki tingkat attrition sebesar **22,44%**, sedangkan kelompok **Very High** memiliki tingkat attrition sebesar **11,47%**. Hal ini menunjukkan bahwa kepuasan kerja perlu menjadi salah satu aspek yang dimonitor oleh HR.

5. **Masa Kerja**

   Kelompok karyawan dengan masa kerja **0–2 tahun** memiliki tingkat attrition paling tinggi, yaitu **29,96%**. Hal ini menunjukkan bahwa periode awal masa kerja merupakan periode penting dalam strategi retensi karyawan.

Secara keseluruhan, hasil analisis menunjukkan bahwa employee attrition di Jaya Jaya Maju berkaitan dengan beberapa aspek pekerjaan, terutama overtime, kepuasan kerja, department, job role, dan masa kerja. Dashboard Metabase dapat digunakan sebagai alat monitoring untuk membantu HR melihat perubahan pola attrition dan menentukan area yang perlu mendapatkan perhatian lebih lanjut.

### Rekomendasi Action Items

1. **Melakukan monitoring overtime**

   HR perlu memonitor karyawan yang sering melakukan overtime dan mengevaluasi beban kerja, distribusi pekerjaan, serta keseimbangan antara pekerjaan dan kehidupan pribadi.

2. **Memperkuat program onboarding dan retensi karyawan baru**

   Karena kelompok masa kerja 0–2 tahun memiliki tingkat attrition paling tinggi, perusahaan dapat memperkuat onboarding, mentoring, evaluasi masa awal kerja, dan komunikasi antara karyawan dengan atasan.

3. **Meningkatkan employee satisfaction**

   HR dapat melakukan employee survey secara berkala untuk mengetahui faktor yang menyebabkan rendahnya job satisfaction serta menyusun program perbaikan berdasarkan hasil survey.

4. **Melakukan evaluasi terhadap job role dengan attrition tinggi**

   Sales Representative perlu mendapatkan perhatian khusus dengan mengevaluasi target kerja, beban kerja, kompensasi, lingkungan kerja, dan peluang pengembangan karier.

5. **Melakukan evaluasi pada department dengan attrition tinggi**

   Department Sales dapat dianalisis lebih lanjut untuk mengetahui faktor internal yang menyebabkan tingkat attrition lebih tinggi dibandingkan department lain.

6. **Menggunakan dashboard sebagai alat monitoring rutin**

   Dashboard Metabase dapat digunakan secara berkala untuk memantau attrition rate berdasarkan department, job role, overtime, job satisfaction, dan tenure sehingga HR dapat lebih cepat mengidentifikasi perubahan pola dan menentukan prioritas tindakan.
