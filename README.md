# Healthcare-Claims-Cost-Analysis-Dashboard
Analyzed healthcare claims data to determine which claim types are most expensive, which CPT and ICD codes drive spending, which members account for the highest costs, and how billed amounts compare to paid amounts through SQL and Power BI dashboards.

Healthcare Claims - Where Is the Money Going?
This time we played a role as a Data Analyst for a health insurance company to figure out the reasons behind losing money. 
In this simulated project, we’ve been given synthetic claims datasets. Our goal is to break down healthcare spending to understand which services, procedures, and members drive the highest costs for C-Level Executives and the company to try to become profitable again.
Business Questions
Based on datasets and analysis, we should answer the following executive questions:
1.	Which claim types are the most expensive?
2.	Which CPT and ICD codes drive the highest spending?
3.	Which members account for the largest share of total costs?
4.	How do billed amounts compare to paid amounts?
Dataset Description
The project and datasets are originally from Analyst builder: https://www.analystbuilder.com/projects/healthcare-claims-where-is-the-money-going-TVHLQ
There are two datasets/tables given in csv format, ‘members’ and ‘claims’, including member demographics, claim types (inpatient, outpatient, ER, pharmacy), diagnosis codes (ICD), procedure codes (CPT), billed amounts, and paid amounts.
Tech Stack
•	Excel: Initial Review for Data and Light Cleaning
•	SQL: Analysis and Aggregations 
•	Power BI: Creating Dashboard 
Data Preparation
The original datasets were preserved in raw format. Data inspection and cleaning were performed on duplicated working files to maintain data integrity and reproducibility.
Using excel, we ensure that there are no NA or missing values, duplicated observations and blank column and rows in both two tables.
Also, we created two pivot tables to summarize the insights and trend from a general overview.
