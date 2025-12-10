# Toyota Corolla Data Analysis using KNIME  
C14230115 Kevin Liem
C14230156 Nicholas Valentino
_Exploratory Data Analysis (EDA), Data Preparation, Outlier Handling, and Visualization_

Proyek ini menganalisis dataset **Toyota Corolla** menggunakan platform **KNIME Analytics Platform**.  
Tujuannya adalah memahami faktor-faktor yang memengaruhi **harga mobil bekas**, melakukan **data preparation**, **data processing**, serta membuat **visualisasi** yang informatif dan dapat digunakan sebagai insight bisnis atau machine learning.

---

## 1. Project Workflow Overview

Workflow terdiri dari tiga tahap utama:

---

### 1. Data Preparation

- **CSV Reader**  
  Mengambil data mentah dari file ToyotaCorolla.csv.

- **Missing Value Handling**  
  Menghapus atau memperbaiki data dengan nilai kosong agar dataset bersih sebelum dianalisis.

- **Numeric Outliers**  
  Menghapus outlier dari kolom numerik penting (`Price` dan `KM`) menggunakan metode **Interquartile Range (IQR)** untuk mencegah bias terhadap visualisasi dan insight.

---

### 2. Data Processing

- **Rule Engine**  
  Menambahkan fitur baru seperti kolom `Transmission` (Automatic/Manual) yang berasal dari kolom `Automatic`.

- **Sorter**  
  Mengurutkan data agar visualisasi tertentu (misalnya Line Plot) lebih mudah dianalisis.

- **Linear Correlation**  
  Menghitung korelasi antar variabel numerik sehingga dapat divisualisasikan dalam bentuk Heatmap.

---

### 3. Data Visualization

Diagram dan grafik berikut digunakan untuk memahami pola dan insight dari dataset Toyota Corolla:

---

##  2. Visualizations & Insights

### 2.1  Box Plot — Range Harga Mobil  
Menampilkan distribusi harga mobil setelah outlier dihapus.

**Insight:**  
- Harga mobil umumnya berada pada rentang **5.000 – 15.000**.  
- Outlier ekstrem berhasil dibersihkan sehingga distribusi lebih stabil.

<img width="841" height="465" alt="Box Plot" src="https://github.com/user-attachments/assets/ebb7fbff-852f-43e4-9fb5-99a5fa22c617" />

---

### 2.2  Scatter Plot — KM Impact on Price  
Memperlihatkan hubungan **kilometer tempuh** terhadap **harga mobil**.

**Insight:**  
- Terdapat korelasi **negatif kuat**: semakin tinggi KM, semakin rendah harga mobil.  
- Jarak tempuh merupakan faktor penentu utama harga mobil bekas.

<img width="841" height="481" alt="Scatter Plot" src="https://github.com/user-attachments/assets/12c77719-c155-47f2-bbf2-5e85ffeea006" />

---

### 2.3  Line Plot — Pengaruh Usia Mobil Terhadap Harga  
Menggambarkan tren penurunan harga berdasarkan usia mobil (`Age_08_04`).

**Insight:**  
- Harga mobil turun secara stabil seiring bertambahnya usia.  
- Depresiasi mobil sangat signifikan pada tahun-tahun awal.

<img width="841" height="409" alt="Line Plot" src="https://github.com/user-attachments/assets/eff1b24b-8af4-488a-86be-706b8b9778f7" />

---

### 2.4  Pie Chart — Distribusi Fuel Type  
Memvisualisasikan proporsi jenis bahan bakar: Diesel, Petrol, dan CNG.

**Insight:**  
- Sebagian besar mobil menggunakan **Petrol**.  
- Mobil Diesel memiliki distribusi lebih kecil namun harga lebih stabil.

<img width="841" height="454" alt="Pie Chart" src="https://github.com/user-attachments/assets/35a0ed04-1e99-41b2-a684-6eee707fab7d" />

---

### 2.5  Box Plot — Pengaruh Transmisi Terhadap Harga  
Menggunakan Rule Engine untuk membuat kategori Automatic/Manual.

**Insight:**  
- Mobil **Automatic** cenderung memiliki harga lebih tinggi dibanding Manual.  
- Variasi harga mobil automatic juga lebih besar.

<img width="841" height="527" alt="Box PlotTransmisi" src="https://github.com/user-attachments/assets/e4a5a4bb-1356-460a-b5e7-cb2e9dc723ff" />

---

### 2.6  Heatmap — Korelasi Antar Variabel  
Menggunakan node Linear Correlation → Heatmap.

**Insight utama:**  
- **Age → korelasi negatif sangat kuat** dengan harga.  
- **KM → korelasi negatif** (lebih banyak dipakai → lebih murah).  
- **Weight & HP → korelasi positif** (mobil lebih besar dan bertenaga lebih mahal).  
- **Mfg_Year & Age** menunjukkan korelasi hampir -1 → fitur redundant.  
- **HP & CC** memiliki korelasi +0.9 → keduanya mewakili karakteristik mesin yang sama (redundancy).

<img width="841" height="445" alt="Heatmap" src="https://github.com/user-attachments/assets/f409e236-68c6-415e-8f36-35caf5bbd264" />

---


##  3. Key Insights Summary

- Harga mobil paling dipengaruhi oleh **Age**, **KM**, **Weight**, dan **HP**.  
- Mobil Automatic lebih mahal daripada Manual.  
- Tipe bahan bakar (Fuel_Type) berpengaruh pada persebaran harga.  
- Beberapa fitur memiliki korelasi sangat kuat dan tidak dianjurkan dipakai bersama dalam model ML (multicollinearity).  
