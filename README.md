# Atliq Business Insight 360-Dashboard

### Dashboard Link : https://shorturl.at/alsyB

This dashboard helps Atliq Hardware get holistic business insights: finance analysis with P&L insights, sales analytics featuring customer and product metrics, marketing view encompassing net sales to net profit, supply chain metrics with accuracy trends, and an executive view providing regional, market share, and top customer/product insights. Invaluable for strategic decision-making.

#### Problem Statement

AtliQ Hardware, a global consumer electronics company, is experiencing rapid growth across multiple countries. However, reliance on complex Excel files for data analytics has proven ineffective, leading to significant losses in Latin America. To address this, senior executives have initiated a data analytics project, assigning a dedicated team to enhance insights and decision-making. They initially shared 5 mockups for the various report pages for the dashboard - Finance, Sales, Marketing, Supply Chain, Executive.

#### Tool Used: Power BI, MySQL, MS Excel, DAX, DAX Studio, Project Charter
#### Skills used: Data Modelling, Power Query, DAX, M-language

### Overview

Following a brief data exploration, here are my initial findings:
   - The database comprises a total of 13 tables from various sources: 10 of the tables come from MySQL database and 3 tables from external sources provided as .xlsx file. 
   - the database can classified into 2 major sets of data
       - The fact tables containing the quantitative information related to sales transaction details, forecast details, gross price, manufacturing cost, freight cost and pre & post invoice deductions.
       - The dimension tables containing details of customers, products & market. These encompass
           - 27 markets divided within 7 subzones (ANZ, India, LATAM, NA, NE, ROA, SE) and 4 regions (APAC, EU, LATAM, NA)
           - 73 products within 14 categories divided within 3 major divisions (N & S, P & A, PC) further subdivided into 6 segements (Accessories, Desktop, Networking, Notebook, Peripherals, Storage).
           - Atliq has 74 unique customers accross the globe.
   -The complete observation period considering both sales transaction and sales forecast data spans from September 2017 to August 2022.
   -The transaction data is denominated in USD.

### Dataset Used

- MySql (from 2 different schema) - dim_customer, dim_market, dim_product, fact_forecast_monthly, fact_sales_monthly, freight_cost, gross_price, manufacturing_cost, post_invoice_deductions, pre_invoice_deductions.
- Excel(.xlsx) Files - NsGmTarget, operational_expenses, marketshare

### Steps followed for Data Preparation

- Step 1 : Load data into Power BI Desktop, dataset came from MySQL Database and Excel files.
- Step 2 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profiling based on entire dataset" options.
- Step 3 : It was observed that in none of the columns errors & empty values were present except column named "region" in dim_market dataset.
- Step 4 : Atliq observes fiscal year starting September to August next year and since there was no date dimension table in the dataset hence created one named dim_date in power query and added calculated columns to it for computing fiscal years. Used dates from  fact_forecast_monthly & fact_sales_monthly dataset as a reference to create this table.
- Step 5 : Validated data against benchmark numbers received from project owner Nick Puri and found a gap of 376K in total forecast quantity which on further drill down found due to data quality issue that I got fixed from the data engineering team.
- Step 6 : I started with Power Query's M formula language and features like table merging to create a unified table with both actuals and estimates.
- Step 7 : After this I created some of the other required calculated columns in power query editor like
    - adding fiscal_year to fact_sales_estimate
    - performing left outer join between two tables
    - calculating new column for Gross Sales & Net Invoice Sales.
- Step 8 : Used a snowflake schema to connect the various tables loaded for data modelling.
 ![image](https://github.com/hem1507/PBI-Business-Insight-360-Dashboard/assets/147921071/c5f30d41-cbdf-42f6-a019-3c27fad4c2fe)
- Step 9 : After this I created rest of the calculated columns using DAX to complete rest of the P & L metrics.
- Step 10 : Performed basic checks for the P&L table visual that was requested in the mockup to spot any obvious data quality problems. Also optimized report size by performing instrumentation through DAX studio.

  ### Steps followed for Dashboard Designing
  
  Based on mockup received I then started designing the dashboard.
    - First I wrote down all the metrics I will be needing to prepare the views. Then I loaded all these metrics into power bi by creating appropriate measures using DAX.
    - Then I started with creating the visuals for the various views requested by the executive team.
    - Once I was done with creating the views I added the landing page for the dashboard, an info page and support page.
 
### The Dashboard Explained

Dashboard consists of a landing page which has links to all other views.
  - Financial Insight
  - Sales Insight
  - Marketing Insight
  - Supply Chain Insight
  - Executive Insight
  - Info Page
  - Support Page

You can find the full interactive dashboard here 


