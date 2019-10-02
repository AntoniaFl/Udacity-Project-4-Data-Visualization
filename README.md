# Udacity-Project-4-Data-Visualization

In this notebook I will be analysing data from the P2P lending marketplace "Prosper" (https://www.prosper.com/ ), in order to get an insight into which loans, borrowers and variables affecting likelihood of default.  The dataset contains 113,937 loans with 81 variables on each loan, including loan amount, borrower rate (or interest rate), current loan status, borrower income, and many others.

The Data is available for download in csv format, along with the variable dictionary.

# Summary of findings:

**Summary of Insights from Univariate Explorations: Loan Parameters**

- Most loans (around 69%) are for the term of 36 months (3 years). Around 29% of all loans are taken out for 60 months (5 years) and only around 2% of all loans are taken out for a year.

- The distribution of original loan amounts is skewed to the right, with a few very high loans (like 35000 USD), but the majority being just under 5000 USD. People usually borrow round sums so there are spikes around 10000 USD, 15000 USD, 20000 USD and 25000 USD.

- Regarding the distribution of the Borrower's APR, this seems to be evenly distributed with most borrowers getting an APR between 0.16 and 0.29. There is a spike around 0.37 suggesting a certain group of borrowers getting this higher amount.

- Of all loans between 2009 and now, 67% are current, 23% are completed, 6% are charged off and 1% are defaulted. The rest are in progress.

- The most common prosper rating is C (around 21%) followed by B (around 18%) and A (around 17%). There are also 8 % that are High risk and 6 % that are rated AA.

**Summary of Insights from Univariate Explorations: Client Parameters**

- The vast majority of loans were taken out for "Debt consolidation" (62.7%). This is followed by "Other"(10.8%) and "Home Improvement" (8%) and "Business" (6%).

- Looking at the employment status of the borrowers, we can tell that the vast majority are employed/full time employed (88%), while 5% are self employed, 0.4 % are retired and 0.3% are employed part-time.

- In terms of occupation most simply refer to themselves as "other" or "professional" - this vague description would be worth looking into more closely for future loans. These categories are followed by "Executive", "Computer programmer", "Teacher" and "Analyst".

- The income ranges from 0 to 12000 USD per month with a few outliers. The median (which we use to avoid bias through outliers) however sits around 5000 USD monthly. Looking at this from the variable of income range this is around 25,000 - 75,000 USD.

- About half are homeowners, and half are not.

- The debt-to-income ratio is skewed to the right with most borrowers being at around 0.2.

**Insights from Bivariate Exploration:**

- Borrowers borrowing higher sums will opt for longer loan terms - this makes sense. Generally 12 month terms will be under 5000 USD, whereas the loan original amount for a 60 month term is more varied.

- It is also to be expected that borrowers of higher income will opt for a higher original amount, which is also what we found. Those of income under 25000 will often opt for a 5000 USD loan, while those above will opt for more - often at "round sums" such as 10,000 USD, 15,000 USD or 20,000 USD etc.

- Lower Prosper Ratings will recieve a higher Borrower APR, to make up for the risk.

- Higher incomes seem to indicate current or completed loans, while lower incomes tend to be past due or defaulted.

- Current loans are of very high values, indicating Prosper is now focussing more on loans of larger original amounts. Moreover, looking at the amounts of completed vs defaulted/chargedoff, we can see that loans with higher original amounts are slightly more likely to be completed, and smaller loans are slightly more likely to not be repayed.

**Insights from Multivariate Exploration:**

- Borrowers of higher income will usually borrow larger amounts of money. These are also most likely to get a higher prosper rating.

- Throughout the last 6 years homeowners have always gotten a marginally lower APR. The average APR of Prosper Loans has fallen steadily.

- In 2013 Prosper decided to drastically increase the Borrower APR for Not Employed borrowers. Borrowers of Status Self-Employed and Not employed have always had among the highest Borrower APRs and Full Time Employed the lowest.

- Loan amounts have increased drastically for highly rated loans over the last 5 years as Prosper.

# So what story do these findings tell us?

- We have seen that it is slightly less risky for Prosper to give out larger loans, as these are more likely to be completed than defaulted or written off.

- Homeowners will also be favoured clients as they are less risky and are given lower rates.

- From our explorations we can also see that the loan amount over time has increased.

- Moreover, we have also seen that the loan amounts for higher rated loans have drastically increased over the last five years, while the lower rated loans have stayed within the same amount.

- This may indicate that Prosper is actively searching for, and attracting wealthier, less risky borrowers and divesting from smaller, riskier loans.

- It looks like Prosper, for the last five years, have been doing this as an active strategy because of the fact that larger loans are less likely to default and are therefore more profitable.


# Reflection

During this analysis, there were sevaral difficulties to overcome. One of the biggest challenges was the sheer amount of variables in the dataset - 81 variables. Without any prior financial knowledge of loans it was very difficult to understand each, and narrow down which ones I would end up looking at more closely. This also made it difficult to decide what topics to focus on, and I often ended up wasting time with variables that were not really relevant to the questions I wanted to ask. It was helpful to look at Prosper's dictionary in order to understand the variables better. The solution to this was to split the variables into loan-specific and client-specific variables, and focus on only a handful of variables. The variables I chose to explore more closely were: 

Loan Parameters

- Term (Term) 
- Loan amount (LoanOriginalAmount) 
- Loan rate (BorrowerAPR)
- Loan Status (LoanStatus) 
- Prosper Rating (ProsperRating_Alpha) 

Client Parameters

- Reason for loan (ListingCategory_Numeric) 
- Employment Status (EmploymentStatus) 
- Occupation (Occupation)
- Duration (EmploymentStatusDuration)
- Income (StatedMonthlyIncome)
- Homeowner (IsBorrowerHomeowner)
- Debt to Income Ratio (DebtToIncomeRatio)


During my initial analysis I noticed a few issues that needed to be wrangled. I made the decision to only analyze the dataset from 2009 onwards as I did not want to work with missing data. However, given that Prosper most likely changed their business model and client base after 2009 it would have in hindsight been interesting to see the data from before 2009 as well (working around the missing data). With this in mind it would also be interesting to see more data in the future to understand how the new strategy is working out for them. 

In the next step I started to understand the data set structure and the variables themselves more closely. To do this I used summary functions ((describe(), info() etc.) and basic data visualization techniques (histograms, boxplots etc.). 

Next, I started to look at the relationship between variables that I thought could be interesting - using violin, box plots, scatter plots and bar plots. I made sure to avoid double-encoding these plots with different colours if the labels already existed. 

And lastly, I used multivariate visualizations using colour to add a third variable to relationships that had already shown interesting correlations in the bivariate exploration stage. It was at this stage that I realized I was missing something, and I added an exploration into variables over time. 

In hindsight, I found it difficult to spot a trend until I decided to look at certain variables over time (especially loan quantities and borrower APR by rating over time). This then showed me how Prosper has changed the types and quantities of loans - and led me to go back to my earlier analysis and look at certain relationships more closely (e.g. likelihood of default vs loan quantity). I then started to understand why the changes over time were occuring - most likely as part of Prosper's new strategy.

