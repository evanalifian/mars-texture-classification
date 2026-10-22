# TextureGuard AI — Artificial Texture Defect Classification

**TextureGuard AI** is a machine learning project for classifying artificial texture images using handcrafted feature extraction and automated machine learning (AutoML).

This project uses the **DAGM 2007 dataset**, **PyFeats** for texture feature extraction, and **PyCaret** to compare and evaluate machine learning classification models.

> **Project status:** In Development  
> **Course:** Machine Learning — Midterm Project (UTS)

## Project Overview

Texture inspection is an important task in quality control and surface defect analysis. Machine learning can help distinguish defective texture patterns from normal patterns by learning from extracted image features.

TextureGuard AI explores a traditional computer vision approach by converting images into numerical feature vectors before applying machine learning classification algorithms.

Instead of relying on deep learning models, this project focuses on **handcrafted features**, such as texture descriptors extracted using PyFeats.

## Objectives

- Explore and preprocess the DAGM 2007 artificial texture dataset.
- Extract handcrafted texture features using PyFeats.
- Convert images into a structured tabular dataset.
- Compare multiple classification algorithms using PyCaret.
- Tune at least two promising models.
- Evaluate model performance using appropriate classification metrics.
- Identify important features when supported by the selected model and evaluation method.

## Dataset

This project uses the **DAGM 2007 Competition Dataset**, which contains artificially generated textured surfaces with defect annotations.

**Dataset source:** [DAGM 2007 Competition](https://conferences.mpi-inf.mpg.de/dagm/2007/prizes.html)

The dataset includes multiple texture classes and corresponding defect information. The selected classes and labeling strategy will be documented during preprocessing.

### Dataset preparation

The preprocessing stage may include:

1. Selecting the texture classes to be used.
2. Loading images and their corresponding annotations.
3. Assigning classification labels based on the experiment design.
4. Resizing images if necessary.
5. Converting images to grayscale when required.
6. Extracting features and creating a tabular dataset.

**Important:** The labeling strategy must match the experiment. For binary classification, the selected samples should have clearly defined `normal` and `defective` labels. Defect masks or annotations should be processed appropriately rather than treated as ordinary image labels.

The original dataset is not included in this repository by default. Please obtain it from the dataset source and follow its usage conditions.

## Technologies

| Technology | Purpose |
|---|---|
| Python | Main programming language |
| OpenCV | Image loading and preprocessing |
| NumPy | Numerical operations |
| Pandas | Tabular data processing |
| PyFeats | Handcrafted feature extraction |
| PyCaret | Automated model comparison and tuning |
| Matplotlib | Visualization |
| Seaborn | Statistical visualization |
| Jupyter Notebook | Experimentation and documentation |

## Methodology

The project follows this workflow:

1. **Dataset collection** — Obtain and organize the DAGM 2007 dataset.
2. **Exploratory data analysis** — Inspect image dimensions, classes, and label distribution.
3. **Image preprocessing** — Prepare images for feature extraction.
4. **Feature extraction** — Extract handcrafted features using PyFeats, such as applicable GLCM, LBP, and other texture descriptors.
5. **Feature dataset construction** — Store the extracted features and their labels in a CSV file.
6. **Data preparation** — Handle missing values where necessary and split the data into training and testing sets.
7. **Model comparison** — Use PyCaret to compare classification algorithms.
8. **Hyperparameter tuning** — Tune at least two promising models.
9. **Model evaluation** — Evaluate the selected models on held-out test data.
10. **Result analysis** — Compare model performance and discuss the findings.

### Feature extraction

The extracted feature table is expected to contain numerical features and a target label.

Example structure:

| feature_1 | feature_2 | feature_3 | target |
|---:|---:|---:|---|
| 0.21 | 14.52 | 0.73 | normal |
| 0.65 | 21.08 | 0.42 | defective |

*The values above are illustrative only. Actual feature columns depend on the selected PyFeats functions.*

### Model development

PyCaret will be used to compare several classification algorithms. At least two promising models will be selected for hyperparameter tuning.

The final algorithms will be determined from the experimental results rather than selected in advance.

## Evaluation Metrics

The evaluation may include:

- **Accuracy** — Overall proportion of correct predictions.
- **Precision** — Proportion of positive predictions that are correct.
- **Recall** — Proportion of actual positive samples correctly identified.
- **F1-score** — Harmonic mean of precision and recall.
- **Confusion matrix** — Distribution of correct and incorrect predictions.
- **ROC-AUC** — Ability to distinguish classes when the selected evaluation setup supports it.
- **Feature importance** — Analysis of influential features for compatible models or explainability methods.

The final report will compare the selected models using consistent evaluation data and metrics.

## Project Structure

```text
textureguard-ai-dagm2007/
├── data/
│   ├── raw/
│   └── processed/
│       └── texture_features.csv
├── notebooks/
│   └── 01_uts_machine_learning.ipynb
├── results/
│   ├── figures/
│   └── metrics/
├── README.md
├── requirements.txt
└── .gitignore
```

Directory purposes:

- `data/raw/` — Original dataset files; excluded from Git by default.
- `data/processed/` — Processed data and extracted features.
- `notebooks/` — Data exploration, feature extraction, training, and evaluation.
- `results/figures/` — Visualizations and evaluation plots.
- `results/metrics/` — Model evaluation results.
- `requirements.txt` — Project dependencies.

The structure may evolve as the project develops.

## Installation

### Prerequisites

- Python 3.11
- pip
- Jupyter Notebook
- DAGM 2007 dataset files

### 1. Clone the repository

```bash
git clone https://github.com/USERNAME/textureguard-ai-dagm2007.git
cd textureguard-ai-dagm2007
```

Replace `USERNAME` with your GitHub username.

### 2. Create a virtual environment

On Windows:

```powershell
py -3.11 -m venv env
.\env\Scripts\Activate.ps1
```

If PowerShell blocks script execution, activate the environment using Command Prompt instead:

```bat
env\Scripts\activate.bat
```

### 3. Install dependencies

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### 4. Launch Jupyter Notebook

```bash
jupyter notebook
```

Open the notebook in the `notebooks/` directory and follow the documented workflow.

## Expected Outputs

The project aims to produce:

- A processed feature dataset in CSV format.
- A comparison of multiple classification models.
- Tuned versions of at least two selected models.
- Confusion matrices and other evaluation visualizations.
- A comparison of model performance.
- An analysis of relevant handcrafted features.
- A conclusion based on the experimental results.

These are planned outputs; results will be added after the experiments have been completed.

## Notes and Limitations

- Results depend on the selected DAGM 2007 classes, sample selection, and labeling strategy.
- Feature extraction time depends on image resolution, feature descriptors, and the number of images.
- Data leakage must be avoided when splitting training and testing samples.
- The final model should be evaluated using held-out data that was not used for model selection or tuning.
- Dataset usage must comply with the original source's terms.

## Academic Information

**Project:** TextureGuard AI — Artificial Texture Defect Classification  
**Course:** Machine Learning  
**Project Type:** Midterm Examination (UTS)  
**Academic Year:** 2026

---

*Built as an academic project to explore handcrafted texture features and machine learning classification using PyFeats and PyCaret.*