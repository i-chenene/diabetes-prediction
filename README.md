# Diabetes Prediction with Statistical Learning

## What this is

A machine learning project tackling diabetes prediction from two angles: **regression** (predicting a continuous risk score) and **multi-class classification** (predicting diabetes stage across 5 classes). Built on the *Diabetes Health Indicators* dataset.

The interesting part isn't just the models — it's dealing with heavy class imbalance in the classification task and figuring out which handful of features actually matter for prediction.


## Dataset

**Diabetes Health Indicators** — lifestyle and medical features (BMI, age, blood pressure, physical activity, smoking status, etc.) linked to diabetes outcomes. The dataset has a strong imbalance toward non-diabetic / early-stage individuals, which makes naive classification misleading.



## Part 1 — Regression: Predicting Risk Score

We tested multiple regression approaches to understand which features drive diabetes risk.

**What we found:**
- A small subset of features explains most of the variance — the model doesn't need everything the dataset gives it
- Statistically significant predictors identified via p-values and confidence intervals (not just correlation)
- High R² score, meaning the linear relationship holds well for this task

**What we used:** Linear Regression with feature selection, confidence intervals on coefficients, and interpretability analysis. The goal here was understanding *why* the model predicts what it predicts, not just optimizing a metric.



## Part 2 — Classification: Predicting Diabetes Stage (5 classes)

This is where it gets harder. Five stages with severe class imbalance — the naive model just predicts the majority class and gets decent accuracy while being clinically useless.

**The problem:** A Random Forest trained on raw data had strong overall accuracy but near-zero recall on rare stages — exactly the ones that matter most clinically.

**Our approach:**
- Downsampling the majority classes to force the model to actually learn minority patterns
- Evaluating on **per-class recall** and **confusion matrix** rather than global accuracy — because 90% accuracy means nothing if you miss every at-risk patient
- Iterating on the balance ratio to find the tradeoff between majority class performance and minority class detection

**Result:** After rebalancing, recall became much more uniform across all 5 stages. We traded some overall accuracy for the ability to actually detect clinically important categories — a tradeoff worth making.



## Honest limitations

- **Downsampling throws away data.** SMOTE or other oversampling techniques on the minority classes might preserve more information. We went with the simpler approach first.
- **Random Forest only.** We didn't compare against gradient boosting (XGBoost, LightGBM) which typically outperforms RF on tabular data with imbalance.
- **No cross-validation tuning.** Hyperparameters were kept at reasonable defaults — a proper grid search would likely squeeze out a few more points.
- **Feature engineering was minimal.** Interaction terms or domain-specific feature construction (e.g., composite metabolic risk scores) could help.



## References

- [Diabetes Health Indicators Dataset](https://www.kaggle.com/datasets/alexteboul/diabetes-health-indicators-dataset)
