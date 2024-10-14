# Home Sales Analysis using PySpark
This project leverages SparkSQL and PySpark to perform analysis on a home sales dataset. The goal is to determine key metrics, including average home prices based on specific criteria, and to work with Spark features such as caching and partitioning for performance optimization.

## Overview
In this project, you'll be working with a dataset containing information about home sales. Using PySpark, we analyze this data to answer specific queries and optimize performance using Spark features like temporary views, caching, and partitioning.

## Files Included
- Home_Sales.ipynb: The main Jupyter notebook that contains the PySpark code for data analysis.
- home_sales_revised.csv: The dataset containing home sales information.
- Images of the analysis process.
- Instructions
- Getting Started
- Clone the repository to your local machine:

- bash
- Copy code
- git clone https://github.com/<your-username>/Home_Sales.git
- cd Home_Sales
- Install necessary dependencies for running the PySpark notebook.

## Data Analysis Steps
- Data Loading: The home_sales_revised.csv file is loaded into a Spark DataFrame.

- The dataset contains information on homes, such as sale price, number of bedrooms, bathrooms, square footage, and more.
- Temporary Table Creation: A temporary SQL view is created from the DataFrame for running SQL queries in Spark.

- python
- Copy code
- df.createOrReplaceTempView("home_sales")
- SQL Queries: The following queries are performed on the dataset:

Average price of a four-bedroom house sold each year:

This query calculates the average price of a four-bedroom house sold in each year, rounded to two decimal places.

sql
Copy code
SELECT year(date) as year_sold, ROUND(AVG(price), 2) as avg_price
FROM home_sales
WHERE bedrooms = 4
GROUP BY year_sold
ORDER BY year_sold
Average price of homes with three bedrooms and three bathrooms:

Calculates the average price of homes with three bedrooms and three bathrooms for each year they were built.

sql
Copy code
SELECT date_built, ROUND(AVG(price), 2) as avg_price
FROM home_sales
WHERE bedrooms = 3 AND bathrooms = 3
GROUP BY date_built
ORDER BY date_built
Average price of homes with specific features:

Homes with three bedrooms, three bathrooms, two floors, and at least 2,000 square feet are analyzed for their average price.

sql
Copy code
SELECT date_built, ROUND(AVG(price), 2) as avg_price
FROM home_sales
WHERE bedrooms = 3 AND bathrooms = 3 AND floors = 2 AND sqft_living >= 2000
GROUP BY date_built
ORDER BY date_built
Average price by view rating for homes over $350,000:

This query finds the average price of homes with a view rating and a price greater than or equal to $350,000.

sql
Copy code
SELECT view, ROUND(AVG(price), 2) as avg_price
FROM home_sales
WHERE price >= 350000
GROUP BY view
ORDER BY avg_price DESC
Caching the Data: The temporary table home_sales is cached for faster query performance.

python
Copy code
spark.catalog.cacheTable("home_sales")
The cached status is checked using spark.catalog.isCached("home_sales").
Query Re-run on Cached Data: The query on average price by view rating is rerun on the cached data, and the runtime is measured and compared to the uncached version.

Partitioning and Writing Parquet: The dataset is partitioned by the date_built field and written to Parquet format to improve query performance for future queries.

python
Copy code
df.write.partitionBy("date_built").parquet("path_to_save_parquet")
Uncaching: After the analysis, the home_sales temporary table is uncached and its cached status is verified.

python
Copy code
spark.catalog.uncacheTable("home_sales")
Requirements
The project is evaluated based on the following criteria:

A Spark DataFrame is created from the dataset.
A temporary table of the original DataFrame is created.
Queries return the average price for:
Four-bedroom houses sold each year.
Homes with three bedrooms and three bathrooms for each year built.
Homes with three bedrooms, three bathrooms, two floors, and over 2,000 square feet for each year built.
Homes by "view" rating for homes priced over $350,000, with the runtime of the query displayed.
Caching of the home_sales temporary table is performed and validated.
Query performance is compared between cached and uncached data.
The dataset is partitioned by the date_built field and written to Parquet.
The final query is run on the parquet data and the runtime is measured.
The home_sales temporary table is uncached and its uncached status is verified.
Running the Notebook
Make sure that you have PySpark installed. You can install it using pip:

bash
Copy code
pip install pyspark
Open the Jupyter notebook:

bash
Copy code
jupyter notebook Home_Sales.ipynb
Run the cells sequentially to complete the analysis.

## Conclusion
This project demonstrates the use of PySpark and SparkSQL for analyzing a home sales dataset. By leveraging caching and partitioning, the project optimizes query performance and explores key metrics from the dataset.
