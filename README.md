# Driving Route Risk Modeling and Analysis
This project details the exploratory data analysis, model building / evaluation, and feature analysis contributing to the ranking of riskiest driving routes in the greater Atlanta area. 
The goal of this project is to result in improved driver safety and efficiency for Michelin Connected Fleet.

**Project Report:** [Report](https://github.com/mikecrist/DrivingRouteRisk/blob/main/Report/Report_DrivingRouteRisk.pdf)

## Credits
This project was created for the Georgia Tech Master of Analytics program.<br>

**Course:** Applied Analytics Practicum<br>
**Team:** Michael Crist, Vishal Jada, Hersh Gupta

## Table of Contents
- [Non-Disclosure Information](#Non-Disclosure-Information)
- [Abstract](#Abstract)
- [Conclusions](#Conclusions)
- [Data Sources](#Data-Sources)
- [Citations](#Citations)

## Non-Disclosure Information
This project was sponsored by Michelin Connected Fleet.  Under written agreement with Michelin, no datasets or source code may be shared publicly.  However, the project report is made available [here](https://github.com/mikecrist/DrivingRouteRisk/blob/main/Report/Report_DrivingRouteRisk.pdf).

## Abstract
Complete report [here](https://github.com/mikecrist/DrivingRouteRisk/blob/main/Report/Report_DrivingRouteRisk.pdf).

In this report we detail the exploratory data analysis, model building / evaluation, and feature analysis contributing to the ranking of riskiest delivery routes in the greater Atlanta area. The goal of this report is to result in improved driver safety and efficiency for Michelin Connected Fleet.

We chose to use a supervised learning approach by creating a response variable representing the risk score of a road segment. The models evaluated in the report include Linear Regression, Ridge Regression, Lasso Regression, Elastic Net Regression, KNN Regression, Random Forest Regression, and Neural Net Regression. Random Forest Regression was determined to be the best performing model for predicting risk score. The most important features for predicting risk were number of road lanes, road priority, and speed limit.

***Background***

Based upon National Highway Traffic Safety Administration data, there were approximately 5.2 million reported accidents in the US in 2020, resulting in over 35,000 fatalities (Bieber, 2023). In addition to the disturbing fatalities figure, road incidents cost Americans approximately $340 billion per year in medical expenses, property damage, lost productivity, and traffic congestion (Gopin, 2023).

Michelin Connected Fleet provides the tools and solutions necessary for fleet operators / managers to safely and efficiently manage their fleets, working as a partner to provide recommendations and data insights to reduce cost, improve productivity, and ensure safety of drivers to manage sustainable fleets. Our aim is to define a data-driven approach to calculate a route safety score to inform fleet managers which delivery routes have the highest risk. We look to accomplish the following goals:
1. Explore available data and evaluate metrics for assessing road risk.
2. Build a variety of models to predict risk along a road segment and determine the features that have the greatest impact on road risk.
3. Rank the highest-risk delivery routes in the greater Atlanta area.

The motivation for this project is to provide the necessary analytics to implement intelligent routing for Michelin Connected Fleet, resulting in improved driver safety, reduced liability cost, and improved efficiency.

## Conclusions
The comparative performance among all models is summarized below, using the following metrics:
- R-squared: the proportion of variance in the response that is explained by the model
- RMSE (root mean square error): square-root of the average of the squared error terms
- MSE (mean squared error): average of the squared error terms
- MAE (mean absolute error): average of the absolute values of error terms
  
<p align="center">
  <img width="460" height="250" src="https://github.com/mikecrist/DrivingRouteRisk/assets/31662579/19e080a8-e45c-4e31-833c-3f8046d8e627">
</p>
<p align="center">
  <img width="460" height="500" src="https://github.com/mikecrist/DrivingRouteRisk/assets/31662579/f030f988-fab2-43e4-93fd-bb5c48cc5a26">
</p>
<p align="center">
Results Summary
</p>

**Best Performing Model:** Random Forest (after hyperparameter tuning)<br>

As can be seen in the summary above, the best performing model for predicting risk score was the Random Forest model (after tuning for optimization of hyperparameters). This model had both the lowest RMSE (2.902) and the highest R-squared (0.531). In addition to the Random Forest model, the KNN model performed very well after tuning to optimize hyperparameters, with an RMSE value of 2.971 and R-squared of 0.508.

***Feature Importance***
Because Random Forest was the best-performing model, we will first use the random forest model to evaluate feature importance. Feature importance in a random forest model is murky, as it is not possible to derive a coefficient for each predicting feature (like in linear regression). However, we can look at relative feature importance using the permutation feature importance method. Permutation feature importance is a method of determining feature contribution by determining the decrease in model score when a single feature value is randomly shuffled.

<p align="center">
  <img width="460" height="350" src="https://github.com/mikecrist/DrivingRouteRisk/assets/31662579/a2c513aa-3279-49ca-9d31-fac5423eea48">
</p>
<p align="center">
Feature importance in random forest model
</p>

As can be seen above, the three most important features to the model are: max road lanes, road priority, and speed limit. If these features are left out of the model, we expect a decrease in model score of 0.13, 0.11, and 0.08, respectively. Also important to the model are average road lanes, average speed limit, and max TRI. It appears that max/min arc slope, tunnel, and bridge may not be very important to the random forest model.

In addition to evaluating the feature importance of the random forest model, we also evaluated feature importance using the linear and ridge regression models. Although these models did not perform as well as the random forest model, they can provide some more meaningful interpretation of the feature contribution to risk score by analyzing the regression coefficients for each feature.

<p align="center">
  <img width="650" height="400" src="https://github.com/mikecrist/DrivingRouteRisk/assets/31662579/df54e123-1171-4cdf-998b-6e50cdd841bc">
</p>
<p align="center">
Feature coefficients for linear/ridge/lasso/elastic net regression models
</p>

The ridge regression model has roughly the same relative model coefficients as linear regression (except all coefficients are “shrunk”), so we will focus on coefficients of the linear regression model for ease of explanation. Interestingly, the feature importance in these models seems to defer from the random forest model:
- The feature with the largest regression coefficient is TUNNEL, with a regression coefficient of ~9.0 for linear regression. This means that the presence of a tunnel is expected to increase risk score by 9.0 vs no tunnel present, holding all other features constant. However, this is a binary feature, so the maximum amount it can contribute to risk score is 9.0. This leads us to the conclusion that the presence of a tunnel significantly increases the risk of a road.
- Min and max arc slope were also significant contributors to the model, with coefficients of ~3.3 and ~3.1, respectively. This means that for a unit increase in min/max arc slope, the predicted risk score will increase by 3.3 and 3.1, respectively, holding all other features constant. We conclude that the slope of a road can significantly impact road safety.
- Max road lanes is also a significant contributor to the model. For each unit increase in number of road lanes, we expect risk score to increase by 1.5, holding all other features constant. As such, we conclude that roads with many lanes (such as large highways) can be substantially more dangerous than single-lane roads.
While the random forest model performed best, the problem with random forest is that it is difficult to surmise any clear interpretation of feature contribution to risk score. Although the linear regression model did not perform as well, it allows us to gain more meaningful insights to the contribution of each feature to risk score.

## Data Sources
As mentioned in the [Non-Disclosure Information](#Non-Disclosure-Information), the datasets used in this project are not public information.  However, generic data source descriptions are provided below.

Multiple data sources were used for this project. We utilized the following datasets:
- TRIPS dataset: 173.5GB dataset (1.3B rows, 54 columns) composed of telematics data from Michelin fleets
- EVENTS dataset: 52.7GB dataset (337M rows, 59 columns) composed of Michelin driver telematics data in which a potential safety event occurred (ex: cell phone usage, excessive speeding, etc)
- CRASHES dataset: 6.6MB dataset (70.8K rows, 51 columns) from GA Department of Transportation containing GA public accident data from 2019 to 2023

The Michelin datasets were collected using multiple methods: infrastructures via road scanning assets collection, and fleet drivers via in-app usage. The TRIPS and EVENTS datasets are composed of a wide variety of categorical and numeric features including geographic information, terrain information, and road information such as speed limit, number of road lanes, etc.

## Citations
Bieber, Christy. “Car Accident Statistics for 2023.” *Forbes*, Forbes Magazine, 18 July 2023, www.forbes.com/advisor/legal/car-accident-statistics/.

Gopin, Michael J. “How Much Do Motor Vehicle Crashes Cost Americans Every Year?” *Law Offices of Michael J. Gopin*, PLLC, 23 May 2023, www.michaelgopin.com/blog/how-much-do-vehicle-crashes-cost-americans-every-year/#:~:text=Cost%20of%20Vehicle%20Collisions%20Each,for%20a%20family%20of%20four.
