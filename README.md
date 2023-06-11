###  Regression Model Building for Used Car Price Prediction

Abstract:
This code implements data cleaning techniques and builds a regression model for predicting the price of used cars. The dataset used is 'quikr_car.csv'. The code performs various data cleaning tasks to address problems related to null values, data types, and outliers in the dataset. It utilizes libraries such as pandas, numpy, seaborn, and matplotlib for data manipulation, visualization, and regression model building.

## Data Cleaning
The code begins by importing the necessary libraries, including` pandas`, `numpy`, `seaborn`, and `matplotlib`. It then loads the dataset into a `pandas DataFrame` named car using the `read_csv()` function. Basic exploratory analysis is performed using methods like `head()`, `shape`, `describe()`, `info()`, and `isnull().sum()` to identify potential issues in the data.

## Identifying Problems

The code focuses on specific columns of interest, such as `year`, `kms_driven`, `Price`, and `fuel_type`, to identify problems within them. For instance, it checks the unique values of the year column and discovers non-relevant data and the column being of object type. Similarly, it investigates the unique values in `kms_driven` and `Price` columns, identifying issues related to non-relevant data and object data type.

## Data Cleaning Operations

To address the identified problems, the code creates a backup copy of the original DataFrame. It then performs specific cleaning operations for each column. For the Price column, commas are removed using the `str.replace()` method, and the column is converted to numeric type using `pd.to_numeric()`. Non-numeric rows are dropped using `dropna()`, and the column is finally converted to integer type. Similarly, the year column is cleaned by removing non-numeric values and converting it to an integer type.

## Cleaning kms_driven and fuel_type

The code focuses on the `kms_driven` column, splitting the string values and extracting only the numeric part. It removes commas, filters out non-numeric rows, and converts the column to integer type. Null values in the `fuel_type` column are removed by excluding the corresponding rows using `~car['fuel_type'].isna()`.

## Modifying name column
The code modifies the name column by keeping only the first three words using `str.split()`, `str.slice()`, and `str.join()` methods. This ensures that only relevant information is retained.

## Outlier Removal

An outlier is detected in the Price column, and the code filters out rows where the price is greater than or equal to 6 million, resulting in a cleaned DataFrame.

## Model Building
The code proceeds to build a regression model for predicting used car prices. The input features (x) are obtained by dropping the Price column, while the target variable (y) is set as the Price column. The dataset is split into training and testing sets using `train_test_split()`. The model chosen for regression is Linear Regression from the sklearn library. One-hot encoding is applied to categorical columns `(name, company, and fuel_type)` using `OneHotEncoder` and `make_column_transformer`. The regression model is then fitted using the training data.

## Model Evaluation
The trained model is used to predict the prices for the test data, and the predictions are evaluated using the `r2_score` metric. Multiple iterations of the train-test split are performed to find the optimal random state for the highest r2_score. The model is retrained using the optimal split and evaluated again. Finally, the trained model is saved using pickle for future use.


## Price Prediction

A sample input is created using the required features, and the trained model is used to predict the price of the car.

In summary, this code demonstrates the data cleaning process for a used car dataset and builds a regression model for predicting car prices. It highlights the steps involved in handling null values, converting data types, and addressing outliers. The final trained model can be used to predict the price of a used car based on the provided features.

![image](https://github.com/saqib772/Car_Price_Prediction/assets/121972215/c3924fb6-b5b8-48c2-bae1-d9a812fb8847)

