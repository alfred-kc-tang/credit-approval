# [SVM and KNN on Credit Approval Data Set](https://alfred-kctang.github.io/credit-approval/)

## Table of Contents

* [Goal](#goal)
* [Data Source](#datasource)
* [Methodology](#methodology)
* [Findings](#findings)
* [License](#license)

## Goal

The goal of this project is to demonstrate the workflow of using k-fold and leave-one-out cross validations to tune the hyperparameters of two common machine learning models, namely Support Vector Machine (SVM) and K-Nearest Neighbor (KNN), and to select the best from them for the credit approval data set.

## Data Source

The data set is obtained from the [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Credit+Approval). However, the data set has been processed to contain data without missing values and categorial variables.

## Methodology

The hold-out method is adopted to in order to have an unbiased estimate of the chosen model's performance; to put it simply, a test set is created from the data that is only used to estimate the performance of the selected model. K-fold cross validation splits the data into k-fold, and then treats one of the folds as validation set at one time and the remaining as training set to predict about the former validation set, where such a procedure is followed k times. By the same token, leave-one-out cross validation makes prediction for a given data point using all the data except the data point itself; that is to say, it treats the data point that the model tries to predict at as being the sole member of the validation set and all the others as being in the training set. In fact, leave-one-out cross validation is a special case of k-fold cross validation, where k equals sample size of the training data. For building the two machine learning models, I used the kernlab and kknn packages in R.

## Findings

![plot of accuracy vs K on KNN in LOOCV](https://github.com/alfred-kctang/credit-approval/blob/master/KNN.png)
![plot of accuracy vs C on SVM in KFCV](https://github.com/alfred-kctang/credit-approval/blob/master/SVM.png)

## License

This repository is covered under the [MIT License](https://github.com/alfred-kctang/credit-approval/blob/master/LICENSE).
