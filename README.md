# bike_sharing_case_study

Problem Statement
A bike-sharing system is a service in which bikes are made available for shared use to individuals on
a short term basis for a price or free. Many bike share systems allow people to borrow a bike from a
"dock" which is usually computer-controlled wherein the user enters the payment information,
 and the system unlocks it. This bike can then be returned to another dock belonging to the same system.
A US bike-sharing provider BoomBikes has recently suffered considerable dips in their revenues due to
the ongoing Corona pandemic. The company is finding it very difficult to sustain in the current market scenario.
So, it has decided to come up with a mindful business plan to be able to accelerate its revenue as soon as the
ongoing lockdown comes to an end, and the economy restores to a healthy state.
In such an attempt, BoomBikes aspires to understand the demand for shared bikes among the people after this
ongoing quarantine situation ends across the nation due to Covid-19. They have planned this to prepare themselves
 to cater to the people's needs once the situation gets better all around and stand out from other service
 providers and make huge profits.

They have contracted a consulting company to understand the factors on which the demand for these shared bikes
depends. Specifically, they want to understand the factors affecting the demand for these shared bikes in the
American market.

The company wants to know:
Which variables are significant in predicting the demand for shared bikes.
How well those variables describe the bike demands
Based on various meteorological surveys and people's styles, the service provider firm has gathered a large dataset on daily bike demands across the American market based on some factors.


Business Goal:
You are required to model the demand for shared bikes with the available independent variables.
It will be used by the management to understand how exactly the demands vary with different features.
They can accordingly manipulate the business strategy to meet the demand levels and meet the
customer's expectations. Further, the model will be a good way for management to understand the
demand dynamics of a new market.

steps to create the regression model
1. Load the data
2. cleaning up the data /understanding the data - checking for null, missing, NA values, duplicate values
3. dropping the unnecessary columns like 'instant', 'casual', 'registered' as we already have the total count and that's our target variable.
4. creating the copy of the dataset to keep the main data set available.
5. creating the dummy variable
    * setting the data type of the catgeory variables as 'catgeory'
    * once done we just use get_dummies method from pandas with drop_first=True, dtype = int, to drop the first column
    and data type as int instead of boolean
6. we split the train and test data as per industry standard of 70/30 using train_test_split method and set the seed as 0
and random_state value as a constant to keep the data set same everytime
7. EDA
    * we perform the EDA to see the pattern using pairplot and found the linear relations between temp, atemp and count.
    * created subplot for all the categorical variables and found below observations
        1. Season seem to have good variation, where season 1 seems to have very less booking with median around 2000 against other seasons which has median around 5000, it will have an impact on total bookings cut variable
        2. month also have a good variation, where season6,7,8 ,9, 10 have around 5000 and surely shows some impact on the total bookings cnt variable
        3. weathersit also have a good variation across all 3 categories and median changing from 2000 to 4000 to 5000, will have a decent effect on total bookings cnt
        4. weekday seems to be having similar median booking across all days and seems to have no to less effect on total bookings
        5. workingday seems to be having similar median booking across 2 categories and seems to have no to less effect on total bookings
    * created a heatmap to check the corelation between variables to identify multicolinearity
8.  Performed rescaling using MinMaxscaler function and applied to all the number variables. and fit_transform the data set
9.  created X and Y sets
10. used RFE technique for the features selection and selected top 15 features.
11. started building the linear model using statsmodels api and checking summary and vif
    * removing high P value variables to have a better significance and having better VIF number ( less than 5 )
    * we keep removing variables based on the above condition and keep rebuilding the model
    * once we see all the features having p value less than 0.05 and vif value also less than 5,
        we stop at that to check R2 value and adjusted R2 value to check the quality of the model.
12. validating the assumptions
    * Error terms are normally distributed with mean zero (not X, Y)
    * Residual Analysis Of Training Data
    * making the predictions on the test data
    * calculting the R2 on the test datat to compare it against the train model's R2 number
    * Plotting y_test and y_pred to understand the spread and best fit line
 13. compare the train R-squared vs test R-squared for better insight on how best the model is working on the test data.
