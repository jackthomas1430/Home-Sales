# Home Sales Analysis

## Overview
This project uses SparkSQL and PySpark to perform analysis on a home sales dataset to determine ther following metrics: 
- What is the average price for a four-bedroom house sold for each year? Round off your answer to two decimal places.
- What is the average price of a home for each year the home was built, that has three bedrooms and three bathrooms? Round off your answer to two decimal places.
- What is the average price of a home for each year the home was built, that has three bedrooms, three bathrooms, two floors, and is greater than or equal to 2,000 square feet? Round off your answer to two decimal places.
- What is the average price of a home per "view" rating having an average home price greater than or equal to $350,000? Determine the run time for this query, and round off your answer to two decimal places.

Spark is then used to create temporary views, partition the data, cache and uncache a temporary table, and verify that the table has been uncached.

## Files 
- Home_Sales_Colab.ipynb: The main Jupyter notebook that contains the PySpark code for data analysis.
- home_sales_revised.csv: The dataset containing home sales information.

## Instructions
### Getting Started
1. Clone the repository to your local machine:
git clone https://github.com/jackthomas1430/Home-Sales.git
cd Home_Sales
2. Open Notebook in Google Collab
3. Run file
   
## Data Analysis Steps
1. Data Loading: The home_sales_revised.csv file is loaded into a Spark DataFrame.
<img width="1190" alt="Screen Shot 2024-10-14 at 9 16 57 AM" src="https://github.com/user-attachments/assets/e89b955c-8de9-4cce-87ee-3dcebb5a3526">

2. Temporary Table Creation: A temporary SQL view is created from the DataFrame for running SQL queries in Spark.
df.createOrReplaceTempView("home_sales")

3. SQL Queries: The following queries are performed on the dataset:

- Average price of a four-bedroom house sold each year:
<img width="942" alt="Screen Shot 2024-10-14 at 9 17 22 AM" src="https://github.com/user-attachments/assets/d7ded82d-efa1-43d7-a304-69137a1fffcd">

- Average price of homes with three bedrooms and three bathrooms:
<img width="762" alt="Screen Shot 2024-10-14 at 9 17 30 AM" src="https://github.com/user-attachments/assets/4f46f754-84c4-44e7-8b3b-984e4f0b37f7">

- Average price of homes with specific features:
<img width="856" alt="Screen Shot 2024-10-14 at 9 17 39 AM" src="https://github.com/user-attachments/assets/d8056a74-7225-40ac-9eae-9cb770f2deba">


- Average price by view rating for homes over $350,000:
<img width="1033" alt="Screen Shot 2024-10-17 at 9 04 21 PM" src="https://github.com/user-attachments/assets/7df9312d-af5b-4a1f-a87e-ed3085557e7e">

4. Caching the Data: The temporary table home_sales is cached for faster query performance
<img width="543" alt="Screen Shot 2024-10-14 at 9 18 16 AM" src="https://github.com/user-attachments/assets/5200bf3f-401e-4141-8837-14d70a806707">

5. Query Re-run on Cached Data: The query on average price by view rating is rerun on the cached data, and the runtime is measured and compared to the uncached version.
<img width="1218" alt="Screen Shot 2024-10-17 at 9 04 11 PM" src="https://github.com/user-attachments/assets/657806d1-9bbf-49e3-9f94-2550e25a8eaa">

6. Partitioning and Writing Parquet: The dataset is partitioned by the date_built field and written to Parquet format to improve query performance for future queries.
<img width="1260" alt="Screen Shot 2024-10-17 at 9 04 01 PM" src="https://github.com/user-attachments/assets/0f3d94ec-b505-45f1-94d6-2c13c31e37f0">

7. Uncaching: After the analysis, the home_sales temporary table is uncached and its cached status is verified.
<img width="997" alt="Screen Shot 2024-10-17 at 9 16 18 PM" src="https://github.com/user-attachments/assets/36107274-c169-4247-8c38-e36cfa0827c6">


## Conclusion
The results show that partitioning the dataset was the most efficient approach, reducing query time from ~0.95 seconds to  ~0.71 seconds. The cached runtime actually incresed to 1.01 seconds, which suggests that partitioning might provide more substantial performance improvements. 

## Acknowledgements
    
    Xpert Learning Assistant was used to answer detailed questions, and assist in debugging.The starter code provided was the base of the report and was modified using course curriculum and activities to fit the requirements of the assignment. The TA and instructor for the course also assisted in adjusting the code during office hours.For more information about the Xpert Learning Assistant, visit [EdX Xpert Learning Assistant](https://www.edx.org/). 

## References
