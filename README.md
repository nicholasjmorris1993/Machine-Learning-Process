# Machine-Learning-Process
Overview of the machine learning process. 
  
This covers supervised machine learning. In the picture below there should be arrows going from **Deployment** to **Model Tuning** and to **Data Processing**, for when performance in deployment is poor.

![alt text](https://github.com/nicholasjmorris1993/Machine-Learning-Process/blob/main/machine_learning_pipeline.png)

## Data & Retrieval
This is where queries are run against a database to pull in structured data. Machine learning works directly on table structures.

## Data Processing
This is where:
- multiple tables are combined into one table
- text data is tokenized into numbers
- categories are converted into binary form
- missing values are predicted
- outliers are removed from the dataset

## Feature Engineering
This is where:
- domain knowledge is used to formulate new information (columns) based on the available data we have
- polynomial combinations can be generated to expand the number of columns
- dimension reduction can be done by merging the columns into a smaller set of columns while minimizing information loss
- non-linear information can be extracted and encoded into new columns to make relationships in the dataset more obvious to models

## Feature Scaling
This is where columns are scaled down to smaller numbers so:
- models like Neural Networks can converge
- models like Linear Regression can generate comparable weights
- models like Support Vector Machines can converge quicker
  
Tree models like Random Forest and XGBoost don't need feature scaling because they filter the data.

## Feature Selection
Models like Lasso Regression, Neural Networks, Random Forest, and XGBoost handle feature selection internally when training. Otherwise, it is wise to use Recursive Feature Elimination to remove the least important columns from the data to speed up training time without sacrificing performance.

## Modeling
Good options for modeling are:
- XGBoost
- Neural Networks
- Random Forest
- Support Vector Machines
- Lasso Regression

## Model Tuning
The most common way to tune a machine learning model is with a Grid Search. 
1. In a Grid Search, a variety of parameter combinations is generated for a single model.
2. Then each parameterization is trained on 60% of the data.
3. Then each parameterization is asked to predict on 20% of the data, which it did not see during training.
4. Those predictions are used to score the performance on unseen data.
5. The top-performing parameterizations are then retrained on 80% of the data (the original 60% and the 20% used for scoring performance).
6. Finally, the top-performing parameterizations are scored on the last 20% of the data, which they haven't seen at all.
7. The best performer is the model for deployment, and gets retrained on all the data before deployment.

## Deployment
In deployment there are specification limits that the model must adhere to at all times. When the model consistently fails to meet the specs, then the model must be sent back to **Model Tuning** or **Data Processing**. The definition of consistently failing is based on Control Chart diagnostics which including drifting, a number of direct violations in a row, and fraction of time spent deviating near the limits.
