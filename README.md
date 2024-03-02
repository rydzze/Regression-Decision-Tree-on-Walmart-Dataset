# Walmart Sales Projections – Navigating with Decision Trees

## Original Author

This project is created and maintained by [rydzze](https://github.com/rydzze).

## Introduction

In the retail industry, accurately predicting sales and anticipating demand is crucial for operational success. This project focuses on Walmart's challenge of forecasting sales across its 45 stores. Existing machine learning algorithms have proven inadequate, leading to unforeseen spikes in demand and customer dissatisfaction. The goal is to implement a reliable machine-learning algorithm that predicts sales accurately while incorporating various influencing factors.

## Dataset Description

The dataset includes historical sales data from 45 Walmart stores, featuring store-specific sales records and economic indicators like CPI, Unemployment Index, temperature, fuel price, and holiday flags. Promotional markdown events aligned with holidays like Super Bowl, Labor Day, Thanksgiving, and Christmas are also included.

### Variables
- Store: Store number
- Date: Date of sales data
- Weekly Sales: Sales for the given store weekly
- Holiday Flag: Binary variable for holiday week (1) or not (0)
- Temperature: Temperature on the selling day
- Fuel Price: Price of fuel in the area on the sale day
- CPI: Consumer Price Index
- Unemployment: Prevailing unemployment rate in the region

## Data Preprocessing Steps

Before building the model, data preprocessing steps were taken:
- Checked for null data
- Checked and changed data types if necessary
- Dropped unnecessary columns like Date
- Converted Store, Holiday_Flag, and Week to object types
- Selected Weekly_Sales as the target variable

## Model Building

Three types of decision tree models were built:
1. **Decision Tree Regressor**
2. **Random Forest**
3. **XGBoost**

Models were trained on the training set and evaluated using:
- Mean Absolute Error (MAE)
- Mean Squared Error (MSE)
- Root Mean Square Error (RMSE)
- R2 Score

Hyperparameter tuning was performed to enhance model performance. The model with the best performance on the test set was selected for sales prediction.

## Model Evaluation

### Decision Tree Regressor

![image](https://github.com/rydzze/Regression-Decision-Tree-on-Walmart-Dataset/assets/86187059/3c529cd1-bf9c-4e7f-a350-ee27b06cc756)

The Decision Tree Regressor achieved a perfect fit for the training set, as indicated by all error values being 0 and an R2 score of 1. However, this model showed signs of overfitting, as seen in the distribution plot of actual versus predicted values. Further hyperparameter tuning is necessary to improve generalization.

### Random Forest Regressor

![image](https://github.com/rydzze/Regression-Decision-Tree-on-Walmart-Dataset/assets/86187059/8c5c7eb8-dbab-4c4f-8456-091baee235e8)

The Random Forest Regressor produced impressive results with significant error measurements and an R2 score approaching 1. The model learned well from the training set, but it exhibited some overfitting, as shown by the distribution plot. Hyperparameter tuning will be performed to refine this model.

### XGBoost Regressor

![image](https://github.com/rydzze/Regression-Decision-Tree-on-Walmart-Dataset/assets/86187059/87712062-57f3-4613-8e02-4cd6c5c922c6)

The XGBoost Regressor performed slightly better than the Random Forest Regressor, leveraging its ability to create a model based on a combination of simple models. The distribution plot illustrates that it learned effectively from the training data, with minor signs of overfitting. Overall, the error measurements and R2 score of this model are the best among the initial evaluation, but can be further improved through hyperparameter tuning.

## Hyperparameter Tuning

After the initial evaluation, hyperparameter tuning was performed to improve the decision tree models. Grid search, a technique that creates a discrete grid within the hyperparameters domain, was utilized to identify the optimal combination of values (Malato, 2021). Cross-validation was also carried out to evaluate the performance metrics of the models.

### Decision Tree Regressor

![image](https://github.com/rydzze/Regression-Decision-Tree-on-Walmart-Dataset/assets/86187059/8a9bb958-2400-4d1b-b75e-8e47231fb907)

For the Decision Tree Regressor, the best parameters were found to be a maximum depth of 14 and a minimum number of samples required to split for the internal node is 40. Although the error measurements and R2 score did not match the training results, the distribution plot and low standard deviation indicate that this model can uncover hidden data for improved prediction.

### Random Forest Regressor

![image](https://github.com/rydzze/Regression-Decision-Tree-on-Walmart-Dataset/assets/86187059/fd4432ab-4660-49cf-999d-7bff88b586af)

The Random Forest Regressor's best parameters included a maximum depth of 14 with 50 estimators. There were slight changes in the error measurements and R2 score, resulting in lower performance compared to the initial evaluation. The distribution plot showed similarities to the previous one, suggesting that the model struggled to overcome the overfitting problem. Despite its complexity, the Random Forest Regressor scored excellently in mean and standard deviation in cross-validation.

### XGBoost Regressor

![image](https://github.com/rydzze/Regression-Decision-Tree-on-Walmart-Dataset/assets/86187059/a7839c3a-c46a-4b38-80e6-e0ce9ba4e169)

The XGBoost Regressor showed significant improvement after hyperparameter tuning. The best parameters for this model were a maximum depth of 7 with 75 estimators. Notably, this model minimized the gap between predicted values and actual values in the distribution plot, indicating improved predictive capabilities and ability to uncover relationships in unseen data. Additionally, the model scored impressively in mean and standard deviation, outperforming the other models in this aspect.

## Results and Analysis

During the first evaluation, all decision tree models achieved impressive results, with R2 scores higher than 0.90 and minimized error measurements. However, observation of the distribution plots revealed overfitting issues in each model, prompting the need for hyperparameter tuning.

Through hyperparameter tuning, the Decision Tree Regressor and XGBoost Regressor models improved, while the Random Forest Regressor model showed a slight reduction in error measurements and R2 score. The best parameters for each model were identified using grid search.

| Model                  | Mean Absolute Error | Mean Squared Error    | Root Mean Squared Error | R2 Score   |
|------------------------|---------------------|-----------------------|-------------------------|------------|
| Decision Tree Regressor| 83080.25            | 24089955356.87        | 155209.39               | 0.9252     |
| Random Forest Regressor| 72422.62            | 17902173285.66        | 133799.00               | 0.9444     |
| XGBoost Regressor      | 60300.89            | 9738827842.30         | 98685.50                | 0.9698     |

Based on the results, the XGBoost Regressor model stands out with an R2 score of 0.9698 (or 96.98%), making it the most suitable decision tree model for predicting sales and demand across Walmart's stores in real-world scenarios. Walmart could benefit from implementing this model to enhance sales forecasting and operational planning.

## Contributors

This project was made possible with the contributions of the following individuals:

- [Ariff Ridzlan](https://github.com/rydzze)
- [Nabil Irfan](https://github.com/nabilang)
- [Hafiz](https://github.com/IbnAsmuni)
- Zaher
