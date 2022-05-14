<div align="center">
    <br>
    <img src="Images\Repo_logo.svg" width="600" title="hover text">
    <p>
    <br>This repository contains my approach to the <a href="https://www.kaggle.com/c/home-data-for-ml-course">Housing Prices Competition</a> on Kaggle.
    </p>
    <hr/>
</div>

<p align="center">
    <a href="https://nbviewer.org/github/KOrfanakis/Housing_Prices_Regression/blob/main/01-Exploratory_Data_Analysis.ipynb">
        <img alt="Nbviewer_01" src="https://img.shields.io/badge/Notebook%2301%20-nbviewer-red.svg">
    </a>
    <a href="https://nbviewer.org/github/KOrfanakis/Housing_Prices_Regression/blob/main/02-Preprocessing_and_Predictions.ipynb">
        <img alt="Nbviewer_02" src="https://img.shields.io/badge/Notebook%2302%20-nbviewer-red.svg">
    </a>
    <br/>
</p>

<p align="center">
    <a href="https://www.python.org/">
        <img alt="Made With" src="https://img.shields.io/badge/Made%20with-Python-blue.svg">
    </a>
    <a href="https://jupyter.org/">
        <img alt="Jupyter" src="https://img.shields.io/badge/And%20-Jupyter-orange.svg">
    </a>
    <a href="https://opensource.org/licenses/MIT">
        <img alt="Licence" src="https://img.shields.io/badge/License-MIT-0298c3.svg">
    </a>
    <a>
        <img alt="Star if useful" src="https://img.shields.io/static/v1?label=%F0%9F%8C%9F&message=If%20Useful&style=style=flat&color=darkgreen">
    </a>
    <br/>
</p>

<br>

**Table of Contents**:

<!--ts-->
* [Motivation](#motivation)
* [Business Objective](#business-objective)
* [Data](#data)
* [Repository Structure](#repository-structure)
* [Accuracy Metric](#accuracy-metric)
* [Results](#results)
* [References](#references)
* [Feedback](#feedback)
<!--te-->

<br>

# Motivation

Imagine that we are hired as data scientists by a real-estate company. The company has compiled a dataset describing the sale of individual residential property in Ames, Iowa, from 2006 to 2010. Our task is to use the data and build a Machine Learning (ML) model that predicts the price of a house given its characteristics.

<br>

**Skills**: *Exploratory Data Analysis, Data Visualisation, Data Pre-processing (Missing Value Imputation, Label Encoding, One-hot Encoding, Dealing with Outliers, Feature Engineering, Feature Selection, Feature Scaling), Building Machine Learning Models, Model Tuning*

**Models Used**: *Ridge Regression, Lasso Regression, SVR, LGBMRegressor*

<br>

# Business Objective

The first question we need to ask our employers is what exactly the business objective is. Building an ML model is probably not the end goal. How does the company expect to benefit from this model?

Our employers answer that our model’s output (used for multiple houses in an area) will be fed to another ML system, along with many other signals. This downstream system will determine whether it is worth investing in a given area or not. Getting this right is critical, as it directly affects revenue.

Our employers also informed us that housing prices are currently estimated manually by experts: a team gathers up-to-date information about a house and uses complex rules to come up with an estimate. This strategy is costly and time-consuming, and their estimates are not always excellent; their typical error rate is about 10%.

<br>

# Data

The competition uses the Ames Housing dataset, which was compiled by Dean De Cock for use in data science education. The dataset contains 2919 instances/observations and 80 explanatory features describing (almost) every aspect of residential homes in Ames. For the complete list of features, please see the [documentation file](https://www.kaggle.com/c/home-data-for-ml-course/data?select=data_description.txt).

For the Kaggle competition, the dataset has already been split into two sets, which are available as separate CSV files:
1)	train.csv - the training set used for exploring the data and training ML models. It consists of 1460 instances and 81 features. 
2)	test.csv - the test set used for testing our models on unseen data. It consists of 1459 instances and 80 features. 

The discrepancy in the number of features is because the training set is labelled, i.e. it contains a column for the price of each house ('SalePrice'). This column is often termed as the target or response variable. The test set’s target variable (what we usually call y_test) is not directly accessible to us; we can only calculate the error between our predictions and the actual values of the test after submitting our results online.

<br>

# Repository Structure

Our approach is divided into two notebooks; one for the Exploratory Data Analysis (**01-Exploratory_Data_Analysis.ipynb**) and one for pre-processing our data and building ML models (**02-Preprocessing_and_Predictions.ipynb**).
The datasets (training and test set) are included in a separate folder, along with a sample submission CSV file. This file will be used as a sample to format our submission in a suitable way for valuation by Kaggle’s online system. Finally, our predictions are included as CSV files in the ‘Submission_Files’ folder.

<br>

# Accuracy Metric

To assess the models' accuracy, we will be scoring the models against the Mean Absolute Error (MAE):

<a href="https://www.codecogs.com/eqnedit.php?latex=MAE&space;=&space;\frac{1}{n}\sum_{i=1}^{n}\left&space;|&space;y_{i}&space;-&space;\hat&space;{y}_{i}&space;\right&space;|&space;\newline&space;where&space;\newline&space;y_{i}&space;=&space;actual&space;\:&space;values,&space;\newline&space;\hat&space;{y}_{i}&space;=&space;predicted&space;\:&space;values,&space;and&space;\newline&space;n&space;=&space;number&space;\:&space;of&space;\:&space;instances." target="_blank"><img src="https://latex.codecogs.com/gif.latex?MAE&space;=&space;\frac{1}{n}\sum_{i=1}^{n}\left&space;|&space;y_{i}&space;-&space;\hat&space;{y}_{i}&space;\right&space;|&space;\newline&space;where&space;\newline&space;y_{i}&space;=&space;actual&space;\:&space;values,&space;\newline&space;\hat&space;{y}_{i}&space;=&space;predicted&space;\:&space;values,&space;and&space;\newline&space;n&space;=&space;number&space;\:&space;of&space;\:&space;instances." title="MAE = \frac{1}{n}\sum_{i=1}^{n}\left | y_{i} - \hat {y}_{i} \right | \newline where \newline y_{i} = actual \: values, \newline \hat {y}_{i} = predicted \: values, and \newline n = number \: of \: instances." /></a>

<br>

# Results

After pre-processing our data, we selected four candidate algorithms (Ridge, Lasso, SVR, and LGBM Regressor). Then, we optimised their performance by performing hyperparameter tuning. The SVR model is the best model with a **MAE ~12,788**. If we assume the median house price (163,000), we get an **error rate ~7.8%**. Therefore, the final performance of our system is **better** than the expert’s price estimates, which are often off by about 10%. Apart from the improved performance, launching this model will free up some time for the experts so that they can work on more interesting and productive tasks.

In terms of the competition, this model puts us at the **94<sup>th</sup> position** (**Top 1%**) of the leaderboard (as of 11/11/2021).

<br>

# References

For a complete list of references, please refer to the end of each notebook. I used the book [Hands-On Machine Learning with Scikit-Learn, Keras, and TensorFlow (2nd Ed.)](https://www.oreilly.com/library/view/hands-on-machine-learning/9781492032632/) to construct the Business Objective section of this file.  

<br>

# Feedback

If you have any feedback or ideas to improve this project, feel free to contact me via:

<a href="https://twitter.com/korfanakis">
  <img align="left" alt="Twitter" width="22px" src="https://cdn.jsdelivr.net/npm/simple-icons@v3/icons/twitter.svg" />
</a>

<a href="https://uk.linkedin.com/in/korfanakis">
  <img align="left" alt="LinkedIn" width="22px" src="https://cdn.jsdelivr.net/npm/simple-icons@v3/icons/linkedin.svg" />
</a>
