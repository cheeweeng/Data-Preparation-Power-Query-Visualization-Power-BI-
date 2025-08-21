This repository contains the summarized table, and visualisation Dashboard developed and submitted in August 2025 for the End-of-Course Assignment in Analysing Data For Business success course at Republic Polytechnic.
This is the first part of the project which focused on processing, cleaning, transforming the data using Power Query and visualising ecommerce customer data (2020 - 2023) by creating a dashboard using Power BI.  

## Data Preparation  
There are duplicated column in "Cusomter_Age" and "Age", so remove one of these column.
There are also null values in the "Returns" column, so we will replace the null values with "0".

1 screenshot
Click on the Returns column, in Power Query editor Transform tab, click on Replace Values.
Enter the "Value to Find" and "Replace With" field.

## Transform transaction-level to customer-level data
Next we will summarized the transaction records by using Groupby customerID.

2 screnshot

In the Transform tab, we will use Groupby and perform the above aggregations.
3
When this is done, a summarized table will be created as above. Notice that the Days_Since_Last_Purchase is in date format, but we want this column to be the number of days, which should be an integer.
4 n 5
In the Add column tab, we will create a custom column named Current_Date with this formula:
>  DateTime.LocalNow()
Next, we will create another custom column which will output the number of days since last purchase using this formula:
> DateTime.LocalNow() - - [Last_Purchase_Date]
6







