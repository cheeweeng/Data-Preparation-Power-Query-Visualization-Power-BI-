This [repository](https://github.com/cheeweeng/Data-Transformation-and-Visualization) contains the summarized table, and visualisation Dashboard developed and submitted in August 2025 for the End-of-Course Assignment in Analysing Data For Business Success course at Republic Polytechnic.
This is the first part of the project which focused on processing, cleaning, transforming the data using Power Query and visualising ecommerce customer data by creating a dashboard using Power BI.  

## Data Preparation  
The dataset consist of 250,000 customer transaction records between year 2020 - 2023. The variables include customer demographics, purchase history, product details and churn status. There are duplicated column in "Cusomter_Age" and "Age", so remove one of these column.
There are also null values in the "Returns" column, so we will replace the null values with "0".

<p><img width="700" height="480" alt="Image" src="https://github.com/user-attachments/assets/b5893c74-da76-4123-bf91-44d9c99fa536" />  </p>
Click on the Returns column, in Power Query editor Transform tab, click on Replace Values.
Enter the "Value to Find" and "Replace With" field.

## Transform transaction-level to customer-level data
Next we will summarized the transaction records by using Groupby customerID.

<img width="600" height="450" alt="Image" src="https://github.com/user-attachments/assets/04cd2208-10df-4cb9-b678-d40db5899912" />

In the Transform tab, we will use Groupby and perform the above aggregations.  

<p><img width="900" height="200" alt="Image" src="https://github.com/user-attachments/assets/ca30f3b7-1edc-4af8-8778-7d791977a2a9" />  </p>
When this is done, a summarized table will be created as above. Notice that the Days_Since_Last_Purchase is in date format, but we want this column to be the number of days, which should be an integer. Perform the following few steps to transform the column.
<p align="center">
  <img src="https://github.com/user-attachments/assets/3825fc08-6252-4615-8310-c0323ca80586" width="45%" />
  <img src="https://github.com/user-attachments/assets/82a8a5ab-9b46-4de2-ae7d-9cc58560bdad" width="45%" />
</p>

In the Add column tab, we will create a custom column named Current_Date with this formula:
>  DateTime.LocalNow()

Next, we will create another custom column which will output the number of days since last purchase using this formula:
> DateTime.LocalNow() - [Days_Since_Last_Purchase_Date]
<p><img width="320" height="450" alt="Image" src="https://github.com/user-attachments/assets/c17c5806-288b-4a96-bb40-1c9c136a8a24" />  </p>
Click on the new custom column, in the Transform tab, select Duration and then Days, this will transform the data to number of days.

Standardise the decimal places of Avg_Order_Value and Return_Rate column to 2 and the data preparation is completed, Close and Load the data and saved the workbook.

## Building Dashboard with Power BI 
Load the summarized table which was created in above steps into Power BI.
Before building the dashboard, we will create a new calculated column to categorise customers' total purchases into "High", "Medium" and "Low" value.

<img width="1300" height="210" alt="Image" src="https://github.com/user-attachments/assets/435958b7-5f2c-431c-8fe1-79051020e5db" />  
In the Table view of Power BI, select New Column and enter this formula:    

>  Customer_Segment = IF(ecommerce_customer_data_large[Total_Purchases] > 5000, "High Value", IF(ecommerce_customer_data_large[Total_Purchases] > 2000, "Medium Value", "Low Value"))

This new Customer_Segment column will help us visualise the Churn rate by Customer Segment.

<img width="567" height="322" alt="Image" src="https://github.com/user-attachments/assets/10b93fad-bc81-47c6-8563-9a043aff3965" />  

The above simple non-interactive dashboard shows the total customer counts, the overall churn and visualised the Churn rate in percentage by Customer Segment. The chart shows that Churn rate is quite constant across the three segments with the high value total purchases having a slightly higher churn rate.

Next, we will build a [churn prediction model in KNIME](https://cheeweeng.github.io/Churn-Prediction-Model-in-KNIME/) in the second and last part of the project.  

Back to [Projects portfolio](https://cheeweeng.github.io)







