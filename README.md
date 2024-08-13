# Amazon Sales Data Analysis
## Overview
This project involves analyzing Amazon sales data to gain insights into sales performance, profitability, and trends. The dataset includes sales information across different regions, item types, and sales channels. The analysis focuses on exploring sales trends, factors impacting sales, profitability, and the relationships between various attributes.

## Dataset
The dataset used in this project is Amazon Sales data.csv and contains the following columns:

* Region: Geographical region of the sale.
* Country: Country of the sale.
* Item Type: Category of the item sold.
* Sales Channel: Sales channel used (Online/Offline).
* Order Priority: Priority of the order.
* Order Date: Date of the order.
* Order ID: Unique identifier for the order.
* Ship Date: Date the order was shipped.
* Units Sold: Number of units sold.
* Unit Price: Price per unit.
* Unit Cost: Cost per unit.
* Total Revenue: Total revenue from the sale.
* Total Cost: Total cost of the sale.
* Total Profit: Total profit from the sale.
  
## Data Preprocessing
1. Conversion of Date Columns: Converted Order Date and Ship Date columns to datetime format for time series analysis.
2. Extraction of Date Components: Extracted month and year from Order Date for trend analysis.
3. Total Sales Calculation: Added a column for total sales (Total Revenue).

## Analysis
1. Sales Trends:

   * Monthly Sales: Analyzed monthly total sales to identify fluctuations and trends.
   * Yearly Sales: Analyzed yearly total sales to observe growth trends over time.
2. Factors Impacting Sales:

   * Sales Channel Impact: Examined how different sales channels affect total sales.
   * Regional Performance: Analyzed sales performance across different regions.
3. Profitability:

   * Revenue vs. Profit: Analyzed the relationship between total revenue and total profit.
   * Order Priority: Evaluated the impact of order priority on total profit.
4. Price Distribution:

  * Unit Price Distribution: Analyzed the distribution of unit prices across the dataset.
5. Performance Across Categories:

   * Product Categories: Compared total revenue and profit across different product categories.
6. Sales Channel Comparison:

  * Online vs. Offline: Compared performance between online and offline sales channels.

## Visualizations
* Scatter Plot: Total Revenue vs. Total Profit.
![image](https://github.com/user-attachments/assets/35668e45-464f-4d27-946f-c04b4f88c40f)

* Correlation Matrix: Heatmap showing correlations between numerical attributes.
  ![correlation map (1)](https://github.com/user-attachments/assets/3923d96f-1972-496e-afff-ca470a3b4527)

* Box Plot: Total Sales by Sales Channel.
![image](https://github.com/user-attachments/assets/76a59eaf-e4e6-477c-9df4-f4f04aaf8544)

* Line Plot: Monthly Total Sales over the Years.
![image](https://github.com/user-attachments/assets/cac94ef9-1bcd-4167-844a-468a40068c00)

* Distribution Plot: Distribution of Unit Price.
 ![image](https://github.com/user-attachments/assets/a37effb3-3e75-48d4-b83d-e93462e0910e)

* Bar Plot: Total Sales by Region.
![image](https://github.com/user-attachments/assets/25307e13-edd4-4d30-b616-4f9fb25b36e3)

* Violin Plot: Total Profit by Order Priority.
![image](https://github.com/user-attachments/assets/3d177117-a844-45c9-9ab9-a3683c94d8d2)

* Pair Plot: Pairwise relationships between numerical variables.
![image](https://github.com/user-attachments/assets/6a97bf47-57a3-4522-b880-d99e63b5652e)
![image](https://github.com/user-attachments/assets/2e3dc9d0-4578-42d7-a034-6ca286dc20d2)

* Time Series Plot: Monthly Total Sales over the years.
![image](https://github.com/user-attachments/assets/5e73ab98-a4eb-473b-a2e8-3d2ba76cfd07)

 
## Advanced Analysis
1. Time Series Analysis:

    * Monthly Sales Trends: Analyzed time series data for seasonal patterns and trends.
    * Decomposition: Identified trend, seasonality, and residual components.
2. Regression Analysis:

   * Predicting Total Sales: Used linear regression to predict total sales based on units sold, unit price, and unit cost.
   * Mean Squared Error: Evaluated model performance using MSE.
## Conclusion
* Sales Trends: Monthly sales show variability with certain months having higher sales. Yearly sales demonstrate overall growth.
* Factors Impacting Sales: Sales channels and regions play significant roles in performance.
* Profitability: Higher revenue generally leads to higher profits.
* Price Distribution: Most items fall within a specific price range, with some high outliers.
* Performance Across Categories: Certain categories contribute more to revenue and profit.
* Sales Channel Comparison: Online channels show more consistent performance compared to offline channels.

## Setup
1. Dependencies: Ensure you have the following Python packages installed:

* pandas
* numpy
* matplotlib
* seaborn
* scikit-learn
2. Running the Analysis:

* Place the Amazon Sales data.csv file in the project directory.
* Run the provided Python scripts to perform the analysis and generate visualizations.
License
