# Diabetes Prediction — Machine Learning Project

**Goal:** Predict diabetes risk score and classify diabetes stage using statistical learning methods.

---

## Project Overview

This project explores two complementary tasks based on the *Diabetes Health Indicators* dataset:

### 1. **Regression — Predicting Diabetes Risk Score**
We evaluate multiple regression models to understand how lifestyle and medical features influence the risk score.  
Key aspects:
- Exploratory data analysis  
- Linear Regression  
- Feature importance & confidence intervals  
- Model interpretability  

### 2. **Classification — Predicting Diabetes Stage (5 classes)**
A multi-class classification problem with strong class imbalance.  
Key techniques:
- Random Forest Classifier  
- Downsampling strategies  
- Performance metrics beyond accuracy (recall, confusion matrix)  
- Improving minority class detection  

---

## Main Results

### Regression
- High R² score  
- Small set of features explains most variance  
- Statistically significant coefficients identified via p-values and confidence intervals  

### Classification
- Initial model biased toward majority classes  
- After downsampling: balanced recall across stages  
- Improved detection of rare and clinically important categories  

---
