# credit_risk_classification

In this challenge, we used a logistic regression method from the sklearn library and a dataset of 77,536 lending records to train a model to predict which borrowers are at risk of defaulting on their loans.

The dataset consisted of 7 common borrower metrics considered the 'independent variables' (loan size, interest rate, borrower income, debt to income ratio, number of bank accounts, derogatory marks, and total debt), and a label, loan status, indicating if the loan has been defaulted on (0 = healthy loan, 1 =  defaulted loan).

We sought to predict the dependent variable, loan status, given the independent variables.

## Overview of the Analysis

The analysis used a simple hold-out validation type approach in which we used most of the data to train the model and split out a small portion to test the model. The following steps were followed:

* We separated out the dependent variable from the independent variables.
* We randomly split the dataset into a training set and a test set. Here we forced the use of 90% of the data for training and only 10% for testing. We observed the class ratio was preserved between training and test sets.
* We set up a logistic regression model using the python sklearn library and fit the training data.
* We used the model to predict the loan status in the test set, using the independent variables from the test set as input.
* Finally, we evaluated our model's performance using our test set's loan status as the source of truth.

## Results

The scikit-learn classification report allows us to evaluate the performance of our classification model by reporting the following performance metrics:

* Precision: The ratio of true positive predictions to all positive predictions, also called the Positive Predictive Value (PPV). A high value indicates a low false positive rate. Precision is reported for both the healthy loan state and the defaulted loan state. We see that precision is much better for the healthy labelled loans (99.6%) than the high-risk labelled loans (87%).  

* Recall: The ratio of true positive predictions to the number of actual positives, also called the Sensitivity or True Positive Rate. A high value indicates a low false negative rate. Recall is reported for both the healthy loan state and the defaulted loan state. We see that recall is much better for the healthy labelled loans (99.5%) than the high-risk labelled loans (89.5%).

* F1-Score: The harmonic mean of precision (false positive rate) and recall (true positive rate). This is useful when there is a class imbalance such as in this dataset.

* Support: The number of observations of each class in the test dataset.

* Accuracy: The ratio of correct predictions (true and false) to the total number of observations. Accuracy is misleading in this imbalanced dataset. At 99.1% it under-represents the proportion of true healthy predictions and over-represents the proportion of true high-risk predictions.

* Macro and Weighted Averages: The class averages for precision, recall and f1-score respectively, either unweighted (macro) or weighted by the class imbalance ratio. In our data, 96.8% of observations have the healthy label while only 3.2% have the high-risk label. Therefore the weighted average precision = (0.996 * 0.968) + (0.87 * 0.032).


## Summary

* Our model is exceptionally good at predicting healthy loans and relatively poor at predicting loans that default.

* This an undesirable situation for our bank because an unacceptably large number of high-risk borrowers will go un-noticed before they default, ultimately costing the bank. 

* We would prefer to have a stronger ability to predict defaulters, even at the cost of incorrectly predicting more healthy loans as likely to default. This is because these false defaulters could be reassured by a more detailed followup borrower review, so little harm would ensue.

* We do not recommend adopting this model.
