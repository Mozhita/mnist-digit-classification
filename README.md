# 🧠 MNIST Digit Recognizer (Kaggle Competition)

This repository contains my solution for the [Digit Recognizer](https://www.kaggle.com/competitions/digit-recognizer) Kaggle competition using the MNIST dataset. The goal is to accurately classify images of handwritten digits (0–9).

> 🏆 Final Kaggle Score: **0.98307**

---

## 🗂️ Dataset

- **Train set**: 42,000 images with labels
- **Test set**: 28,000 images (labels hidden)
- Each image is 28x28 grayscale pixels, flattened to 784 features
- All pixel values are integers between 0 and 255

---

## 🚀 My Approach

### ✅ 1. Baseline Models
- Started with basic models like **Logistic Regression**, **k-NN**, and **Random Forest**
- Accuracy ranged from **0.92 to 0.95**

### ✅ 2. MLP (Multi-Layer Perceptron)
- Built a deep neural network using TensorFlow/Keras
- Architecture:
  - Dense(512) → BatchNorm → Dropout(0.3)
  - Dense(256) → BatchNorm → Dropout(0.3)
  - Dense(128) → BatchNorm → Dropout(0.3)
  - Output: Dense(10, softmax)
- Optimizer: `Adam`, Loss: `SparseCategoricalCrossentropy`
- Achieved **0.97928** on Kaggle!

### ✅ 3. Pseudo-Labeling
- Used the trained model to **predict labels on the test set**
- Selected only **high-confidence predictions (probability ≥ 0.99)**
- Added them back into training data as pseudo-labeled samples
- Retrained the same model with the expanded dataset
- Boosted performance to **0.98307**

---

## 📈 Results

| Model              | Kaggle Score |
|--------------------|--------------|
| Logistic Regression| 0.925        |
| Random Forest      | 0.943        |
| MLP (baseline)     | 0.97928      |
| MLP + PseudoLabel  | **0.98307**  |

---
