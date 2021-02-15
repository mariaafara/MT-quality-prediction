# MT-quality-prediction

Translation Error Rate (TER) is a commonly used as a metric to evaluate the quality of translation.
Its an edit distance between the candidate translation sentence and a reference translation. 
It is the number of edits that need to be done on a translation to obtain a human-level translation quality, 
normalized by the number of words in the reference sentence.

In this work, we are given several samples (source, MT, human post-editing, TER) for one specific MT engine.
We want to try to predict the TER from the source sentence and the MT output. That is, to predict the quality of the MT.

The data set contains 7 000 samples of (source, target, reference, TER).
Language pair: ende (English to German).

## Work done

Our dataset contains 7000 samples of source, target, reference and the TER of which we want
to predict. The aim is to know whether we can predict the TER from the source sentence alone
or from the source and the MT output in the aim of knowing the quality of the translation. This
task is considered a Regression problem since the target variable is continuous (numeric).
For training a model we initially split the model into 3 parts: Training data, Validation data
and Testing data. Since we are going to work with cross validation technique, we need only to
divide the data into training and testing data, where the former will be divided in the cross
validation into training and validation. We work on 90/10 splits throughout the work.
We start the work with selecting baseline regression models such as SVR, XGBoost, Gradient
Boosting, RandomForests, etc. All regressors. Setting a baseline model's performance at first
when comparing with applying scaling or transformation to the feature(s) with cross validation.
Then perform hyperparameter tuning on the most performed models using RandomizedSearch
and cross validation. If the results are enhanced try out setting different pipelines. However the
results almost just progressed a little. There was an obvious problem in the data where the
predicted values are always centered around the mean. Working with SMOGN, enhanced the
results but did not totally solve it. Adding more features, more tuning, trying out NNs
architectures, experimenting with more SMOGN parameter might give other results.