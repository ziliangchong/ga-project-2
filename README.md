# Predicting house prices in Ames, Iowa

Using the Ames housing data set, we will create a regression model that predicts the prices of houses in Ames, Iowa. The data set consists of features that are continuous, discrete, ordinal, and nominal.

### Goal

We are provided with two separate files, `train.csv` and `test.csv`. For each `Id` in the test set, we must predict the value of the `SalePrice` variable.

### Evaluation

Kaggle leaderboard standings will be determined by root mean squared error (RMSE).

## Contents:
- Data Cleaning
- Exploratory Data Analysis
- Building a Prediction Model
- Exploratory Data Analysis
- Cleaning `test.csv`
- 1st Round of Testing on Test Data
- 2nd Round of Testing on Test Data
- Conclusion

## Conclusion

### Findings

- There were a large number of null values in the dataset. Instead of dropping them, we filled them methodically, always having a logical reason behind why we are filling a certain value in.
- From our data exploration and various modelling using lasso regression, we identified certain features that were especially important to producing good predictions, including:
    - `Gr Liv Area`
    - `Overall Qual`
    - `Garage Area`
    - `Total Bsmt SF`
    - `Neighborhood`
    - `MS SubClass`
- We systematically eliminated numeric features that caused multicollinearity and produced illogical coeffients, and combined this with various sets of nominal features. In the end, the best result was achieved when we put in all the nominal features and allowed the lasso regression to zero out some of them.  
- Although we experimented with feature engineering, we did not manage to engineer useful features. We made interaction terms logically (for example, combining `Total Bsmt SF` and `Bsmt Qual`) but this worsened prediction performance. This could possibly be because the dataset is already complex and multicollinearity was already a factor.

## Limitations

- The large number of null values may have skewed the data in a way we cannot compensate for, even though we tried our best to fill the values logically.
- There is obviously strong multicollinearity among features in the dataset. Although we tried to mitigate this through feature selection and use of regularization, the effect cannot be completely eliminated.
- Certain features are also skewed instead of normally distributed. While we corrected the `saleprice` through log transformation, this is still a factor we have to consider in analyzing our outcomes.
- Lastly, our data may not be homoscedastic as shown by the scatter plots done of the predictions vs real values during our testing on holdout data. In particular, the residuals of the higher-price homes were usually larger.

## Further exploration

- We should explore other common factors that have an impact on property prices, such as:
    - Data about a house's proximity to schooling, shopping malls, or other facilities, similar to the `Condition 1` and `Condition 2` features.
    - Data on the demographic changes in Ames (change in overall city population, change in overall age of population) as the number of people likely to seek a home will influence the property market.
- Even though the feature engineering that was attempted did not pan out, further exploration of potential relationships between features may yet yield a breakthrough. 
