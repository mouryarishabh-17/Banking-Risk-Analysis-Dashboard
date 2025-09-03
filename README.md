# Banking Risk Analysis Dashboard
This repository contains a Power BI dashboard designed to help financial institutions with risk analytics in banking and financial services. The solution provides a data-driven approach to minimize the risk of losing money on loans by analyzing applicant data and assessing their likelihood of repayment.

## Key Performance Indicators (KPIs)
The following KPIs are tracked to provide a comprehensive overview of banking metrics:

- **Total Clients:** A count of all clients in the banking system.

- **Total Loan:** The combined value of all bank loans, business lending, and credit card balances.

- **Total Deposit:** The sum of all deposits across various account types.

- **Total Fees:** The total amount of fees charged by the bank.

- **Engagement Account:** The total length of client engagement with the bank, measured in days.

- **Bank Loan, Business Lending, Credit Cards Balance:** Individual metrics for each loan category.

- **Bank Deposit, Savings Account Amount, Checking Account Amount, Foreign Currency Amount:** Individual metrics for each deposit category.

## Visualizations and Analysis
The project includes several dashboards for detailed analysis:

- **Home Dashboard:** A high-level summary of all major KPIs.

- **Loan Analysis Dashboard:** Provides a detailed breakdown of loan data by banking relationship, income band, and nationality.

- **Deposit Analysis Dashboard:** Offers insights into deposit data, categorized by banking relationship, income band, and nationality.

- **Summary Dashboard:** A consolidated view of all key metrics for easy monitoring.

## Dataset
The analysis is based on a Dataset that includes detailed information about bank accounts and clients, structured across multiple interconnected tables: ```Banking Relationship```, ```Client-Banking```, ```Gender```, ```Investment Advisor```, and ```Period```.


## Data Cleaning and Calculated Functions
The following transformations and calculations were applied to the raw data using **Power BI's DAX formulas**.

### Column Creation
These are the calculated columns created to clean and prepare the data.
- **Engagement Timeframe**
```
Engagement Timeframe = 
SWITCH(TRUE(),
'Clients - Banking'[Engagment Days] < 365, "< 1 Years",
'Clients - Banking'[Engagment Days] < 1825, "< 5 Years",
'Clients - Banking'[Engagment Days] < 3650, "< 10 Years",
'Clients - Banking'[Engagment Days] < 7300, "< 20 Years",
"> 20 Years"
)
```
- **Engagment Days**
```
Engagment Days = 
DATEDIFF('Clients - Banking'[Joined Bank],TODAY(), DAY)
```
- **Income Band**
```
Income Band = 
SWITCH(TRUE(),
'Clients - Banking'[Estimated Income] < 100000, "Low",
'Clients - Banking'[Estimated Income] < 300000, "Mid",
"High"
)
```
- **Processing Fees**
```
Processing Fees = 
SWITCH('Clients - Banking'[Fee Structure],
"High",0.05,
"Mid",0.03,
"Low",0.01,
0
)
```
### DAX Measures
These are the DAX measures used to calculate the various KPIs.

- **Total Clients**
```
Total Clients = DISTINCTCOUNT('Clients - Banking'[Client ID])
```
- **Total Loan**
```
Total Loan = SUM('Clients - Banking' [Bank Loan]) + SUM('Clients - Banking'[Business Lending]) +
             SUM('Clients - Banking'[Credit Cards Balance])
```
- **Total Deposit**
```
Total Deposit = SUM('Clients - Banking'[Bank Deposit]) + SUM('Clients - Banking'[Savings Account]) +
                SUM('Clients - Banking'[Foreign Currency Account]) + SUM('Clients - Banking'[Checking Accounts])
```
- **Total Fees**
```
Total Fees = SUMX('Clients - Banking' , [Total Loan] * 'Clients - Banking'[Processing Fees])
```
- **Total CC Amount**
```
Total CC Amount = SUM('Clients - Banking'[Amount of Credit Cards])
```
- **Engagement Length**
```
Engagment Length = SUM('Clients - Banking'[Engagment Days])
```
## Conclusion and Future Work
Power BI dashboards are effective resources for the banking sector, empowering them with data visualization techniques and key performance metrics.

These dashboards can help banks understand a particular investor's total loan amount and other details. Future applications include:

- **Strategic Planning:** Identifying which types of banks have more clients (e.g., private banks) to help other banks develop strategies for client acquisition.


- **Risk Assessment:** Gaining insights into which nationalities have the highest bank loans to inform risk models.


- **Account Analysis:** Providing information on the various amounts in different types of accounts held by investors













