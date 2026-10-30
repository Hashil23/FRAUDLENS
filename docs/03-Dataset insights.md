
# FraudLens — Data Understanding and Audit

## 1. Dataset Source and Description

* Dataset: Credit Card Fraud Detection
* Source: Kaggle — [MLG-ULB Credit Card Fraud Detection](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud/data)

* The dataset contains credit card transactions made by
European cardholders during September 2013. It covers
a period of two days and contains 284,807 transactions.
.The dataset was collected and analysed through a research
collaboration between Worldline and the ULB Machine
Learning Group.

## 2. Dataset Schema


<img width="617" height="677" alt="Screenshot 2026-10-31 005657" src="https://github.com/user-attachments/assets/1445ddb1-a58d-4ff8-b0e2-01171368c30d" />




|Feature |Description | Role|
|--------|------------|-----|
|Time|Seconds elapsed between a transaction and the first transaction in the dataset|Input|
|V1–V28|Numerical features obtained through Principal Component Analysis (PCA)|Input|
|Amount|Transaction amount|Input|
|Class|Target variable indicating whether a transaction is fraudulent|Target|

 observations:
* Time: Represents elapsed time in seconds, not an actual calendar timestamp.
* V1–V28: These features are PCA-transformed components. Their original feature meanings and background information are not publicly provided due to confidentiality.
* Amount: Represents the transaction amount. The currency is not specified in the available dataset description.
* Class: The response variable, where 1 represents fraud and 0 represents a legitimate transaction.
* The anonymised PCA features will retain their original names and will not be assigned invented real-world interpretations.



## 3. Dataset Dimensions and Data Types
* Total records: 284,807
* Total columns: 31
* Input features: 30
* Target variable: 1
* The dataset is provided in CSV format.

   
## 4. Class Distribution

- Legitimate transactions: 284,315
- Fraudulent transactions: 492
- Fraud proportion: Approximately 0.172%

According to the dataset description, the target distribution is:

|Transaction Class|Count|Percentage|
|--|--|--|
|Legitimate (0)|284,315|99.828%|
|Fraudulent (1)|492|0.172%|
|Total|284,807|100%|

* observation: The dataset is highly imbalanced, with fraudulent transactions representing approximately 0.172% of all records which implies accuracy
 alone is therefore insufficient to evaluate model performance so the 
evaluation should prioritise precision, recall and the area under the Precision-Recall Curve (PR-AUC)

## 5. Data Quality Findings


## 6. Evaluation Considerations

Accuracy alone is not sufficient for evaluating this
highly imbalanced dataset.

Planned evaluation metrics include:
- Precision
- Recall
- F1-score
- PR-AUC
- Confusion matrix
- Precision@K and Recall@K
-The evaluation process will also consider the class distribution and the suitability of the train, validation and test split.

## 8. Dataset Limitations

* Original meanings of PCA features are not provided .
* Only two days of transactions are represented.
* Real-world account and device relationships cannot be established by the supplied dataset description.
* The Time feature is not a calendar timestamp.
* There is no available  description  about the transaction currency.


