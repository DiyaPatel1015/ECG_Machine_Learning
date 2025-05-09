This project explores the use of Convolutional Neural Networks (CNNs) for automated classification of ECG signals to detect arrhythmias, especially atrial fibrillation. Two deep learning approaches are implemented: 
    1D CNN using raw ECG time-series signals
    2D CNN using spectrograms generated from ECG

📌 Project Overview
Manual interpretation of ECGs is prone to human error and time-consuming. This machine learning-based solution aims to:    
    Improve diagnostic accuracy
    Enable real-time heart monitoring
    Reduce reliance on manual review

🧠 Tech Stack
Python, Jupyter
TensorFlow / Keras
NumPy, Matplotlib, Seaborn
Short-Time Fourier Transform (STFT)
Dataset: PhysioNet

🛠 Methodology
Preprocessing
    Denoise ECG signals
    Normalize and segment into 5000-sample windows
    Apply STFT to generate spectrograms
Modeling
    1D CNN for time-series classification
    2D CNN for spectrogram image classification
Evaluation
    Accuracy, confusion matrix, classification report

📊 Results
Model   	 Input Type	     Accuracy	    Notes
1D CNN	   Raw ECG	       100%	        May be overfitted or leaked
2D CNN	   Spectrograms	   100%	        Trained quickly, but same concern

⚠️ Why 100% Accuracy? [Important]
Although both models report perfect classification, this is likely due to data leakage and overfitting:
    Random Sample-Level Splitting: Windows from the same ECG may exist in both training and test sets, leading to memorization.
    No Patient-Level Segregation: The model has likely seen similar patterns during training.
    Lack of Real-World Noise: Clean, balanced datasets are easy to learn from but do not reflect clinical conditions.

🔧 How to Fix
    Split the data by patient ID, not signal window.
    Use GroupKFold for cross-validation.
    Add dropout or L2 regularization to reduce overfitting.
    Test on external ECG datasets or real-world scenarios.
