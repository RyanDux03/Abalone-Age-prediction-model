# Report for Assignment 1 - Linear Regression model 

This data set includes information on abalone, a sea snail. The included variables are Sex, Length, Diameter, Height, Whole weight, Shucked weight, Viscera weight, Shell weight, Rings. The target variable is rings for it is used to calculate the age of the abalone.


## Pre-processing Notes and Analysis

This data set had no null values, missing data, or data inconsistencies. There is one categorical variable, Sex, which I encoded.


**Ring size distribution**

<img width="571" height="432" alt="image" src="https://github.com/user-attachments/assets/251dda92-c6c2-4a33-9ea3-2ee9420b8d91" />

**Correlation Matrix**

<img width="623" height="531" alt="image" src="https://github.com/user-attachments/assets/1f4058be-5f21-436d-9e02-d5231e2f0ea3" />


**Model Decisions**
- I opted to use three features, the three with the highest correlation: Shell weight, Diameter, and Height
- For both models, I opted to do a 80/20 train and test split, resulting in the respective data frame sizes
((3340, 3), (836, 3))

## SGDRegressor Model Testing Metrics
**Metrics with max_iter=1000, tol=1e-3**
| Metric                  | Value                   |
| ----------------------- | ----------------------- |
| Coefficients            | \[1.567, -0.260, 0.907] |
| Intercept               | 9.945                   |
| Training R²             | 0.417                   |
| Test MSE                | 6.960                   |
| Test RMSE               | 2.628                   |
| Test MAE                | 1.892                   |
| Test Explained Variance | 0.301                   |
| Test R²                 | 0.301                   |

**Metrics with max_iter=1000, tol=1e-3 and learning_rate = 'optimal'**
- R^2 dropped slightly
- Error metrics improved slightly
  
| Metric                  | Value                   |
| ----------------------- | ----------------------- |
| Coefficients            | \[1.577, -0.418, 0.509] |
| Intercept               | 10.006                  |
| Training R²             | 0.394                   |
| Test MSE                | 6.636                   |
| Test RMSE               | 2.576                   |
| Test MAE                | 1.897                   |
| Test Explained Variance | 0.333                   |
| Test R²                 | 0.333                   |

**Metrics with max_iter=2500, tol=1e-3 and learning_rate = 'optimal'**
- R^2 dropped again
- Error Metrics increased
- Model converges around 1000 iterations, anymore than that increases error metrics

| Metric                  | Value                   |
| ----------------------- | ----------------------- |
| Coefficients            | \[1.869, -0.777, 0.644] |
| Intercept               | 9.338                   |
| Training R²             | 0.366                   |
| Test MSE                | 7.166                   |
| Test RMSE               | 2.677                   |
| Test MAE                | 1.816                   |
| Test Explained Variance | 0.327                   |
| Test R²                 | 0.280                   |

## OLS Model Metrics

Data from summary,

| Metric             | Value |
| ------------------ | ----- |
| R-squared          | 0.417 |
| Adjusted R-squared | 0.417 |
| F-statistic        | 796.8 |
| Prob (F-statistic) | 0.000 |
| No. Observations   | 3340  |
| AIC                | 15530 |
| BIC                | 15560 |
| Durbin-Watson      | 1.999 |
| Condition No.      | 72.3  |

| Variable | Coef | Std Err | t | P>abs(t) | [0.025 | 0.975] |
|----------------|--------|---------|---------|-----|----------|---------|
| const | 5.381 | 0.275 | 19.590 | 0.000 | 4.843 | 5.920 |
| Shell weight | 11.217 | 0.769 | 14.584 | 0.000 | 9.709 | 12.725 |
| Diameter | -2.844 | 1.169 | -2.432 | 0.015 | -5.137 | -0.551 |
| Height | 21.613 | 2.686 | 8.047 | 0.000 | 16.347 | 26.880 |

### Analysis

- R-squared (0.417), Model explains 41.7 percent of variance in Rings
- Adjusted R-squared (0.417), meaning predictors are useful
- F-statistic (796.8), model is statistically significant
- coefficeints, Height has the highest estimated effect on the ring size, followed by shell weight.
- Standard Error, Shell weight was the most precise with a standard error of 0.769
- t-value, Again shell weight had the strongest t-value followed by height and diameter.
- p-value, The p-value for each feature is less than 0.05 indicating statistical significance

### Comparison
<img width="790" height="590" alt="image" src="https://github.com/user-attachments/assets/c0574a4a-c8c2-46b0-808a-6c3ed0a84333" />
