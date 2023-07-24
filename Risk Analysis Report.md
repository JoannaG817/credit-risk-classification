## Overview of the Analysis

* Describe the stages of the machine learning process you went through as part of this analysis.
* Briefly touch on any methods you used (e.g., `LogisticRegression`, or any resampling method).

I used a dataset of historical lending activity from a peer-to-peer lending services company to build a model that can identify and predict the creditworthiness of borrowers.

THe data included information on:

-the size of the loan
-its interest rate
-the borrower's income
-the borrower's debt to income ratio
-the number of accounts the borrower held
-derogatory marks against the borrower
-the borrower's total debt
-the loan status classified either as a "0" meaning low-risk or "1" meaning high-risk 

The dataset of 77,536 data points was first used to create labels set (y) from the “loan_status” column, and then to create the features (x) DataFrame from the remaining columns. I used value_counts to check the balance of the labels variable (y) with a result of 75036 low-risk loans and 2500 high-risk loans.  The dataset was then split into training and testing sets. The training set was used to build an initial logistic regression model using the LogisticRegression module from scikit-learn. The first logistic regression model was then applied to the testing dataset. The purpose of the model was to determine whether a loan to the borrower in the testing set would be low- or high-risk.

Since the intial logistic regression model was drawing from a dataset with 75,036 low-risk loan data points and 2,500 high-risk data points, I resampled the training data to ensure that the model had an equal number of data points to draw from.  Once the data was resampled with the RandomOverSampler module from imbalanced-learn, it resulted in 56,271 data points for low-risk "0" and high-risk "1" loans each, based on the original dataset.

The resampled data was used to build a second logistic regression model. The purpose was to determine whether a loan to the borrower in the testing set would be low- or high-risk. The results from both models are summarized below.

## Results

* Machine Learning Model 1:
  Accuracy: 99%
  Precision: 100% for "0" and 85% for "1"
  Recall: 99% for "0" and 91% for "1"
  
* Machine Learning Model 2:
  Accuracy: 99%
  Precision: 100% for "0" and 84% for "1"
  Recall: 99% for both loans
  
## Summary

Both of the models models have the same accuracy of 99%, indicating that they correctly classify the majority of instances.  For low-risk loans, both models have a precision of 100%, indicating that they correctly identify all instances of loans "0". However, for high-risk loans, Model 1 has a precision of 85%, while Model 2 has a precision of 84%. In this case, Model 1 is slightly better in terms of precision for high-risk loans.

For loans "0", both models have a recall of 99%, they correctly identify almost all instances of "0" loans. However, for loans "1", Model 1 has a recall of 91%, while Model 2 has a recall of 99%. Here, Model 2 outperforms Model 1 with a higher recall for loans "1".

Based on these results, Model 2 seems to be slightly better overall, as it has a higher recall for loans "1", which means it is better at identifying instances of loan "1" correctly. However, both models have similar accuracy and perform well in general. 
