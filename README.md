# Advanced-Data-Science-Final-Project

## Breast Cancer

Frist of all the aim is to explore breast cancer dataset. The features of the dataset are computed from a digitized image of a fine needle aspirate (FNA) of a breast mass. They describe characteristics of the cell nuclei present in the image. This data analysis is useful to predict the breast cancer cells in human body.

### Let see what we have in our data set:

<class 'pandas.core.frame.DataFrame'>
RangeIndex: 569 entries, 0 to 568
Data columns (total 32 columns):

![text_alt](Image/info.png)

So we have 569 records against 32 columns and all of them have 569 non-null records and the data type is float64.

Target columns is the diagnosis

![text_alt](Image/target_column.png)

AS seen in chart the Number of Benign is 357 and Number of Malignant is  212.





### Data Exploration

data visualization, we are going to use seaborn plots. Histgram , Scatter , Violin and finaly heatmap plots usually helps us to understand data easily.

![text_alt](Image/distrbution_of_data.png)

As seen the previous plot Now, we know the distribution for each feature on data we can know is a normal distribution or skewness.

![text_alt](Image/correlation_between_columns.png)

As seen the previous plot can know the correlation between features with target column.



![text_alt](Image/e1_strong_correlation_between_columns.png)

As seen the previous plot that example mean_ columns of heatmap That shown extent correlation between features with target column strong or weak.



### Feature Selection and Classification
In this Section, we will use 3 feature selection techniques and will test them with 2 Classifiers.

#### Following Feature Selection Techniques will be used:

1. Feature Importance
2. Principal component analysis (PCA)
3. Feature Selection by using correlation Heatmap


In Classifications, we will use following 2 Techniques to train our model and predict:

1. Random Forest
2. Support Vector Machine
We choose Random Forest because power to handle a large data set with higher dimensionality. for SVM because ususlly use for two classes.

We gone use F1 performance indicator because better measure of the incorrectly classified cases

And use one technique which helps us to prevent Overfitting:

Cross-validation: In standard k-fold cross-validation, we partition the data into k subsets, called folds. Then, we iteratively train the algorithm on k-1 folds while using the remaining fold as the test set (called the “holdout fold”)..




#### 1- Feature Importance
You can get the feature importance of each feature of your dataset by using the feature importance property of the model. Feature importance gives you a score for each feature of your data, the higher the score more important or relevant is the feature towards your output variable. Feature importance is an inbuilt class that comes with Tree Based Classifiers, we will be using Extra Tree Classifier for extracting the top 15 features for the dataset.


![text_alt](Image/Feature_Importances.png)


Based on Extra Tree/plot that is most 15 importances feature in data.

Random Forsest Accuracy on Test Data: 0.9649122807017544 , F1 : 0.9724770642201834

2-fold cross-validation:
[0.94736842 0.95422535]
The average accuracy of the Random Forest classifier is : 0.95.

![text_alt](Image/Confusion_Matrix.png)

About the Overfit
Moreover, Accuracy gap between training and testing dataset is not wide, so our model isn't overfitting.
If our model does much better on the training set than on the test set, then we’re likely overfitting.Second point we use 2-Cross-validation to prevent overfitting.

Lets test these features with SVM classifier.

Support Vector Machine  Accuracy on Test Data: 0.9649122807017544 , F1 : 0.9722222222222222.




#### 2- Principal component analysis (PCA)
Principal component analysis (PCA) is a technique for reducing the dimensionality https://scikit-learn.org/stable/modules/generated/sklearn.decomposition.PCA.html.

![text_alt](Image/PCA.png)


As shown on the last plot. 11 componants give us high accuracy. We adopt this number.

Random Forsest Accuracy on Test Data: 0.9415204678362573 , F1 : 0.9537037037037037.

Support Vector Machine  Accuracy on Test Data: 0.9649122807017544 , F1 : 0.9724770642201834.




#### 3- Feature Selection by using Correlation Heatmap.
![text_alt](Image/e1_strong_correlation_between_columns.png)
As we seen in the heatmap each two-column show less than 0.9 we selected and the greater than 0.9 we drop one of them.


the columns we going to drop it 'perimeter_mean','area_mean','concave_points_mean','perimeter_sd_error','area_sd_error','radius_worst', 'texture_worst', 'perimeter_worst', 'area_worst' and 'concave_points_worst'are highly correlated.That why we remove it.



Random Forsest Accuracy on Test Data: 0.9766081871345029 , F1 : 0.981651376146789

Support Vector Machine  Accuracy on Test Data: 0.9473684210526315 , F1 : 0.9589041095890412.



let try Deep learning with pca .

#### Deep Learning with PCA.

Activation Functions is relu.

Loss Function is Binary Crossentropy.

optimizer is adam.

We get 0.9590643.






### Summary:
The data is almost normally distributed and it's not skewed. 37% of variables are highly correlated and have similar affect on data.

As we have tested 2 models with 3 feature selection techniques and Random Forest worked best with Feature Importance using Extra Tree Classified feature selection in our case with 20 features.SVM with PCA show the same accuracy but with 11 features and that we will use as our final model.Both of them achived on F1 98.1%

finally, we use a neural network that achieved 96.5%, not bad accuracy. Right !!.

The data is divided into training(70%) and testing(30%) and Random forest model scored well with the testing dataset.
