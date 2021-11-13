# Housing_Prices_Regression

## Motivation

Imagine that we are hired as data scientists by a real-estate company. The company has compiled a dataset describing the sale of individual residential property in Ames, Iowa, from 2006 to 2010. Our task is to use the data and build a Machine Learning (ML) model that predicts the price of a house given its characteristics

## Business Objective

The first question we need to ask our employers is what exactly the business objective is. Building an ML model is probably not the end goal. How does the company expect to benefit from this model?

Our employers answer that our model’s output (used for multiple houses in an area) will be fed to another ML system, along with many other signals. This downstream system will determine whether it is worth investing in a given area or not. Getting this right is critical, as it directly affects revenue.

Our employers also informed us that housing prices are currently estimated manually by experts: a team gathers up-to-date information about a house and uses complex rules to come up with an estimate. This strategy is costly and time-consuming, and their estimates are not always excellent; their typical error rate is about 10%.

## Data

The competition uses the Ames Housing dataset, which was compiled by Dean De Cock for use in data science education. The dataset contains 2919 instances/observations and 80 explanatory features describing (almost) every aspect of residential homes in Ames. For the complete list of features, please see the documentation file.

For the Kaggle competition, the dataset has already been split into two sets, which are available as separate CSV files:
1)	train.csv - the training set used for exploring the data and training ML models. It consists of 1460 instances and 81 features. 
2)	test.csv - the test set used for testing our models on unseen data. It consists of 1459 instances and 80 features. 

The discrepancy in the number of features is because the training set is labelled, i.e. it contains a column for the price of each house ('SalePrice'). This column is often termed as the target or response variable. The test set’s target variable (what we usually call y_test) is not directly accessible to us; we can only calculate the error between our predictions and the actual values of the test after submitting our results online.

## Repository Structure

Our approach is divided into two notebooks; one for the Exploratory Data Analysis (01-Exploratory_Data_Analysis.ipynb) and one for pre-processing our data and building ML models (02-Preprocessing_and_Predictions.ipynb).
The datasets (training and test set) are included in a separate folder, along with a sample submission CSV file. This file will be used as a sample to format our submission in a suitable way for valuation by Kaggle’s online system.

## Accuracy Metric

In order to assess the models' accuracy, we will be scoring the models against the Mean Absolute Error (MAE):

## Results

After pre-processing our data, we selected four candidate algorithms (Ridge, Lasso, SVR, and LGBM Regressor). Then, we optimised their performance by performing hyperparameter tuning. The SVR model is the best model with a MAE ~12,788. If we assume the median house price (163,000), we get an error rate ~7.8%. Therefore, the final performance of our system is better than the expert’s price estimates, which are often off by about 10%. Apart from the improved performance, launching this model will free up some time for the experts so that they can work on more interesting and productive tasks.

In terms of the competition, this models puts us at the 94th position (Top 1%) of the leaderboard (as of 11/11/2021).


## References

For a complete list of references, please refer to the end of each notebook. I have used Aurélien Géron’s book to construct the Business Objective section of this file.  



