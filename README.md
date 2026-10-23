# TextureGuard AI — DAGM 2007

Klasifikasi citra tekstur buatan (6 kelas) dengan fitur *handcrafted* **PyFeats** dan AutoML **PyCaret**.
Tugas: Proyek UTS Pembelajaran Mesin.

| | |
|---|---|
| Nama | Evan Rafa Radya Alifian |
| NIM | 240411100063 |
| Kelas | Machine Learning - E |

## Dataset
DAGM 2007 — https://conferences.mpi-inf.mpg.de/dagm/2007/prizes.html
Unduh `Class1.zip` ... `Class6.zip`, ekstrak ke `datasets/raw/Class1` ... `datasets/raw/Class6`
(6 kelas x 1000 citra PNG grayscale 512x512).

## Struktur
```
datasets/raw/        citra asli (tidak di-commit jika terlalu besar)
datasets/processed/  features_dagm2007.csv, train_features.csv, test_features.csv
notebooks/           01_uts_machine_learning.ipynb
results/             grafik, tabel CSV, dan model terbaik (.pkl)
docs/                laporan
```

## Cara menjalankan
```bash
python -m venv .venv && .venv\Scripts\activate      # Windows
pip install -r requirements.txt
jupyter lab notebooks/01_uts_machine_learning.ipynb
```
Jalankan **Restart Kernel & Run All**. Ekstraksi fitur memakai cache `features_dagm2007.csv`;
set `FORCE_REEXTRACT = True` pada sel konfigurasi untuk menghitung ulang dari awal.

## Alur
1. Pemeriksaan data -> pra-pemrosesan (grayscale, resize 128x128, uint8)
2. Ekstraksi fitur PyFeats (FOS, GLCM, GLDS, NGTDM, SFM, LTE, GLRLM, FPS, LBP) -> CSV
3. Pembersihan data (inf/NaN, fitur konstan, outlier IQR, korelasi) -> split stratified 80:20
4. PyCaret: `setup()` -> `compare_models()` -> `tune_model()` (2 model terbaik) -> visualisasi -> `predict_model()` pada data uji
5. `finalize_model()` + `save_model()` ke `results/`
