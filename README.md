# CUSTOMER NET SALES PERFORMANCE REPORT

### PURPOSE
The purpose of this report is to analyze the net sales performance of AtliQ Hardwares for fiscal years 2019, 2020, and 2021, with a specific focus on evaluating the percentage variation in sales between 2020 and 2021. This report outlines the complete process—from data extraction and cleaning to transformation and analysis—culminating in actionable insights that help the organization understand year-over-year sales trends.
<div align="center">
  <img src="https://github.com/user-attachments/assets/84178526-0764-4467-952d-4cd123d016fd" alt="Capture">
</div>



## OBJECTIVES:
**1**. Calculate **net sales** for FY 2019, 2020, and 2021.

**2**. Analyze the **Net Sales % change** between 2020 and 2021 to measure growth or decline.

---

## EXTRACT, TRANSFORM AND LOAD (ETL)
Data was extracted from raw CSV files into Power Query in Excel. The datasets were large, consisting of sales, customer, product, and market tables containing thousands of rows of data (almost 800k) for four consecutive years. 

**Files used**

**1**. Dim_Customer

**2**. Dim_Market

**3**. Dim_Product

**4**. Fact_Sales_Monthly

---

## DATA CLEANING
**1. Standardized customer naming conventions**: Replaced variations like `AltiQ Exclusive` and `Atliq Exclusive` with `AtliQ Exclusive` (Dim_Customer Table).
<div align="center">
  <img src="https://github.com/user-attachments/assets/f9106d64-5ede-4782-8d22-847a3a31add9" alt="1">
</div>

**2. Enhanced geographical data accuracy**: By replacing invalid entries (`nan`) with `NA` (North America) in the Sub Zone and Region columns (Dim_Market Table).
<div align="center">
  <img src="https://github.com/user-attachments/assets/e46168cc-a548-40c8-968e-5a0a0e904828" alt="2">
</div>

**3. Corrected inaccuracies in sales data**: Converted negative values in the Quantity column of the Fact_Sales_Monthly table to positive, ensuring consistency and accuracy for further analysis.
<div align="center">
  <img src="https://github.com/user-attachments/assets/89706cc2-043b-4fd7-9c24-26036a2e97ab" alt="3a">
         <img src="https://github.com/user-attachments/assets/6664cc34-1295-4585-b429-a29533e2e981" alt="3b">
</div>

---

## DATA TRANSFORMATION
A Date Table was created in Power Query to facilitate accurate time-based analysis and to link various sales and customer tables on a common timeline:
  - A blank query was initialized, and the minimum and maximum dates from the Fact_Sales table were used as reference points.
<div align="center">
  <img src="https://github.com/user-attachments/assets/94205c91-888a-48b9-80bf-dafdef7b4204" alt="5">
</div>

   - The date column was transformed into a table, and its data type was set to "Date". Additional columns were created to extract: Start of the month, Fiscal month, Fiscal year (calculated from fiscal month)

<div align="center">
  <img src="https://github.com/user-attachments/assets/b577a462-e56f-4b2f-b71e-068c9ce12aaf" alt="6">
</div>
<div align="center">
  <img src="https://github.com/user-attachments/assets/18bbffb4-7422-441a-adb3-310be83484b3" alt="7">
</div>

  - Unnecessary columns such as Year and Fiscal Month were removed after extracting relevant date metrics.


---

## DATA MODELLING
Data modeling was done to create relationships between the various tables. Proper data modeling was crucial for establishing connections between:
  - Sales data (Fact_Sales_Monthly)
  - Customer data (Dim_Customer)
  - Product data (Dim_Product)
  - Market segmentation (Dim_Market)
  - Time-based data (Date Table)
**Creating a Unified Data Model**:
The unified data model enabled dynamic reporting and ensured that changes in any of the related tables would be reflected across all analyses. This model acted as the backbone for the pivot tables and DAX calculations used in the later stages of the analysis.
<div align="center">
  <img src="https://github.com/user-attachments/assets/6675e690-4e57-46cc-b256-89bab8addf4e" alt="4">
</div>
---

## DATA ANALYSIS
### 1. **DAX Measures for Key Calculations**

  Various **DAX (Data Analysis Expressions)** measures were developed to calculate:
  - **Net Sales**: This measure calculated the total revenue from sales.
<div align="center">
  <img src="https://github.com/user-attachments/assets/71939c0a-ede8-4b29-97e0-4e0db6bdaf61" alt="8">
</div>

  - **Net Sales for Fiscal Years 2019, 2020, and 2021**: Individual measures were created for each fiscal year, providing a clear year-over-year comparison.
  <div align="center">
  <img src="https://github.com/user-attachments/assets/6cb446ca-d09a-4a02-a655-4226f6b60fa0" alt="9">
  &nbsp;&nbsp;&nbsp;
  <img src="https://github.com/user-attachments/assets/082bfd5a-88e2-4968-b786-fd2cec550027" alt="10">
  &nbsp;&nbsp;&nbsp;
  <img src="https://github.com/user-attachments/assets/ce4b221b-5ffe-4543-a1e5-c0aaed2b97cd" alt="11">
</div>
  
  - **Percentage Change in Net Sales (2020 vs 2021)**: Calculated the year-over-year percentage growth in sales between 2020 and 2021. This calculation helped identify the trajectory of the company's sales performance.
<div align="center">
  <img src="https://github.com/user-attachments/assets/46336d79-a372-4c11-a35a-339a28b3c5b3" alt="12">
</div>

### 2. **Pivot Tables for Dynamic Reporting**
  Created pivot table to summarize the data:
  - **Sales by Year**: Displayed the net sales for 2019, 2020, and 2021.
  - **Sales by Customers**: Showed the distribution of sales across various customers.

## KEY ACHIEVEMENTS

- Efficiently executed the ETL process, extracting and processing over **800k rows** of sales data from large CSV files into Power Query. 

- Developed and implemented data transformations, including the creation of a comprehensive Date Table and deriving fiscal periods, which **optimized reporting** for year-over-year analysis.

- Built a **robust data model** by connecting **5 key tables**, ensuring seamless querying and enabling dynamic pivot reporting, resulting in faster data retrieval and analysis.

- Created **DAX calculations** to compute key performance metrics such as Net Sales for FY 2019, 2020, and 2021.
