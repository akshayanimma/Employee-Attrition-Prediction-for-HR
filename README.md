# Employee Attrition Prediction for HR

An interactive HR analytics dashboard that explores employee attrition patterns and estimates attrition risk with a Random Forest classifier.

**[Launch the live Streamlit app](https://employee-attrition-prediction-for-hr-kwm82y32a2wqbawje7wvzx.streamlit.app/)**

## Overview

This project uses the IBM HR Analytics employee attrition dataset to explore workforce patterns and demonstrate how machine learning can support HR analysis. The dashboard reports 1,470 employees and 35 features.

## Dashboard Features

- **Overview:** Employee count, attrition count, attrition rate, and comparisons between employees who left and stayed.
- **Exploratory Analysis:** Charts comparing attrition across job roles, departments, travel, satisfaction, work-life balance, and other employee attributes.
- **Predict Risk:** Enter employee attributes to receive a model-based attrition risk estimate.
- **At-Risk Watch List:** Review employees flagged by the model for elevated risk.
- **Visual Analysis:** Interactive charts to help explore patterns in the dataset.

## Machine Learning

- **Models:** class-weighted Logistic Regression (baseline) and Random Forest (200 trees, max depth 10)
- **Split:** stratified 80/20 train/test (1,176 / 294 employees), `random_state=42`
- **Imbalance:** only about 16% of employees left, so both models use `class_weight='balanced'` and are judged on recall and precision for the "Left" class, not accuracy alone
- **Model loading:** the application expects saved model and feature-name artifacts in the `models/` directory

### Results (held-out test set: 294 employees, 47 who left)

| Model | Accuracy | Precision (Left) | Recall (Left) | F1 (Left) | ROC-AUC | 5-fold CV ROC-AUC |
|---|---|---|---|---|---|---|
| Logistic Regression | 0.759 | 0.361 | 0.660 | 0.466 | 0.795 | 0.826 ± 0.055 |
| Random Forest | 0.827 | 0.444 | 0.340 | 0.386 | 0.779 | 0.791 ± 0.062 |

The Random Forest is more accurate overall but finds only 16 of the 47 employees who left. The logistic regression baseline finds about two thirds of them, with more false alarms. Threshold tuning and hyperparameter search are the next steps.

### Limitations

- The test set is small (47 leavers), so these figures have wide error bars.
- The At-Risk Watch List scores all 1,470 employees, most of whom the model was trained on, so its probabilities are optimistic. Use the held-out results above to judge performance.
- The Predict Risk form collects 12 inputs; the remaining model features are set to 0.
- The dashboard's "risk factors" are simple rules, not model explanations.

The dashboard's risk bands are model-based indicators, not certainty that an employee will leave. This project is for learning and demonstration and should not be used as the sole basis for employment decisions.

## Tech Stack

- Python
- pandas, NumPy
- scikit-learn and joblib
- Streamlit
- Matplotlib and Seaborn
- Random Forest and Logistic Regression

## Run Locally

1. Clone this repository.
2. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

3. Ensure the dataset is available at `data/WA_Fn-UseC_-HR-Employee-Attrition.csv`.
4. Ensure the saved model and feature-name files expected by `app.py` exist in `models/`. If needed, run `03_model_building.ipynb` from top to bottom (Run All) from the repository root to rebuild them.
5. Start the dashboard:

   ```bash
   streamlit run app.py
   ```

## Dataset

The project uses the IBM HR Analytics employee attrition dataset included in the repository. Analysis and predictions are intended for educational demonstration.

## Live Demo

**[Open the Employee Attrition Dashboard](https://employee-attrition-prediction-for-hr-kwm82y32a2wqbawje7wvzx.streamlit.app/)**