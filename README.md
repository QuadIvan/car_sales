# Car Sales Forecasting Project

## Project Overview
The purpose of this project is to analyze and forecast car sales using **Excel**.  
This project demonstrates key skills in time series forecasting, scenario analysis, and correlation analysis between customer demographics and vehicle prices.  

**Tools Used:**  
- Excel (forecasting, what-if scenarios, correlation analysis)  

---

## Objectives
1. **Sales Forecasting**  
   Predict future car sales using Excel’s built-in forecasting tools.  

2. **What-If Scenario Analysis**  
   Simulate different business scenarios, such as price increases or changes in demand, to assess their potential impact.  

3. **Correlation Analysis**  
   Explore whether there is a relationship between customers’ annual income and the price of the vehicles they purchase.  

---

## Dataset
- **Source:** [Car Sales Dataset](https://www.kaggle.com/datasets/missionjee/car-sales-report)  
- **License:** [Apache License 2.0](http://www.apache.org/licenses/LICENSE-2.0)  
- **Main Variables:**  
  - `Car_id`  
  - `Date`  
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
  - `Dealer_Region`  

---

## Methodology
### 1. Data Cleaning
- Removed duplicates and anonymized personal identifiers.  
- Converted `Date` into proper datetime format and created a continuous calendar.  
- Standardized numerical columns such as `Annual Income` and `Price ($)`.  

### 2. Forecasting
- Built a Forecast Sheet in Excel using `FORECAST.ETS()`.  
- Compared results **with outliers** vs. **without outliers**.  
- Adjusted the lower confidence bound to avoid negative values.  

### 3. Scenario Analysis (Excel What-If)  
- **Price Sensitivity Analysis:** simulated how projected sales change with ±10% price variations.  
- **Elasticity Analysis:** assumed that every +5% price increase reduces demand by 3%, and simulated multiple price–demand scenarios using a 2-variable Data Table.  

### 4. Correlation Analysis
- Used the Excel function `=CORREL(Annual_Income, Price)` to test if higher income leads to higher vehicle prices.  
- Result: correlation coefficient = **0.012**, showing no significant linear relationship.  

---

## Results
- Forecasts of car sales values with and without outliers.  
- What-If Analysis tables showing how sales respond to changes in price and demand.  
  - Example: if prices increase by **15%** and demand decreases by **9%**, total sales would still be **20.35% higher** compared to the baseline.  
- Correlation analysis showing no clear relationship between annual income and car prices.  

---

## Documentation
The repository includes additional resources for transparency and reproducibility:

- **Excel Workbook** [Car Sales Project] 
  Contains the cleaned dataset, pivot tables, forecast sheets, what-if scenarios, and the final dashboard.  

- **Project Notes (Markdown)** [Project Notes] 
  Step-by-step notes documenting the workflow (data cleaning, forecasting, what-if analysis, correlation).  

  ---
  
## Learnings
- Demonstrated ability to forecast sales and perform scenario analysis in Excel.  
- Learned how outliers can strongly distort forecasts and how to adjust for them.  

---

## License
The dataset used in this project is provided under the [Apache License 2.0](http://www.apache.org/licenses/LICENSE-2.0).

