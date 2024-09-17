# CUSTOMER NET SALES PERFORMANCE REPORT

### PURPOSE
The purpose of this report is to analyze the net sales performance of AtliQ Hardwares for fiscal years 2019, 2020, and 2021, with a specific focus on evaluating the percentage variation in sales between 2020 and 2021. This report outlines the complete process—from data extraction and cleaning to transformation and analysis—culminating in actionable insights that help the organization understand year-over-year sales trends.

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
**1**. Standardized customer naming conventions: Replaced variations like `AltiQ Exclusive` and `Atliq Exclusive` with `AtliQ Exclusive` (Dim_Customer Table).

**2**. Enhanced geographical data accuracy by replacing invalid entries (`nan`) with `NA` (North America) in the Sub Zone and Region columns (Dim_Market Table).

**3**. Corrected inaccuracies in sales data: Converted negative values in the Quantity column of the Fact_Sales_Monthly table to positive, ensuring consistency and accuracy for further analysis.

---

## DATA TRANSFORMATION
A Date Table was created in Power Query to facilitate accurate time-based analysis and to link various sales and customer tables on a common timeline:
  - A blank query was initialized, and the minimum and maximum dates from the Fact_Sales table were used as reference points.
  - The date column was transformed into a table, and its data type was set to `Date`. Additional columns were created to extract:
    - Start of the month
    - Fiscal month
    - Fiscal year (calculated from fiscal month)
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

---

## DATA ANALYSIS
### 1. **DAX Measures for Key Calculations**

  Various **DAX (Data Analysis Expressions)** measures were developed to calculate:
  - **Net Sales**: This measure calculated the total revenue from sales.
  - **Net Sales for Fiscal Years 2019, 2020, and 2021**: Individual measures were created for each fiscal year, providing a clear year-over-year comparison.
  - **Percentage Change in Net Sales (2020 vs 2021)**: Calculated the year-over-year percentage growth in sales between 2020 and 2021. This calculation helped identify the trajectory of the company's sales performance.

### 2. **Pivot Tables for Dynamic Reporting**
  Created pivot table to summarize the data:
  - **Sales by Year**: Displayed the net sales for 2019, 2020, and 2021.
  - **Sales by Customers**: Showed the distribution of sales across various customers.

## KEY ACHIEVEMENTS AND INSIGHTS

**1. Accurate Sales Reporting**: Delivered a comprehensive, accurate analysis of **net sales** for 2019, 2020, and 2021, revealing important sales trends and variations.

**3. Actionable Insights for Decision-Makers**: Provided insights that can guide future business strategies.

**4. Improved Data Quality**: Standardized and cleaned the data, eliminating inconsistencies that could skew analysis, ultimately leading to more reliable insights.
