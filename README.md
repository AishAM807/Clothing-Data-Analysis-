
# Men's Clothing Data Analysis 

### Dashboard Link :

### Data Source: Azure SQL Database 

## Problem Statement:
The project aims to perform exploratory data analysis on Men’s T-shirt data to evaluate relationships between original price and sale price, identify discount patterns, and assess brand-wise product distribution. The goal is to generate actionable insights to optimize pricing strategies and improve product offerings.


### Steps followed 

- Step 1: First, an Azure SQL account was created, and the data was subsequently loaded into the Azure SQL database.
- Step 2: Using a SELECT statement, 1000 records of men’s T-shirts were retrieved, as shown below.

  <img width="1328" height="519" alt="Image" src="https://github.com/user-attachments/assets/70a356a9-8822-41a9-92c7-113c417e19fa" />

  
- Step 3: Upon analysis, the Original Price and Sale Price columns contained unwanted '?' characters. These were successfully cleaned by executing UPDATE and SET statements to replace them with blank values, as demonstrated below.

<img width="1088" height="593" alt="Image" src="https://github.com/user-attachments/assets/60f12abd-d99f-4467-8d21-6facd83c523e" />
  
- Step 4: Established a connection between Power BI Desktop and the Azure SQL Database using the Database option.


<img width="685" height="664" alt="Image" src="https://github.com/user-attachments/assets/9a3ef0b8-dc2d-4742-bf7b-cc85c42ac66d" />

- Step 5: During data exploration, 16 records were found to have missing values across all columns. Since these records do not provide any meaningful information, they were removed from the dataset.


<img width="1102" height="628" alt="Image" src="https://github.com/user-attachments/assets/87f1a303-080c-4b29-af87-ac93f363acf3" />


- Step 6: Similarly, I observed that the Original Price column contains missing (NA) values, while the corresponding Sales Price column has valid entries, as shown below.

  
- Step 7: The Sales Price column was filtered to exclude NA (missing) values by unselecting them in the filter, ensuring only valid sales prices are considered for analysis.

  
- Step 8: A conditional column named Factor was created to calculate 50% more than the Sales Price value.

<img width="926" height="408" alt="Image" src="https://github.com/user-attachments/assets/e9060a8f-ee53-4adb-ad10-0cdd4672f09f" />

- Step 9: A new custom column was created to calculate the product of the Sales Price and Factor columns.

  <img width="699" height="435" alt="Image" src="https://github.com/user-attachments/assets/5c82d2b9-1a60-471c-8968-be15bccc71c3" />
  
- Step 10: A subsequent conditional column was added to compute the final Original Price based on the defined business logic.

<img width="925" height="407" alt="Image" src="https://github.com/user-attachments/assets/60568fe8-25fb-435b-a1ef-d555bafd1241" />


- Step 11: A new calculated column was added to measure the discount percentage based on the difference between the Original Price and Sales Price.

		Discount % = DIVIDE('Men+Tshirt (1)'[Final Original Price] - 'Men+Tshirt (1)'[Sale_Price], 'Men+Tshirt (1)'[Final Original Price]) *100


- Step 12: Created a calculated column by assuming a profit percentage ranging from 2% to 17%

 		Profit % = RANDBETWEEN(2, 17)   

- Step 13: Implemented a calculated column to compute the Cost Price based on the Selling Price and assumed Profit Percentage.

		Cost price = DIVIDE('Men+Tshirt (1)'[Sale_Price], 1 + 'Men+Tshirt (1)'[Profit %]/ 100)

- Step 14: Developed the Brands Overview page with a canvas background and updated wallpaper color for improved visual presentation.

- Step 15: Used a Multi-Row Card visual to display all brand names.

 # Report Snapshot (Power BI DESKTOP)

<img width="963" height="497" alt="Image" src="https://github.com/user-attachments/assets/483993d6-c09f-464e-b2aa-cddd45eaecf1" />

- Step 16: Created a second report page titled “Detail”, where a bar chart was added to display the top 5 brands based on average discount percentage.
  
- Step 17: The Top N filter was applied through the filter pane to identify the leading brands. Additionally, conditional formatting was implemented on the bar chart to visually represent the range from minimum to maximum values across brands.
  
- Step 18: Added a donut chart to present the top five brands with the highest product variety, enabling a clear and intuitive comparison of brand diversity and distribution.

- Step 19: Added a ribbon chart to effectively showcase the top five brands based on average sales price.
  
- Step 20: Added an Area chart to illustrate the top five brands based on average percentage, providing a clear view of performance trends. Similarly, a pie chart was incorporated to represent the bottom five brands by average percentage, enabling an intuitive comparison of lower-performing brands.


 # Report Snapshot (Power BI DESKTOP)


<img width="1105" height="502" alt="Image" src="https://github.com/user-attachments/assets/7a7256ab-5bd1-476a-8e5a-2fef723abb86" />




A two-page report was created on Power BI Desktop & it was then published to Power BI Service.

The following inferences can be drawn from the dashboard;

 # Insights

### [1]  Top 5 Brands by Average Sales Price

- ARMANI EXCHANGE → 6.1K
- BROOKS BROTHERS → 5.1K
- Terra Luna → 5.0K
- SCOTCH & SODA → 4.5K
- Kingdom of White → 3.6K

➡️ Insight: Price drops by ~2.5K from highest to lowest, showing a premium-to-mid range spread.

### [1] Top 5 Brands by Distinct Variety

- The Indian Garage Co → 51 products (22.87%)
- U.S. Polo Assn. → 44 products (~19.7%)
- SNITCH → 36 products (~16%)
- NETPLAY → 38 products (17.04%)
- GAP → 27 products (~12%)

➡️ Insight: The top brand alone contributes nearly 23% of the total variety.

### [2] Top 5 Brands by Average Percent %

- Parali, Rookies, Terra Luna, Thinc → 17% (tie for highest)
- VENTUSY, Kingdom of White → 16%

➡️ Insight: Very narrow variation (1%), indicating consistent performance across these brands.

### [3]  Bottom 5 Brands by Average Profit %

- Colorplus → 17.65%
- GESPO → ~17%
- MANIAC → 17.65%
- Trybest → 17.65%
- Pactimo → 11.76% (lowest)

➡️ Insight: Pactimo significantly underperforms with a ~6% lower profit than others.

📊 Overall Key Takeaways

Highest discount brand (72%) does not align with highest price brand (6.1K) → No direct correlation between discount and price.
Product variety leader (51 items) also appears in the top discount → aggressive pricing strategy.
Profit % among bottom brands is mostly stable except for one clear outlier (11.76%).
Sales price variation is wide, while percentage metrics are relatively tight and consistent.
