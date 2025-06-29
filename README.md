
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

▪ Add tree map and stacked bar chart to display the below insight and place the column under the correct data field.

![Image](https://github.com/user-attachments/assets/c7d2e812-0b46-467f-aec7-1d7c25d17658)

▪ Use the bookmark feature to create the below functionality to switch values between sales and profit by clicking on the button on sales and profit.

![Image](https://github.com/user-attachments/assets/c0b08d87-843b-44ac-90e8-9e842e1ae1cb)

▪ Go to the View tab and select the Bookmarks and Selection pane.

▪ Add two buttons with button text and create line charts for sales and profit. Place these line charts on top of each other.

▪ Capture two bookmarks and define proper names for them. From the Selection pane,hide the visuals and link the buttons with the respective bookmark.

![Image](https://github.com/user-attachments/assets/a802bc7f-38a0-46a9-8c59-0bac6c8267cf)

Step 5: Create a new page using the duplicate page feature for “Q&A Analysis”.

▪ Remove all the visuals except the header part.

▪ Now add a Q&A visual on the new report page which will display suggested questions
automatically

![Image](https://github.com/user-attachments/assets/ee2e31b5-fae7-4fd8-ba6f-4e7318de8558)

▪ To train the Q&A data model, click on the settings icon on this visual and then choose to add synonyms option.

![Image](https://github.com/user-attachments/assets/b5be807c-fb7d-40d3-8896-ec1fe93f66e1)

▪ Add map visual to show “Total sales by country” and change the data color property same as the below screenshot.

![Image](https://github.com/user-attachments/assets/a9a1231a-4f47-41c4-9d1e-b96adb95f3e4)

Step 6: Create Roles (Row level security) in the designed report as below.

▪ In the Modeling tab, click on the Manage roles and then create button.

![Image](https://github.com/user-attachments/assets/584e4685-9e43-443f-84b2-eeec7fba569b)

▪ Similarly, other roles will also be created in the above Manage roles window based on the requirement.

Step 7: Create Dynamic Roles (Dynamic row level security) using the
USERPRINCIPALNAME() function.

▪ Create an excel sheet with the name “Country Access” with columns – UserID/EmailID and Country.

▪ Add your Desktop ID and EmailID which are used to log into the Power BI Service, and in Country Column add country names that you want to assign to that particular user as shown in the below example.

![Image](https://github.com/user-attachments/assets/776e6609-d1f8-445b-aa09-9fb7fe8bd817)

Step 8: Import the Country Access table in the Power BI model, and add table relationship between Country Access table and Orders table based on “Country” Column.

![Image](https://github.com/user-attachments/assets/86fa5707-94c9-4174-ab02-6f38656e2224)

Step 9: Under the Modeling tab, click on Manage roles.

![Image](https://github.com/user-attachments/assets/3152f388-0b58-4a13-90cf-3606b4f2af52)

Step 10: Click on Create and give a role name as “DynamicCountryRole”, select the table to filter the “Emil_ID/User_ID” column with USERPRINCIPALNAMR().

DAX: [Email_ID/User_ID] = USERPRINCIPALNAME()

▪ Finally, click on save.

![Image](https://github.com/user-attachments/assets/01e9ce3d-3886-4e29-8568-4d3c19d280bd)

Step 11: Under the Modeling tab, click on View as.

![Image](https://github.com/user-attachments/assets/8fbb5a55-a2dd-4570-81a6-ba3c9caf45be)

Step 12: Select the role you want to test, for example, let’s select DynamicCountryRole and click on Ok.

![Image](https://github.com/user-attachments/assets/126db86c-5e0d-48fd-bec8-dc3290ae0874)

▪ Now, you will be able to view the report assigned to your desktop ID as in the Country Access table.

![Image](https://github.com/user-attachments/assets/ae8702f0-77f7-458e-aeb4-5d2a4ee57c1b)

Step 13: Publish report on Power BI Service.

▪ Now, save this report and publish it to Power BI Service in the workspace.

▪ But before you share this report with any user you need to add users under the security roles created otherwise data will not be visible to any users.

▪ Go to the Dataset and select the Security option on right-click.

![Image](https://github.com/user-attachments/assets/ae2e4583-6ac4-4d1b-9c13-044ee149fe45)

![Image](https://github.com/user-attachments/assets/c4580cbd-4c71-40e5-b20c-c8f2e92d1b53)

Step 14: Share report with users:

![Image](https://github.com/user-attachments/assets/55497242-071b-45ae-b210-3a685a1e23f3)


▪ Once the report is shared with business users or other report viewers they will get data access in the report as per the defined roles (RLS) only.

Step 15: To test the roles in the Power BI service, add a user to the role as shown below:

![Image](https://github.com/user-attachments/assets/61742dce-b6d1-40b7-b601-f5c681a9d2f1)

Step 16: After adding the user to the role, click on hover beside the role and select Test as role.

![Image](https://github.com/user-attachments/assets/61abb5e6-8836-4e08-b288-7ce80d01e25c)

▪ Now, you will be able to view the report assigned to your desktop ID as in the Country Access table.

![Image](https://github.com/user-attachments/assets/6d55ac91-4d74-4f04-a394-97b9285e95eb)

Step 17: You can pin your entire report to a dashboard. Click on the hover to select the Pin to dashboard option.

![Image](https://github.com/user-attachments/assets/c18b1f34-1ed0-4899-8418-1bb333f39d23)

Step 18: Select the New dashboard option and give a dashboard name, and click on Pin live.

![Image](https://github.com/user-attachments/assets/db2c833b-827e-4034-a3db-cb8c3cc87abe)

▪ You will see the live interactive pinned dashboard now.

![Image](https://github.com/user-attachments/assets/af16563a-d3bd-422d-83ba-285db11d707f)



### Output

The final report should contain the following two pages:

(Most of the time, you would have sample designs, mock-ups, and wireframes of the visuals/reports)

1. Sales Summary

![Image](https://github.com/user-attachments/assets/065742e6-dafd-4688-962e-85a555eddca9)

2. Q&A Analysis

![Image](https://github.com/user-attachments/assets/6bea9500-646e-455d-9f5e-7be84d4c1462)




        
