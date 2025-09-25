# Car Sales Forecasting Project

## Project Overview
The purpose of this project is to analyze and forecast car sales using Excel and Python.  
This project demonstrates key skills in time series forecasting, scenario analysis, and correlation analysis between customer demographics and vehicle prices.  

**Tools Used:**  
- Excel (forecasting, what-if scenarios, correlation analysis)  
- Python (forecasting models, validation, visualization)  

---

## Objectives
1. **Sales Forecasting**  
   Predict future car sales using Excel’s built-in forecasting tools and Python time series models.  

2. **What-If Scenario Analysis**  
   Simulate different business scenarios, such as price increases or changes in sales growth, to assess their potential impact.  

3. **Correlation Analysis**  
   Explore whether there is a relationship between customers’ annual income and the price of the vehicles they purchase.  

---

## Dataset
- **Source:** [Car Sales Dataset](https://www.kaggle.com/datasets/missionjee/car-sales-report)
- **License:** [Apache License 2.0](http://www.apache.org/licenses/LICENSE-2.0)  
- **Main Variables:**  
  - `Car_id`  
  - `Date`  
  - `Customer Name`  
  - `Gender`  
  - `Annual Income`  
  - `Dealer_Name`  
  - `Company`  
  - `Model`  
  - `Engine`  
  - `Transmission`  
  - `Color`  
  - `Price ($)`  
  - `Dealer_No`  
  - `Body Style`  
  - `Phone`  
  - `Dealer_Region`  

---

## Methodology
### 1. Data Cleaning
- Remove duplicates and missing values  
- Convert `Date` into proper datetime format  
- Standardize numerical columns such as `Annual Income` and `Price ($)`  

### 2. Forecasting
- Excel: `FORECAST.ETS()` and trendlines  
- Python: ARIMA / Prophet models for time series prediction  

### 3. Scenario Analysis (Excel What-If)  
- Price increase simulation (e.g., +5%, +10%)  
- Sales growth sensitivity analysis  

### 4. Correlation Analysis
- Pearson correlation between `Annual Income` and `Price ($)`  
- Scatter plots with regression lines  

---

## Results
- Forecast charts showing projected car sales  
- Scenario analysis tables for business decisions  
- Correlation insights (positive, negative, or no relationship)  

---

## Learnings & Next Steps
- Demonstrated ability to forecast sales and analyze scenarios in Excel and Python  
- Learned how to connect customer demographics with vehicle pricing  
- Next steps: extend the model with external factors (fuel prices, interest rates, macroeconomic indicators)  

---

## License
The dataset used in this project is provided under the [Apache License 2.0](http://www.apache.org/licenses/LICENSE-2.0).
