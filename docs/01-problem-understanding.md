
# SENTINEL — Problem Understanding

## 1. Project Overview
FraudLens is an adaptive fraud intelligence platform designed to help identify potentially fraudulent card transactions and prioritise them for investigation and rectification.

 In this project  i aim to demonstrate how machine learning can be integrated into a complete software system rather than being limited to a standalone model . It combines fraud-risk prediction using ml algorithms, a configurable decision policy, an investigation queue , prediction explanations, analyst feedback, and system monitoring.

The initial version i used a publicly available historical credit card transaction dataset  taken from kaggle to develop and evaluate a fraud-risk prediction model. The system will be developed as a portfolio project to demonstrate  practical skills in machine learning, backend engineering, data management, testing, deployment, and MLOps.

## 2. Problem Statement
Problem statement: How can we build a reproducible, end-to-end fraud intelligence prototype that estimates transaction risk, prioritises suspicious transactions for investigation, records investigation outcomes, and evaluates its effectiveness using appropriate metrics?

Card fraud detection is challenging because fraudulent transactions represent a small proportion of overall transactions, fraudulent behaviour can change over time and investigation resources are limited.

A fraud detection system must identify suspicious transactions while avoiding excessive false alerts . Missing fraudulent transactions can result in connsiderable financial loss, while incorrectly flagging legitimate transactions can create unnecessary investigations and inconvenience customers.

A machine learning model alone does not solve the entire problem. Predictions must be converted into actionable priorities, investigators need a way to review suspicious cases and model performance must be evaluated against reliable outcomes when those outcomes become available.


## 3. Challenges
This project will address following challenges:
1. Class imbalance: Fraudulent transactions may be much less common than legitimate transactions, making accuracy as an unreliable measure for model quality.
2. False positives: Legitimate transactions may be incorrectly flagged, increasing investigation workload on the analyst.
3. False negatives: Fraudulent transactions may be classified as legitimate which cause the system to miss potential fraud.
4. Investigation capacity: Analysts may be unable to review every flagged transaction, making risk ranking n transactions at a time.
5. Model interpretability: Investigators need useful information about the factors contributing to a prediction, while recognising that explanations do not establish causality.
6. Changing data patterns: Changes in transaction behaviour or input data over time may reduce the usefulness of the model we selected.


## 4. Proposed Solution

 As solution for problem  the "FraudLens" use a modular architecture and proposed workflow go as:

* Transaction input: Accept transaction features available to the prototype and validate the input.
* Risk prediction: Use a trained machine learning pipeline to produce a fraud-risk score.
* Decision policy: Apply a separately configurable policy to categorise and prioritise transactions.
* Investigation queue: Rank each transactions by risk and support prioritisation under a defined review capacity of the analyst.
* Prediction explanation: Provide feature-contribution explanations where supported by the selected model and data.
* Case management: Store investigation records and allow authorised prototype users to record outcomes such as confirmed fraud, legitimate, or inconclusive.
* Evaluation and monitoring: Track data quality, service health, prediction patterns, and model metrics when reliable outcome labels become available.
* Model lifecycle management: Track experiments and model versions, and evaluate candidate models before promoting them.

The planned technology stack includes:
* Python, pandas, scikit-learn and suitable gradient-boosting libraries for machine learning
* FastAPI for the backend
* PostgreSQL for persistence
* Streamlit for the user dashboard
* Docker for reproducible deployment.
* MLflow will be considered for experiment and model tracking.


## 5. Assumptions and Limitations

> The initial model will be developed using a publicly available historical credit card fraud dataset and the  dataset is expected to contain labelled transactions, but its exact schema, feature meanings, timestamp availability, data quality, and suitability for the intended evaluation must be verified before implementation decisions are finalised.

*Anonymised features will not be assigned invented real-world meanings.
* Historical dataset performance may not represent performance on future transactions or in a real financial institution.
* The dataset may not contain account, device, merchant-network, or other relational information required for graph-based fraud analysis.
* Prediction explanations will describe model feature contributions, not prove the cause of fraud
* A model score will not automatically be interpreted as a calibrated probability.
* Confirmed outcomes may be delayed, incomplete, or uncertain because the model performance is measured only against appropriate available labels in  the dataset.
* Investigation outcomes recorded in the prototype will be treated as feedback requiring validation .
