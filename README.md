# Supermarket Sales Analysis

## Introduction

This project presents the results of a supermarket sales analysis aimed at addressing the issue of zero net profit due to gross income being entirely offset by a 5% tax. Despite sales activity, the supermarket is not making any net profit. The analysis includes deriving various objectives to understand the underlying issues and to propose actionable recommendations.

## Data Description

The dataset includes the following fields:

- Invoice ID: Unique identifier for each transaction.
- Branch: Branch where the transaction occurred (Branch A, B and C).
- City: City where the branch is located (Yangon, Mandalay, Naypyitaw).
- Customer Type: Type of customer (Member’s Card and Non-member’s Card).
- Gender: Gender of the customer.
- Product Category: Category of the product.
- Cost Price: The acquisition cost per unit of the product.
- Quantity: The number of units of the product purchased in each transaction.
- Tax: 5% of Cost of Goods Sold (COGS).
- Sales: Total amount paid including tax.
- Date: Date of transaction (January to March 2019).
- Time: Time of the transaction (10:00 AM to 8:59 PM).
- Time Slot: The categorized time period of the transaction (Morning, Afternoon, Evening, Night).
- Payment Method: Payment method used by customer (Cash, Credit Card, Ewallet).
- COGS: Cost of goods sold.
- Gross Margin Percentage: Gross margin percentage.
- Gross Income: Gross income from the transaction.
- Rating: Customer rating of the transaction (Scale of 1 – 10).
- Rating Group: Customer satisfaction level categorized into four groups (Low, Moderate, High, Exceptional Satisfaction).

### Basic statistics about the dataset:

- Total Sales: $322,967
- Total Cost Price: $55,672
- Total Quantity Sold: 5510 items
- Total Cost of Goods Sold (COGS): $307,587
- Total Tax: $15,379
- Number of Unique Customers: 1000
- Number of Product Category: 6

## Methodology

### Data Collection

The dataset for this analysis was provided by the TData Initiative, an organization that supplies educational datasets for learning and training purposes. The data was provided in CSV format, making it accessible for analysis.

### Data Manipulation

1. Data Cleaning:
   - Checked for Spelling Errors, Duplicate Values, and Blank Cells: Ensured data quality by correcting any spelling errors, removing duplicate entries, and addressing missing values.
   - Standardization: Used find and replace to standardize certain fields:
     - Changed Customer Type values from "0" to "Non-members card" and "1" to "Members card".
     - Changed Gender values from "M" to "Male" and "F" to "Female".
       
2. Data Transformation:
   - Data Types and Formatting: Ensured all data fields were assigned the correct data types, with numerical fields formatted as currencies where appropriate, and date fields set to date format.
   - Sorting: Sorted the dataset by the Date column to organize transactions chronologically.
   - Created New Columns:
     - Time Slot: Added a new column to categorize transactions based on the time of purchase using an IF function:
       ```
          =IF(AND(L2 >= TIME(10, 0, 0), L2 < TIME(12, 0, 0)), "Morning",
           IF(AND(L2 >= TIME(12, 0, 0), L2 < TIME(17, 0, 0)), "Afternoon",
           IF(AND(L2 >= TIME(17, 0, 0), L2 < TIME(19, 0, 0)), "Evening", "Night")))
       ```   
     - Month: Extracted the month from the Date column using the TEXT function.
     - Rating Group: Categorized customer ratings into groups using an IF function:
       ```
       =IF(AND(S2 >= 4, S2 <= 4.9), "Low Satisfaction",
        IF(AND(S2 >= 5, S2 <= 6.9), "Moderate Satisfaction",
        IF(AND(S2 >= 7, S2 <= 7.9), "High Satisfaction",
        IF(AND(S2 >= 8, S2 <= 10), "Exceptional Satisfaction", "Other"))))
       ```
       
3. Validation:
   - Gross Margin Percentage: Verified the accuracy of the Gross Margin Percentage calculation using the formula: ((Sales - COGS) / Sales).
     
4. Column Renaming:
   - Renamed columns for clarity and better understanding:
     - "Product line" to "Product Category"
     - “Unit price” to “Cost Price”
     - "Total" to "Sales"
     - "Payment" to "Payment Method"

### Tools used
- Microsoft Excel. [Download-here](https://www.microsoft.com/en-us/microsoft-365/excel)

## Dashboard Overview






