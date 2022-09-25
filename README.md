# Module 15. MechaCar_Statistical_Analysis
## Overview 

The purpose of this project is to review the AutosRUs’ newest prototype ( MechaCar) production data for insights that may help the manufacturing team to solve potential issues. R language is going to be used to perform several statistical tests on the MechaCar_mpg dataset.

## Deliverable 1: Linear Regression to Predict MPG
The goal of this deliverable is to perform multiple linear regression analysis to identify which variables in a dataset predict the mpg of MechaCar prototypes. Some metrics, such as vehicle length, vehicle weight, spoiler angle, and ground clearance, were collected for each vehicle. 
The chart below shows the linear model that predicts the mpg of MechaCar prototypes using variables stated above. Eeach Pr(>|t|) value in the summary represents the probability that each coefficient contributes a random amount of variance to the linear model.


![image](https://user-images.githubusercontent.com/107591542/192155613-f71b8be7-e037-4bff-8d17-b125de4c5653.png)

 

-	Q1. Which variables/coefficients provided a non-random amount of variance to the mpg values in the dataset?

-	A1. 
Th p-value for of vehicle_lenght (2.6 x 10-12), and ground_clearance (5.21 x 10-8) (as well as intercept) is much smaller than the assumed significance level (0 ,05) so, they are  are statistically unlikely to provide random amounts of variance to the linear model. Therefore, I can state that the vehicle_lenght and ground_clearance have a significant impact on mpg. 

-	Q2. Is the slope of the linear model considered to be zero? Why or why not?

-	A2. 

The Pr(>|t|) value in the summary (above) for the intercept is 5.08 x 10-8. It means that the intercept is statistically significant (less than 0,05) and not zero. This would suggest that the intercept term explains a significant amount of variability in the dependent variable when all independent variables are equal to zero.

It could mean that the significant features (such as vehicle_weight and ground_clearance) may need scaling or transforming to help improve the predictive power of the model; or there are other variables tha can help explain the variability of our dependent variable (mpg) that have not included in our model.

-	Q3. Does this linear model predict mpg of MechaCar prototypes effectively? Why or why not?

-	A3. 

As we know, the Multiple R-squared value indicates how well the regression model approximates real-world data points and it is  used as a probability metric to determine the likelihood that future data points will fit the model
In this case, thhe multiple R-squared value is 0.7149 (while the p-value remained significant (very small) which is a strong negative correlation. It means that the model  does an adequate job of predicting mpg. 

## Deliverable 2: Summary Statistics on Suspension Coils
The purpose of this deliverable is to use the MechaCar Suspension_Coil.csv dataset that contains the results from multiple production lots determine if the manufacturing process is consistent across production lots.
The charts below shows summary statistics on the pounds per square inch (PSI) of the suspension coils from the manufacturing lots

 ![image](https://user-images.githubusercontent.com/107591542/192155663-cdc46b62-b7ee-4d8d-b56d-8807789193b4.png)

![image](https://user-images.githubusercontent.com/107591542/192155676-2b2f30cc-ea04-444b-b1bc-c5c44d3be11f.png)

 
-	Q1. The design specifications for the MechaCar suspension coils dictate that the variance of the suspension coils must not exceed 100 pounds per square inch. Does the current manufacturing data meet this design specification for all manufacturing lots in total and each lot individually? Why or why not?

-	A1. 
As we can see in the chart about  all manufacturing lots in total (total_summary) the variance is 62.29 (less than 1000). It means that, in total, the specifications are met.

-	Q2. Does the current manufacturing data meet this design specification for all manufacturing lots in total and each lot individually? Why or why not?

-	A2. 

By examining the mean, median and variance for each lot (lot_summary) to determine if the variance is within the 100 pounds per square inch we can conclude that Lot 1 (mean= 1500, var=0.97 and sd=0,98) and and Lot 2 (mean= 1500, var=7.46 and sd=2.73)  are within specifications.However Lot 3 (mean= 1496, var=170 and sd=13.04) has a variance that exceeds specifications (100 PSI).
It means that the current manufacturing data does not meet this design specification for all manufacturing lots.

## Deliverable 3: T-Test on Suspension Coils
The purpose of this deliverable is to perform t-tests to determine if all manufacturing lots and each lot individually are statistically different
-	Q1. Are all manufacturing lots (and each lot individually)  statistically different from the population mean of 1,500 pounds per square inch.

o	As it is showed below a t.test, for all manufacturing lots was performed. It used  PSI and mu of 1500 in order to evaluate the resulting p-value with a 0.05 level of significance.

![image](https://user-images.githubusercontent.com/107591542/192155733-e41c63a6-7b83-408b-bebf-38cd31356f58.png)

 
All lots are NOT significantly different from the population mean (with a p-value of 0.060)

o	A t.test using subsers to examine the resulting p-value for significance was performed (by lots using subsets) in order to determine if each lot individually are statistically different

It shows that Lot 1 is NOT significantly different from the population mean (with a p-value of 1)

![image](https://user-images.githubusercontent.com/107591542/192155757-1b36dc08-654e-43d9-9053-f6185001a3d5.png)

 
o	Lot 2 is NOT significantly different from the population mean (with a p-value of 0.61)

![image](https://user-images.githubusercontent.com/107591542/192155776-72d10feb-d915-43fa-b8f7-2de5b7d7e270.png)

 
o	Lot 3 IS significantly different from the population mean (with a p-value of 0.042)

![image](https://user-images.githubusercontent.com/107591542/192155792-22712def-bf6d-4d43-9272-2a29ce7c67a5.png)

 
## Deliverable 4: Study Design: MechaCar vs Competitions
The MechaCar_mpg dataset has six columns. Five of them could be independent variables and mpg is the dependent one

![image](https://user-images.githubusercontent.com/107591542/192155798-cd842418-60e1-4644-9ca4-677c6dd7d14a.png)

 
•	To quantify how the MechaCar performs against the competition it would be useful to consider other variables like annual maintenance cost and horsepower ((not in the dataset). Maintenance cost is a very important factor for customers.

•	It would interesting to perform (again) multiple linear regression analysis to identify whether or not these new variables in the dataset predict the mpg of MechaCar prototypes. We could consider annual maintenance cost as a dependent variable to figure out how other variables impact this cost.

•	What is the null hypothesis or alternative hypothesis?

Ho: There is no statistical difference when horsepower is included as independent variable
Ha : There is a statistical difference when horsepower is included as independent variable

Ho: Variables in the data set have a significant impact in maintenance cost
Ha : Variables in the data set do not have a significant impact in maintenance cost

•	What statistical test would you use to test the hypothesis? And why?
We could use simple linear regression -lm() - to predict values for the dependent variable from a independent value in this case horsepower.
However we should use multiple linear regression models -lm()- to predict how much variance in the dependent variable is accounted for in a linear combination of independent variables. In this case mpg or maintenance cost

•	What data is needed to run the statistical test?
Horsepower and annual cost maintenance must be collected and included in the data set to be used in statistical tests

