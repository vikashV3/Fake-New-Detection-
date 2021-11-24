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

### File descriptions

#### DataPrep.py
This file contains all the pre processing functions needed to process all input documents and texts. First we read the train, test and validation data files then performed some pre processing like tokenizing, stemming etc. There are some exploratory data analysis is performed like response variable distribution and data quality checks like null or missing values etc.


### Logistic Regression 

<p align="center">
  <img width="600" height="50" src="https://github.com/vikashV3/Fake-New-Detection-/blob/main/Accuracy2.PNG">
</p>

<p align="center">
  <img width="600" height="350" src="https://github.com/vikashV3/Fake-New-Detection-/blob/main/LogisticRegression.PNG">
</p>

### Random Forest

<p align="center">
  <img width="600" height="50" src="https://github.com/vikashV3/Fake-New-Detection-/blob/main/Accuracy1.PNG">
</p>

<p align="center">
  <img width="600" height="350" src="https://github.com/vikashV3/Fake-New-Detection-/blob/main/RandomForest.PNG">
</p>

### Ensemble Technique 

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
