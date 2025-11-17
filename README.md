# 📌 Cataract Classification Using SVM with HOG + LBP Feature Extraction

Repository ini berisi proyek machine learning untuk **klasifikasi katarak berdasarkan citra retina (fundus)** menggunakan algoritma **Support Vector Machine (SVM)**.  

Model memanfaatkan kombinasi fitur **HOG (Histogram of Oriented Gradients)**, **LBP (Local Binary Pattern)**, serta **fitur warna RGB**, kemudian direduksi menggunakan **PCA** agar lebih efisien dan mengurangi overfitting.

---

## 📂 Dataset

Dataset dapat diunduh melalui link berikut:

🔗 **Google Drive – ODIR-5K Dataset**  
https://drive.google.com/drive/folders/1XiYvd60C28ScQUQ5ImLUEp4iERVZCrez

### Struktur Dataset
ODIR-5K/
│
├── Training Images/             # Citra retina untuk proses training
│     ├── xxx_left.jpg
│     ├── xxx_right.jpg
│     └── ...
│
├── Testing Images/              # Citra retina untuk proses testing
│     ├── yyy_left.jpg
│     ├── yyy_right.jpg
│     └── ...
│
├── dataset_labeled/             # Versi dataset yang sudah dipisah berdasarkan label
│     ├── cataract/
│     ├── normal/
│     └── ...
│
├── test_predictions_final.csv   # File prediksi baseline dari dataset ODIR
│
└── data.xlsx                    # Informasi pasien dan label kondisi mata

### Kelas Label
- `0` — Normal  
- `1` — Cataract  

Total data yang digunakan: **3.411 citra retina**.

---

## 🔧 Preprocessing

Tahapan preprocessing mencakup:

- Resize gambar menjadi **128×128**
- Konversi ke RGB
- Normalisasi piksel (0–1)
- Augmentasi data:
  - Rotasi ±15°
  - Zoom ±10%
  - Horizontal flip
  - Translasi kecil
- Ekstraksi fitur:
  - **HOG**
  - **LBP**
  - **RGB Mean & Std**
- Standarisasi fitur menggunakan **StandardScaler**
- Reduksi dimensi dengan **PCA → 100 komponen**

---

## 🧠 Model

Model utama yang digunakan adalah **Support Vector Machine (SVM)** dengan alasan:

- Bekerja baik pada dataset kecil–menengah  
- Efektif pada data berdimensi tinggi  
- Menghasilkan hyperplane pemisah yang optimal  

**Pembagian data:**  
- 80% → Train  
- 20% → Test  

---

## 📈 Evaluasi Model

Akurasi model: **95%**

### Classification Report

| Kelas     | Precision | Recall | F1-Score |
|-----------|-----------|--------|----------|
| Normal    | 0.97      | 0.97   | 0.97     |
| Cataract  | 0.92      | 0.92   | 0.92     |

Model mampu mengenali katarak secara stabil meskipun citra memiliki variasi pencahayaan dan noise.

---

## 📊 Perbandingan dengan Model Lain

| Model                               | Akurasi    | Catatan                                |
| ----------------------------------- | ---------- | -------------------------------------- |
| **SVM + HOG + LBP (Model Ini)**     | **95.52%** | Stabil, ringan, mudah diterapkan       |
| **CNN (Scratch)**                   | **96.09%** | Performa tertinggi                     |
| **MobileNetV2 (Transfer Learning)** | 71.26%     | Kurang optimal pada dataset fundus ini |

---

## 🎯 Kesimpulan

Model SVM dengan fitur HOG, LBP, dan RGB memberikan performa tinggi dalam klasifikasi katarak pada citra retina.  
Model ini **ringan, cepat**, dan dapat digunakan sebagai **alat skrining awal** untuk mendukung analisis medis otomatis.

---

## 🚀 Teknologi yang Digunakan

- Python  
- OpenCV  
- Scikit-learn  
- NumPy & Pandas  
- Matplotlib  
- PCA  

---

