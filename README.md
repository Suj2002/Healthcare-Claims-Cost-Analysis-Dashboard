# Healthcare-Claims-Cost-Analysis-Dashboard
Analyzed healthcare claims data to determine which claim types are most expensive, which CPT and ICD codes drive spending, which members account for the highest costs, and how billed amounts compare to paid amounts through SQL and Power BI dashboards.

## Healthcare Claims - Where Is the Money Going?
In this project, I assumed the role of a Data Analyst at a health insurance company tasked with investigating the drivers behind rising claim costs and declining profitability.

Using a synthetic healthcare claims dataset, the objective was to analyze healthcare spending patterns and identify which services, procedures, and members contribute most significantly to overall costs. 

The final deliverable was designed to support C-level executives in understanding financial leakage and improving cost management strategies.


## Business Questions
Based on datasets and analysis, the project aimed to answer the following executive-level questions:
1.	Which claim types are the most expensive?
2.	Which CPT and ICD codes drive the highest spending?
3.	Which members account for the largest share of total costs?
4.	How do billed amounts compare to paid amounts?

## Dataset Description
The project and datasets were sourced from Analyst Builder: https://www.analystbuilder.com/projects/healthcare-claims-where-is-the-money-going-TVHLQ

Two datasets were provided in CSV format:\
•	Members: member demographics and plan information\
•	Claims: claim records including claim types (Inpatient, Outpatient, ER, Pharmacy), CPT procedure codes, ICD diagnosis codes, billed amounts, and paid amounts

Each row in the Claims dataset represents an individual healthcare claim.


## Tech Stack
•	Excel: Initial Data Review and Light Cleaning \
•	SQL: Data Aggregation and Cost Analysis \
•	Power BI: Dashboard Development

## Data Preparation
The original datasets were preserved in raw format. Data inspection and cleaning were performed on duplicated working files to maintain data integrity and reproducibility.

Using Excel, initial data validation was conducted to check missing values, inconsistent values and columns, duplicate observations, or blank rows and columns across both tables.

Two pivot tables were created to provide a high-level overview of the data.

For the Members table, a total of 100 members were identified. The pivot table summarized member counts and average age across plan types and gender categories.

<img width="975" height="439" alt="image" src="https://github.com/user-attachments/assets/d54da340-fe7d-40fb-82d2-20177ce6190e" /> 

For the Claims table, 449 claims were recorded. The pivot table summarized claim volumes, total billed amounts, and total paid amounts across different claim types.

 <img width="955" height="277" alt="image" src="https://github.com/user-attachments/assets/844d9e4f-58e5-45d0-8dff-f76b362d2b43" /> 
 
Both tables contained a member_id field, which would be served as the key for joining the datasets in subsequent SQL analysis.

## Analysis Approach
### 1. Claim Type Cost Breakdown
Group all claims by claim_type and calculate:
1. Total billed_amount
2. Total paid_amount
3. Number of claims

Then rank all claim types from most expensive to least expensive based on total paid amount.

### 2. CPT & ICD Cost Drivers
Find the top 10 CPT codes by total paid amount.

Find the top 10 ICD codes by total paid amount.

Identify CPT codes with a high paid amount per claim by calculating:

average_paid_per_claim = total_paid_amount ÷ claim_count

This will tell you which procedures are most expensive.

### 3. Member-Level Analysis
Calculate total paid amount per member.

Identify the top 5–10 highest-cost members.

For each high-cost member, break down which claim types (inpatient, outpatient, ER, pharmacy) drive their costs.

### 4. Billed vs Paid Ratio
Calculate:

1. paid_ratio = paid_amount ÷ billed_amount

Then compare average paid ratios by:

1. claim_type

2. provider

3. CPT code

Look for claim types where the insurer pays significantly less or significantly more than the billed amount.
