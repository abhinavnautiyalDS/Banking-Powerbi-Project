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

## **Q8 Identify high-value transactions and analyze their characteristics. What constitutes a high-value transaction in your analysis?**

High-value customers are those who spend more than a certain threshold. In my case, I have set this threshold at 10,000, as it represents the 80th percentile value.
![image](https://github.com/user-attachments/assets/2f9b2eaa-2246-49c6-baca-cd50b73f46a8)

1.  **High-Value Customers by Sector**
Education and Healthcare have the most high-value customers
This suggests that professionals from these industries earn well and engage actively with financial products.
Finance has the lowest count despite being a money-centric field.
This could indicate that finance professionals prefer diversified investments outside traditional banking.
2. **High-Value Customers by Account Type**
Savings and Checking accounts dominate 
High-value customers prefer liquidity and easy access to funds rather than locking them in long-term investments.
Loan-based customers are the lowest
This suggests that high-value customers rely less on borrowing and more on managing their own capital.
3. **High-Value Customers by Payment Type**
Withdrawals, Transfers, and Payments are equally high 🔄
High-value customers are financially active and regularly move money across accounts.
Deposits are slightly lower, but still significant
This means these customers continue to put money into the bank, but their spending/transactions are equally high.


## **Q9 Investigate if there are patterns in the times of day when different types of transactions are made.**
![image](https://github.com/user-attachments/assets/72922b97-ddfc-4699-8b92-86fc06dbc628)
- Transaction Volume Increases Throughout the Day:
Transactions are lowest during Late Night (171) and increase steadily through the Evening (193) and Afternoon (215), reaching their peak in the Morning (222).
This suggests that customers are more active in making transactions during the Morning and Afternoon than at night.

- Transaction Type Patterns:
Deposits are highest in the Morning (59) and lowest during Late Night (37).
Payments remain relatively stable throughout the day, with slight variations.
Transfers peak in the Morning (60) and Afternoon (57), indicating that fund movements are higher during business hours.
Withdrawals increase as the day progresses, peaking in the Morning (54) and Afternoon (49).

- Business Hours Drive Transactions:
Since transactions peak in the Morning and Afternoon, this suggests that banking and financial activities are primarily driven by business hours and customer convenience.
The lower transaction count at Late Night aligns with fewer banking operations and reduced customer activity.

## **Q10 Analyze the distribution of credit scores among account holders. What insights can you gather?**

![image](https://github.com/user-attachments/assets/396df908-6208-4108-8c04-2f3226702638)

- Majority of Account Holders Have a Poor Credit Score:
The largest segment (407 account holders) falls under the "Poor" credit score category.
This suggests that a significant proportion of customers may have financial difficulties, high debt levels, or a history of missed payments.

- Smaller Proportion of High Credit Score Customers:
Only 82 account holders have an "Excellent" credit score, and 86 have a "Very Good" score.
This indicates that financially stable and highly creditworthy customers are a minority.

- Fair to Good Credit Score Holders Are Relatively Balanced:
Fair (120) and Good (106) credit score holders are almost equal in number.
These customers might be on the verge of improving or worsening their creditworthiness depending on their financial behavior.

## **Q11 Explore if there's a correlation between the age of an account (time since opening) and its current balance.**

![image](https://github.com/user-attachments/assets/e25fc7a3-bc0e-44a0-aebc-cdb059b2b971)

- **Ideally**
 In many banking scenarios, one might expect a positive correlation between a customer’s tenure and their account balance. The longer someone banks with an institution, the more opportunities they have to grow their savings, accumulate interest, or deposit larger amounts. Over time, loyal customers might consolidate their finances, leading to increasing balances.

-**What the Data Shows (-0.04)**
However, our actual data reveals a very weak negative correlation between tenure and balance. A value of -0.04 is so close to zero that it essentially indicates no meaningful relationship. In other words, how long someone has been with the bank doesn’t necessarily predict whether their balance is high or low.

- Possible Reasons for This Discrepancy
- - **Multiple Bank Relationships:**
Customers may spread their savings and investments across different banks or platforms, reducing the chance of a growing balance in just one institution.
- - **Varied Financial Goals:**
Long-standing customers might have specific reasons for keeping balances low, such as using other investment vehicles (stocks, mutual funds, real estate) instead of a bank account.

## **Q12 Create a measure to rate branches based on transaction volume and value.**

For this, I created a measure called Branch Performance Score using the following formula:
Branch Performance Score = 0.5 × Transaction Count + 0.5 × Transaction Volume

![image](https://github.com/user-attachments/assets/0234c0fb-0da0-48c7-8177-e486ae598efe)

- **Highest Performing Branches:**
Branch 479 has the highest performance score (0.777), driven by the highest normalized transaction count (1.00).
Branch 466 follows closely (0.772), likely due to its high transaction volume.

- **Low Performing Branches:**
Branches with a low transaction count or low volume have a lower performance score despite contributing significantly in one metric.

## **Q13 Using DAX, develop a risk assessment model based on transaction patterns, account balances, and credit scores.**

A risky transaction could be one that follows these patterns:

- Transaction Patterns: Frequent high-value transactions may indicate risk if high_value_transaction = 1.
- Account Balances: Lower balances may correlate with higher risk if balance < 1000.
- Credit Scores: A lower credit score increases the risk if the credit score is Poor or Fair.
- 
I have created a calculated column called Credit Risk based on the above conditions and categorized it into Very Low Risk, Low Risk, Medium Risk, and High Risk.

![image](https://github.com/user-attachments/assets/0e2b898f-2ab0-4e4b-8277-f8ede670f365)

- **Count of Accounts by Credit Risk:**

The majority of accounts fall under Very Low Risk.
Higher-risk categories (Medium and High Risk) have significantly fewer accounts.
Average Balance by Credit Risk:

- **Very Low Risk accounts have the highest average balance (~25K).**
As risk increases, the average balance decreases, with High Risk accounts having the lowest balances.

- **Average Credit Score by Credit Risk:**
Interestingly, Low Risk accounts have the highest average credit score.
High Risk accounts have the lowest credit scores, confirming that lower credit scores correlate with higher risk.


# **Dashboard**

### ** Dashboard 1**

![Time series](https://github.com/user-attachments/assets/2081c348-1b4f-4b6f-a092-41f3c7a3cd8a)

1. **Account Opening Trends (Top Left)**
- Insight: Account openings peaked in March (37 accounts) and July (32 accounts) but declined significantly in the later months (November & December at 13).
- Possible Reasons:
- Seasonality: Certain months may attract more new customers due to marketing campaigns, promotions, or financial cycles.
- Customer Behavior: The decline in account openings towards the year-end could be due to reduced financial activity.
  
2. **Monthly Transactions by Account Type (Top Right)**
- Insight: Checking & Credit accounts have the highest transaction volume, followed by Loan and Savings.
Transaction activity fluctuates across months, with some peaks in March and July.
- Possible Reasons:
Checking & Credit are frequently used for daily transactions, whereas Loan & Savings accounts may see fewer movements.
Certain months might involve higher spending (e.g., summer vacation, back-to-school season).

3. **Transaction Patterns Over Time (Bottom Left)**
- Insight: The overall transaction volume remains stable over time, with occasional slight fluctuations.
   A sudden drop in July 2024 might indicate a reporting delay, a seasonal trend, or policy changes.
- Possible Reasons:
Economic conditions could influence spending behavior.
System updates or reporting adjustments may cause a temporary drop.

4. **Sum of Amount (USD) and Count of Transactions by Month (Bottom Right)**
- Insight:
Transaction amounts were highest between March–July, then declined from August onward.
Transaction count follows a similar downward trend.
- Possible Reasons:
Customers might spend more in the first half of the year, influenced by tax refunds, bonuses, or planned purchases.
The decline after July suggests seasonal changes in spending habits or lower financial activity post-holiday.


### **Dashboard2**
![loan data dashboard](https://github.com/user-attachments/assets/84cbf51b-cc22-494e-ae08-468179216d09)

1. **Overall Loan and Credit Metrics**
- Total Loan Amount: 8.55M
- Total Credit Score Sum: 183K
- Credit Score Measure: 849 (Likely the highest credit score recorded)

2. **Average Loan Amount by Account Type (Bottom Left)**
- Insight:
Savings and Credit accounts have the highest average loan amounts.
Checking and Loan accounts have lower average loan amounts.
- Possible Reasons:
Savings accounts may be linked to secured loans (higher amounts).
Credit accounts might be associated with credit-based borrowing.

3. **Credit Score vs. Loan Amount (Middle Bottom)**
- Insight:
Loan amounts vary widely across different credit scores.
Borrowers with higher credit scores tend to receive higher loan amounts.

- Possible Reasons:
Lenders trust high credit score individuals, leading to higher approved loan amounts.
Lower credit scores may limit borrowing capacity.

4.  **Loan Distribution by Interest Rate (Bottom Right)**

- Insight:
The distribution of interest rates is quite dense, indicating many accounts with varying interest rates.
- Possible Reasons:
Loans might be offered at customized rates based on creditworthiness and risk factors.
Lower interest rates may be offered to high credit score individuals, while higher risk borrowers receive higher rates.

### **Dashboard3**


![transection and acount date dashboard](https://github.com/user-attachments/assets/c1cf8809-c327-4807-a1e9-1dab31c89b31)

1. **Distribution of Transaction Types (Pie Chart - Top Left)**

- Transfers (24.73%) and Payments (22.94%) are the most common transaction types.
- Deposits (23.84%) are also significant.
- Withdrawals (22.4%) make up a smaller portion.
- Unknown transactions (6.09%) exist but are relatively low.

- Possible Reasons:

Customers rely heavily on transfers and payments, suggesting frequent financial activity.
The high deposit percentage indicates substantial inflows into accounts.
Unknown transactions could be system errors, unclassified transactions, or pending verifications.

2. **Yearly Trend in Transaction Amounts (Line Chart - Top Right)**
   
- Observation:
Transaction amounts have declined across all transaction types from 2023 to 2024.
Deposits, Payments, and Transfers show similar downward trends.
Unknown transactions remain consistently low.

- Possible Reasons:

Market slowdown, economic changes, or lower customer activity.
A possible shift toward alternative banking or investment options.
Banking policy changes affecting transactions.

3. **Transaction Amount by Currency (Stacked Bar Chart - Bottom Left)**
Observation:

USD, EUR, and GBP dominate the transaction amounts.
Each currency has a diverse mix of deposits, payments, transfers, and withdrawals.

- Possible Reasons:

USD dominance suggests international transactions.

4. **Credit Score Segmentation (Pie Chart - Bottom Right)**
- Observation:
Good credit score users (60.53%) outnumber average score users (39.47%).
- Possible Reasons:
A majority of users maintain good credit, possibly due to strict bank policies on creditworthiness.
Average credit users (39.47%) indicate potential lending opportunities for financial institutions.


# **Conclusion**

This project involved an in-depth analysis of customer transactions, loan data, and account trends to uncover patterns in financial behaviors. The dashboards created provided valuable insights into transaction trends, loan distributions, and credit scores, helping to understand the key factors influencing financial decision-making.

- Key Findings:
1. **Time-Based Analysis:**

- Account openings fluctuated over the year, with a notable decline in later months.
- Transaction volumes remained stable, but the total transaction amount decreased over time, indicating potential shifts in spending behavior.

2. **Loan Data Analysis:**

- Loan amounts varied across account types, with savings and credit accounts having higher loan amounts.
- A strong correlation between credit scores and loan amounts was observed, suggesting that customers with higher credit scores tend to secure larger loans.
- Loan distributions by interest rates appeared consistent, indicating stable lending policies.

3. **Transaction and Account Analysis:**
   
- Transfers, deposits, and payments dominated transaction types, highlighting common financial activities.
- Transactions declined over time, possibly due to economic shifts or evolving banking preferences.
- A majority of customers had a good credit score, but a significant portion fell into the average category, presenting potential risks and lending opportunities.
  
**Overall Impact:**
This project successfully identified key financial trends that can assist businesses, banks, and financial institutions in making data-driven decisions. The insights can be used to optimize lending strategies, improve transaction security, and enhance customer engagement.















