# Car Sales Forecasting – Excel Notes

## Step 1: Initial Preparation
- Converted dataset into **Excel Table** for structured referencing.
- Applied **Currency format** to:
  - `Annual Income`
  - `Price ($)`

## Step 2: Data Cleaning
- Identified inconsistent values in the `Engine` column:
  - Found two categories: `Overhead Camshaft` and `DoubleÃ‚Â Overhead Camshaft`.
  - The second one contained encoding errors.
- Cleaned the value to `Double Overhead Camshaft` for consistency.

- Removed the column `Customer Name`:
  - Did not provide analytical value for forecasting or correlation.
  - Improved **data anonymization** by excluding potentially sensitive information.

### Rationale
- Maintaining clean categorical values avoids misinterpretations in analysis.  
- Removing irrelevant columns keeps the dataset focused and avoids noise.  


## Step 3: Exploratory Data Analysis (Pivot Tables)

### Pivot Table 1
- **Rows:** `Gender`  
- **Columns:** `Transmission`  
- **Values:** `Sum of Price ($)`  

**Insight:**  
Men tend to purchase higher-priced cars compared to women.

---

### Pivot Table 2
- **Rows:** `Gender`  
- **Values:** `Sum of Annual Income`  

**Insight:**  
Male customers report higher annual income than female customers.

---

### Pivot Table 3
- **Rows:** `Company`  
- **Columns:** `Dealer_Region`  
- **Values:** `Sum of Price ($)`  

**Insight:**  
The **Austin** region records the highest total value of car sales.

---

### Summary of Findings
1. Male customers have both **higher annual income** and tend to buy **more expensive cars**.  
2. The **Austin region** is the strongest market in terms of total sales value.  
3. Transmission type may interact with gender preferences in car purchases.  

## Step 4: Building a Continuous Calendar
- Created a new sheet `Calendar Sales` with a full daily timeline:
  - From 03/01/2022 to 12/12/2023.
  - Used **Fill → Series → Date → Day → Step 1**.

## Step 5: Aggregate Daily Sales
- Brought sales totals into the `Calendar Sales` table using `SUMIF`:  
  ```excel
  =SUMIF(Sales[Date],[@Date],Sales[Price ($)])
Now each date has a daily sales total (0 if no sales).

This prepares the dataset for Forecast Sheet.

## Step 6: Monthly Aggregation

- Created a list of unique months from the `Month_Key` column.
- Applied the following formula to calculate monthly sales totals:

=SUMIFS(B:B, A:A, ">=" & [@[Month Key]], A:A, "<" & EOMONTH([@[Month Key]], 0) + 1)
Where:

A:A → Date column from the daily calendar.

B:B → Total daily sales column.

[@[Month Key]] → First day of the month used as reference.

EOMONTH([@[Month Key]],0)+1 → First day of the following month.

Result:
Obtained a clean table with one row per month showing total monthly sales, ready for use in the Forecast Sheet.


## Step 7: Adjusting Lower Confidence Bound

Created a Forecast Sheet named Forecast with all values to include the entire time series (full data range).

- In the Forecast Sheet, the lower confidence interval sometimes produced negative values, which are not realistic for sales.
- Original formula for the lower bound:
  ```excel
  =C26-FORECAST.ETS.CONFINT(A26,$B$2:$B$25,$A$2:$A$25,0.95,1,1)
Modified the formula to ensure the bound never goes below zero:

=MAX(0, C26-FORECAST.ETS.CONFINT(A26,$B$2:$B$25,$A$2:$A$25,0.95,1,1))
This adjustment sets the lower confidence bound to 0 whenever the calculation would otherwise return a negative number.

## Step 8: Forecast Without Outliers

- Identified January and February 2022 as clear outliers (30M and 100M total sales value, while the rest of the months peaked at 16M).  
- Created a second Forecast Sheet excluding these two months, named **Forecast without outliers**.  
- Comparison of forecast results:  
  - With outliers: forecasted total sales value ≈ **4M**  
  - Without outliers: forecasted total sales value ≈ **14M**  
- Important note: these figures represent the **sum of car values sold**, not the count of transactions.

## Step 9: Simple What-If Analysis (Price Change Only)

- Objective: simulate how total sales value changes if the average car price increases, assuming demand remains constant.  
- Baseline: **$389,009,883** (total sales value).  
- Formula:
  =$F$1 * (1+$K$1)
Built a 1-variable Data Table with ΔPrice values: −10%, −5%, 0%, +5%, +10%.

Result: projected sales scale linearly with price increases/decreases since demand is fixed.

## Step 10: Elasticity What-If Analysis

Objective: analyze how simultaneous changes in price and demand affect the projected sales value.
Assumption: every +5% increase in price leads to a −3% decrease in demand.
Setup

Used baseline total sales value: $389,009,883
Built a 2-variable Data Table with:
Rows (ΔPrice): 0%, +5%, +10%, +15%
Columns (ΔDemand): 0%, −3%, −6%, −9%

Formula in the top-left corner of the table:

=($K$3*(1 + $K$1)) *  ($C$1 * (1+$P$3))

Visualization

Applied conditional formatting (heatmap) to highlight sales values across scenarios.
Example result: with +15% price and −9% demand, projected sales value reached $468,163,668.94.

## Step 11: Growth Calculation

Formula for relative growth:
=(New_Value - Base_Value) / Base_Value

Where:
New_Value = projected sales under scenario.
Base_Value = baseline total sales ($389,009,883).

Example:

Scenario (+15% price, −9% demand): $468,163,668.94
Growth = (468,163,669 − 389,009,883) / 389,009,883
Result = 20.35% growth relative to baseline.

## Step 12: Correlation Analysis (Annual Income vs. Vehicle Price)

- Objective: test if there is a linear relationship between customers' **Annual Income** and the **Price of the vehicles** they purchase.  

### Method
- Used the Excel function:
  =CORREL(Annual_Income_Range, Price_Range)
  
Result
The correlation coefficient obtained was 0.012.

This value is almost zero, indicating no significant linear relationship between annual income and vehicle price in this dataset.

Conclusion
Annual income does not explain the variation in car prices purchased by customers in this dataset.

## Step 13: Dashboard Design

- Created an **interactive dashboard in Excel** to summarize the analysis.  
- **Title of the dashboard:** *Car Sales Forecasting & Scenarios Dashboard*  

### Features
- **KPIs (cards):**
  - Total Sales Value  
  - Total Cars Sold  
  - Average Price per Car  
  - Forecasted Sales (without outliers)  

- **Charts:**
  - Line chart for Forecasting (with and without outliers)  
  - Heatmap / matrix for Elasticity Analysis (Step 10)  

- Added a table displaying the **Forecast without Outliers** values next to the chart, to provide a clear numerical reference alongside the visualization.


- **Interactivity:**
  - Slicers added for filters:
    - Dealer Region  
    - Company  
    - Transmission   
  - Timeline slicer for filtering by month/year  

### Formatting
- Axis Y formatted in **millions ($)** using the custom format:  
 
  $0,,"M"

Axis X (dates) formatted as month/year for readability:
mm/yyyy