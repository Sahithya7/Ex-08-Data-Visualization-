# Ex-08-Data-Visualization-

## AIM
To Perform Data Visualization on the given dataset and save the data to a file. 

# Explanation
Data visualization is the graphical representation of information and data. By using visual elements like charts, graphs, and maps, data visualization tools provide an accessible way to see and understand trends, outliers, and patterns in data.

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature generation and selection techniques to all the features of the data set
### STEP 4
Apply data visualization techniques to identify the patterns of the data.
# CODE
```
#Import required libraries

import pandas as pd

import seaborn as sns

import matplotlib.pyplot as plt

#Load the dataset

df = pd.read_csv('Superstore2.csv', encoding='unicode_escape')

#Data Cleaning: Drop unnecessary columns

df.drop(['Row ID', 'Order ID', 'Ship Date', 'Customer ID', 'Postal Code', 'Product ID'], axis=1, inplace=True)

#Feature Generation: Extract Year and Month from Order Date

df['Year'] = pd.DatetimeIndex(df['Order Date']).year

df['Month'] = pd.DatetimeIndex(df['Order Date']).month_name()

#1. Which Segment has Highest sales?

segment_sales = df.groupby('Segment')['Sales'].sum().reset_index()

plt.figure(figsize=(8,5))

sns.barplot(x='Segment', y='Sales', data=segment_sales)

plt.title('Segment-wise Sales')

plt.show()

#2. Which City has Highest profit?

city_profit = df.groupby('City')['Profit'].sum().reset_index().sort_values(by='Profit', ascending=False)

plt.figure(figsize=(12,8))

sns.barplot(x='City', y='Profit', data=city_profit.head(10))

plt.title('Top 10 Cities by Profit')

plt.show()

#3. Which ship mode is profitable?

shipmode_profit = df.groupby('Ship Mode')['Profit'].sum().reset_index()

plt.figure(figsize=(8,5))

sns.barplot(x='Ship Mode', y='Profit', data=shipmode_profit)

plt.title('Ship Mode-wise Profit')

plt.show()

#4. Sales of the product based on region

region_sales = df.groupby('Region')['Sales'].sum().reset_index()

plt.figure(figsize=(8,5))

sns.barplot(x='Region', y='Sales', data=region_sales)

plt.title('Region-wise Sales')

plt.show()

#5. Find the relation between sales and profit

plt.figure(figsize=(8,5))

sns.scatterplot(x='Sales', y='Profit', data=df)

plt.title('Sales vs. Profit')

plt.show()

#6. Find the relation between sales and profit based on the following category.

#i) Segment

segment_sales_profit = df.groupby('Segment')['Sales', 'Profit'].mean().reset_index()

plt.figure(figsize=(8,5))

sns.barplot(x='Segment', y='Sales', data=segment_sales_profit, color='blue', alpha=0.5, label='Sales')

sns.barplot(x='Segment', y='Profit', data=segment_sales_profit, color='green', alpha=0.5, label='Profit')

plt.title('Segment-wise Sales and Profit')

plt.legend()

plt.show()

#ii) City

city_sales_profit = df.groupby('City')['Sales', 'Profit'].mean().reset_index().sort_values(by='Profit', ascending=False).head(10)

plt.figure(figsize=(12,8))

sns.barplot(x='City', y='Sales', data=city_sales_profit, color='blue', alpha=0.5, label='Sales')

sns.barplot(x='City', y='Profit', data=city_sales_profit, color='green', alpha=0.5, label='Profit')

plt.title('Top 10 Cities by Sales and Profit')

plt.legend()

plt.show()

#iii) States

plt.figure(figsize=(8,5))

sns.scatterplot(x='Sales', y='Profit', hue='State', data=df)

plt.title('Sales vs. Profit based on State')

plt.show()

#iv) Segment and Ship Mode

plt.figure(figsize=(8,5))

sns.scatterplot(x='Sales', y='Profit', hue='Segment', style='Ship Mode', data=df)

plt.title('Sales vs. Profit based on Segment and Ship Mode')

plt.show()

#v) Segment, Ship mode and Region

plt.figure(figsize=(8,5))

sns.scatterplot(x='Sales', y='Profit', hue='Segment', style='Ship Mode', size='Region', data=df)

plt.title('Sales vs. Profit based on Segment, Ship Mode and Region')

plt.show()
```
# OUPUT
![image](https://github.com/Sahithya7/Ex-08-Data-Visualization-/assets/133002193/d5173bc7-9bc0-4f11-ab46-54400e914567)
![image](https://github.com/Sahithya7/Ex-08-Data-Visualization-/assets/133002193/2b181741-69d2-4392-82bc-f298f8938134)
![image](https://github.com/Sahithya7/Ex-08-Data-Visualization-/assets/133002193/23739e6c-3fd5-42a1-a231-5d65c3ce8dbb)
![image](https://github.com/Sahithya7/Ex-08-Data-Visualization-/assets/133002193/48d6b373-728e-4bd1-85f7-127967e26776)
![image](https://github.com/Sahithya7/Ex-08-Data-Visualization-/assets/133002193/32743538-4589-456a-95c6-c2c1de8f2ba6)
![image](https://github.com/Sahithya7/Ex-08-Data-Visualization-/assets/133002193/fdba1b8a-3b90-4423-aeac-fdd47ceaf614)
![image](https://github.com/Sahithya7/Ex-08-Data-Visualization-/assets/133002193/c0552e0d-cad3-41c6-b335-92a09686fa30)
![image](https://github.com/Sahithya7/Ex-08-Data-Visualization-/assets/133002193/4945e426-b142-4f54-adee-102517e27ae6)
![image](https://github.com/Sahithya7/Ex-08-Data-Visualization-/assets/133002193/69b00fbd-d81f-4127-8ff8-010a92cb64ba)
![image](https://github.com/Sahithya7/Ex-08-Data-Visualization-/assets/133002193/3079239a-046c-498d-9d86-9dd2814ef7f1)
# RESULT:
Thus, to Perform Data Visualization on the given dataset and save the data to a file has been successfully performed.
