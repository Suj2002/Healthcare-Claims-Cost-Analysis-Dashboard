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

The Claims dataset were provided in CSV format, including member demographics, claim types (Inpatient, Outpatient, ER, Pharmacy), CPT procedure codes, ICD diagnosis codes, billed amounts, and paid amounts.

Each row in the dataset represents an individual healthcare claim.


## Tech Stack
•	Excel: Initial Data Review and Light Cleaning \
•	SQL: Data Aggregation and Cost Analysis \
•	Power BI: Dashboard Development

## Data Preparation
The original datasets were preserved in raw format. Data inspection and cleaning were performed on duplicated working files to maintain data integrity and reproducibility.

Using Excel, initial data validation was conducted to check missing values, inconsistent values and columns, duplicate observations, or blank rows and columns across both tables.

A pivot table were created to provide a high-level overview of the data.

For the Claims table, 449 claims were recorded. The pivot table summarized claim volumes, total billed amounts, and total paid amounts across different claim types.

 <img width="955" height="277" alt="image" src="https://github.com/user-attachments/assets/844d9e4f-58e5-45d0-8dff-f76b362d2b43" /> 
 

## Analysis Approach
### 1. Claim Type Cost Breakdown
Group all claims by claim_type and calculate:
1. Total billed_amount
2. Total paid_amount
3. Number of claims

Then rank all claim types from most expensive to least expensive based on total paid amount.

| claim type | total billed amount | total paid amount | number of claims|
| ---------- | ------------------- | ----------------- | --------------- |
| Inpatient	 | 1478601.25      	   | 1092456.0	       | 99 |
| Emergency  | 384241.55	       | 294441.36	       | 88 |
| Outpatient | 160717.75	       | 129052.75	       | 105|
| Lab	     | 25789.9	           | 23412.35	       | 76 |
| Pharmacy 	 | 12814.6	           | 11382.45	       | 81 |
 
#### Insights: 
It is clear that the 'Inpatient' is the most expensive claim type with 99 claims within this category, and 'Emergency' takes the second rank.

### 2. CPT & ICD Cost Drivers
#### Find the top 10 CPT codes by total paid amount.
| CPT code | total paid amount |
| ----- | --------- |
| 67890	| 242735    |
| 23456	| 203790.75 |
| 123	| 122010    |
| 12345	| 115236.9  |
| 99223	| 57350     |
| 34567	| 54445     |
| 45678	| 52054.2   |
| 567	| 38969     |
| 54321	| 36600     |
| 56789	| 33207     |


#### Find the top 10 ICD codes by total paid amount.
| ICD code | total paid amount |
| ------ | ------- |
| I10	 | 259566  |
| A12.3	 | 152147.0|
| B20	 | 140990  |
| B20.1	 | 105210  |
| C34.91 | 62905   |
| B99.4	 | 51000   |
| E11.65 | 50512   |
| J45.909| 44465.56|
| E11.9	 | 34766.0 |
| A01.1	 | 34260   |


#### Identify CPT codes with a high paid amount per claim by calculating:

average_paid_per_claim = total_paid_amount ÷ claim_count

| CPT code | average paid per claim |
| ----- | -----  |
| 36512	| 25600  |
| 10101	| 17250.6|
| 89012	| 15250  |
| 512   | 14000  | 
| 50255	| 13000  |
| 20610	| 12000  |
| 61234	| 10500  |
| 99217	| 10200  |
| 43752	| 10200  |
| 123	| 10167  |
| 99234	| 10020  |

#### Insights:
1. It can be seen in the first table that CPT code of '67890' drives the total highest spendings among all CPT codes.
2. Also, the ICD code of 'I10' drives the highest total spendings among all CPT codes.
3. However, the CPT code of '36512' takes the lead in average paid amount per claim compared to other CPT codes.
 
### 3. Member-Level Analysis
Calculate total paid amount per member.

Identify the top 5–10 highest-cost members.

For each high-cost member, break down which claim types (inpatient, outpatient, ER, pharmacy) drive their costs.
| member ID | total paid amount | Emergency (%) | Inpatient (%) | Lab (%) | Outpatient (%) | Pharmacy (%) |
| -- | -----    | ----  | ----  | ---   | ---  | ---- |
| 6	 | 43300	| 18.0	| 72.0	| 2.0	| 6.0  | NULL |
| 32 | 40080	| 7.0	| 87.0	| 0.0	| 3.0  | 0.0  |
| 58 | 35920	| 18.0	| 69.0	| NULL  | 10.0 | 0.0  |
| 82 | 30690	| 11.0	| 83.0	| NULL 	| 4.0  | 0.0  |
| 28 | 30560	| 3.0	| 83.0	| 0.0	| 11.0 | 0.0  |
| 20 | 30375	| 9.0	| 82.0	| 1.0	| 5.0  | 0.0  |
| 71 | 30230	| 3.0	| 82.0	| 1.0	| 11.0 | 0.0  |
| 1  | 30120	| NULL  | 92.0	| 1.0	| 5.0  | 0.0  |
| 36 | 25530.75 | 29.0	| 59.0	| 1.0	| 10.0 | 1.0  |
| 8	 | 23046.8	| 18.0	| 75.0	| 1.0	| 6.0  | 0.0  |

#### Insights:
We have outlined the top 10 highest-cost members in the table. It showcases that the claim type of 'Inpatient' make the most of their costs, and the claim type drives the least perportion of their costs.

### 4. Billed vs Paid Ratio
Calculate paid_ratio = paid_amount ÷ billed_amount.

Then compare average paid ratios accross different claims type, by taking the sum of paid amounts divided by sum of billed amounts for each type.

Finally Look for claim types where the insurer pays significantly less or significantly more than the billed amount.
| claim type | weighted paid ratio | claim count |
| --------- | ---- | --- |
| Inpatient | 0.74 | 99  |
| Emergency | 0.77 | 88  |
| Outpatient| 0.8  | 105 |
| Pharmacy  | 0.89 | 81  |
| Lab	    | 0.91 | 76  |

#### Insights:
Comparing all the claim types, claim type 'Inpatient' has the least paid ratio, and 'Lab' has the highest measure. Viewing in general, there are no claim types where the insurer the insurer pays significantly less or significantly more than the billed amount. We will break down this part in the dashboard.

## Dashboard


