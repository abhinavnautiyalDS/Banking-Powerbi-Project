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

## **Q3 Investigate which branch  has the highest number of transactions.**

![image](https://github.com/user-attachments/assets/dce64728-df87-4540-b76c-f1a29b3cda6f)

- Branch 479 Leads in Transactions
  This branch has the highest number of transactions, suggesting it could be in a high-traffic area or serve a large customer base.
- Branch 232 Follows Closely
A slight drop from the top branch but still a key location for banking activity.
- Remaining 8 Branches Have an Equal Number of Transactions (5 Transactions Each)

This indicates a uniform distribution of transaction activity across multiple branches, possibly due to standard service levels or customer distribution.

## **Q4 Using DAX, analyze the correlation between interest rates and account balances. Does a higher interest rate correlate with higher balances?**

I have plotted a scatter plot between interest rate and account balance, and I have also calculated the correlation coefficient between them
![image](https://github.com/user-attachments/assets/d931ee55-a804-4d42-ac09-ed984ab1d739)

Ideallly there should be positive corelation between interset rate and balance, bcz higher interest rate encourage customer to deposite more money leading to higher 
account balance but here the correaltion coefficient is almost zero which shows zero or no relation between them.

there can be multiple reasons for it.
1. the average interset rate in this dataset is 2.67% , if the interest rates offered are generally low, the additional earnings from larger deposits may not be significant enough to motivate customers to save more.

2. because of this low interset rate customer may are choosing diffrent alternative they might invest on mutual funds or stock which could return them more .

## **Q5 Examine the relationship between loan amount and credit score. Do higher credit scores correlate with larger loan amounts?**
![image](https://github.com/user-attachments/assets/923e4050-01d4-42d2-befd-91d1d11c0dc1)

Ideally there should be some kind of relationship between credit score and loan amount 

- Higher Credit Score → Higher Loan Balance (Linear Relationship)
A person with a high credit score is considered low risk by lenders.
They are more likely to qualify for larger loans with lower interest rates.
This creates a positive correlation between credit score and loan balance.

- Lower Credit Score → Lower Loan Balance (Higher Interest Rate)
A low credit score means the borrower is high risk.
Lenders reduce the loan amount to minimise risk.
Even if they get a loan, it comes with a higher interest rate, making it harder to borrow more.

But here  there is almost zero or no correlation between credit score and loan balance.
this means here loan amount may influenced by other factors like income level or there could be diffrent policies accross banks

## **Q6 Analyze transaction trends over time. Are there any noticeable patterns or seasonal fluctuations?**

![image](https://github.com/user-attachments/assets/94421578-2153-4568-8cbb-0f5631580cc8)
![image](https://github.com/user-attachments/assets/61f0a023-12f4-4015-ad00-538d30289fa4)

- **Highest Transactions in Summer (2.7M):**
The peak in summer suggests that people and businesses engage in more financial activity during this season.
Possible reasons? Vacation spending, travel bookings, summer sales, and financial planning for the second half of the year.

- **Slight Drop in Monsoon Season (2.4M):**
While transactions remain high, there's a minor decline compared to summer.
This could be due to less travel and outdoor spending, with people preferring to stay indoors and limit expenses.

- **Lowest Transactions in Winter (2.1M):**
The decline in winter could be related to post-holiday financial caution, where people and businesses recover from year-end spending and focus on savings.
Another reason could be that some industries slow down during colder months, reducing overall transaction volumes.

## **Q7 Calculate the duration of each account's relationship with the bank (from 'OpeningDate' to the most recent transaction date). Who are the longest-standing customers?**
![image](https://github.com/user-attachments/assets/19fbd89d-e399-4510-a07d-32b3a83486f6)

The earliest account opening date in the table is August 2020, with customers consistently transacting up to mid-2025.
Loyal customers such as Elizabeth Anderson, Jessica Taylor, and Robert Miller have maintained active relationships with the bank for the longest period.



















