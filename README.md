# Machine-Learning-Process
Overview of the machine learning process

![alt text](https://github.com/nicholasjmorris1993/Machine-Learning-Process/blob/main/machine_learning_pipeline.png)

## Data & Retrieval
This is where queries are run against a database to pull in structured data. Machine learning works directly on table structures.

## Data Processing
This is where:
- text data is tokenized into numbers
- categories are converted into binary form
- missing values are predicted
- outliers are removed from the dataset

## Feature Engineering
This is where:
- domain knowlegde is used to formulate new information (columns) based on the available data we have
- polynomial combinations can be generated to expand the number of columns
- dimension reduction can be done by merging the columns into a smaller set of columns while minimizing information loss
- non-linear information can be extracted and encoded into new columns to make relationships in the dataset more obvious to models

## Feature Scaling
This is where columns are scaled down to smaller numbers so:
- models like Neural Networks can converge
- models like Linear Regression can generate comparable weights
- models like Support Vector Machines can converge quicker
  
Tree models like Random Forest and XGBoost don't need feature scaling because they filter the data instead of navigating a gradient.

## Feature Selection
Models like Lasso Regression, Neural Networks, Random Forest, and XGBoost handle feature selection internally when training. Otherwise, it is wise to use Recursive Feature Elimination to remove the least important columns from the data to speed up training time without sacrificing performance.

