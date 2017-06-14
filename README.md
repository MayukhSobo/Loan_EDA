
# Prosper Loan Data Analysis

## Introduction
This data set contains 113,937 loans with 81 variables on each loan, including loan amount, borrower rate (or interest rate), current loan status, borrower income, borrower employment status, borrower credit history, and the latest payment information.

## Data
The data is available in the CSV format and can be downloaded from 
[**Here**](https://www.google.com/url?q=https://s3.amazonaws.com/udacity-hosted-downloads/ud651/prosperLoanData.csv&sa=D&ust=1496756846241000&usg=AFQjCNElEYjVf30dH0pH07Q-YkyjDNIt0g). A detailed information of the variables is mentioned [**Here**](https://docs.google.com/spreadsheets/d/1gDyi_L4UvIrLTEC6Wri5nbaMmkGmLQBk-Yx3z0XDEtI/edit#gid=0) 

## Variables Explored
1.	**Term :** Amount of month customers opted for loan
2.	**LoanStatus :** Current status of the loan like chargedoff, completed, defauted etc...
3.	**EstimatedEffectiveYield :** Yield of lenders from borrowers minus the processing fee and late fines
4.	**ProsperScore :** Risk Factor score from 1 to 10. 10 being least risky
5.	**BorrowerAPR :** The Borrower's Annual Percentage Rate (APR) for the loan.
6.	**BorrowerRate :** The Borrower's interest rate for this loan. 
7.	**ListingCategory..numeric. :** Prosper rating for borrowers in numbers
8.	**EmploymentStatus : ** Current type of employment 
9.	**Occupation :** Occupation of borrower at the time of listing
10. **EmploymentStatusDuration :** How long the employee has been employed
11.	**IsBorrowerHomeowner :** Does the borrower owns house at the time of listing (True & False)
12.	**ProsperRating..Alpha. :** Prosper rating for borrowers in alphabets
13.	**IncomeVerifiable :** If the income of the borrower is verifiable at the time of listing (True & False)
14.	**StatedMonthlyIncome :** Monthly income of the borrower
15.	**MonthlyLoanPayment :** Monthly loan payment amount
16.	**Recommendations :** Recommendations the borrowers has at the time of listing
17.	**DebtToIncomeRatio :** The debt to income ratio of the borrower at the time the credit profile was pulled. 
18.	**LoanOriginalAmount :** Original amount of the loan
19.	**LoanOriginationQuarter :** Quarter of the month when loan was originated

## Exported Report
- **Simplified HTML:** [Download](https://raw.githubusercontent.com/MayukhSobo/Loan_EDA/master/EDA_Loan.nb.html)
- **Curated HTML:** [Download](https://github.com/MayukhSobo/Loan_EDA/raw/master/EDA_Loan.html)
- **Hosted Curated HTML:** [Read](http://rpubs.com/mayukhsobo/prosper_loan_data_analysis)
- **Knitr Simplified PDF:** [Download](https://raw.githubusercontent.com/MayukhSobo/Loan_EDA/master/EDA_Loan.pdf) *(Recommended)*
- **MS Docx:** [Download](https://github.com/MayukhSobo/Loan_EDA/raw/master/EDA_Loan.docx)
- **Markdown:**[Download](https://github.com/MayukhSobo/Loan_EDA/raw/master/EDA_Loan.md) (without plots)
- **Hosted PDF :** [Read](http://mydo.cx/MDUxNDEw)

## Dependent Packages
1. [**ggplt2**](ggplot2.tidyverse.org)
2. [**ggthemes**](https://github.com/jrnold/ggthemes)
3. [**dplyr**](https://cran.r-project.org/web/packages/dplyr/index.html)
4. [**reshape2**](https://cran.r-project.org/web/packages/reshape2/index.html)
5. [**memisc**](https://cran.r-project.org/web/packages/memisc/index.html)
6. [**gridextra**](https://cran.r-project.org/web/packages/gridExtra/index.html)
7. [**RColorBrewer**](https://cran.r-project.org/web/packages/RColorBrewer/index.html)
8. [**plotrix**](https://cran.r-project.org/web/packages/plotrix/index.html)
9. [**DT**](https://cran.r-project.org/web/packages/DT/index.html)
10. [**scales**](https://cran.r-project.org/web/packages/scales/index.html)
