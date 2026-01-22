# 📊 Prediksi Risiko Stres Mahasiswa

Aplikasi web berbasis **Streamlit** yang menggunakan algoritma **Random Forest** untuk memprediksi risiko stres pada mahasiswa berdasarkan berbagai faktor akademik, sosial, dan gaya hidup.

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Streamlit](https://img.shields.io/badge/Streamlit-1.28+-red.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)

## 📋 Daftar Isi

- [Fitur Utama](#-fitur-utama)
- [Teknologi yang Digunakan](#-teknologi-yang-digunakan)
- [Struktur Proyek](#-struktur-proyek)
- [Instalasi](#-instalasi)
- [Cara Penggunaan](#-cara-penggunaan)
- [Model Machine Learning](#-model-machine-learning)
- [Fitur-Fitur Aplikasi](#-fitur-fitur-aplikasi)
- [Disclaimer](#-disclaimer)
- [Lisensi](#-lisensi)

## ✨ Fitur Utama

- 🎯 **Prediksi Risiko Stres** - Prediksi akurat menggunakan Random Forest Classifier
- 📊 **Analisis Data Interaktif** - Visualisasi data dengan Plotly
- 🔍 **Model Performance** - Dashboard performa model dengan confusion matrix dan feature importance
- 💡 **Rekomendasi Personal** - Saran kesehatan yang disesuaikan dengan profil mahasiswa
- 📥 **Download Hasil** - Kartu hasil prediksi dalam format PNG
- 🔄 **Batch Prediction** - Prediksi hingga 5 data sekaligus

## 🛠 Teknologi yang Digunakan

| Teknologi | Versi | Kegunaan |
|-----------|-------|----------|
| **Python** | ≥3.8 | Bahasa pemrograman utama |
| **Streamlit** | ≥1.28.0 | Framework web interaktif |
| **Pandas** | ≥1.5.0 | Manipulasi dan analisis data |
| **NumPy** | ≥1.23.0 | Komputasi numerik |
| **Scikit-learn** | ≥1.2.0 | Machine learning algorithms |
| **Plotly** | ≥5.15.0 | Visualisasi data interaktif |
| **Pillow** | ≥10.0.0 | Generate gambar hasil prediksi |

## 📁 Struktur Proyek
```
random-forest-resiko-stress-mahasiswa/
│
├── requirements.txt                # Dependencies Python
├── README.md                       # Dokumentasi proyek
├── save_model.py                   # Script untuk menyimpan model
│
├── app/
│   ├── app.py                      # Entry point aplikasi Streamlit
│   ├── pages/                      # Halaman-halaman aplikasi
│   │   ├── analysis.py             # Halaman analisis data
│   │   ├── home.py                 # Halaman beranda
│   │   ├── model_performance.py    # Halaman performa model
│   │   └── prediction.py           # Halaman prediksi
│   └── styles/
│       └── custom_styles.py        # Custom CSS styling
│
├── data/
│   └── raw/
│       └── dataset.csv             # Dataset mahasiswa (separator: ';')
│
├── models/
│   ├── best_model.pkl              # Model terlatih (auto-generated)
│   └── preprocessing_stats.pkl     # Statistik preprocessing (auto-generated)
│
├── src/
│   ├── data_preprocessing.py       # Fungsi preprocessing data
│   ├── model_training.py           # Training model Random Forest
│   └── utils.py                    # Utility functions
│
├── notebooks/
│   ├── 01_EDA.ipynb                # Exploratory Data Analysis
│   └── 02_modeling.ipynb           # Model development
│
└── reports/
    ├── LaporanAkhirDataMining...   # Laporan akhir project
    └── SlideProjectAkhirDataMini...# Slide presentasi
```

## 🚀 Instalasi

### 1. Clone Repository
```bash
git clone <repository-url>
cd random-forest-resiko-stress-mahasiswa
```

### 2. Buat Virtual Environment (Opsional tapi Direkomendasikan)
```bash
# Windows
python -m venv venv
venv\Scripts\activate

# Linux/Mac
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

### 4. Persiapkan Dataset

Pastikan file `dataset.csv` berada di folder `data/raw/` dengan format:

- **Separator**: `;` (titik koma)
- **Kolom yang diperlukan**:
  - Gender
  - Umur
  - Jurusan/Program Studi
  - Jam Belajar per Hari
  - Jam Tidur per Hari
  - IPK
  - Jumlah Tugas Besar per Minggu
  - Frekuensi Olahraga
  - Pemasukan Keluarga
  - Status Hubungan
  - Label (Sehat / Risiko Stres)

### 5. Jalankan Aplikasi
```bash
cd app
streamlit run app.py
```

Aplikasi akan terbuka di browser pada `http://localhost:8501`

## 📖 Cara Penggunaan

### 1️⃣ Halaman Beranda

- Lihat ringkasan dataset
- Metrik akurasi model
- Distribusi label dan gender
- Preview data

### 2️⃣ Halaman Prediksi

1. Pilih jumlah data yang ingin diprediksi (1-5)
2. Isi form untuk setiap mahasiswa:
   - **Data Pribadi**: Nama, Gender, Umur, Jurusan, Status Hubungan
   - **Data Akademik**: IPK, Jam Belajar, Jumlah Tugas
   - **Data Kesehatan**: Jam Tidur, Frekuensi Olahraga
   - **Data Ekonomi**: Pemasukan Keluarga
3. Klik **"🔮 Prediksi Sekarang"**
4. Lihat hasil prediksi dan rekomendasi personal
5. Download kartu hasil dalam format PNG

### 3️⃣ Halaman Analisis Data

- **Tab Distribusi**: Box plot dan histogram fitur numerik
- **Tab Korelasi**: Analisis kategorikal dengan grouped bar chart
- **Tab Statistik**: Statistik deskriptif dengan filter

### 4️⃣ Halaman Performa Model

- Gauge chart akurasi
- Confusion matrix
- Feature importance (Top 10 fitur)
- Parameter model

## 🤖 Model Machine Learning

### Algoritma: Random Forest Classifier

**Parameter Model:**
```python
RandomForestClassifier(
    n_estimators=200,      # Jumlah decision trees
    max_depth=4,           # Kedalaman maksimum tree
    random_state=42,       # Reproducibility
    n_jobs=-1              # Parallel processing
)
```

### Pipeline Preprocessing

1. **Numeric Features** (Z-score normalization):
   - Umur
   - Jam Belajar per Hari
   - Jam Tidur per Hari
   - IPK
   - Jumlah Tugas Besar per Minggu

2. **Categorical Features** (One-Hot Encoding):
   - Gender
   - Jurusan/Program Studi
   - Frekuensi Olahraga
   - Pemasukan Keluarga
   - Status Hubungan

### Metrik Evaluasi

- **Accuracy**: Persentase prediksi yang benar
- **F1-Score (Weighted)**: Harmonic mean dari precision dan recall
- **Confusion Matrix**: Visualisasi true positive, false positive, dll

### Model Persistence

Model dan statistik preprocessing disimpan otomatis di folder `models/`:

- `best_model.pkl` - Model terlatih
- `preprocessing_stats.pkl` - Mean dan std untuk normalisasi

## 🎨 Fitur-Fitur Aplikasi

### 1. Rekomendasi Personal

Aplikasi memberikan saran spesifik berdasarkan input pengguna:

- ⏰ **Pola Tidur**: Rekomendasi jam tidur optimal (7-9 jam)
- 📚 **Waktu Belajar**: Saran durasi belajar efektif
- 🏃 **Aktivitas Fisik**: Anjuran frekuensi olahraga
- 📈 **Performa Akademik**: Tips berdasarkan IPK
- 📝 **Manajemen Tugas**: Strategi mengelola beban tugas

### 2. Generate Certificate

Fitur download kartu hasil dengan:

- Header dengan branding
- Nama mahasiswa
- Hasil prediksi (warna-kode)
- Probabilitas
- Ringkasan data input
- Timestamp otomatis

### 3. Reset Form

Tombol reset untuk mengulang prediksi dengan data baru tanpa reload halaman.

### 4. Batch Processing

Prediksi hingga 5 mahasiswa sekaligus dengan hasil individual untuk masing-masing.

## 📓 Notebooks

Project ini dilengkapi dengan Jupyter Notebooks untuk eksplorasi dan development:

- **01_EDA.ipynb**: Exploratory Data Analysis
  - Analisis distribusi data
  - Visualisasi korelasi fitur
  - Identifikasi outliers
  
- **02_modeling.ipynb**: Model Development
  - Preprocessing pipeline
  - Model training & tuning
  - Evaluasi performa model

## 📊 Reports

Dokumentasi lengkap project tersedia di folder `reports/`:

- Laporan akhir project (PDF)
- Slide presentasi project

## ⚠️ Disclaimer

**PENTING**: 

- Aplikasi ini diperuntukkan untuk **Mahasiswa S1** dengan rentang umur **maksimal 25 tahun**
- Hasil prediksi **BUKAN diagnosis medis**
- Hasil hanya sebagai **referensi awal** untuk awareness kesehatan mental
- Jika mengalami gejala stres berat, **segera konsultasi dengan profesional** (psikolog/konselor)

## 📄 Lisensi

Distributed under the MIT License. See `LICENSE` for more information.

## 👨‍💻 Pengembang

Dibuat dengan ❤️ menggunakan Python dan Streamlit

---

**Catatan**: Pastikan untuk mengupdate dataset secara berkala untuk meningkatkan akurasi model!