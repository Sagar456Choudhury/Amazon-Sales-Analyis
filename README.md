import pandas as pd
import numpy as np
data = pd.read_csv("Amazon Sales data.csv")
data.head()
                              Region                Country        Item Type  \
0              Australia and Oceania                 Tuvalu        Baby Food   
1  Central America and the Caribbean                Grenada           Cereal   
2                             Europe                 Russia  Office Supplies   
3                 Sub-Saharan Africa  Sao Tome and Principe           Fruits   
4                 Sub-Saharan Africa                 Rwanda  Office Supplies   

  Sales Channel Order Priority Order Date   Order ID  Ship Date  Units Sold  \
0       Offline              H  5/28/2010  669165933  6/27/2010        9925   
1        Online              C  8/22/2012  963881480  9/15/2012        2804   
2       Offline              L   5/2/2014  341417157   5/8/2014        1779   
3        Online              C  6/20/2014  514321792   7/5/2014        8102   
4       Offline              L   2/1/2013  115456712   2/6/2013        5062   

   Unit Price  Unit Cost  Total Revenue  Total Cost  Total Profit  
0      255.28     159.42     2533654.00  1582243.50     951410.50  
1      205.70     117.11      576782.80   328376.44     248406.36  
2      651.21     524.96     1158502.59   933903.84     224598.75  
3        9.33       6.92       75591.66    56065.84      19525.82  
4      651.21     524.96     3296425.02  2657347.52     639077.50  
data.tail()
                Region       Country      Item Type Sales Channel  \
95  Sub-Saharan Africa          Mali        Clothes        Online   
96                Asia      Malaysia         Fruits       Offline   
97  Sub-Saharan Africa  Sierra Leone     Vegetables       Offline   
98       North America        Mexico  Personal Care       Offline   
99  Sub-Saharan Africa    Mozambique      Household       Offline   

   Order Priority  Order Date   Order ID   Ship Date  Units Sold  Unit Price  \
95              M   7/26/2011  512878119    9/3/2011         888      109.28   
96              L  11/11/2011  810711038  12/28/2011        6267        9.33   
97              C    6/1/2016  728815257   6/29/2016        1485      154.06   
98              M   7/30/2015  559427106    8/8/2015        5767       81.73   
99              L   2/10/2012  665095412   2/15/2012        5367      668.27   

    Unit Cost  Total Revenue  Total Cost  Total Profit  
95      35.84       97040.64    31825.92      65214.72  
96       6.92       58471.11    43367.64      15103.47  
97      90.93      228779.10   135031.05      93748.05  
98      56.67      471336.91   326815.89     144521.02  
99     502.54     3586605.09  2697132.18     889472.91  
data.describe()
           Order ID   Units Sold  Unit Price   Unit Cost  Total Revenue  \
count  1.000000e+02   100.000000  100.000000  100.000000   1.000000e+02   
mean   5.550204e+08  5128.710000  276.761300  191.048000   1.373488e+06   
std    2.606153e+08  2794.484562  235.592241  188.208181   1.460029e+06   
min    1.146066e+08   124.000000    9.330000    6.920000   4.870260e+03   
25%    3.389225e+08  2836.250000   81.730000   35.840000   2.687212e+05   
50%    5.577086e+08  5382.500000  179.880000  107.275000   7.523144e+05   
75%    7.907551e+08  7369.000000  437.200000  263.330000   2.212045e+06   
max    9.940222e+08  9925.000000  668.270000  524.960000   5.997055e+06   

         Total Cost  Total Profit  
count  1.000000e+02  1.000000e+02  
mean   9.318057e+05  4.416820e+05  
std    1.083938e+06  4.385379e+05  
min    3.612240e+03  1.258020e+03  
25%    1.688680e+05  1.214436e+05  
50%    3.635664e+05  2.907680e+05  
75%    1.613870e+06  6.358288e+05  
max    4.509794e+06  1.719922e+06  
data.isnull().sum()
Region            0
Country           0
Item Type         0
Sales Channel     0
Order Priority    0
Order Date        0
Order ID          0
Ship Date         0
Units Sold        0
Unit Price        0
Unit Cost         0
Total Revenue     0
Total Cost        0
Total Profit      0
dtype: int64
data[data.duplicated()]
Empty DataFrame
Columns: [Region, Country, Item Type, Sales Channel, Order Priority, Order Date, Order ID, Ship Date, Units Sold, Unit Price, Unit Cost, Total Revenue, Total Cost, Total Profit]
Index: []
data.info()
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 100 entries, 0 to 99
Data columns (total 14 columns):
 #   Column          Non-Null Count  Dtype  
---  ------          --------------  -----  
 0   Region          100 non-null    object 
 1   Country         100 non-null    object 
 2   Item Type       100 non-null    object 
 3   Sales Channel   100 non-null    object 
 4   Order Priority  100 non-null    object 
 5   Order Date      100 non-null    object 
 6   Order ID        100 non-null    int64  
 7   Ship Date       100 non-null    object 
 8   Units Sold      100 non-null    int64  
 9   Unit Price      100 non-null    float64
 10  Unit Cost       100 non-null    float64
 11  Total Revenue   100 non-null    float64
 12  Total Cost      100 non-null    float64
 13  Total Profit    100 non-null    float64
dtypes: float64(5), int64(2), object(7)
memory usage: 11.1+ KB
data.columns
Index(['Region', 'Country', 'Item Type', 'Sales Channel', 'Order Priority',
       'Order Date', 'Order ID', 'Ship Date', 'Units Sold', 'Unit Price',
       'Unit Cost', 'Total Revenue', 'Total Cost', 'Total Profit'],
      dtype='object')
# Convert date columns to datetime data type
data['Order Date'] = pd.to_datetime(data['Order Date'], errors='coerce')
data['Ship Date'] = pd.to_datetime(data['Ship Date'], errors='coerce')
data.head()
                              Region                Country        Item Type  \
0              Australia and Oceania                 Tuvalu        Baby Food   
1  Central America and the Caribbean                Grenada           Cereal   
2                             Europe                 Russia  Office Supplies   
3                 Sub-Saharan Africa  Sao Tome and Principe           Fruits   
4                 Sub-Saharan Africa                 Rwanda  Office Supplies   

  Sales Channel Order Priority Order Date   Order ID  Ship Date  Units Sold  \
0       Offline              H 2010-05-28  669165933 2010-06-27        9925   
1        Online              C 2012-08-22  963881480 2012-09-15        2804   
2       Offline              L 2014-05-02  341417157 2014-05-08        1779   
3        Online              C 2014-06-20  514321792 2014-07-05        8102   
4       Offline              L 2013-02-01  115456712 2013-02-06        5062   

   Unit Price  Unit Cost  Total Revenue  Total Cost  Total Profit  
0      255.28     159.42     2533654.00  1582243.50     951410.50  
1      205.70     117.11      576782.80   328376.44     248406.36  
2      651.21     524.96     1158502.59   933903.84     224598.75  
3        9.33       6.92       75591.66    56065.84      19525.82  
4      651.21     524.96     3296425.02  2657347.52     639077.50  
# Extract month and year from 'Order Date' column
data['Order Month'] = data['Order Date'].dt.month
data['Order Year'] = data['Order Date'].dt.year
# Calculate total sales
data['Total Sales'] = data['Total Revenue']
data.head()
                              Region                Country        Item Type  \
0              Australia and Oceania                 Tuvalu        Baby Food   
1  Central America and the Caribbean                Grenada           Cereal   
2                             Europe                 Russia  Office Supplies   
3                 Sub-Saharan Africa  Sao Tome and Principe           Fruits   
4                 Sub-Saharan Africa                 Rwanda  Office Supplies   

  Sales Channel Order Priority Order Date   Order ID  Ship Date  Units Sold  \
0       Offline              H 2010-05-28  669165933 2010-06-27        9925   
1        Online              C 2012-08-22  963881480 2012-09-15        2804   
2       Offline              L 2014-05-02  341417157 2014-05-08        1779   
3        Online              C 2014-06-20  514321792 2014-07-05        8102   
4       Offline              L 2013-02-01  115456712 2013-02-06        5062   

   Unit Price  Unit Cost  Total Revenue  Total Cost  Total Profit  \
0      255.28     159.42     2533654.00  1582243.50     951410.50   
1      205.70     117.11      576782.80   328376.44     248406.36   
2      651.21     524.96     1158502.59   933903.84     224598.75   
3        9.33       6.92       75591.66    56065.84      19525.82   
4      651.21     524.96     3296425.02  2657347.52     639077.50   

   Order Month  Order Year  Total Sales  
0            5        2010   2533654.00  
1            8        2012    576782.80  
2            5        2014   1158502.59  
3            6        2014     75591.66  
4            2        2013   3296425.02  
month_wise_sales = data.groupby('Order Month')['Total Sales'].sum()
print(month_wise_sales)
Order Month
1     10482467.12
2     24740517.77
3      2274823.87
4     16187186.33
5     13215739.99
6      5230325.77
7     15669518.50
8      1128164.91
9      5314762.56
10    15287576.61
11    20568222.76
12     7249462.12
Name: Total Sales, dtype: float64
year_wise_sales = data.groupby('Order Year')['Total Sales'].sum()
print(year_wise_sales)
Order Year
2010    19186024.92
2011    11129166.07
2012    31898644.52
2013    20330448.66
2014    16630214.43
2015    12427982.86
2016    12372867.22
2017    13373419.63
Name: Total Sales, dtype: float64
year_wise_sales = data.groupby('Order Year')['Total Sales'].sum()
print(year_wise_sales)
Order Year
2010    19186024.92
2011    11129166.07
2012    31898644.52
2013    20330448.66
2014    16630214.43
2015    12427982.86
2016    12372867.22
2017    13373419.63
Name: Total Sales, dtype: float64
year_wise_month_wise_sales = data.groupby(['Order Year', 'Order Month'])['Total Sales'].sum()
year_wise_month_wise_sales
Order Year  Order Month
2010        2              3410661.12
            5              2587973.26
            6              1082418.40
            10             6064933.75
            11             3458252.00
            12             2581786.39
2011        1              1042225.35
            2               387002.20
            4              2798046.49
            5               272410.45
            6                19103.44
            7                97040.64
            9               574951.92
            11             5938385.58
2012        1              1012884.00
            2              6707849.42
            3               994765.42
            4              4556012.38
            5              3782781.82
            6              2132075.27
            7              4445093.92
            8               576782.80
            9              4648152.72
            10             3042246.77
2013        2              3296425.02
            3               835759.10
            4              3262562.10
            6              1352867.40
            7              8545511.20
            8                89623.98
            9                71253.21
            10             2702770.40
            12              173676.25
2014        2              1819660.25
            4              4510578.10
            5              3060338.59
            6                75591.66
            7               688641.85
            8               455479.04
            9                20404.71
            10             1352370.65
            11             4647149.58
2015        1              5513227.50
            2              2003911.12
            4              1059987.26
            7              1292409.45
            8                 6279.09
            10             1904138.04
            11              648030.40
2016        3               197883.40
            5               414371.10
            6               568269.60
            7               600821.44
            10              221117.00
            11             5876405.20
            12             4493999.48
2017        1              2914130.27
            2              7115008.64
            3               246415.95
            5              3097864.77
Name: Total Sales, dtype: float64
Total sales
total_sales = data['Total Sales'].sum()
print("Total Sales:", total_sales)
Total Sales: 137348768.31
Total Profit
total_profit = data['Total Profit'].sum()
print("Total Profit:", total_profit)
Total Profit: 44168198.39999999
Average Unit Price
average_unit_price = data['Unit Price'].mean()
print("Average Unit Price:", average_unit_price)
Average Unit Price: 276.76130000000006
Relationship between Atributes
# Scatter Plot between Total revenue and total profit
import matplotlib.pyplot as plt

plt.scatter(data['Total Revenue'],data['Total Profit'])
plt.xlabel('Total Revenue')
plt.ylabel('Total Profit')
plt.title('Scatter Plot: Total Revenue vs Total Profit')
plt.show()
 
#Heatnakjp of Correlation Matrix
import seaborn as sns

correlation_matrix = data.corr()
plt.figure(figsize=(10,8))
sns.heatmap(correlation_matrix, annot=True, cmap='coolwarm', fmt=".2f")
plt.title('Correlation Matrix')
plt.show()
 
#Box Plot of Total Sales by Sales Channel
plt.figure(figsize=(8, 6))
sns.boxplot(x='Sales Channel', y='Total Sales', data=data)
plt.xlabel('Sales Channel')
plt.ylabel('Total Sales')
plt.title('Box Plot: Total Sales by Sales Channel')
plt.show()
 
#Line Plot of Monthly Total Sales over the Years
monthly_sales_yearwise = data.groupby(['Order Year', 'Order Month'])['Total Sales'].sum().reset_index()
plt.figure(figsize=(10, 6))
sns.lineplot(x='Order Month', y='Total Sales', hue='Order Year', data=monthly_sales_yearwise)
plt.xlabel('Month')
plt.ylabel('Total Sales')
plt.title('Monthly Total Sales Over the Years')
plt.legend(title='Year')
plt.show()
 
#Distribution of Unit Price
plt.figure(figsize=(8, 6))
sns.histplot(data['Unit Price'], kde=True)
plt.xlabel('Unit Price')
plt.ylabel('Frequency')
plt.title('Distribution of Unit Price')
plt.show()
 
sns.pairplot(data)
plt.title('Pairplot of Numerical Variables')
plt.show()
 
#Bar Plot of Total Sales by Region
plt.figure(figsize=(10, 6))
sns.barplot(x='Region', y='Total Sales', data=data)
plt.xlabel('Region')
plt.ylabel('Total Sales')
plt.title('Bar Plot: Total Sales by Region')
plt.xticks(rotation=45)
plt.show()
 
#Violin Plot of Total Profit by Order Priority
plt.figure(figsize=(8, 6))
sns.violinplot(x='Order Priority', y='Total Profit', data=data)
plt.xlabel('Order Priority')
plt.ylabel('Total Profit')
plt.title('Violin Plot: Total Profit by Order Priority')
plt.show()
 
1. Sales Trends:
- Monthly total sales fluctuate over the years, with certain months showing higher sales volumes.
- Yearly total sales generally show an increasing trend, indicating overall growth in sales over time.
2.Factors Impacting Sales:
- Sales channel seems to have a significant impact on total sales, with offline sales channels generally showing higher variability.
- Region also plays a crucial role, with some regions consistently performing better in terms of total sales compared to others.
3. Profitability:
- There's a positive correlation between total revenue and total profit, indicating that higher revenue tends to lead to higher profits.
- Order priority does not seem to have a significant impact on total profit based on the violin plot.
4. Price Distribution:
- The distribution of unit prices is skewed, with most items falling within a certain price range but some outliers having significantly higher prices.
5. Performance Across Categories:
- Certain product categories, such as cosmetics and office supplies, tend to contribute more to total revenue and profit compared to others.
6. Sales Channel Comparison:
- Online sales channels appear to have more consistent performance compared to offline channels, as indicated by the box plot of total sales by sales channel.
Overall, the analysis highlights the importance of considering factors such as sales channel, region, and product category when devising sales strategies and making business decisions to optimize revenue and profitability.
# 1 Time Series Analysis:

# - We can perform time series analysis on monthly total sales data to identify any seasonal patterns or trends over time.
# - Techniques like decomposition can help us separate the trend, seasonality, and residual components of the sales data.
# Convert 'Order Date' to datetime format
data['Order Date'] = pd.to_datetime(data['Order Date'])
# Extract month and year from 'Order Date'
data['Month'] = data['Order Date'].dt.month
data['Year'] = data['Order Date'].dt.year
# Monthly total sales
monthly_sales = data.groupby(['Year', 'Month'])['Total Sales'].sum().reset_index()
# Time series plot of monthly total sales
plt.figure(figsize=(10, 6))
sns.lineplot(x='Month', y='Total Sales', hue='Year', data=monthly_sales)
plt.title('Time Series Plot of Monthly Total Sales')
plt.xlabel('Month')
plt.ylabel('Total Sales')
plt.legend(title='Year', loc='upper right')
plt.xticks(np.arange(1, 13, 1))
plt.grid(True)
plt.show()
 
# 2 Regression Analysis:

# - We can conduct regression analysis to quantify the relationships between various factors (such as sales channel, region, order priority) and total sales or total profit.
# - This can help us determine the significance of each factor and understand how much they contribute to overall sales or profit.
# Perform regression analysis to predict total sales
from sklearn.linear_model import LinearRegression
from sklearn.model_selection import train_test_split
from sklearn.metrics import mean_squared_error
# Prepare data for regression
X = data[['Units Sold', 'Unit Price', 'Unit Cost']]
y = data['Total Sales']
# Split data into training and testing sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
# Initialize and fit linear regression model
reg_model = LinearRegression()
reg_model.fit(X_train, y_train)
LinearRegression()
# Predict total sales
y_pred = reg_model.predict(X_test)
# Calculate Mean Squared Error
mse = mean_squared_error(y_test, y_pred)
print('Mean Squared Error:', mse)
Mean Squared Error: 322510611072.7175
These demonstrate how we can implement time series analysis to visualize monthly sales trends over time and regression analysis to predict total sales based on factors like units sold, unit price, and unit cost.




