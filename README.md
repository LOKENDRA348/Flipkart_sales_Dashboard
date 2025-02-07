# Flipkart_sales_Dashboard

Overview

This Flipkart Sales Dashboard is built using Microsoft Power BI to analyze and visualize sales data effectively. The process includes data loading, transformation, modeling, DAX calculations, and adding visuals for insights.

Step 1: Data Loading and Transformation

Loading Data:

Connected Power BI to an Excel dataset.

Used Power Query for data profiling and quality checks.

Checked distinct and unique values.

Data Cleaning & Pre-processing:

Detected and resolved incorrect data types.

Used the first row as headers.

Removed unnecessary columns from the product dimension table.

Formatted column names by capitalizing the first letter of each word.

Custom Columns Created:

Total Profit Calculation:

Custom Formula = [Total Sales] - [Product Price] * Quantity

Changed data type to decimal.

Discount Price Calculation (INR):

Discount Price INR = [Selling Price] * [Discount]

Determined the discount amount in INR for each product.

Step 2: Data Modeling

Fact Table: Contains quantitative data and foreign keys.

Dimension Tables: Contain descriptive data with primary keys.

Relationships Established (One-to-Many Cardinality):

Fact table Region ID → Dimension table Region ID

Fact table Product ID → Dimension table Product ID

Fact table Date ID → Dimension table Date ID

Fact table Customer ID → Dimension table Customer ID

Fact table Delivery Status ID → Dimension table Delivery Status ID

Fact table Payment Status ID → Dimension table Payment Status ID

Added a Text Box titled "Flipkart Sales Dashboard" on the canvas.

Step 3: DAX Formulas for Cards

Total Sales:

Total_Sales = SUM(fact_table[Total Sales])

Total Orders:

Total_Order = COUNT(fact_table[Order ID])

Total Profit:

Total_Profit = SUM(fact_table[total_profit])

Previous Year 2024 Sales:

Previous_Year_Sales = CALCULATE([Total_Sales], PREVIOUSYEAR(DATESYTD(date_dimension_table[Order Date])))

Previous Q4 Sales:

Previous_Q4_Sales = CALCULATE([Total_Sales], PREVIOUSQUARTER(DATESQTD(date_dimension_table[Order Date])))

Current Q1 Sales:

Current_Q1_Sales = TOTALQTD([Total_Sales], DATESQTD(date_dimension_table[Order Date]))

Growth Between Q1 and Q4:

Growth_Q1_Between_Q4 = DIVIDE([Current_Q1_Sales], [Previous_Q4_Sales]) - 1

Formatted Growth Q1 Between Q4 to Percentage instead of General Number.

Step 4: Adding Visuals

Stacked Bar Chart:

X-Axis: Total Sales

Y-Axis: Product Name

Legend: Region

Stacked Column Chart:

X-Axis: Month

Y-Axis: Total Profit

Donut Chart:

Legend: Region

Values: Sum of Total Sales

Pie Chart:

Legend: Region

Values: Total Profit

Funnel Chart:

Category: Payment Method

Values: Sum of Total Sales

Line Chart:

X-Axis: Order Date (Year, Quarter, Month)

Y-Axis: Sum of Total Sales

Ribbon Chart:

X-Axis: Quarter

Y-Axis: Sum of Total Profit

Legend: Region

Stacked Bar Chart:

X-Axis: Sum of Quantity

Y-Axis: Product Name

Legend: Payment Method
