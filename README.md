# Prototype-Selection-for-Nearest-Neighbors
One way to speed up nearest neighbor classification is to replace the training set by a carefully chosen subset of “prototypes”. Think of a good strategy for choosing prototypes from the training set, bearing in mind that the ultimate goal is good classification performance on test data. Assume that 1-NN will be used. Then implement your algorithm, and test it on the MNIST dataset, available at: http://yann.lecun.com/exdb/mnist/index.html

## KDTree + XGBoost Submission - Binary Image Classification Model for Poverty Map Dataset by WILDS

XGBoost stands for eXtreme Gradient Boosting. In this submission, the model is built on the base KDTree + XGBoost model given by the TA, for the given binary classification task. 

### Trained the KD Tree on higher number of images (1000)

Encoded the whole dataset

### Added nightlight in the features

### One-Hot Encoding for the Countries
The KDTree encoder was saved in a pickel file

### Data Split into Urban and Rural and run separate models

### Tuning the hyperparameters
#### Training split: 80:20 to tune hyperparameters

We tuned the hyper paramters of the XGBoost classifier. Specifically, changing the following hyperparameters:

- train_ratio: 0.9
- ensemble_size: 20
- max_depth: 10
- eta: 0.01
- verbosity: 0
- objective: 'binary:logistic'
- nthread: 7
- eval_metric: ['error', 'logloss']
- num_round': 100
- gamma: 0.1
- subsample: 1
- min_child_weight: 3
- alpha: 0
- seed: 0

We split the data into train and test with the ratio of 9:1 and ran the code for 20 iterations. Then, we kept the maximum depth of the tree as 10 since keeping this value as too high can lead to overfitting. Then, the learning rate we used in our model is 0.01 as the higher learning rate of 0.3 does not fit the model very well. The loss function to be minimized has been used as the binary:logistic that is, logistic regression for binary classification, which returns predicted probability (not class). This is preferably used for a binary classification problem. The evaluation metrics used for the model are the negative log likelihood, and binary classification error rate. We tuned the hyperparameter gamma to be 0.1 which specifies the minimum loss reduction required to make a split. For inducing regularization, we have used the alpha hyperparameter which tunes the L1 regularization. Also, we kept a seed value in order to reproduce the results.
