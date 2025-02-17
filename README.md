# Stellar Classification Using Different Algorithms

## Description
A brief overview of the project: What is the main objective of this project?

The main objective of this project is to classify Steller Objects "Stars, "Quasars" and "Galaxy" using Classification algorithm which is a method in Supervised Machine Learning Technique specifically used for Classification or Predicting a target variable with a categorical data. 


## Installation
This project is based on python.

To install these dependencies, you can use `pip`. Below are the commands to install each library:
```pip install pandas, Scikit-Learn, seaborn, matplotlib```


## Data Description

The dataset that is used for this project comes from the space observation of SSDD17, this dataset can be obtained from open-source dataset website. This dataset has 17 labelled featured and 1 labelled target column with 3 classes('Stars', 'Quasars', 'Galaxy'). This data is already cleaned, has no missing values.


## Algorithms Used in this project for Classification

For Classification we have used:

* Decision Tree Classifier- A Decision Tree Classifier is a Supervised Technique to predict a categorical labelled data. The working idea of Decision Tree Classifier algorithm is it works in Greedy Top Down Recursive way, Decision Tree Classifier partitions feature space into parent regions by asking question based on threshold and then it splits the parent region further into child nodes and eventually predicts the class at leaf node. The splitting of nodes is determined by splitting criteria like entropy gain, gini index.

* Random Forest Classifier- A Random Forest Classifier is a supervised machine learning technique is a type of an ensemble learning models that uses multiple decision trees to predict the classes. The Random Forest Classifier trains the decision trees on random samples of data. Each decision tree is trained independently and predicts the class outcome The predicted outcome of Random Forest Classifier is an aggregation from the predicted class of each decision tree that is used to construct a Random Forest.

## Model Optimization

Models are optimized by tuning the sets of hyperparameter by using Grid Search CV method.
Grid Search CV is a finds the combination of best parameters over range of values of hyperparameter of a given model and validates on set of training folds. For our models like Decision Tree Classifier  hyperparameters(splitting criteria, maximum depth, minimum sample leaf, minimum samples split) and for Random Forest Classifier hyperparameters(maximum depth of tree, number of decision tree, minimum sample leaf, minimum samples split) needs to be set. It fits the model on 216 folds for Decision Tree Classifier and 324 fits for Random Forest Classifier and validates on each folds for Decision Tree Classifier and Random Forest Classifier to find out the best set of combination for parameters in Decision Tree Classifier and Random Forest Classifier. The combination with highest average performance metrics on validation dataset is considered to be the best parameters for the model and best model.


## Results
Grid Seach CV helped to achieve the combination of best values for hyperparameters of learning models.

For Decision Tree Classifier the best parameters has a value of splitting criteria: entropy, maximum depth of tree = 10, minimum sample leaf = 4 and minimum samples split = 10

For Random Forest Classifier the best parameters has a value of maximum depth of tree = 20,number of decision tree = 200, number of sample splits = 5 and number of leaf = 1

The final performance of a model for Decision Tree Classifier and Random Forest Classifier is evaluated on Validation Dataset before evaluating on Test Datasets.
Decision Tree Classifier and Random Forest Classifier are able to achieve an accuracy rate of more than 97% for both Validation and Test dataset. 

A Comprehensive Classification Report for both models to measure precision, recall f1 score are given below:

For Decision Tree Classifier-
 

* Galaxy:
precision rate = 0.97, recall rate = 0.99, f1 score = 0.98. 

* Quasars:
precision rate = 0.96, recall rate = 0.92, f1 score = 0.94. 

* Star:
precision rate = 1.0, recall rate = 1.00, f1 score = 1.00.



For Random Forest Classifier-

* Galaxy:
precision rate = 0.98, recall rate = 0.99, f1 score = 0.99.

* Quasars:
precision rate = 0.97, recall rate = 0.93, f1 score = 0.95

* Star:
precision rate = 0.99, recall rate = 1.00, f1 score = 1.00


## Conclusion
This project has optimized the machine learning models well to predict the classes accurately from SSDD17 datasets. The model has achieved accuracy rate of more than 97% in predicting classes on Test Datasets.
