# 🫀 ECG Arrhythmia Detection Using CNNs

This project explores the use of **Convolutional Neural Networks (CNNs)** for the **automated classification of ECG signals** to detect arrhythmias, particularly **atrial fibrillation (AFib)**.

Two deep learning approaches are implemented:
- 🧩 **1D CNN** using raw ECG time-series signals  
- 🖼 **2D CNN** using spectrograms generated from ECG via STFT

---

## 📌 Project Overview

Manual ECG interpretation is time-consuming and susceptible to human error. This project presents a machine learning solution to:
- ✅ Improve diagnostic accuracy  
- 🕐 Enable real-time heart monitoring  
- 👨‍⚕️ Reduce reliance on manual ECG review  

---

## 🧠 Tech Stack

- **Language & Tools**: Python, Jupyter  
- **Libraries**: TensorFlow / Keras, NumPy, Matplotlib, Seaborn  
- **Signal Processing**: Short-Time Fourier Transform (STFT)  
- **Dataset**: [PhysioNet MIT-BIH Atrial Fibrillation Database](https://physionet.org/physiobank/database/afdb/)

---

## 🛠 Methodology

### 🔃 Preprocessing
- Denoise ECG signals  
- Normalize and segment into 5000-sample windows  
- Generate spectrograms using STFT  

### 🧠 Modeling
- **1D CNN** for raw time-series classification  
- **2D CNN** for spectrogram-based image classification  

### 📈 Evaluation
- Accuracy  
- Confusion matrix  
- Classification report  

---

## 📊 Results

| Model   | Input Type     | Accuracy | Notes                                    |
|---------|----------------|----------|------------------------------------------|
| 1D CNN  | Raw ECG        | 100%     | Likely overfitted or data leakage        |
| 2D CNN  | Spectrograms   | 100%     | Trained quickly, similar concerns        |

---

## ⚠️ Why 100% Accuracy? *(Important)*

Perfect scores suggest issues with **data leakage** and **overfitting**:

- ❌ **Random sample-level splitting**: ECG windows from the same patient may be in both training and test sets.
- ❌ **No patient-level separation**: The model may memorize patient-specific patterns.
- ❌ **Ideal dataset conditions**: Clean, well-balanced datasets lack real-world noise and variability.

---

## 🔧 Recommendations for Improvement

- ✅ Use **patient-level splits** to avoid data leakage  
- ✅ Apply **GroupKFold** cross-validation by patient ID  
- ✅ Introduce **dropout** or **L2 regularization** to combat overfitting  
- ✅ Test on **external datasets** or noisier, real-world ECG data  

---
