# Housing_Prices_Regression

This repository contains my approach to the [Housing Prices Competition](https://www.kaggle.com/c/home-data-for-ml-course) on Kaggle.

<br>

<p align="center">
  <img src="https://images.unsplash.com/photo-1524813686514-a57563d77965?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1332&q=80" width="700" title="hover text">
</p>
<p align="center">
  <em>Photo by Tom Rumble (Unsplash)</em>
</p>

**Table of Contents**:

<!--ts-->
* [Motivation](#motivation)
* [Business Objective](#business-objective)
* [Data](#data)
* [Repository Structure](#repository-structure)
* [Accuracy Metric](#accuracy-metric)
* [Results](#results)
* [References](#references)
<!--te-->

<br>

## Motivation

Imagine that we are hired as data scientists by a real-estate company. The company has compiled a dataset describing the sale of individual residential property in Ames, Iowa, from 2006 to 2010. Our task is to use the data and build a Machine Learning (ML) model that predicts the price of a house given its characteristics

<br>

## Business Objective

The first question we need to ask our employers is what exactly the business objective is. Building an ML model is probably not the end goal. How does the company expect to benefit from this model?

Our employers answer that our model’s output (used for multiple houses in an area) will be fed to another ML system, along with many other signals. This downstream system will determine whether it is worth investing in a given area or not. Getting this right is critical, as it directly affects revenue.

Our employers also informed us that housing prices are currently estimated manually by experts: a team gathers up-to-date information about a house and uses complex rules to come up with an estimate. This strategy is costly and time-consuming, and their estimates are not always excellent; their typical error rate is about 10%.

<br>

## Data

The competition uses the Ames Housing dataset, which was compiled by Dean De Cock for use in data science education. The dataset contains 2919 instances/observations and 80 explanatory features describing (almost) every aspect of residential homes in Ames. For the complete list of features, please see the documentation file.

For the Kaggle competition, the dataset has already been split into two sets, which are available as separate CSV files:
1)	train.csv - the training set used for exploring the data and training ML models. It consists of 1460 instances and 81 features. 
2)	test.csv - the test set used for testing our models on unseen data. It consists of 1459 instances and 80 features. 

The discrepancy in the number of features is because the training set is labelled, i.e. it contains a column for the price of each house ('SalePrice'). This column is often termed as the target or response variable. The test set’s target variable (what we usually call y_test) is not directly accessible to us; we can only calculate the error between our predictions and the actual values of the test after submitting our results online.

<br>

## Repository Structure

Our approach is divided into two notebooks; one for the Exploratory Data Analysis (**01-Exploratory_Data_Analysis.ipynb**) and one for pre-processing our data and building ML models (**02-Preprocessing_and_Predictions.ipynb**).
The datasets (training and test set) are included in a separate folder, along with a sample submission CSV file. This file will be used as a sample to format our submission in a suitable way for valuation by Kaggle’s online system.

<br>

## Accuracy Metric

In order to assess the models' accuracy, we will be scoring the models against the Mean Absolute Error (MAE):

<a href="https://www.codecogs.com/eqnedit.php?latex=MAE&space;=&space;\frac{1}{n}\sum_{i=1}^{n}\left&space;|&space;y_{i}&space;-&space;\hat&space;{y}_{i}&space;\right&space;|&space;\newline&space;where&space;\newline&space;y_{i}&space;=&space;actual&space;\:&space;values,&space;\newline&space;\hat&space;{y}_{i}&space;=&space;predicted&space;\:&space;values,&space;and&space;\newline&space;n&space;=&space;number&space;\:&space;of&space;\:&space;instances." target="_blank"><img src="https://latex.codecogs.com/gif.latex?MAE&space;=&space;\frac{1}{n}\sum_{i=1}^{n}\left&space;|&space;y_{i}&space;-&space;\hat&space;{y}_{i}&space;\right&space;|&space;\newline&space;where&space;\newline&space;y_{i}&space;=&space;actual&space;\:&space;values,&space;\newline&space;\hat&space;{y}_{i}&space;=&space;predicted&space;\:&space;values,&space;and&space;\newline&space;n&space;=&space;number&space;\:&space;of&space;\:&space;instances." title="MAE = \frac{1}{n}\sum_{i=1}^{n}\left | y_{i} - \hat {y}_{i} \right | \newline where \newline y_{i} = actual \: values, \newline \hat {y}_{i} = predicted \: values, and \newline n = number \: of \: instances." /></a>

<br>

## Results

After pre-processing our data, we selected four candidate algorithms (Ridge, Lasso, SVR, and LGBM Regressor). Then, we optimised their performance by performing hyperparameter tuning. The SVR model is the best model with a **MAE ~12,788**. If we assume the median house price (163,000), we get an **error rate ~7.8%**. Therefore, the final performance of our system is **better** than the expert’s price estimates, which are often off by about 10%. Apart from the improved performance, launching this model will free up some time for the experts so that they can work on more interesting and productive tasks.

In terms of the competition, this models puts us at the **94<sup>th</sup> position** (**Top 1%**) of the leaderboard (as of 11/11/2021).

<br>

## References

For a complete list of references, please refer to the end of each notebook. I have used Aurélien Géron’s book to construct the Business Objective section of this file.  



