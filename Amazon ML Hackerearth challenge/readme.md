This was a competition held by Amazon India in Hackerearth.

The objective of this competition was to predict the customer type given some data relating to the customers.

Approach - 

1. EDA
I plotted KDE plots for the given data. KDE plots allowed me to inspect the different distributions of the features.
I ploted the KDE seperately for the two customer classes. The KDE allowed me to see which features were correlated and hence could be of importance. By seeing the distributions on the same graph, I found that customer_ctr_score, customer_stay_score , customer_product_variation_score had distinct distributions and so the algorithms would be able to leverage these features.
To confirm this I also checked the correlations of the different features to the Target feature (customer_category).

After this I further created the KDE of test and train data for the same variables. This is important as it roughly lets us know the distribution of the Train and test data. In this case the KDE's matched almost perfectly and so the distributions were likely the same and the data split was good.

2. Data Cleaning.

I cleaned the data by imputing the null values by mean or mode as most of the columns did not have a lot of missing data. I didnt bother creating seperate columns (which indicated whether a feature was imputed or no) though now that I think of it, could have helped.

3. Model Creation and Training

I then created dummy variables and fit the data to a RF classifier with 10000 trees and trained with stratified K fold.
I chose 4 folds.

I tweaked the parameters by hand (without hyperopt or grid search).
It gave an average precision score of 0.97 and an F1 of 0.88.

This was a good starter model.

The second model I tried was a LGBM.
