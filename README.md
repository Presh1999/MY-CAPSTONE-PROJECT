# MY-CAPSTONE-PROJECT
-----
This report is a company's customer and sales dataset used to analyze the company's top performing products, and regional breakdowns.

### Overview
-----
This project aims to analyze and visualize the sales performance of a company across different regions, customers, products, and customer's subscription types. By combining the sales data and customer data, we will derive insights such as sales trends, top-performing products, and subscription revenue. The analysis will be done using Excel for basic data handling, SQL for querying and aggregating data, and Power BI for advanced visualizations.

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
     -  Product: The item purchased.
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


 ### Data Analysis
 ----
 -	Excel: For preliminary data cleaning, filtering, and basic analysis (e.g., calculating total sales, monthly trends).
 - 	SQL: For querying the database, joining tables, and aggregating data (e.g., revenue, total sales, and region-specific metrics).
 - 	Power BI: For visualizing data trends and metrics, including creating dashboards and interactive reports that can display sales trends, region-specific insights, and performance of 
    products.

#### Excel(Pivot tables)
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
 
-  Step 3: Visual Analysis
     - In Power BI, we will create the following visualizations:
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


### Inferences
-----
 - Basic subscription dominates: Majority of customers opt for the basic subscription, indicating a price-sensitive market/customers prioritize affordability.
 - Premium subscription potential: Despite being the second-highest, premium subscription has room for growth.
 - For products, hats are the top performing products with a percentage of 23.1%, shoes are the second-best performing product with a percentage of 21.01%, shirts and gloves have relatively lower sales with a percentage of 18.12% and 18.12% each.
 - Regional Breakdown:
    - South: Gloves, shoes, and socks are top sellers.
    - East:  Hats, jackets, shoes, and shirts are top sellers.
    - North: Hats, jackets, shirts are top sellers.
    - West: Gloves, hats, shoes, and socks are top sellers.
N/b; Underperforming products like shirts and gloves have potential for growth.

        
### Solutions
----
 - Conduct customer survey to understand subscription choices.
 - Refine pricing strategy to attract more premium subscribers
 - Improve basic subscription features to encourage upgrade and avoid loss of cutomers due to low quality.
 - Product Optimization;
   
   - Shirts:
       - Enhance design and quality    
       - Organize marketing campaigns
   
   -  Gloves:
         - Improve material and durability
         - Also organize marketing campaigns, and promote it as a complementary product.
   
   - Regional Product Adaptation;
     - South:
       - Introduce hats with sourthern-style designs.
       - Offer bundled deals (example gloves + hats)

      - East:
         - Develop gloves with eastern-inspired designs.
         - Collaborate with local fashion influencers.

      -  North:
         - Create shoe designs appealing to northern customers
         - Collaborate with local shoe retailers.

     -  west:
        - Design jackets with westeern-inspired styles.
        - Offer bundled deals (example hats + jackets).

- Also, conduct customer surveys to understand product preferences, and expand product lines to cater to regional preferences.       
   





