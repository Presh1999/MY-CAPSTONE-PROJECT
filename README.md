# MY-CAPSTONE-PROJECT
-----
This report is a company's customer and sales dataset used to analyze top performing products, and regional breakdowns.

### Overview
-----
This project aims to analyze and visualize the sales performance of a company across different regions, customers, products, and subscription types. By combining the sales data and customer data, we will derive insights such as sales trends, top-performing products, and subscription revenue. The analysis will be done using Excel for basic data handling, SQL for querying and aggregating data, and Power BI for advanced visualizations.

### Project Objective
------
The objective of this analysis is to:
  -   Identify overall sales trends over time.
  -   Determine the top customers in each region based on their total sales.
  -   Evaluate the performance of products in different regions and identify  the highest-selling products.
  -   Analyze subscription types with the highest revenue, focusing on Premium, Standard, and Basic subscriptions.
  -   Provide key metrics to help inform business decisions related to product offerings, customer segmentation, and regional sales strategies.


  ### Data Sources
  -----
  - Sales Data (Excel)
 The sales data consists of the following columns:
     -	OrderID: Unique identifier for each order.
     -	Customer Id: Unique identifier for customers.
     -    Product: The item purchased.
     -	Region: The region where the sale occurred.
     -	OrderDate: The date the order was placed.
     -	Quantity: The number of items purchased.
     -	UnitPrice: Price per unit of the product.
     - Transaction Category: The level of the transaction (Low, Medium, High).
     -	Total Sales: The total value of the sale (calculated as Quantity * 
     UnitPrice).
     -	Customer Name: Name of the customer.
      
- Customer Data (Excel)
 This dataset includes information on customer subscriptions:
     -  Customer Name: Name of the customer.
     -  Region: Region of the customer.
     -  Subscription Type: Type of subscription (Basic, Premium, Standard).
     -  Subscription Start/End: Start and end dates of the subscription.
     -  Canceled: Whether the subscription was canceled.
     -  Revenue: Total revenue generated from the customer during the subscription 
       period.
     -  Subscription Duration: Duration of the subscription in days.
  
-  SQL Reports
SQL queries have been written to extract key sales and customer metrics, such as:
   -  Total sales for each product.
   -  Sales transactions by region.
   -  Top-selling products.
   -  Sales by region and product.
   -  Customer revenue and monthly sales totals.


### Tools Used
-----
- 	Excel: For preliminary data cleaning, filtering, and basic analysis (e.g., calculating total sales, monthly trends). 
- 	SQL: For querying the database, joining tables, and aggregating data (e.g., revenue, total sales, and region-specific metrics).
- 	Power BI: For visualizing data trends and metrics, including creating dashboards and interactive reports that can display sales trends, region-specific insights, and performance of 
     products.
  	

### Data cleaning and preparations
-----
 In the initial phase of the data cleaning and preparations, the following action was carried out
   -	Data loading into excel, SQL and powerBi
   -	Handling missing variables
   -	Data cleaning and formatting


###	Exploratory Data Analysis
-----
 Exploratory data analysis involves exploring the dataset to answer some questions about the data such as;
  -  What is the overall sales trend
  -  Top customers in different regions
  -  Top performing products in different regions
  -  Subscription type with the highest revenue

     ### Key Metrics
     -----
The following key metrics will be derived:
 -  Total Revenue: The sum of all sales transactions across products and regions.
 -  Revenue by Subscription Type: A breakdown of revenue from Basic, Premium, and Standard subscriptions.
-  Top 5 Products by Sales: The five products with the highest sales figures.
     Customers by Region: The customers who contributed the most revenue in each region.
 -   Monthly Sales Growth: Month-over-month change in total sales.
 -   Subscription Duration: The average subscription duration for each type of subscription.


 ### Data Analysis
 ----
 -	Excel: For preliminary data cleaning, filtering, and basic analysis (e.g., calculating total sales, monthly trends).
 - 	SQL: For querying the database, joining tables, and aggregating data (e.g., revenue, total sales, and region-specific metrics).
 - 	Power BI: For visualizing data trends and metrics, including creating dashboards and interactive reports that can display sales trends, region-specific insights, and performance of 
    products.

 - Pivot 1
https://github.com/Presh1999/MY-CAPSTONE-PROJECT/blob/966d70415587e5b2eec09ab5b9717986c9054336/pivot1.png

 - Pivot 2
https://github.com/Presh1999/MY-CAPSTONE-PROJECT/blob/5955e29a8e59d9559ca8947af5d8a07b85bc051a/pivot2.png
   	

### SQL Queries and Aggregation
The SQL queries provided will be used for deeper insights, such as:
- 	Total Sales per Product: Querying total sales for each product category.
  
   ```
  SELECT COUNT(Quantity*UnitPrice) as TOTAL_SALES,[Product] FROM [dbo].[SalesData$]
GROUP BY [Product]
``` 
  
- 	Regional Sales Analysis: Determining the total number of sales transactions by region.

```
SELECT COUNT(Quantity*UnitPrice) as TOTAL_SALES,Region FROM [dbo].[SalesData$]
GROUP BY Region
ORDER BY Region desc
```
  
- 	Top five(5) customers by the total purchase amount: Identifying which subscription types generate the highest revenue.

```
SELECT TOP 5
[Customer Id],
SUM (unitPrice) AS TOTAL_PURCHASE_AMOUNT FROM SalesData$
GROUP BY [Customer Id]
ORDER BY TOTAL_PURCHASE_AMOUNT DESC
```

-  Total Revenue : Using SQL joins to combine sales data with customer information and calculate total revenue per customer.

```
SELECT SUM(Revenue) as TOTAL_REVENUE FROM CustomerData$
INNER JOIN SalesData$
ON SalesData$.[Customer Id]=CustomerData$.[CustomerID]
GROUP BY [Customer ID]
```

### Data Analysis in PowerBI
-  Step 1: Import the Data
      -  Open Power BI Desktop.
      -  Go to Home > Get Data > Excel or SQL Server (depending on where your data is stored).
       - 	Import the dataset into Power BI.

-  Step 2: Create a calculated column for Revenue
    -     Total Revenue = Sum (Data[Revenue])
 
    



  - Sales Trend Analysis: We can create time-series visualizations in Power BI to see how sales have evolved over time (e.g., by month, quarter, or year).
 -  Customer Revenue by Subscription Type: A bar chart or pie chart to visualize which subscription types are generating the most revenue.
 -  Product Performance by Region: Power BI dashboards will provide a visual breakdown of which products are performing best in each region.
 -  Key Metrics Dashboard: A Power BI dashboard will consolidate important metrics like total sales, highest-selling products, top regions, and customer revenues.


### Visual Analysis and Inference
----
In Power BI, we will create the following visualizations:
 - Sales by Region and Product: A stacked bar chart or pie chart showing the total sales per region and per product.
 - Sales Trend Over Time: Line charts showing total sales by month, allowing us to observe any seasonality or trends.
 - Customer Revenue by Subscription Type: A bar chart comparing revenue generated by customers based on their subscription type.
 - Top Customers by Region: A table or bar chart to identify the highest-spending customers in each region.
 - Top Performing Products: A visual representation (e.g., bar or column chart) to highlight the best-selling products by region.
 -  Revenue by Transaction Category: A pie chart or bar chart comparing the revenue for each transaction category (Low, Medium, High).

PowerBI Table
https://github.com/Presh1999/MY-CAPSTONE-PROJECT/blob/5103aa09c39f5c32ab3e355a567f522a6a20e05e/PowerBI%20table.png

PowerBI Visualization
https://github.com/Presh1999/MY-CAPSTONE-PROJECT/blob/10e7abcc186df183da084733b831cc52ecbb6c17/PowerBI%20visualization.png


### Inferences:
-----
 -  Sales Trends: Identify periods of peak sales (e.g., specific months or seasons) and low sales. Adjust marketing or inventory strategies accordingly.
  - Top Customers: Recognizing the most valuable customers can help tailor retention strategies, loyalty programs, or targeted promotions.
 -  Product Performance: Insight into which products are performing best in which regions can help guide stock replenishment and marketing focus.
 -  Subscription Insights: Analyzing which subscription types generate the most revenue will inform pricing or promotional strategies.











