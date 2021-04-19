# FEMA-Budget-Time-Series-Analysis

# FEMA Disaster Relief Analysis and Budget Forecasting

### Problem Statement
Natural disasters can strike at a moment's notice, leaving little to no time for adequate preparations to be made. This leaves quite the large chore of cleanup and eventually recovery to get back to life as normal. From tornadoes to floods, earthquakes to pandemics, a community can be ravaged and left, literally, out in the cold if recovery costs are not met. The information we hope to present should solve the issue of budget allocation in future disaster recovery scenarios, such that all future funding can be optimized.

**Based on past budgeting and past natural disasters , can a data science model be optimized to predict the future allocation budget for future disasters?**

## Table of Contents
1. To view this analysis, refer to the Project 5 Master Submission notebook.
2. For initial cleanup of the original data file, refer to the Initial Data Cleaning notebook.

## Requirements
To properly run this analysis, the following packages are needed:
- pandas
- numpy
- pyplot, patches from matplotlib
- statsmodels packages including: seasonal_decompose, acf, plot_acf, pacf, plot_pacf, adfuller, ARIMA
- sklearn packages including: mean_squared_error, model_selection, train_test_split


## Data
The data for this project was sourced directly from the FEMA website and can be found at: Public Assistance Funded Projects Details. The dataset provided detailed information about past disasters in the United States and its affiliated territories dating back to August of 1998. For the purposes of this project, the data was broken down into a 10 year set (2011-2020) and two different 5 year sets (2016-2020): one with COVID-19 data intact and one with COVID-19 data removed to provide a best and worst case scenario for 2020. The 10 year data has COVID-19 data intact as well, to determine what effect the pandemic has on a longer scale.

## Data Cleaning & Exploration
Standard data cleaning steps were taken to ensure an ARIMA model could be appropriately implemented to forecast. Unnecessary columns were removed, the date of disaster declaration was converted to date-time format and implemented as the dataframe index and all relevant numerical columns were appropriately reclassified. 

Exploration started with plotting the aggregate funding per state to get an idea of where the impacts of disasters were felt the hardest. The data was then broken down into regional subsets to explore the funding allocations respective to regions of the United States and its territories. The result of these visualizations showed that the American territories were the hardest hit by natural disasters, showing almost double the recovery cost over the next region, the American South. 

## Modeling
Tests for stationarity and autocorrelation were performed to check for any trending or seasonality in the data that needed to be accounted for and corrected. No trend and no seasonality were detected after performing a Dickey-Fuller test and interpreting an autocorrelation plot. Before modeling, the dependent variable was resampled as the sum of all disaster relief efforts per month to have a clear number to work with and avoid any 0 values that may affect the forecast outcome. 

ARIMA(0, 1, 1) models were fit on all datasets after searching to find appropriate values of p and q through a manual gridsearch. All models performed as expected and returned results in line with initial hypotheses.

## Conclusion & Recommendations
For a longer look at forecast budget allocations, a 10 year model projects the lowest needed budget, clocking in at approximately $8.08B when factoring out a once-in-a-lifetime pandemic such as COVID-19. The shorter models of only 5 years both show a projected budget of around $10.39B, and reveal that a large-scale global disaster has little effect on short term FEMA budgeting. If data can be found from the time of previous pandemics, it may lead to more insight into the budget needs for such an event. 

The comparison between the 10 year and 5 year models could be an indicator of the effect of accelerated climate change on the rate of natural disasters and the associated costs of recovery. The world has seen this accelerated rate in recent years and as such, the frequency and intensity of associated disasters, such as hurricanes and disease has intensified as well. Ultimately, the final recommendation would be to budget according to the 5 year model, unless future iterations of this model with new data shows a decrease in the frequency and scale of natural disasters.
