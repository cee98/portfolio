# Classification of Prematurity using Structural Connectivity


## Problem description:
To predict whether the baby is born preterm from the structural connectivity matrices, which are a measure of connectivity between pairs of brain regions. 

![image](https://github.com/cee98/portfolio/assets/112065175/b95fc54b-7cb4-486b-b794-48db3a473cef)


## Feature variables:
There is 90 regions and matrices have 90x90 values, giving rise to a total of 4005 features.
## Target variables:
1 - premature <br>
0 - term-born

## Programming language:
Python 

## Libraries:
Scikit-learn, Pandas, NumPy, Matplotlib

## Algorithms:
- Principal Component Analysis (PCA)
- Feature Selection using ANOVA F-value (f_classif)
- StandardScaler for feature scaling
- SelectKBest for selecting top k features based on the ANOVA F-value
- Train-test split for splitting the dataset into training and testing sets
- Cross-validation for model evaluation (using cross_val_score and cross_val_predict)
- GridSearchCV for hyperparameter tuning of models

## Models built:
Logistic Regression Classifier and Random Forest Classifier

## Methods of model evaluation
Accuracy, Sensitivity, Specificity, Recall

## Summary of Results:

![image](https://github.com/cee98/portfolio/assets/112065175/e089a5ea-fa0c-4052-944c-a5d33ce91596)

In comparing the test set results across different classifiers and feature selection techniques, the following observations can be made:

Logistic Regression Classifier:<br>
Accuracy: 0.94<br>
Sensitivity: 0.76<br>
Specificity: 0.99<br>
Mean recall: 0.88<br>

Logistic Regression Classifier with SelectKBest:<br>
Accuracy: 0.93<br>
Sensitivity: 0.76<br>
Specificity: 0.97<br>
Mean recall: 0.87<br>

Random Forest Classifier:<br>
Accuracy: 0.84<br>
Sensitivity: 0.65<br>
Specificity: 0.89<br>
Mean recall: 0.77<br>

Random Forest Classifier with SelectKBest:<br>
Accuracy: 0.86<br>
Sensitivity: 0.71<br>
Specificity: 0.90<br>
Mean recall: 0.80<br>

From these results:<br>

- Logistic Regression Classifier exhibits the highest accuracy and specificity among all models, indicating its effectiveness in correctly classifying instances and distinguishing between classes.
- Random Forest Classifier, while having decent accuracy, shows lower sensitivity compared to Logistic Regression, suggesting it may misclassify positive instances more often.
- Feature selection using SelectKBest did not significantly improve the performance metrics in this scenario. However, it slightly affects the accuracy and specificity of both classifiers.
- Despite the Random Forest model having slightly lower accuracy and sensitivity, both models have comparable cross-validation scores, indicating similar generalization performance, when compared to both logistic regression classifiers which exhibit overfitting.
- Overall, Logistic Regression Classifier performs the best in terms of accuracy and specificity, making it a suitable choice for this classification task.

## Limitations:
- There were a large number of features compared to the number of samples, so the classifiers were prone to overfitting.
- The dataset used was unbalanced so the smaller class (preterm) will be more difficult to predict correctly.


