# Banking Risk Analysis Dashboard
## Project Overview

This project provides a **Power BI dashboard** designed for the banking and financial services sector to help minimize the risk of financial loss from lending money. By leveraging data visualization and analytics, the dashboards enable informed decision-making based on an applicant's profile, helping to determine the likelihood of loan repayment.

## Key Features

- **Risk Analytics:** The dashboard helps banks develop a fundamental understanding of risk analytics by showing how data can be used to mitigate the risk of losing money on loans.

- **Data-Driven Decisions:** With a comprehensive view of client data, banks can make data-driven decisions on whether to approve a loan based on an applicant's profile.

- **KPIs:** The solution includes several key performance indicators (KPIs) to track crucial metrics, such as ```Total Clients```, ```Total Loan```, ```Total Deposit```, and ```Total Fees```.

- **Data Cleaning and Transformation:** The project includes calculated columns to clean and transform the raw data into more useful formats, such as categorizing clients by ```Engagement Timeframe``` and ```Income Band```.

## Dataset

The dataset contains various tables linked by primary and foreign keys, including:

-  ```Banking Relationship```

- ```Client-Banking ```

- ```Gender``` 

- ```Investment Advisor``` 

- ```Period```

## Calculated Measures (DAX)

The following calculated measures were created using Data Analysis Expressions (DAX) in Power BI:

- **Total Clients:** ```DISTINCTCOUNT('Clients - Banking'[Client ID] )``` 

- **Total Fees:** ```SUMX('Clients - Banking' , [Total Loan] * 'Clients - Banking'[Processing Fees] )``` 

- **Engagement Days:** ```DATEDIFF('Clients - Banking'[Joined Bank], TODAY(), DAY )```

- **Total Loan:** ```[Bank Loan] + [Business Lending] + [Credit Cards Balance]``` 

- **Total Deposit:** ```[Bank Deposit] + [Savings Account] + [Foreign Currency Account] + [Checking Accounts]``` 

- **Total CC Amount:** ```SUM('Clients - Banking'[Amount of Credit Cards] )```  

- **Engagement Length:** ```SUM('Clients - Banking'[Engagment Days])``` 

 ## Dashboards and Visualizations
 
The project features multiple dashboards for a comprehensive analysis of banking data:

- **Home:** A high-level overview of key metrics. 

- **Loan Analysis:** Detailed insights into loan data. 

- **Deposit Analysis:** Breakdown of deposit types and amounts. 

- **Summary Dashboard:** A consolidated view of all KPIs. 

## Conclusion

Power BI dashboards are an effective tool for the banking industry. This project demonstrates how a banking operations dashboard can be developed using key metrics and KPIs to provide valuable insights. Banks can use this tool to easily see a client's total loan amount and other crucial information. It can also reveal which types of banks have the most clients and provide insights into which nationalities have the highest bank loans.
















