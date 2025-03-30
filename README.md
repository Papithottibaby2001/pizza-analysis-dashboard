# pizza-analysis-dashboard

Step 1: Data Cleaning
Check Data Quality:

Inspect each column for inconsistencies, missing values, and incorrect data types.

Identify outliers or irrelevant data.

Handle Missing Values:

If a column has too many missing values and does not contribute to insights, consider removing it.

Otherwise, impute missing values using appropriate techniques (mean, median, mode, or a placeholder like "Unknown").

Replace Null Values:

Use suitable replacement strategies (e.g., 0 for numerical data, "N/A" for categorical data).

Ensure Data Format Consistency:

Convert dates into the correct format.

Ensure numerical values are properly formatted.

Standardize text data (e.g., "Large", "large", "LARGE" should be consistent).

Step 2: Load Data into Power BI
Use Transform Data to validate the dataset:

Check for Data Quality: Identify duplicates, missing values, or inconsistencies.

Verify Data Types: Ensure numerical fields are not stored as text, and dates are in proper datetime format.

Remove Unnecessary Columns: Drop columns that are irrelevant to the analysis.

Step 3: Entity Relationship (ER) Modeling
Establish relationships between datasets:

Define primary and foreign keys.

Set up one-to-many or many-to-many relationships as needed.

Validate relationships using Manage Relationships in Power BI.

Step 4: Dashboard and Key Measures
1) Home Dashboard
KPIs & Metrics:

Total Revenue = SUM(pizza_sales[total_price])

Average Order Value = [Total Revenue] / [Total Orders]

Total Pizzas Sold = SUM(pizza_sales[quantity])

Total Orders = DISTINCTCOUNT(pizza_sales[order_id])

Average Pizzas per Order = [Total Pizzas Sold] / [Total Orders]

Trends & Performance:

Daily and Monthly Order Trends: Use DATEADD() and TIME INTELLIGENCE functions to analyze trends.

Busiest Day Analysis: Find the day with the highest orders.

Sales Performance by Category & Pizza Slice:

% of Sales by Pizza Category = DIVIDE(SUM(pizza_sales[total_price]), SUMX(ALL(pizza_sales), pizza_sales[total_price]), 0)

% of Sales by Pizza Slice = Similar formula as above but by slices.

2) Best/Worst Seller Dashboard
Top 5 & Bottom 5 Pizzas Analysis

Top 5 Pizzas by Revenue: TOPN(5, pizza_sales, SUM(pizza_sales[total_price]))

Top 5 Pizzas by Quantity: TOPN(5, pizza_sales, SUM(pizza_sales[quantity]))

Top 5 Pizzas by Orders: TOPN(5, pizza_sales, COUNT(pizza_sales[order_id]))

Bottom 5 Pizzas by Revenue, Quantity, and Orders: Use BOTTOMN() function.
