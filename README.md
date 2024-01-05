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

## Data Sources
As mentioned in the [Non-Disclosure Information](#Non-Disclosure-Information), the datasets used in this project are not public information.  However, generic data source descriptions are provided below.

Multiple data sources were used for this project. We utilized the following datasets:
• TRIPS dataset: 173.5GB dataset (1.3B rows, 54 columns) composed of telematics data from Michelin fleets
• EVENTS dataset: 52.7GB dataset (337M rows, 59 columns) composed of Michelin driver telematics data in which a potential safety event occurred (ex: cell phone usage, excessive speeding, etc)
• CRASHES dataset: 6.6MB dataset (70.8K rows, 51 columns) from GA Department of Transportation containing GA public accident data from 2019 to 2023

The Michelin datasets were collected using multiple methods: infrastructures via road scanning assets collection, and fleet drivers via in-app usage. The TRIPS and EVENTS datasets are composed of a wide variety of categorical and numeric features including geographic information, terrain information, and road information such as speed limit, number of road lanes, etc.

## Citations
Bieber, Christy. “Car Accident Statistics for 2023.” *Forbes*, Forbes Magazine, 18 July 2023, www.forbes.com/advisor/legal/car-accident-statistics/.

Gopin, Michael J. “How Much Do Motor Vehicle Crashes Cost Americans Every Year?” *Law Offices of Michael J. Gopin*, PLLC, 23 May 2023, www.michaelgopin.com/blog/how-much-do-vehicle-crashes-cost-americans-every-year/#:~:text=Cost%20of%20Vehicle%20Collisions%20Each,for%20a%20family%20of%20four.
