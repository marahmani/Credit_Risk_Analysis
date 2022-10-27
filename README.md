# Credit_Risk_Analysis

Overview of the analysis: 

Credit risk has always been very sensitive and needed to have an accurate prediction. Credit risk needs to be safe, and every possible unsafe caution needs to be considered. In this project we will take a look at all the factors for loan to help with someone’s high risk status prediction. For this purpose, we follow the familiar pattern as we instantiate a model, train it, create predictions, then validate the model.

In this project different methods has been used to check the best model for credit risk. In resampling after cleaning the data, we did split the data into training and testing we saw this :
low_risk     68470
high_risk      347
Name: loan_status, dtype: int64


In Oversampling, we used a random state of 1 for each sampling algorithm to ensure consistency between tests. We got the confusion matrix array as bellow:
array([[   54,    33],
       [ 5945, 11173]], dtype=int64)

And imbalanced classification report like:

                   pre       rec       spe        f1       geo       iba       sup

  high_risk       0.01      0.62      0.65      0.02      0.64      0.40        87
   low_risk       1.00      0.65      0.62      0.79      0.64      0.41     17118
avg / total       0.99      0.65      0.62      0.79      0.64      0.41     17205


SMOTE Oversampling

we also did resample the resample the training data with SMOTE

the confusion matrix is :

array([[   54,    33],
       [ 6165, 10953]], dtype=int64)
       
and the the imbalanced classification report is as bellow:

                   pre       rec       spe        f1       geo       iba       sup

  high_risk       0.01      0.62      0.64      0.02      0.63      0.40        87
   low_risk       1.00      0.64      0.62      0.78      0.63      0.40     17118

avg / total       0.99      0.64      0.62      0.78      0.63      0.40     17205


Undersampling

the confusion matrix is 

array([[  51,   36],
       [9682, 7436]], dtype=int64)
       
and the imbalanced classification report for it is :

                   pre       rec       spe        f1       geo       iba       sup

  high_risk       0.01      0.59      0.43      0.01      0.50      0.26        87
   low_risk       1.00      0.43      0.59      0.60      0.50      0.25     17118

avg / total       0.99      0.44      0.59      0.60      0.50      0.25     17205

Combination (Over and Under) Sampling

the consusion Matrix 

array([[  61,   26],
       [7293, 9825]], dtype=int64)
       
imbalanced classification report:


                   pre       rec       spe        f1       geo       iba       sup

  high_risk       0.01      0.70      0.57      0.02      0.63      0.41        87
   low_risk       1.00      0.57      0.70      0.73      0.63      0.40     17118

avg / total       0.99      0.57      0.70      0.73      0.63      0.40     17205

Ensemble Learners

Balanced Random Forest Classifier

the confusion matrix

array([[   30,    57],
       [   11, 17107]], dtype=int64)
       
       
 imbalanced classification report:
 
                   pre       rec       spe        f1       geo       iba       sup

  high_risk       0.73      0.34      1.00      0.47      0.59      0.32        87
   low_risk       1.00      1.00      0.34      1.00      0.59      0.37     17118

avg / total       1.00      1.00      0.35      1.00      0.59      0.37     17205 

List the features sorted in descending order by feature importance


feature_name	importance
15	total_rec_prncp	0.087587
13	total_pymnt	0.077704
14	total_pymnt_inv	0.066812
20	last_pymnt_amnt	0.064594
16	total_rec_int	0.050392
...	...	...
19	collection_recovery_fee	0.000000
46	delinq_amnt	0.000000
23	acc_now_delinq	0.000000
22	policy_code	0.000000
94	debt_settlement_flag_N	0.000000
95 rows × 2 columns

Easy Ensemble AdaBoost Classifier

the balanced accuracy score is 0.925427358175101

the confusion matrix array([[   79,     8],
       [  979, 16139]], dtype=int64)
       

 imbalanced classification report:
 
                   pre       rec       spe        f1       geo       iba       sup

  high_risk       0.07      0.91      0.94      0.14      0.93      0.85        87
   low_risk       1.00      0.94      0.91      0.97      0.93      0.86     17118

avg / total       0.99      0.94      0.91      0.97      0.93      0.86     1720


SUMMARY

The overall based ont all machine learining methods used in this project, we can see that the best-performing Machine Learning (ML) model was the EasyEnsemble with AdaBoost classifier. 

Even though the EasyEnsemble algorithm performs better than the others, we can coclude that it still has a very low precision (9%) for High Credit Risk individuals. It means for a person with a bad credit risk, there's only a 9% chance that they dont get approved vs customers with good credit risks which would be denied credit.
