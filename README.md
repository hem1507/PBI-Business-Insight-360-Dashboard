# Atliq Business Insight 360-Dashboard

For the interactive dashboard [click here](https://app.powerbi.com/view?r=eyJrIjoiMDllNGMzMGYtMTBkNy00ZTA0LTlhOGItY2M5ZWQzMWYyYzBlIiwidCI6IjNiNzE1MDMxLTJiY2QtNGUxOC04MTI5LTYzZThhNzFmZGFhMyJ9)<br>
You can access the full report [here](https://pp150786.sharepoint.com/sites/MySol/Shared%20Documents/Business%20Insight%20360%20Files/pbix%20file/BusinessInsight-360-V2.pbix)<br>

This dashboard helps Atliq Hardware get holistic business insights: finance analysis with P&L insights, sales analytics featuring customer and product metrics, marketing view encompassing net sales to net profit, supply chain metrics with accuracy trends, and an executive view providing regional, market share, and top customer/product insights. Invaluable for strategic decision-making.

I successfully wrapped up this project within the [Codebasics Data Analyst 2.0 Bootcamp](https://codebasics.io/bootcamps/data-analytics-bootcamp-with-practical-job-assistance) Power BI Course. Check out the details and the skills honed during this journey:

### Tech Portfolio
- Power BI Desktop & Power BI Service
- MySQL
- DAX
- M-Language
- DAX Studio (for dashboard optimization)
- Project Charter File

### Power BI techniques:
- 🔗 **Load & Connect:** Access data from diverse sources (MySQL, Excel, Azure Folder).
- **𝄜 Table Operations:** Create new tables, add calculated columns, merge, and append tables in Power Query.
- 🛠️ **Data Modeling:** Implement Star & Snowflake schema techniques.
- 📈 **DAX Utilization:** Leverage DAX for calculated columns, measures, and table creation.
- 🗃️ **Static Table:** Develop a static table for specific data representation.
- 📊 **Visual Storytelling:** Utilize various Power BI visuals to convey data insights effectively.
- 🎨 **Conditional Formatting:** Enhance visual appeal with conditional formatting.
- 🔖 **Bookmarks:** Organize multiple visuals in a single slot for seamless presentation.
- 🚀 **Power BI Services:** Publish reports, create apps, generate live Excel reports, and embed dashboards on the web.
- 🔄 **Data Refresh:** Set up automatic data refresh through a personal gateway.
- ⚙️ **Optimization:** Enhance performance with DAX Studio & Performance Analyzer, for smooth data exploration & visualization experience.

### Github Tweaks (self learning)
- Using Git lfs to load large files into github repository.
- Github Markdown coding.

### Business Terminologies
- **Gross Price:** The total price of a product or service before any deductions or expenses.
- **Pre-Invoice Deductions:** Reductions applied to the total price before the invoice is issued, such as discounts or promotions.
- **Post-Invoice Deductions:** Adjustments made to the invoice amount after it has been issued, including returns or additional discounts.
- **Net Invoice Sale:** The final amount after deducting pre and post-invoice deductions from the gross price.
- **Gross Margin:** The percentage difference between the gross price and the cost of goods sold (COGS), representing profitability.
- **Net Sales:** The revenue generated after accounting for all deductions and adjustments.
- **Net Profit:** The remaining profit after subtracting all expenses, including the COGS and other deductions, from the net sales.
- **COGS (Cost of Goods Sold):** The total direct costs associated with producing goods or services sold during a specific period.
- **Operational Expenses:** Day-to-day costs to run a business or organization.
- **Net Error:** Measure of overall forecast accuracy, considering all data points.
- **Absolute Error:** Magnitude of the difference between predicted and actual values.
- **Forecast Accuracy:** Precision in predicting outcomes, crucial for data-driven decision-making.
- **YTD (Year to Date):** Cumulative financial performance from the beginning of the current calendar year up to the present date.
- **YTG (Year to Go):** Anticipated financial performance for the remainder of the current calendar year.
- **Direct Channel:** Sales or transactions that occur directly between the producer or manufacturer and the end consumer.
- **Retailer:** Businesses that sell products directly to consumers, often through physical or online stores.
- **Distributors:** Intermediaries between manufacturers and retailers, distributing products to various points of sale.
- **Consumer:** The end-user or individual who purchases and uses the product or service.

#### Now lets delve into the intricacies of the dashboard creation process.

### Problem Statement

AtliQ Hardware, a global consumer electronics company, is experiencing rapid growth across multiple countries. However, reliance on complex Excel files for data analytics has proven ineffective, leading to significant losses in Latin America. To address this, senior executives have initiated a data analytics project, assigning a dedicated team to enhance insights and decision-making. 

They initially shared 5 mockups for the various insights - Finance, Sales, Marketing, Supply Chain, Executive.

**Tools Used:** Power BI, MySQL, MS Excel, DAX Studio, Project Charter.<br>
**Skills used:** Data Modelling, Power Query, DAX, M-language.<br>
**Dataset Used:**
- dim_customer, dim_market, dim_product, fact_forecast_monthly, fact_sales_monthly, freight_cost, gross_price, manufacturing_cost, post_invoice_deductions, pre_invoice_deductions. (loaded from MySql)
- NsGmTarget, operational_expenses, marketshare. (loaded from external Excel(.xlsx) Files)

### Steps Followed for Data Preparation & Dashboard Designing

***Step 1:*** I began by employing SQL queries within MySQL Workbench for an initial dive into the data. Following a brief data exploration, here are my initial findings:
   - The database comprises a total of 13 tables from various sources: 10 of the tables come from MySQL database and 3 tables from external sources provided as .xlsx file. 
   - the database can be classified into 2 major sets of data
       - The fact tables containing the quantitative information related to sales transaction details, forecast details, gross price, manufacturing cost, freight cost and pre & post invoice deductions.
       - The dimension tables containing details of customers, products & market. These encompass
           - 27 markets across 7 subzones (ANZ, India, LATAM, NA, NE, ROA, SE) and 4 regions (APAC, EU, LATAM, NA).
           - The product lineup includes 73 offerings within 14 categories, organized into 3 major divisions (N & S, P & A, PC) and 6 segments (Accessories, Desktop, Networking, Notebook, Peripherals, Storage).
           - Globally, Atliq serves 74 unique customers.<br>
   - The complete observation period considering both sales transaction and sales forecast data spans from September 2017 to August 2022.
   - Fiscal Year observed by Atliq is from September to August.
   - The transaction data is denominated in USD.

***Step 2:*** After gaining a foundational understanding of the data, I initiated the **ETL(Extract, Transform, Load)** process. My observations:
   - It was observed that in none of the columns errors & empty values were present except column named "region" in dim_market dataset.
   - There was no date dimension table in the dataset hence created one named dim_date in power query and added calculated columns to it for computing fiscal years.
   - For the above process I used dates from  fact_forecast_monthly & fact_sales_monthly dataset as a reference to create this table.


***Step 3:*** Following the completion of initial transformations, I proceeded to load the refined data into the primary report and started with the subsequent phase of **data modeling** laying the foundation for a robust analytical framework.<br><br>
 ![image](https://github.com/hem1507/PBI-Business-Insight-360-Dashboard/assets/147921071/c5f30d41-cbdf-42f6-a019-3c27fad4c2fe)
   - I used a snowflake schema to connect the various tables loaded.

***Step 4:*** Next came the data validation phase, where I received benchmark numbers from the project owner. Upon scrutinizing my data against these benchmarks, an observation surfaced:
   - Uncovered a discrepancy of 376K in the total forecast quantity, which on further inspection was revealed stemmed from a data quality issue.
   - Swiftly collaborating with the data engineering team, rectified the issue.

***Step 5:*** Once I was confirmed my data was clean and ready I started with the dashboard designing. This intricate process entailed the creation of remaining calculated columns and measures, employing the power of DAX (Data Analysis Expressions) and finally building the visuals required ensuring a harmonious blend of meaningful insights and aesthetic appeal.

***Step 6:*** The final step in the process was performance optimization of the dashboard. By leveraging DAX Studio, I fine-tuned the dashboard's performance, achieving a remarkable 30% reduction in file size and significantly faster data loading. This optimization guarantees a seamless experience, enhancing the efficiency of data exploration and visualization.

### Dashboard Explained

This dashboard will serve as a central hub with links to specialized views focusing on different aspects of the business, such as finance, sales, marketing, supply chain, and executive-level insights. Additionally, there are information and support pages to enhance user experience and understanding. Let's now explore the intricacies of the dashboard:

- 🏡 Home - This is the main interface offering a comprehensive snapshot of diverse insights and direct links to specific views. It also includes details about the currency denomination used in the data, the date of the latest transactional data, and the timestamp indicating when the report was last refreshed.<br><br>![image](https://github.com/hem1507/PBI-Business-Insight-360-Dashboard/assets/147921071/adb792f6-918a-4e23-8286-a5e4d8127fe9)<br><br>
- 📊 Financial Insight - A dedicated view focusing on financial data and analysis, offering insights into the company's monetary performance.<br><br> ![image](https://github.com/hem1507/PBI-Business-Insight-360-Dashboard/assets/147921071/04476455-7c01-43eb-ac02-8684d85a542c)<br><br>
- 📈 Sales Insight - This view emphasizes customer performance metrics, including net sales, gross margin, and percentage metrics for decision-making.<br><br>![image](https://github.com/hem1507/PBI-Business-Insight-360-Dashboard/assets/147921071/57137fe8-f0c1-4a38-9163-4570e6630ef1)<br><br>
- 🎯 Marketing Insight - Here the focus is on product performance metrics showcasing net sales, gross margin, gross margin %, net profit, net profit % for informed decision-making.<br><br>![image](https://github.com/hem1507/PBI-Business-Insight-360-Dashboard/assets/147921071/406b4b79-3889-4172-9e64-679f6ffc14b3)<br><br>
- 🔄 Supply Chain Insight - This view puts the spotlight on supply chain metrics by customer and product. Offers insights on year-over-year and target performance, accuracy trends, and key KPIs.<br><br>
    ![image](https://github.com/hem1507/PBI-Business-Insight-360-Dashboard/assets/147921071/3dc98f83-35f8-4c21-ac44-e53dae5dd0e2)<br><br>
- 👔 Executive Insight - This view offers regional insights with YoY and target comparisons, market share trends, yearly metric trends, top 5 customer/product details, and vital KPIs for strategic planning.<br><br>
    ![image](https://github.com/hem1507/PBI-Business-Insight-360-Dashboard/assets/147921071/8c399dba-5cf6-4fb2-8d6a-cac70729c8be)<br><br>
- ℹ️ Info Page - A supplementary page providing general information, guidelines, or additional context about the dashboard and its components.<br><br>
    ![image](https://github.com/hem1507/PBI-Business-Insight-360-Dashboard/assets/147921071/3abe16b0-9c9d-4e79-b814-c8b9a713e257)<br><br>
- 💡 Support Page - A dedicated support section, offering resources or information to assist users in navigating and understanding the dashboard. There is also a link to a feedback form where suggestions can be made for improving the dashboard.<br><br>
    ![image](https://github.com/hem1507/PBI-Business-Insight-360-Dashboard/assets/147921071/5caeca5e-ff99-4529-a72a-af6fd50fbaef)<br><br>
Some common pointers about the insight views:
   - I have added filter criteria where data can be easily filtered by market, region, customers, products, segments, categories, fiscal years, fiscal quarters, YTD(Year-To-Date)/YTG(Year-To-Go).
   - The sales, finance & executive view also include a dedicated filter each, enabling a more granular drill-down into the data for comparisons with the previous year or target metrics.



