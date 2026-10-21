# MarsTexture AI — Klasifikasi Tekstur Permukaan Mars

Proyek Ujian Tengah Semester (UTS) mata kuliah **Machine Learning** yang berfokus pada klasifikasi citra tekstur permukaan Mars menggunakan ekstraksi fitur berbasis *handcrafted features* dengan PyFeats dan pemodelan klasifikasi otomatis menggunakan PyCaret.

## Deskripsi Proyek

MarsTexture AI merupakan proyek klasifikasi citra yang bertujuan untuk mempelajari karakteristik tekstur permukaan planet Mars melalui pengolahan citra digital dan algoritma Machine Learning.

Proyek ini menggunakan fitur numerik yang diekstraksi dari citra untuk membangun model klasifikasi. PyFeats digunakan untuk memperoleh karakteristik tekstur citra, sedangkan PyCaret digunakan untuk membandingkan beberapa algoritma klasifikasi, memilih model potensial, melakukan *hyperparameter tuning*, dan mengevaluasi performanya.

Proyek ini disusun sebagai pemenuhan tugas UTS mata kuliah Machine Learning.

## Tujuan

1. Melakukan pra-pemrosesan citra untuk mempersiapkan data sebelum ekstraksi fitur.
2. Mengekstraksi fitur tekstur citra menggunakan PyFeats.
3. Membentuk dataset numerik yang dapat digunakan untuk pemodelan Machine Learning.
4. Membandingkan performa beberapa algoritma klasifikasi menggunakan PyCaret.
5. Melakukan *hyperparameter tuning* terhadap minimal dua model terbaik.
6. Mengevaluasi performa model menggunakan metrik dan visualisasi yang sesuai.

## Dataset

**Dataset:** AI4MARS — A Dataset for Terrain-Aware Autonomous Driving on Mars

**Sumber:** [NASA Open Data — AI4MARS](https://data.nasa.gov/dataset/ai4mars-a-dataset-for-terrain-aware-autonomous-driving-on-mars)

AI4MARS merupakan dataset citra permukaan Mars yang dikembangkan untuk mendukung pengenalan kondisi medan oleh sistem navigasi rover.

Dataset ini memiliki label terrain yang dapat digunakan sebagai dasar untuk membentuk tugas klasifikasi tekstur permukaan Mars.

**Catatan:** AI4MARS menyediakan label dalam bentuk mask segmentasi. Oleh karena itu, diperlukan tahap pemrosesan label untuk menentukan kelas citra atau wilayah citra yang akan diklasifikasikan. Kelas yang digunakan dan jumlah sampel akan dicantumkan setelah proses eksplorasi dataset selesai.

Dataset asli tidak disertakan langsung dalam repository ini. Silakan unduh dari sumber resmi dan letakkan sesuai struktur direktori proyek.

## Teknologi dan Library

Proyek ini menggunakan:

- **Python 3.11** — bahasa pemrograman.
- **OpenCV** — membaca dan melakukan pra-pemrosesan citra.
- **NumPy** — operasi numerik.
- **Pandas** — pengolahan tabel fitur.
- **PyFeats** — ekstraksi fitur tekstur citra.
- **PyCaret 3.3.2** — pemodelan dan perbandingan algoritma klasifikasi.
- **Matplotlib** dan **Seaborn** — visualisasi hasil eksperimen.
- **Jupyter Notebook** — lingkungan eksperimen.

## Alur Pengerjaan

Proses eksperimen dirancang melalui tahapan berikut:

1. **Dataset Preparation**  
   Mengunduh dataset, memeriksa struktur citra dan label, serta menentukan kelas yang digunakan.

2. **Image Preprocessing**  
   Membaca citra, mengubah citra menjadi grayscale jika diperlukan, dan menyeragamkan ukuran citra.

3. **Feature Extraction**  
   Mengekstraksi karakteristik tekstur menggunakan metode PyFeats, seperti GLCM, LBP, atau metode lain yang sesuai.

4. **Feature Dataset Construction**  
   Menggabungkan hasil ekstraksi menjadi tabel numerik dengan label kelas dan menyimpannya dalam format CSV.

5. **Data Preparation**  
   Memeriksa nilai yang hilang, nilai tidak valid, distribusi kelas, serta membagi data menjadi data latih dan data uji.

6. **Model Comparison**  
   Menggunakan PyCaret untuk membandingkan algoritma klasifikasi berdasarkan metrik evaluasi yang ditentukan.

7. **Hyperparameter Tuning**  
   Melakukan optimasi parameter terhadap minimal dua model terbaik berdasarkan hasil perbandingan awal.

8. **Model Evaluation**  
   Mengevaluasi model menggunakan data uji dan menampilkan visualisasi performa.

9. **Conclusion**  
   Menyusun kesimpulan berdasarkan hasil eksperimen dan perbandingan model.

## Struktur Direktori

```text
mars-texture-classification-pyfeats-pycaret/
├── data/
│   ├── raw/
│   └── processed/
├── notebooks/
│   └── main.ipynb
├── results/
│   ├── figures/
│   └── metrics/
├── README.md
├── requirements.txt
└── .gitignore
```

Keterangan:

- `data/raw/` — menyimpan dataset asli dan label yang telah diunduh.
- `data/processed/` — menyimpan data hasil pemrosesan dan tabel fitur.
- `notebooks/` — menyimpan notebook eksperimen.
- `results/figures/` — menyimpan grafik dan visualisasi evaluasi.
- `results/metrics/` — menyimpan ringkasan metrik hasil eksperimen.
- `requirements.txt` — mencatat dependensi Python yang digunakan.

## Instalasi dan Penggunaan

### 1. Clone repository

```bash
git clone https://github.com/USERNAME/mars-texture-classification-pyfeats-pycaret.git
cd mars-texture-classification-pyfeats-pycaret
```

Ganti `USERNAME` dengan nama pengguna GitHub pemilik repository.

### 2. Buat virtual environment

Pastikan Python 3.11 telah terpasang.

Windows:

```powershell
py -3.11 -m venv env
.\env\Scripts\Activate.ps1
```

### 3. Instal dependensi

```bash
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

### 4. Jalankan Jupyter Notebook

```bash
jupyter notebook
```

Buka notebook pada direktori `notebooks/` dan jalankan setiap cell secara berurutan.

### 5. Siapkan dataset

Unduh AI4MARS dari sumber resminya. Susun gambar dan label sesuai struktur direktori yang digunakan dalam kode eksperimen.

Pastikan pemetaan label, pembentukan sampel, dan pembagian data dilakukan secara konsisten sebelum pelatihan model.

## Evaluasi Model

Performa model akan dievaluasi menggunakan metrik yang sesuai dengan karakteristik dataset dan tugas klasifikasi, meliputi:

- **Accuracy** — proporsi prediksi yang benar.
- **Precision** — ketepatan prediksi pada setiap kelas.
- **Recall** — kemampuan model mengenali sampel dari setiap kelas.
- **F1-score** — keseimbangan antara precision dan recall.
- **Confusion Matrix** — distribusi prediksi benar dan salah.
- **ROC-AUC** — kemampuan diskriminasi kelas apabila sesuai dengan skema klasifikasi dan skor prediksi yang tersedia.
- **Feature Importance** — kontribusi fitur pada model yang mendukung analisis tersebut.

Hasil akhir, termasuk algoritma terbaik dan nilai metrik, akan ditambahkan setelah eksperimen selesai dilaksanakan.

## Status Proyek

**Status:** Dalam pengembangan

Tahapan yang direncanakan mencakup persiapan dataset, ekstraksi fitur, perbandingan model, optimasi parameter, dan evaluasi akhir.

## Informasi Akademik

- **Nama Proyek:** MarsTexture AI
- **Repository:** `mars-texture-classification-pyfeats-pycaret`
- **Mata Kuliah:** Machine Learning
- **Jenis Kegiatan:** Ujian Tengah Semester (UTS)
- **Tahun:** 2026

## Lisensi dan Atribusi

Dataset AI4MARS berasal dari sumber eksternal. Penggunaan dan distribusinya harus mengikuti ketentuan lisensi serta atribusi yang ditetapkan oleh penyedia dataset.

Proyek ini merupakan implementasi akademik untuk pembelajaran pengolahan citra dan Machine Learning.
