# 🏥 Task 4: Disease Prediction from Medical Data

![Python](https://img.shields.io/badge/Python-3.8%2B-blue?style=flat-square&logo=python)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-1.0%2B-orange?style=flat-square&logo=scikit-learn)
![XGBoost](https://img.shields.io/badge/XGBoost-1.6%2B-red?style=flat-square)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?style=flat-square&logo=jupyter)
![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)

---

## 📌 Overview

This project predicts the possibility of diseases based on patient medical data using supervised machine learning classification techniques. It covers three real-world medical datasets and compares four powerful algorithms, ending with an interactive UI dashboard built using `ipywidgets` inside a Jupyter Notebook.

---

## 🎯 Objective

> Predict whether a patient is at risk of a disease based on clinical features such as age, blood pressure, glucose level, cholesterol, and more.

---

## 📂 Datasets Used

| Dataset | Source | Features | Target |
|---|---|---|---|
| **Heart Disease** | UCI ML Repository (Cleveland) | Age, BP, Cholesterol, Max HR, etc. | 0 = No Disease, 1 = Disease |
| **Diabetes** | Pima Indians (Kaggle / Brownlee) | Glucose, BMI, Insulin, Age, etc. | 0 = No Diabetes, 1 = Diabetes |
| **Breast Cancer** | sklearn built-in (UCI) | Mean Radius, Texture, Perimeter, etc. | 0 = Malignant, 1 = Benign |

---

## 🤖 Algorithms Used

- **Logistic Regression** — Simple, interpretable linear baseline
- **SVM (Support Vector Machine)** — RBF kernel, great for high-dimensional data
- **Random Forest** — Ensemble of decision trees, handles feature interactions
- **XGBoost** — Gradient boosted trees, best overall performance

---

## 📊 Results Summary

| Dataset | Best Model | Accuracy | AUC-ROC |
|---|---|---|---|
| Heart Disease | Random Forest / XGBoost | ~85% | ~0.91 |
| Diabetes | XGBoost | ~78% | ~0.84 |
| Breast Cancer | SVM / Logistic Regression | ~97% | ~0.99 |

---

## 🗂️ Project Structure

```
disease-prediction/
│
├── Task4_Disease_Prediction.ipynb   # Main notebook (EDA + Models + Dashboard)
├── dashboard_ui.py                  # Standalone dashboard code (paste into Jupyter)
├── README.md                        # This file
└── requirements.txt                 # Python dependencies
```

---

## ⚙️ Installation & Setup

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/disease-prediction.git
cd disease-prediction
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

Or install manually:

```bash
pip install numpy pandas scikit-learn xgboost matplotlib seaborn ipywidgets jupyter
```

### 3. Enable ipywidgets (if dashboard doesn't display)

```bash
jupyter nbextension enable --py widgetsnbextension
```

### 4. Launch Jupyter Notebook

```bash
jupyter notebook Task4_Disease_Prediction.ipynb
```

---

## 🖥️ Interactive UI Dashboard

The project includes a fully interactive prediction dashboard built with `ipywidgets`.

### Features
- Select any of the 3 datasets from a dropdown
- Select any of the 4 ML models from a dropdown
- Adjust patient parameters using sliders (age, glucose, blood pressure, heart rate, etc.)
- Click **Predict** to get instant risk prediction
- Colour-coded **Risk Meter** (🟢 Low / 🟡 Moderate / 🔴 High)
- Expandable table showing the exact input values used
- **Reset** button to restore slider defaults

### How to Use

1. Open `Task4_Disease_Prediction.ipynb` in Jupyter
2. Run all cells from top to bottom (`Kernel → Restart & Run All`)
3. Scroll to **Section 8 – Interactive UI Dashboard**
4. Adjust sliders and click **🔬 Predict**

Alternatively, copy the entire contents of `dashboard_ui.py` into a single Jupyter cell and run it directly — it loads data, trains models, and launches the dashboard all in one step.

---

## 🔍 Key Features of This Project

- **EDA Visualisations** — Class distribution bar charts, correlation heatmaps, feature distribution plots
- **Feature Importance** — Random Forest importance scores for all 3 datasets
- **ROC Curves** — AUC-ROC comparison across all models and datasets
- **Confusion Matrices** — Best model per dataset displayed visually
- **Cross-Validation** — 5-fold stratified CV for reliable accuracy estimates
- **Preprocessing Pipeline** — Missing value imputation, StandardScaler, stratified train/test split
- **Interactive Dashboard** — Real-time predictions from slider input with proper scaling

---

## 🧠 How the Dashboard Prediction Works

```
User adjusts sliders (raw real-world values)
        ↓
All features filled from unscaled training medians
        ↓
Slider values overwrite the relevant features (still raw)
        ↓
Entire raw row passed through StandardScaler (fitted on training data)
        ↓
Scaled input passed to the chosen ML model
        ↓
model.predict_proba() → Disease Probability → Risk Level
```

This ensures slider changes actually affect the prediction — a common bug is mixing raw and scaled values before calling the scaler, which causes the model to always output the same result.

---

## 📦 Requirements

```
numpy>=1.21
pandas>=1.3
scikit-learn>=1.0
xgboost>=1.6
matplotlib>=3.4
seaborn>=0.11
ipywidgets>=7.6
jupyter>=1.0
```

---

## 📁 Dataset Sources

- Heart Disease: [UCI ML Repository](https://archive.ics.uci.edu/ml/datasets/Heart+Disease)
- Diabetes: [Kaggle / Jason Brownlee](https://raw.githubusercontent.com/jbrownlee/Datasets/master/pima-indians-diabetes.data.csv)
- Breast Cancer: Built into `sklearn.datasets.load_breast_cancer()`

---

## ⚠️ Disclaimer

This project is built for **educational and demonstration purposes only**. The predictions made by these models should **not** be used as a substitute for professional medical diagnosis or advice. Always consult a qualified healthcare professional for medical decisions.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).

---

## 🙋 Author

**Your Name**
- GitHub: [@your-username](https://github.com/your-username)
- LinkedIn: [your-linkedin](https://linkedin.com/in/your-linkedin)

---

> ⭐ If you found this project helpful, please give it a star on GitHub!
