# Home Sales Analysis
This project leverages SparkSQL and PySpark to perform analysis on a home sales dataset. The goal is to determine key metrics, including average home prices based on specific criteria, and to work with Spark features such as caching and partitioning for performance optimization.

## Overview
In this project, you'll be working with a dataset containing information about home sales. Using PySpark, we analyze this data to answer specific queries and optimize performance using Spark features like temporary views, caching, and partitioning.

## Files Included
- Home_Sales.ipynb: The main Jupyter notebook that contains the PySpark code for data analysis.
- home_sales_revised.csv: The dataset containing home sales information.
- Images of the analysis process.
## Instructions
### Getting Started
1. Clone the repository to your local machine:
git clone https://github.com/<your-username>/Home_Sales.git
cd Home_Sales
2. Install necessary dependencies for running the PySpark notebook.

## Data Analysis Steps
1. Data Loading: The home_sales_revised.csv file is loaded into a Spark DataFrame.
- The dataset contains information on homes, such as sale price, number of bedrooms, bathrooms, square footage, and more.
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
<img width="985" alt="Screen Shot 2024-10-14 at 9 17 48 AM" src="https://github.com/user-attachments/assets/1c0a8529-ada3-49c5-b521-4a9403bda2e2">

4. Caching the Data: The temporary table home_sales is cached for faster query performance
<img width="543" alt="Screen Shot 2024-10-14 at 9 18 16 AM" src="https://github.com/user-attachments/assets/5200bf3f-401e-4141-8837-14d70a806707">

5. Query Re-run on Cached Data: The query on average price by view rating is rerun on the cached data, and the runtime is measured and compared to the uncached version.
<img width="743" alt="Screen Shot 2024-10-14 at 9 19 25 AM" src="https://github.com/user-attachments/assets/f5891acb-efdc-4d64-a82f-b3a952c9648e">

6. Partitioning and Writing Parquet: The dataset is partitioned by the date_built field and written to Parquet format to improve query performance for future queries.
<img width="1190" alt="Screen Shot 2024-10-14 at 9 16 57 AM" src="https://github.com/user-attachments/assets/b473730a-301a-46f0-a888-a81ae3da04ef">

7. Uncaching: After the analysis, the home_sales temporary table is uncached and its cached status is verified.

## Running the Notebook
1. Make sure that you have PySpark installed. You can install it using pip:
pip install pyspark

2. Open the Jupyter notebook:
jupyter notebook Home_Sales.ipynb

3. Run the cells sequentially to complete the analysis.
   
## Conclusion
This project demonstrates the use of PySpark and SparkSQL for analyzing a home sales dataset. By leveraging caching and partitioning, the project optimizes query performance and explores key metrics from the dataset.

## Acknowledgements
    
    Xpert Learning Assistant was used to answer detailed questions, and assist in debugging.The starter code provided was the base of the report and was modified using course curriculum and activities to fit the requirements of the assignment. The TA and instructor for the course also assisted in adjusting the code during office hours.For more information about the Xpert Learning Assistant, visit [EdX Xpert Learning Assistant](https://www.edx.org/). 

## References
