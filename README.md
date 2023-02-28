# Credit_Risk_Analysis

## Overview
Loans are an incredibly important part of our society, allowing people to pay for higher cost items such as vehicles and homes.  However, it is a system that is also dependent on the loans being able to be paid back.  As a result, it is very imporatant to try and determine what level of risk is involved with providing a loan to a given person.  With that said, the goal of this project is to do just that.  We wanted to use supervised Machine Learning to create a model capable of predicting the risk associated with giving a loan to someone, based off a large number of factors that we had access too.

## Results
We built a number of different models since it is not usually obvious what will be the best approach.  It is worth noting that we also had to account for target value imbalance as our dataset contains over 68000 examples of low risk cases but only 347 cases of high risk.  To do this we tried oversampling (2 variations in fact), undersampling, and SMOTEENN which combines both methods.  These were used in conjunction with the Logistic Regression model, which is the default for models where the target takes a binary value.

* Random Oversampling had an accuracy score of 0.6266
* SMOTE Oversampling had an accuracy score of 0.6271 (see below)
* Cluster based Undersampling had an accuracy score of .5061
* The SMOTEEN method resulted in an accuracy score of .6082

To give a quick overview of the output of our analysis below you will see the results of the SMOTE oversampling method which had the highest accuracy score of the previous 4 methods.  It did have good precision for low risk (1) results but the precision (pre) and harmonic mean (F1) for high risk (0) was low.

![SMOTE Logistic Regression Results] (Resources/LogisticRegressionResults.png)

We went a step further and used two types of decision tree style models on the same dataset, both which by default handle the imbalance using undersampling.

* The Balanced Random Forest method resulted in an accuracy score of .7885
* The Easy Ensemble method resulted in an accuracy score of .9317 (see below)

Here we can see the output from the Easy Ensemble method which is model that builds off of itself, using the results of the first decision tree to improve the model of the second and so on.  As with the results of the SMOTE method above the results here score well for low risk.  However, it scores higher across the board including high risk as well.

![Easy Ensemble Results] (Resources/EasyEnsembleResults.png)

### Summary
If we need to decide which of these examples is best the choice is very clear.  Our results from the Easy Ensemble method (which is a form of boosting) out perform all the rest and it isn't very close.  However, even with these results there still a fundemental flaw shared by them all.  When predicting the outputs of test variables the reliablity (precision) of predicting a high risk case was poor.  This means, more people were labeled high risk than there actually were.  While this output may not be as bad as labeling high risk cases as low risk I believe it would be worth checking out models to see if any of them can score better.