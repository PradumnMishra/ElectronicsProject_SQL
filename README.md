# ElectronicsProject_SQL
This project demonstrates a full data pipeline using MySQL. It starts with raw data ingestion and moves through rigorous data cleaning, feature engineering, and Exploratory Data Analysis (EDA). The goal is to transform messy e-commerce listings into a structured format suitable for business intelligence and statistical modeling.
Key Features
Data Ingestion: Automated loading of CSV data into SQL tables.

Complex Cleaning: Handling "Price Ranges" (e.g., "$100 through $200") by calculating the mean.

Feature Engineering: Extracting Brand Names from product titles.

Deriving MRP based on discount logic.

Creating categorical flags for Discount Status.

Regex Extraction: Using Regular Expressions to parse numeric ratings and review counts from unstructured text strings.

Advanced Statistics: Implementation of Covariance, Correlation, and Linear Regression Slope calculations within SQL.
Data Cleaning & Transformation
Price Normalization: Removed currency symbols and handled range-based pricing by splitting strings and calculating the average.

Discount Logic: Created a new MRP column using conditional logic:

If "No Discount": MRP = Price.

If "After [Amount]": MRP = Price + Amount.

General Case: Applied a standard 27% markup estimate for missing data.

Rating Parsing: Used REGEXP_SUBSTR to isolate numerical values from strings like "4.5 out of 5 stars with 120 reviews."

Exploratory Data Analysis (EDA)
Outlier Detection: Implemented a stored procedure GetPriceByPercentile to calculate Interquartile Range (IQR) and identify statistical outliers.

Price Distribution:
To understand the market positioning of the products, I performed price bucketing. The distribution shows a significant concentration of products in the 0-500 USD range, with a long tail extending toward luxury electronics above 6,000 USD. This helped identify the target demographic for the majority of the inventory.
<img width="567" height="213" alt="Histrogram" src="https://github.com/user-attachments/assets/1d54f937-3ac6-4935-957c-b60e7f9a7017" />

Category Distribution
I also analyzed which sub-category products were ordered more and concluded that laptops and notebooks computers had more orders as compared to other subcategories
<img width="898" height="349" alt="PieChart" src="https://github.com/user-attachments/assets/50619fc6-ddf7-4168-9ec8-6a8732b9ed3f" />


Brand Performance: Aggregated statistics (Mean, Min, Max, StdDev) per brand.

Statistical Insights
Correlation: Calculated the Pearson correlation between Average_Rating and Reviews_Count.

Regression: Calculated the Slope of the relationship between Price and MRP.

Covariance: Measured the relationship between ratings and volume of reviews across different sub-categories.

How to Use

Prepare the Data: Ensure your source file is located at D:\ElectronicsData.csv (or update the LOAD DATA INFILE path).

Run Scripts: Execute the SQL script in a MySQL environment.

View Results: Use the final SELECT statements to view the statistical summaries.
