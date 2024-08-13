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
- Microsoft Excel. [Download here](https://www.microsoft.com/en-us/microsoft-365/excel)
  

## Dashboard Overview

![](https://github.com/Adeyemi012/Supermarket-Sales-Analysis/blob/main/Supermarket%20Sales%20Dashboard.png)


## Data Analysis and Insights Generation

1.	Customer Insight: To gain a deeper understanding of customer demographics and purchasing patterns to enhance customer segmentation and personalize marketing efforts.

![](https://github.com/Adeyemi012/Supermarket-Sales-Analysis/blob/main/Screenshot%202024-07-27%20203009.png)

### Insights:
- Members with membership cards spend the most on everyday essentials like Food and Beverages, totaling $31,358. This shows that our membership benefits are driving more frequent and consistent shopping across various categories. On the other hand, non-members prefer high-value, occasional purchases, with Electronic Accessories leading at $29,839. This indicates that non-members are more likely to make significant one-time purchases.
- Gender affects spending in our membership program. Female members spend more than males, likely due to perceived benefits. Non-members show a smaller spending gap between genders, suggesting less impact from membership incentives. Female members focus on essentials like Food and Beverages, while non-member males spend more on Electronic Accessories and females on Fashion Accessories.

2. Sales Optimization: To analyze sales trends across different cities, times, and seasons to optimize operational efficiency and staffing.

![](https://github.com/Adeyemi012/Supermarket-Sales-Analysis/blob/main/Screenshot%202024-07-27%20203800.png)

### Insights:
- Morning Sales
  - Yangon: Declining from $9,803 in January to $6,199 in March.
  - Mandalay: Fluctuates, peaking in February at $8,474 but dropping to $3,786 in March.
  - Naypyitaw: Gradual decline from $7,977 in January to $5,248 in March.
   
- Afternoon Sales
  - Yangon: Strong performance with a rise from $17,587 in January to $19,124 in March.
  - Mandalay: Stable sales around $15,000 each month.
  - Naypyitaw: Highest in January at $21,670, dips in February, then recovers to $15,843 in March.
    
- Evening Sales
  - Yangon: Steady decline from $7,112 in January to $3,853 in March.
  - Mandalay: Gradual increase, reaching $6,680 in March.
  - Naypyitaw: Increasing trend, peaking at $6,886 in March.

- Night Sales
  - Yangon: Significant increase in March to $8,483.
  - Mandalay: Peaks in January at $9,691, then stabilizes.
  - Naypyitaw: Rising trend, highest in March at $9,222

3. City Comparison: To compare the performance of various cities to share best practices and improve overall company performance.

![](https://github.com/Adeyemi012/Supermarket-Sales-Analysis/blob/main/Screenshot%202024-07-27%20204803.png)

### Insights:
- Naypyitaw: Leads in total sales with $110,569 despite selling 1831 units, indicating potentially higher-priced items or larger transaction values per sale.
- Yangon: Close behind Naypyitaw with $106,200 in sales and 1859 units sold, showcasing a competitive market with strong transaction volume and customer engagement.
- Mandalay: Shows solid performance with $106,198 in sales and 1820 units sold, reflecting consistent customer interest and robust purchasing activity.

4. Payment Preferences: To understand customer payment preferences and their effect on purchase behavior, potentially leading to the promotion of certain payment methods.

![](https://github.com/Adeyemi012/Supermarket-Sales-Analysis/blob/main/Screenshot%202024-07-27%20205324.png)

### Insights:
- Cash: Leads in total sales with $112,207 and 1896 transactions. This indicates a strong preference for cash transactions among customers.
- E-Wallet: Follows closely with $109,993 in sales and 1892 transactions, showing increasing popularity and usage of digital payment methods.
- Credit Card: Despite lower total sales at $100,767, credit card transactions total is 1722, highlighting a preference for convenience and deferred payment options.

5. Customer Satisfaction Analysis: To analyze customer ratings to identify factors that affect customer satisfaction and their correlation with sales performance.

![](https://github.com/Adeyemi012/Supermarket-Sales-Analysis/blob/main/Screenshot%202024-07-27%20205844.png)

### Insights:
- Low Satisfaction: Generates $53,916 in sales with 845 transactions. This segment indicates areas where improvements in customer experience may be needed to increase satisfaction.
- Moderate Satisfaction: Leads in sales with $109,312 and 1891 transactions. This suggests a satisfactory level of customer experience, with potential for further enhancement to drive loyalty.
- High Satisfaction: Shows $53,379 in sales and 936 transactions. Customers in this segment are highly satisfied, indicating effective service delivery and positive customer relations.
- Exceptional Satisfaction: Achieves $106,360 in sales with 1838 transactions. This segment represents loyal customers who are highly satisfied, driving significant revenue and potential referrals.

## Recommendations

1.	Customer insight: To boost satisfaction and sales, enhance the shopping experience for female members. They spend the most, especially on Food and Beverages. Offer personalized promotions, loyalty rewards, and targeted marketing to further increase their engagement and spending, driving overall growth.

2.	Sales optimization: Focus on enhancing afternoon sales strategies across all cities, as this time slot shows the highest potential for consistent revenue growth. Implement targeted promotions and customer engagement activities during this period to maximize sales.

3.	City comparison: Focus on increasing sales initiatives in Naypyitaw during the morning and afternoon periods, as this city shows potential for growth with consistent demand across these times. Implement targeted marketing campaigns and promotions tailored to local preferences to maximize sales opportunities throughout the day.

4.	Payment preferences: Since many customers prefer paying with cash, it's a good idea to make sure we always have cash as an option. We could also promote using e-wallets more by offering discounts or special deals for customers who use them. This way, we can make it easier for customers to pay and encourage them to spend more in our store.

5.	Customer satisfaction analysis: To sustain growth and boost loyalty, focus on exceeding the expectations of customers who rate their experience 8-10. Consistently deliver exceptional service to foster loyalty, increase retention, and leverage positive word-of-mouth to attract new customers, strengthening our customer base and driving long-term profitability.

## Conclusion

The supermarket faces a profitability challenge with its gross income offset by government taxes. Our recommendations focus on boosting revenue through enhanced customer satisfaction, optimized pricing strategies, and leveraging popular payment methods. Implementing these strategies aims to improve financial performance and ensure sustainable profitability.

## Additional Resources
[Link to Dataset](https://github.com/Adeyemi012/Supermarket-Sales-Analysis/blob/main/TDI%20Excel%20Capstone%20(Supermarket%20Sales%20Datatset).xlsx)




