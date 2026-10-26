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

- **Model:** Random Forest classifier
- **Explainability:** SHAP library is included in the application workflow
- **Model loading:** The application expects saved model and feature-name artifacts in the `models/` directory.

The dashboard's risk bands are model-based indicators, not certainty that an employee will leave. This project is for learning and demonstration and should not be used as the sole basis for employment decisions.

## Tech Stack

- Python
- pandas, NumPy
- scikit-learn and joblib
- Streamlit
- Matplotlib and Seaborn
- Random Forest
- SHAP

## Run Locally

1. Clone this repository.
2. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

3. Ensure the dataset is available at `data/WA_Fn-UseC_-HR-Employee-Attrition.csv`.
4. Ensure the saved model and feature-name files expected by `app.py` exist in `models/`. If needed, review `03_model_building.ipynb` to build the model artifacts.
5. Start the dashboard:

   ```bash
   streamlit run app.py
   ```

## Dataset

The project uses the IBM HR Analytics employee attrition dataset included in the repository. Analysis and predictions are intended for educational demonstration.

## Live Demo

**[Open the Employee Attrition Dashboard](https://employee-attrition-prediction-for-hr-kwm82y32a2wqbawje7wvzx.streamlit.app/)**