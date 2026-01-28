# ❤️ Cleveland Heart Disease: Predictive Modeling & Clinical Interpretability

**Author:** Naroa Iparraguirre  
**Focus:** Explainable AI (XAI) | Clinical Decision Support | Semi-Supervised Learning

## 📌 Executive Summary
In medical diagnostics, **trust is as important as accuracy**. This project develops a predictive model for heart disease presence (Cleveland Database) that achieves **90% accuracy** while remaining fully interpretable to clinicians.

Unlike "black box" approaches, this work prioritizes **Explainable AI (XAI)**, using **SHAP** values to explain risk factors and **DiCE** to generate actionable counterfactuals (e.g., *"If this patient lowers their heart rate by 10 bpm, their risk classification flips to 'Healthy'"*).

## 🔬 Methodology

### 1. Model Selection (The Principle of Parsimony)
We benchmarked multiple classifiers (SVM, Random Forest, KNN) against linear models.
* **Finding:** A **Logistic Regression** model with L1 Regularization performed statistically equivalently to complex ensembles ($p > 0.05$ in paired t-tests).
* **Decision:** Selected Logistic Regression for deployment due to its inherent transparency (coefficients = odds ratios).

### 2. Explainability & Actionability
* **SHAP (Shapley Additive Explanations):** Used to visualize exactly *why* a specific patient was classified as high-risk (e.g., "High ST depression contributed +20% to risk probability").
* **DiCE (Diverse Counterfactual Explanations):** Implemented to answer "What if?" scenarios, providing patients with concrete, minimal changes needed to improve their health outcome.

### 3. Data Efficiency Experiment (Semi-Supervised)
Simulated a "data scarcity" scenario common in rare diseases:
* **Self-Training:** We hid 80% of the labels and used a self-training loop to pseudo-label the data.
* **Result:** The model recovered **88% accuracy** using only **20% of the ground truth labels**, demonstrating the viability of this pipeline for datasets with expensive labeling costs.

## 📊 Results Snapshot
* **Final Accuracy:** 90.0% (Test Set)
* **Recall (Sensitivity):** 92.4% (Crucial for minimizing false negatives in medicine)
* **Key Predictors:** Thalium Stress Test, Number of Major Vessels, Chest Pain Type.

## 🛠️ Libraries Used
* **Modeling:** `scikit-learn`, `statsmodels`
* **Explainability:** `shap`, `dice_ml`
* **Data Viz:** `matplotlib`, `seaborn`, `plotly`

## 📂 Repository Structure
* `Heart_disease_cleveland.ipynb`: End-to-end analysis, modeling, and XAI implementation.
