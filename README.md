
# Sales_Dashboard

### Dashboard Link : https://app.powerbi.com/reportEmbed?reportId=227edeac-7d4a-4bbc-b996-40da34112006&autoAuth=true&ctid=7a95ad65-55ee-41e3-ba46-acbdf605ee3d

## Problem Statement

Global Super Store is a multinational e-commerce platform that sells products across diverse categories such as Furniture, Office Supplies, and Technology. As the Sales Manager, your objective is to analyze historical sales data to extract actionable insights that will enhance decision-making regarding inventory planning, customer segmentation, and product performance. This analysis aims to uncover patterns in customer purchasing behavior, evaluate regional and category-level sales trends, and identify opportunities for operational efficiency and revenue growth.

Goals of the Analysis:
- Identify top-performing and underperforming products across regions and categories.
- Analyze seasonal trends and forecast future demand.
- Understand customer behavior by segmenting based on purchase history, location, and profitability.
- Assess delivery performance, returns, and their impact on customer satisfaction.
- Provide data-driven recommendations to improve inventory management, marketing strategies, and resource allocation.





### Task 

1. Load data from the provided data sources (excel workbooks).
2. Perform the required data transformations in the Power Query Editor window.
3. Create the relationships between the loaded tables.
4. Create the required measures for key performance indicators like Sales, Profit, and Ratio.
5. Use the visuals as per the provided design to plot dimensions like Category, Year,Region, Market, Sub-category, Manager, and so on. Add key slicers to slice and dice data in the visuals.
6. Train the Q&A data model for the below synonyms:

Revenue: Sales

Income: Profit

Income Percentage: Profit Ratio

7. Managers should have restricted data access as per their market allocation by the organization. (Implement RLS)
8. Publish a report in the Power BI Service and share it with other users of the same market role.

### Steps followed

Step 1: Analyze the requirements and extract data from PBI Desktop.

1. Analyze the excel sheet data and try to understand the business data as per the asked questions in the tasks/requirements.

2. Load data (both excel files one by one) in the Power BI Desktop and use the Transform Data button to load data in the Power Query Editor for transformation purposes.


![Image](https://github.com/user-attachments/assets/f37aa82c-6416-464a-aa98-984c873c1f35)

3. For the Returns table, promote the first row as headers.
4. For the People table, remove the top row and then promote the first row as headers.
5. Remove extra columns from the Fact tables to keep the data model size reduced.

   Columns like ship date, product name, postal code, and so on can be removed.
6. Load data in the Power BI Desktop and load another excel file (Date table) into the PBI Desktop.

Step 2: Manage the table relationships.

Create the relationships as per business and data understanding for this project. These tables should be linked like the below model.

![Image](https://github.com/user-attachments/assets/924ffc1b-bbf0-45df-a8fa-a2944f049305)

![Image](https://github.com/user-attachments/assets/eb04a32b-e1af-46b7-b672-3a31c041a19c)


Step 3: Create the required measures.

The below formulas will be used to create these measures in visualizations on the report page.

Total Sales = SUMX(Orders, Orders[Unit Price] * Orders[Quantity])

Total Profit = SUM(Orders[Profit])

Profit Ratio = DIVIDE([Total Profit],[Total Sales],0)
As of Date = "Report as of date: " & Max(Orders[Order Date])
UserPrincipalName = USERPRINCIPALNAME()

Step 4: Add Visualizations

Use card visuals to display the UserPrincipalName. 

![Image](https://github.com/user-attachments/assets/8e5da285-8a34-40f5-8978-83498170071e)

▪ Use card visuals to show Total Sales, Total Profit, and Profit Ratio. Add a text box for the title of the cards.

▪ Add a clustered column chart to show “Total Sales by Year and Category”. Drag and drop the fields on the added visual and make sure fields are added under the correct data fields property.

![Image](https://github.com/user-attachments/assets/6737b386-3f40-4a6a-8c29-5d5d9c4677a4)

▪ Add a Donut chart to show “Total Sales Contribution by Category”.

![Image](https://github.com/user-attachments/assets/47676846-e133-4ddb-b43c-715596b31ff2)

▪ Add table visual from the visuals list to show “Region Contribution In Profit”. Apply the conditional formatting based on the Profit ratio field as shown below.

▪ Right-click on the Profit Ratio field and select data bars under the Conditional formatting option.

![Image](https://github.com/user-attachments/assets/dc82f3b8-45f2-4c4e-974a-a87da03c2093)

▪ Add another table visual to show the below information. Apply Conditional formatting on the Profit field as we did in the above step.

![Image](https://github.com/user-attachments/assets/22588a2f-9251-4c27-b71d-0cdb9c3b8bde)



### Output

The final report should contain the following two pages:

(Most of the time, you would have sample designs, mock-ups, and wireframes of the visuals/reports)

1. Sales Summary

![Image](https://github.com/user-attachments/assets/065742e6-dafd-4688-962e-85a555eddca9)

2. Q&A Analysis

![Image](https://github.com/user-attachments/assets/6bea9500-646e-455d-9f5e-7be84d4c1462)




        
