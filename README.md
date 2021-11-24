# Fake-New-Detection 

### Members

Ayush Gupta RA1811003010438 CSE (Core) H1 Section 

Vikash Mishra RA1811003010344 CSE (Core) F1 Section


### Introduction 

Fake news / False information is often being circulated to people who become a victim to such fake and misleading information. This actions are always harmful in one and another way and should be avoided.
As a solution , fact-checking and knowing the source of news if it is trustable is a big concern and it the root of the problem.

Thus we required a solution feasible and quickly accessible to all generation of society , be it old , the younger generation. So we came up with the idea of Fake news Detector , which checks the reliability of a news as to whether it is fake or real 


### Prerequisites

What things you need to install the software and how to install them:

1. Python 3.6 
   - This setup requires that your machine has python 3.6 installed on it. you can refer to this url https://www.python.org/downloads/ to download python. Once you have python downloaded and installed, you will need to setup PATH variables (if you want to run python program directly, detail instructions are below in *how to run software section*). To do that check this: https://www.pythoncentral.io/add-python-to-path-python-is-not-recognized-as-an-internal-or-external-command/.  
   - Setting up PATH variable is optional as you can also run program without it and more instruction are given below on this topic. 
2. Second and easier option is to download anaconda and use its anaconda prompt to run the commands. To install anaconda check this url https://www.anaconda.com/download/
3. You will also need to download and install below 3 packages after you install either python or anaconda from the steps above
   - Sklearn (scikit-learn)
   - numpy
   - scipy

  - if you have chosen to install python 3.6 then run below commands in command prompt/terminal to install these packages
   ```
   pip install -U scikit-learn
   pip install numpy
   pip install scipy
   ```
   - if you have chosen to install anaconda then run below commands in anaconda prompt to install these packages
   ```
   conda install -c scikit-learn
   conda install -c anaconda numpy
   conda install -c anaconda scipy
   ```     
  
#### Dataset used
The data source used for this project is LIAR dataset which contains 2 files with .tsv format for test and train . Below is some description about the data files used for this project.

LIAR: A BENCHMARK DATASET FOR FAKE NEWS DETECTION

William Yang Wang, "Liar, Liar Pants on Fire": A New Benchmark Dataset for Fake News Detection, to appear in Proceedings of the 55th Annual Meeting of the Association for Computational Linguistics (ACL 2017), short paper, Vancouver, BC, Canada, July 30-August 4, ACL.

the original dataset contained 13 variables/columns for train and train sets as follows:

* Column 1: the ID of the statement ([ID].json).
* Column 2: the label. (Label class contains: True, Mostly-true, Half-true, Barely-true, FALSE, Pants-fire)
* Column 3: the statement.
* Column 4: the subject(s).
* Column 5: the speaker.
* Column 6: the speaker's job title.
* Column 7: the state info.
* Column 8: the party affiliation.
* Column 9-13: the total credit history count, including the current statement.
* 9: barely true counts.
* 10: false counts.
* 11: half true counts.
* 12: mostly true counts.
* 13: pants on fire counts.
* Column 14: the context (venue / location of the speech or statement).

To make things simple we have chosen only 2 variables from this original dataset for this classification. The other variables can be added later to add some more complexity and enhance the features.

Below are the columns used to create 2 datasets that have been in used in this project
* Column 1: Statement (News headline or text).
* Column 2: Label (Label class contains: True, False)

You will see that newly created dataset has only 2 classes as compared to 6 from original classes. Below is method used for reducing the number of classes.

* Original 	--	New
* True	   	--	True
* Mostly-true	-- 	True
* Half-true	-- 	True
* Barely-true	-- 	False
* False		-- 	False
* Pants-fire	-- 	False


### Test Dataset 

<p align="center">
  <img width="600" height="300" src="https://github.com/vikashV3/Fake-New-Detection-/blob/main/test.PNG">
</p>


### Train Dataset 

<p align="center">
  <img width="600" height="300" src="https://github.com/vikashV3/Fake-New-Detection-/blob/main/train.PNG">
</p>

### Voting for unfitted estimators (Soft Voting/Majority Rule classifier)

A voting ensemble is an ensemble machine learning model that combines the predictions from multiple other models. It is a technique that may be used to improve model performance, ideally achieving better performance than a single model used in the ensemble.

The Voting Classifier

The voting classifier works like an polling system in which a prediction on a data point is made based on a voting system of the members of a group of machine learning models. There are option of either soft voting or hard voting depending upon the usage and on user input.

The hard voting type is applied to predicted class labels for majority rule voting. This uses the idea of vote for majority i.e. decisions is made in favor of whoever has more than half of the vote.

The soft voting, predicts the class label based on the sums of the predicted probabilities of the individual estimators that make up the ensemble. The soft voting is often recommended in the case of an ensemble of fitted classifiers.

The performance of the voting classifier depends largely on the results of the base models. It is recommended to use well-fitted estimators as base models with the soft voting type, for better predictions.

### File descriptions

#### DataPrep.py
This file contains all the pre processing functions needed to process all input documents and texts. First we read the train, test and validation data files then performed some pre processing like tokenizing, stemming etc. There are some exploratory data analysis is performed like response variable distribution and data quality checks like null or missing values etc.


### Logistic Regression 

Logistic Regression Logistic Regression is a parametric classifier which is easy to train and has low variance. The feature sampling probability is adapted according to the predictive performance and the weights of the logistic regression. 

<p align="center">
  <img width="600" height="50" src="https://github.com/vikashV3/Fake-New-Detection-/blob/main/Accuracy2.PNG">
</p>

<p align="center">
  <img width="600" height="350" src="https://github.com/vikashV3/Fake-New-Detection-/blob/main/LogisticRegression.PNG">
</p>

### Random Forest

Random forest is an ensemble of decision tree algorithms and it is a natural extension of bagging.
It is an extension of bootstrap aggregation (bagging) of decision trees and can be used for classification and regression problems.
In bagging, a number of decision trees are created where each tree is created from a different sample of the training dataset. A bootstrap sample is a sample of the training dataset where a sample may appear more than once in the sample, referred to as sampling with replacement.

Unlike bagging, random forest also involves selecting a subset of input features (columns or variables) at each split point in the construction of trees

<p align="center">
  <img width="600" height="50" src="https://github.com/vikashV3/Fake-New-Detection-/blob/main/Accuracy1.PNG">
</p>

<p align="center">
  <img width="600" height="350" src="https://github.com/vikashV3/Fake-New-Detection-/blob/main/RandomForest.PNG">
</p>

### Ensemble Technique 

Ensemble methods use multiple learning algorithms to obtain better predictive performance than could be obtained from any of the constituent learning algorithms

Two common methods to ensemble are:

1.Averaging method - The principle is to build several estimators independently and then to average their predictions comparatively. The combined estimator is usually better than the single base estimator on averaging because the variance is reduced. Examples: Stacking methods, Forests of randomized trees,etc. 

2.Boosting method - Base estimators are built sequentially and one tries to reduce the bias of the combined estimator. The idea is to combine several weak models to produce a powerful ensemble. Examples: AdaBoost, Gradient Tree Boosting, Extreme gradient boosting,etc. 

<p align="center">
  <img width="600" height="50" src="https://github.com/vikashV3/Fake-New-Detection-/blob/main/Accuracy3.PNG">
</p>

<p align="center">
  <img width="600" height="350" src="https://github.com/vikashV3/Fake-New-Detection-/blob/main/Ensemble.PNG">
</p>

<p align="center">
  <img width="600" height="200" src="https://github.com/vikashV3/Fake-New-Detection-/blob/main/Result.png">
</p>

### Block Diagram 

<p align="center">
  <img width="600" height="750" src="https://github.com/vikashV3/Fake-New-Detection-/blob/main/image.png">
</p>

### Questionnaire / FAQ 

Advantages of using ensemble learning:

The main advantages are that of performance and robustness. It reduces variance - the aggregate  of many models is less noisy than a single opinion of one of the models. It makes the final combined model less susceptible to given values corresponding to local minima.
suppose after training we get 3 models m1, m2, and m3. these models are indistinguishable with respect to their training error and they might have different generalization performances.so a safe option would be to use them all and average their outputs.

What are the common methods to ensemble: 

1.Averaging method
2.Boosting method

What are the types of voting:

1.Soft voting 
2.Hard voting

What are base classifiers:

The base classifier gives an initial prediction of the target class.

What are the advanced methods to ensemble:

1.Bagging 
2.Blending
3.Stacking
4.Boosting

What is XGBoosting:
Extereme Gradient Boosting or XGBoosting is the latest algorithm used in machine learning and is in trend accordingly. XGBoost is a library for developing fast and high performance gradient boosting tree models. That XGBoost is achieving the best performance on a range of difficult machine learning tasks.
