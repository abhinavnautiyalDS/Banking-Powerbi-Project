![image](https://github.com/user-attachments/assets/e1930944-db51-42ae-a804-6268bbd13fb4)


# **Banking Analytics Using Power BI**


Unlocking Financial Insights in Banking Data

# **Introduction**

Financial institutions operate in a data-intensive environment where understanding customer behavior, risk assessment, and transaction patterns is crucial. As a data analyst at FinInsight Group, a consultancy specializing in banking analytics, the primary objective is to extract actionable insights from banking datasets. This project involves analyzing two comprehensive datasets: 'Banking Transactions' and 'Customer Account Details.' Leveraging Power BI, the study focuses on identifying trends, relationships, and financial patterns that impact banking operations.

# **Problem Statement**

Banking institutions struggle with understanding customer financial behavior, managing risks, and optimizing services. The challenge is to interpret vast amounts of transactional and account-related data to enhance customer relationships, improve risk assessment models, and drive strategic business decisions. This study aims to bridge this gap by providing a data-driven approach to analyzing banking data.

# **Dataset Overview**

We have Two Dataset Banking Dataset 1 and 2

## **1. BankingDataset1**
   contains information of transactions 

- **TransactionID**: A unique identifier for each transaction.
- **AccountNumber**: The account number associated with the transaction. (Foreign Key)
- **TransactionType**: The type of transaction (e.g., Transfer, Deposit, Withdrawal, Payment).
- **Amount**: The amount of money involved in the transaction.
- **TransactionDate**: The date when the transaction occurred.
- **BranchCode** : The code of the bank branch where the transaction took place.
- **Currency**: The currency in which the transaction was made.
- **TransactionTime**: The time of day when the transaction occurred (in hours).

## **2. BankingDataset2**

: contains information of accountholder

- **AccountNumber**: A unique identifier for each account, corresponding to 'AccountNumber' in "BankingDataset1.xlsx". (Primary Key)
- **AccountHolder**: The name of the account holder.
- **AccountType** : The type of account (e.g., Credit, Loan, Checking).
- **Balance**: The current balance of the account.
- **InterestRate**: The interest rate applicable to the account.
- **CreditScore**: The credit score of the account holder.
- **OpeningDate**: The date when the account was opened.
- **LoanAmount**: The amount of loan associated with the account (if applicable).
- **AccountHolderDetails**: Details about account holders -


# **Merging and Data Preprocessing**

- merged the two tables using the AccountNumber column, which is common in both datasets.
- There were some missing values in columns like AccountHolder and others, which I removed.
- replaced null values in the Balance column with 0.
- removed unwanted values such as -999, *^#, and $.
- split the address details into multiple columns, including Sector, City, and Year of Living.

# **Exploratory Data Analysis**

## **Q1.  Calculate the average account balance for each account type. Which account type has the highest average balance?**

![image](https://github.com/user-attachments/assets/0564c448-be8a-4687-ab3c-e004ca91d6b0)

**Savings Accounts Have the Highest Balance (25.2K)**
 - It Makes sense,People park their money here for long-term goals, emergency funds, or just to earn some interest. Plus, many banks require a minimum balance, so customers tend to keep more in these accounts.
   
**Credit Accounts Hold a Surprisingly High Balance (24.3K)**
- This could mean customers have high credit limits or use their cards regularly but pay off balances on time. It also suggests responsible credit usage or even customers carrying some revolving debt while managing payments well.
  
**Checking Accounts Sit in the Middle (22.2K)**

- No surprises here—this is the go-to account for everyday spending, bills, and direct deposits. Since checking accounts usually don’t offer much interest, people don’t keep large sums sitting idle.

**Loan Accounts Have the Lowest Balance (21.2K)**

- Loans shrink over time as people pay them off, which explains the lower balance. It could also mean that most loans in this dataset are on the smaller side or customers are managing their debt well.

## **Q2 Analyze the impact of currency exchange rates on transaction amounts. Convert all transactions to a standard currency for comparison.**

This dataset contains amounts in multiple currencies, so I converted all currencies into a standard one—US dollars—using their respective exchange rates.

![image](https://github.com/user-attachments/assets/935bbb81-fe46-4873-b071-8fe7080e14fe)

- USD Shows a Significant Increase in Converted Amount (4.6M vs. 1.0M)
The large gap suggests that the exchange rate has a strong impact when converting transactions in USD. A weaker local currency against the USD could be a major factor.
- GBP Also Shows a Notable Increase (1.6M vs. 0.9M)
- EUR Remains Almost Unchanged (1.1M in Both Values)
- JPY Shows No Increase in Converted Amount (0.0M vs. 1.0M)











