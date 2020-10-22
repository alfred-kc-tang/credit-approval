# [SVM and KNN on Credit Approval Data Set](https://alfred-kctang.github.io/credit-approval/)

## Table of Contents

* [Goal](#goal)
* [Data Source](#data-source)
** [subpoint](#subpoint)
* [Methodology](#methodology)
* [Findings](#findings)
* [Keywords](#keywords)
* [Coding Style](#coding-style)
* [License](#license)

## Goal

The goal of this project is to demonstrate the workflow of using k-fold and leave-one-out cross validations to tune the hyperparameters of two common classification models in machine learning, namely Support Vector Machine (SVM) and K-Nearest Neighbor (KNN), and to select the best from them for the credit approval data set.

## Data Source

### subpoint

The data set is obtained from the [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Credit+Approval). However, the data set has been processed to contain data without missing values and categorial variables.

## Methodology

The hold-out method is adopted to in order to have an unbiased estimate of the chosen model's performance; to put it simply, a test set is created from the data that is only used to estimate the performance of the selected model.

K-fold cross validation splits the data into k-fold, and then treats one of the folds as validation set at one time and the remaining as training set to predict about the former validation set, where such a procedure is followed k times.

Leave-one-out cross validation, on the other hand, makes prediction for a given data point using all the data except the data point itself; that is to say, it treats the data point that the model tries to predict at as being the sole member of the validation set and all the others as being in the training set. In fact, leave-one-out cross validation is a special case of k-fold cross validation, where k equals sample size of the training data.

For building the two machine learning models, I used the kernlab and kknn packages in R.

## Findings

<p align="center">
  <img src="https://github.com/alfred-kctang/credit-approval/blob/master/SVM.png?raw=true" alt="plot of accuracy vs C on SVM in KFCV"/>
</p>

As shown by the above plot, there is no significant difference between linear and polynomial kernels in terms of accuracy, so there is probably a linear pattern in the data. The highest accuracy is attained when C is 0.01 or above. Thus, the best SVM model is built with C = 0.01 with linear kernel, because of its simplicity with comparable performance to models with higher Cs and polynomial kernel.

<p align="center">
  <img src="https://github.com/alfred-kctang/credit-approval/blob/master/KNN.png?raw=true" alt="plot of accuracy vs K on KNN in LOOCV"/>
</p>

The above plot shows that the KNN model performs better on this data set when K >= 5 and using Manhattan distance. Although the highest accuracy is attained with a different K given the randomness, odd number of K is preferred in case that a tie between the two classes exists.

As it turns out, SVM performs better than KNN for this data set. Its performance on the test set is not far from its performance on the training and validation sets during the cross-validations, which is roughly 0.85 on average. It even achieved accuracy of 0.885 in a run, as shown on the [markdown webpage](https://alfred-kctang.github.io/credit-approval/).

## Keywords

classification, Holdout method, k-fold cross validation, K-Nearest Neighbors (KNN), leave-one-out cross validation (LOOCV), Support Vector Machine (SVM), validation

## Coding Style

This projects follows [Google's R Style Guide](https://google.github.io/styleguide/Rguide.html), which is a fork of the [Tidyverse Style Guide](https://style.tidyverse.org/) by Hadley Wickham.

## License

This repository is covered under the [MIT License](https://github.com/alfred-kctang/credit-approval/blob/master/LICENSE).
