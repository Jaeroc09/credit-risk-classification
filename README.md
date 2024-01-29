# credit-risk-classification
Using supervised learning techniques to train and evaluate loan risk models

by Jason Estrada

## Overview of the Analysis

The purpose of the analysis is to train and evaluate a model based on loan risk.  A dataset of historical lending activity from a peer-to-peer lending services company was used to build a model that can identify the creditworthiness (low risk vs. high risk) of borrowers.

The dataset consisted of 77536 samples (rows), with the following features (columns):
- Loan size
- Interest rate
- Borrower's income
- Debt to income ratio
- Number of open accounts
- Derogatory marks (from credit history)
- Total debt

Of the 77536 samples, 2500 of them were labeled as 'high risk' (`loan_status` column of 1).  With the outcome/label being binary (0 or 1), a logistic regression model was used for training and further evaluated.  Steps performed for the first model below:

- Data separated between features (X) and label (y)
- Data further split into training and testing datasets using `train_test_split`
- Logistic Regression model was created and fit with training dataset
- Predictions created/saved using testing feature data and fitted model
- Model was evaluated by reviewing the balanced accuracy score, confusion matrix, and classification report

A second model was created by using the `imblearn` library and using the `RandomOverSampler` module to create resampled testing data (based on original training data) with an equal number of datapoints for the outcome/label.  The Logistic Regression model was then fit and predicted with the resampled data and evaluated to compare against the first model.

## Results

* Machine Learning Model 1 (Original Data):
  * Balanced Accuracy Score: 94.4%
  * Low Risk; Precision: 100%, Recall: 100%
  * High Risk; Precision: 87%, Recall: 89%



* Machine Learning Model 2 (Resampled Data):
  * Balanced Accuracy Score: 99.6%
  * Low Risk; Precision: 100%, Recall: 100%
  * High Risk; Precision: 87%, Recall: 100%

## Summary

- Comparing the balanced accuracy scored of both models, both are very accurate (94.4% vs 99.6%, respecively)
- Both models faired well when predicting low risk borrowers (precision and recall scores were 100% for both models)
- The second (resampled data) model was better than the first model in reducing the false negative rate (recall score of 89% for first model vs 100% for second model), but both models are the same for the false positive rate (precision score for both models were 87%)

In summary, I would recommend using the second model with resampled data due to the very low false negative rate for predictions.  The false negative category are high risk borrowers that are put in the low risk category.  As a lender, mitigating the risk of loan defaults from the false negative category is better for the company's bottom line.