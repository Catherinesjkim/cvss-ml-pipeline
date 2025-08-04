🔐 CVSS-Based Vulnerability Risk Scoring with Synthetic Data & ML


✅ Project Overview

This project demonstrates how to automate vulnerability risk scoring using synthetic data, CVSS-like features, and machine learning.
The solution simulates a Rapid7-style ML pipeline for predicting exploit availability of vulnerabilities.
Key highlights:

Generates a synthetic dataset mimicking NVD/Rapid7 CVE data

Trains a Random Forest model to predict exploit likelihood

Provides a foundation for AWS SageMaker pipeline integration



✅ Dataset Description

## CVE Feature Descriptions

| **Feature Name**          | **Description**                                           | **Example Values**                     |
|---------------------------|-----------------------------------------------------------|----------------------------------------|
| `cve_id`                  | Unique identifier for the vulnerability                    | `CVE-2025-0001`                       |
| `attack_vector (AV)`      | How the vulnerability can be exploited                     | `NETWORK`, `ADJACENT`, `LOCAL`        |
| `attack_complexity (AC)`  | Complexity of the attack                                   | `LOW`, `HIGH`                         |
| `privileges_required (PR)`| Level of privileges required                               | `NONE`, `LOW`, `HIGH`                 |
| `user_interaction (UI)`   | Whether user interaction is required                       | `NONE`, `REQUIRED`                    |
| `base_score`              | CVSS Base Score (0.0 to 10.0)                              | `7.5`, `4.3`                          |
| `days_since_disclosure`   | Number of days since vulnerability was disclosed           | `1`, `180`                            |
| `exploit_available`       | Target variable (whether an exploit is publicly available) | `0` (No), `1` (Yes)                   |



✅ Architecture Diagram

[Data Sources]
   ├── NVD Feeds
   ├── Synthetic Data Generator
   └── Vulnerability Scanner Exports
       ↓
[SageMaker Processing Job]
   - Data Cleaning
   - Feature Engineering
       ↓
[SageMaker Training Job]
   - RandomForest or XGBoost Model
       ↓
[SageMaker Model Registry]
       ↓
[SageMaker Endpoint]
   - Real-Time Exploitability Prediction API
(This notebook simulates the data prep and ML modeling stage. SageMaker deployment can be added later.)



✅ Steps to Run the Notebook

1. Clone this repository
git clone https://github.com/your-username/cvss-ml-pipeline.git
cd cvss-ml-pipeline

2. Create a virtual environment (optional but recommended)
python3 -m venv venv
source venv/bin/activate

3. Install dependencies
pip install -r requirements.txt

4. Launch Jupyter Notebook
jupyter notebook

5. Open the notebook
- Open cvss_risk_scoring.ipynb
- Run all cells to:
   - Generate synthetic dataset
   - Train the ML model
   - View performance metrics and feature importance


✅ What This Notebook Does
✔ Generates synthetic vulnerability dataset
(similar to Rapid7-style CVSS-based data)

✔ Includes CVSS-like features
(attack_vector, attack_complexity, privileges_required, etc.)

✔ One-hot encodes categorical features
(for ML compatibility)

✔ Trains a RandomForestClassifier
(predicts exploit_available)

✔ Outputs classification report and feature importance visualization
(evaluates model performance)

✔ Shows an example prediction
(demonstrates inference for a single vulnerability)


✅ Example Outputs
Classification Report:

              precision    recall  f1-score   support
           0       0.89      0.91      0.90       512
           1       0.90      0.88      0.89       488
    accuracy                           0.90      1000

Feature Importance Plot:
- base_score and days_since_disclosure are the top predictors
- Attack vector and privileges required also significantly impact exploit likelihood


✅ Future Enhancements
- Implement full AWS SageMaker Pipeline for automated training and deployment
- Integrate with threat intelligence feeds (CISA KEV, ExploitDB)
- Add CI/CD for ML models using AWS CodePipeline or Jenkins
- Use Explainable AI (SHAP) for model interpretability in GRC context

📌 Author
Catherine Kim | GRC Security & ML Automation Enthusiast
