## Abstract
A minimum root mean square error of 0.3769 was obtained on the validation dataset with a Stacked Regressor model to predict the sale price of a house with the Kaggle dataset. A total of nine different supervised models were used. Grid search was also used to for hyper-parameter tuning of some of the models. Root mean square error and cross validation scores were used to evaluate the models. Stacked regressor model was formed by stacking Random forest, Support vector regressor, K -nearest neighbour regressor and ridge regressor model with random forest as the final estimator. Stacked Regressor model helped to improve the performance of all its constituent models.

## Introduction
Predicting house prices is an important objective. Recent studies have found that asset prices can help to forecast output and inflation. Changes in housing prices can provide knowledge about consumption and inflation. In the business cycle, housing market play an important role.  Studying Housing sales and prices is necessary to understand demand and supply.

Models that can forecast housing prices can provide policy makers and economists with an idea about the future economy and therefore, help them design better policies. It can also help economists to estimate prepayments, housing mortgage and housing affordability.  In recent years, machine learning has become a popular approach to predict house prices based on its attributes. Predicting house prices is usually approached as a regression problem.

## Dataset
The housing dataset is available on Kaggle under “House Prices: Advanced Regression Techniques”. The “train.csv” file contains the training data and “test.csv” contains the testing data. The training data contains data for 1460 rows which corresponds to 1460 house’s data and   80 columns which correspond to the feature of those houses. Similarly, the testing data contains data of 1461 houses and their 79 attributes.  

## Feature Engineering
- A Jupyter notebook with Python kernel was used to perform all the tests. Sklearn was the primary library used for all data modelling and optimisation. Pandas and NumPy library were also frequently used for data loading, manipulation and transformation. Seaborn and matplotlib were used to plot visualisations.

- Given a large dataset, pre-processing the data was an important task. First the Id column was dropped from the features because it is not required for prediction. Scatter plot was used to check for any large outliers which may lead to biased predictions. “GrLivArea” which is the second most correlated column to the label was found to have outliers. The data points between “GrLivArea” greater than 4000 and sale price less than 300,000 were deleted in order to prevent skewed predictions. Similarly, for the data points where “EnclosedPorch” is greater than 400  and  sale price  greater  that    700,000
were removed. 

- The sale is highly skewed with a positive skewness of 1.56. Therefore, log transformation was applied to the sale price for prediction. 
Variables with more than 90 percent missing data were removed from both the testing and training set. Since “Utilities” had only one unique value, it was also dropped. For rest of the variables, the values were filled after studying what information the feature held. For example, null values for the column “Fence” most likely meant that the house had no fence. So, it was filled as “None”. Similarly, for other categorical features like ‘FireplaceQu’, ‘MasVnrType’, 'MSSubClass', 'GarageType', 'GarageFinish', 'GarageQual', 'GarageCond', 'BsmtQual', 'BsmtCond', 'BsmtExposure', 'BsmtFinType1' and 'BsmtFinType2', the empty values were filled as “None”. For numerical features like 'GarageCars' which meant there is most likely no garage therefore no garage, the null entries were filled as 0. For features like 'Electrical', 'SaleType', 'KitchenQual' etc which had very few null values, the empty values were filled with the most recurrent data in the column. Lot frontage, which means the feet of street connected to property, would most likely be similar to the neighbourhood houses, so the median value of this column was filled into the null values of this column.

- New columns were added to the data frame such as total surface, total bathrooms, total porch surface, total square feet and total quality. Dummy values were obtained for all the categorical features as otherwise they cannot be used for data modelling. Only numerical features can be used for regression modelling. Training and testing data were aligned to have the same columns. After all the feature engineering, the training data was split to 70 percent training and 30 percent validation set. This was done to be able to estimate the model accuracy on validation set. 

## Data Modelling
A total of nine different models were used for prediction.Root mean square error and k-fold cross validation were the primary metrics used for evaluating the models. 

#Model,	RMSE on validation set,  Mean CV Score

- Linear Regression:	0.42793480397157035,0.4752199075347933

- Ridge:	0.3957886167433282,0.4167270749625921

- Lasso:	0.4059493256188701, 0.4297643272515321

- K- Nearest Neighbour: 0.41351487769327555
	
- Decision Tree:	0.4583579345988703 , 0.45825272349446555

- Random Forest:	0.38616747296757176, 0.403804172243945

- Support Vector Regressor:	0.3900469727418305, 0.40963206887105647

- Gradient Boosting Regressor:	0.4118219430457788, 0.4292489907640939

- Stacked Regressor:	0.3769718491202983, 0.4093903027876036

From the cross-validation error scores, it can be observed that the random forest and stacked regressor model have the lowest error.  The root mean square error of stacked regressor is the lowest. Scatter plots were also observed between the actual values and predicted values. Overall, it is observed that the stacked regressor model showed improved performance compared to the performance of all the other models used as estimators for this model.

