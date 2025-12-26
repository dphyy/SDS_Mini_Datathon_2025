# NUS SDS Mini Datathon 2025
This competition is hosted by NUS Statistics and Data Science Society. In this edition, our goal is to predict medical insurance charges from a dataset with 1338 observations and 7 variables while providing insights on the different feature variables. Our team decided to perform our analysis in R.

**Team Name:** Misters

**Team Members:**

  * Julian
  * James

## Our Approach
  1. Data Cleaning
  2. Exploratory Data Analysis (EDA)
  3. Regression and Modelling
  4. XGBoost Decision Tree Model
  5. Fairness Analysis
  6. Personal Reflection

## Data Cleaning
We started our data cleaning by removing observations with at least one missing value and removed all duplicated values. In our case, there was a duplicated value which had exactly the same values across all variables. Following which, we performed one-hot encoding on the `region` variable. This allows us to train more accurate machine learning model to predict our outcome variable, `charges`.

## EDA
### Checking for Outliers

We plotted a distribution curve for both `charges` and `bmi` to decide if we should remove any outliers. Based on the visualisation and our domain knowledge, we decided not to remove any outliers as outliers in `charges` are normal due to the factors such as severity of incident, type of incident and coverage limits. We also did not remove any outliers in `bmi` as it is unlikely to exclude people with high BMI from insurance if they purchased the insurance since young.

### Checking relationship between variables

By making use of both boxplots and scatterplots, we plotted data visualisations between variables such as `charges`, `sex`, `children`, `smoker`, `region`, `age` and `bmi` to try and uncover any relationships between variables. Additionally, by making use of correlation coefficients and chi-square test, we checked if there was any significant association between any variables. We realised that there is a statistically significant association between `sex` and `smoker`.

## Regression and Modelling

Before running a linear regression model on our dataset, we made use of the `regsubsets()` function with backward elimination to perform variable selection and identified the best model which for this case, excluded `sex` as a feature variable. By making use of a 70/30 train-test split, we fit the model to the training data and evaluated the accuracy using out-of-sample root mean squared error. We plotted a predicted vs actual charges scatterplot to visualise the accuracy.

## XGBoost Decision Tree Model

Similarly, we fitted our train data to a XGBoost model and evaluated its accuracy using out-of-sample root mean squared error and plotted a predicted vs actual charges scatterplot to visualise the accuracy. Using this model, we realised that our out-of-sample accuracy improved by 23%. Additionally, we performed a feature importance to assess which feature variable affects `charges` the most. We found that `smoker` had the highest contribution to `charges`.

## Fairness Analysis

We assessed fairness of `charges` across `sex` and `region`. Firstly, we made use of the boxplots and p-values to evaluate if difference in `charges` is significant across `sex`. Following which, we performed a Kruskal-Wallis test across `region` to check for fairness. By combining the different regions, we are also able to compare `charges` across a more generalised `region` such as North vs South and East vs West. By making use of the p-value from the Kruskal-Wallis test, we conclude that `charges` across East and West is statistically significant at 5% significance level, indicating possible unfairness.

## Personal Reflection

This was my first experience joining a datathon, with no clear expectations of what was needed. This was a very enriching experience and I learnt a lot. Firstly, when creating data visualisation, I realised that more effort should be placed into the design so that it looks aesthetically pleasing and not as plain. This can be done using `ggplot2` colour palatte. Additionally, more work should be put in designing the presentation slides to both capture only the key insights and making it look aesthetic. Secondly, when performing variable selection with linear regression, it should be carried out on the train data only instead of the whole dataset. Last but not least, we should have also explored tuning the hyperparameters for our XGBoost decision tree model to improve accuracy. Overall, it was a enjoyable experience which made me want to learn more about data analysis and more machine learning models!
