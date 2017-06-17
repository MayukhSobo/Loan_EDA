# Prosper Loan Data Analysis
Mayukh Sarkar  





## Introduction
This dataset is financial dataset and this is related to the loan, borrowers, lenders, interest rates and stuffs like that. Prosper or [Prosper Marketplace Inc.](https://www.prosper.com/) is a San Francisco, California based company specializing in loans at low interest rates to the borrowers. In this dataset, we are using the data from the Posper to analyse it and trying to find the pattern in the Prosper data. This may be tedious because of the sheer size of the dataset and the complicated nature of all the financial datasets. We are using R, an advanced high level programming language of the analysis with some of its most popular graphic package ```ggplot```. The codes are not visible in the HTML/PDF export for the simlicity but the codes can be reviewed from the RMD file. 

The dataset is comprised of 81 variables and contains 113937 entries. The variable that are explored in the dataset are the following 
Term : Amount of month customers opted for loan

**LoanStatus** : Current status of the loan like chargedoff, completed, defauted etc...

**EstimatedEffectiveYield** : Yield of lenders from borrowers minus the processing fee and late fines

**ProsperScore** : Risk Factor score from 1 to 10. 10 being least risky

**BorrowerAPR** : The Borrower's Annual Percentage Rate (APR) for the loan.

**BorrowerRate** : The Borrower's interest rate for this loan.

**ListingCategory..numeric.** : Prosper rating for borrowers in numbers

**EmploymentStatus** : Current type of employment

**Occupation** : Occupation of borrower at the time of listing

**EmploymentStatusDuration** : How long the employee has been employed

**IsBorrowerHomeowner** : Does the borrower owns house at the time of listing (True & False)

**ProsperRating..Alpha.** : Prosper rating for borrowers in alphabets

**IncomeVerifiable** : If the income of the borrower is verifiable at the time of listing (True & False)

**StatedMonthlyIncome** : Monthly income of the borrower

**MonthlyLoanPayment** : Monthly loan payment amount

**Recommendations** : Recommendations the borrowers has at the time of listing

**DebtToIncomeRatio** : The debt to income ratio of the borrower at the time the credit profile was pulled.

**LoanOriginalAmount** : Original amount of the loan

**LoanOriginationQuarter** : Quarter of the month when loan was originated

A basic exploration of the datset would give the following information

```
## 'data.frame':	113937 obs. of  81 variables:
##  $ ListingKey                         : Factor w/ 113066 levels "00003546482094282EF90E5",..: 7180 7193 6647 6669 6686 6689 6699 6706 6687 6687 ...
##  $ ListingNumber                      : int  193129 1209647 81716 658116 909464 1074836 750899 768193 1023355 1023355 ...
##  $ ListingCreationDate                : Factor w/ 113064 levels "2005-11-09 20:44:28.847000000",..: 14184 111894 6429 64760 85967 100310 72556 74019 97834 97834 ...
##  $ CreditGrade                        : Factor w/ 9 levels "","A","AA","B",..: 5 1 8 1 1 1 1 1 1 1 ...
##  $ Term                               : int  36 36 36 36 36 60 36 36 36 36 ...
##  $ LoanStatus                         : Factor w/ 12 levels "Cancelled","Chargedoff",..: 3 4 3 4 4 4 4 4 4 4 ...
##  $ ClosedDate                         : Factor w/ 2803 levels "","2005-11-25 00:00:00",..: 1138 1 1263 1 1 1 1 1 1 1 ...
##  $ BorrowerAPR                        : num  0.165 0.12 0.283 0.125 0.246 ...
##  $ BorrowerRate                       : num  0.158 0.092 0.275 0.0974 0.2085 ...
##  $ LenderYield                        : num  0.138 0.082 0.24 0.0874 0.1985 ...
##  $ EstimatedEffectiveYield            : num  NA 0.0796 NA 0.0849 0.1832 ...
##  $ EstimatedLoss                      : num  NA 0.0249 NA 0.0249 0.0925 ...
##  $ EstimatedReturn                    : num  NA 0.0547 NA 0.06 0.0907 ...
##  $ ProsperRating..numeric.            : int  NA 6 NA 6 3 5 2 4 7 7 ...
##  $ ProsperRating..Alpha.              : Factor w/ 8 levels "","A","AA","B",..: 1 2 1 2 6 4 7 5 3 3 ...
##  $ ProsperScore                       : num  NA 7 NA 9 4 10 2 4 9 11 ...
##  $ ListingCategory..numeric.          : int  0 2 0 16 2 1 1 2 7 7 ...
##  $ BorrowerState                      : Factor w/ 52 levels "","AK","AL","AR",..: 7 7 12 12 25 34 18 6 16 16 ...
##  $ Occupation                         : Factor w/ 68 levels "","Accountant/CPA",..: 37 43 37 52 21 43 50 29 24 24 ...
##  $ EmploymentStatus                   : Factor w/ 9 levels "","Employed",..: 9 2 4 2 2 2 2 2 2 2 ...
##  $ EmploymentStatusDuration           : int  2 44 NA 113 44 82 172 103 269 269 ...
##  $ IsBorrowerHomeowner                : Factor w/ 2 levels "False","True": 2 1 1 2 2 2 1 1 2 2 ...
##  $ CurrentlyInGroup                   : Factor w/ 2 levels "False","True": 2 1 2 1 1 1 1 1 1 1 ...
##  $ GroupKey                           : Factor w/ 707 levels "","00343376901312423168731",..: 1 1 335 1 1 1 1 1 1 1 ...
##  $ DateCreditPulled                   : Factor w/ 112992 levels "2005-11-09 00:30:04.487000000",..: 14347 111883 6446 64724 85857 100382 72500 73937 97888 97888 ...
##  $ CreditScoreRangeLower              : int  640 680 480 800 680 740 680 700 820 820 ...
##  $ CreditScoreRangeUpper              : int  659 699 499 819 699 759 699 719 839 839 ...
##  $ FirstRecordedCreditLine            : Factor w/ 11586 levels "","1947-08-24 00:00:00",..: 8639 6617 8927 2247 9498 497 8265 7685 5543 5543 ...
##  $ CurrentCreditLines                 : int  5 14 NA 5 19 21 10 6 17 17 ...
##  $ OpenCreditLines                    : int  4 14 NA 5 19 17 7 6 16 16 ...
##  $ TotalCreditLinespast7years         : int  12 29 3 29 49 49 20 10 32 32 ...
##  $ OpenRevolvingAccounts              : int  1 13 0 7 6 13 6 5 12 12 ...
##  $ OpenRevolvingMonthlyPayment        : num  24 389 0 115 220 1410 214 101 219 219 ...
##  $ InquiriesLast6Months               : int  3 3 0 0 1 0 0 3 1 1 ...
##  $ TotalInquiries                     : num  3 5 1 1 9 2 0 16 6 6 ...
##  $ CurrentDelinquencies               : int  2 0 1 4 0 0 0 0 0 0 ...
##  $ AmountDelinquent                   : num  472 0 NA 10056 0 ...
##  $ DelinquenciesLast7Years            : int  4 0 0 14 0 0 0 0 0 0 ...
##  $ PublicRecordsLast10Years           : int  0 1 0 0 0 0 0 1 0 0 ...
##  $ PublicRecordsLast12Months          : int  0 0 NA 0 0 0 0 0 0 0 ...
##  $ RevolvingCreditBalance             : num  0 3989 NA 1444 6193 ...
##  $ BankcardUtilization                : num  0 0.21 NA 0.04 0.81 0.39 0.72 0.13 0.11 0.11 ...
##  $ AvailableBankcardCredit            : num  1500 10266 NA 30754 695 ...
##  $ TotalTrades                        : num  11 29 NA 26 39 47 16 10 29 29 ...
##  $ TradesNeverDelinquent..percentage. : num  0.81 1 NA 0.76 0.95 1 0.68 0.8 1 1 ...
##  $ TradesOpenedLast6Months            : num  0 2 NA 0 2 0 0 0 1 1 ...
##  $ DebtToIncomeRatio                  : num  0.17 0.18 0.06 0.15 0.26 0.36 0.27 0.24 0.25 0.25 ...
##  $ IncomeRange                        : Factor w/ 8 levels "$0","$1-24,999",..: 4 5 7 4 3 3 4 4 4 4 ...
##  $ IncomeVerifiable                   : Factor w/ 2 levels "False","True": 2 2 2 2 2 2 2 2 2 2 ...
##  $ StatedMonthlyIncome                : num  3083 6125 2083 2875 9583 ...
##  $ LoanKey                            : Factor w/ 113066 levels "00003683605746079487FF7",..: 100337 69837 46303 70776 71387 86505 91250 5425 908 908 ...
##  $ TotalProsperLoans                  : int  NA NA NA NA 1 NA NA NA NA NA ...
##  $ TotalProsperPaymentsBilled         : int  NA NA NA NA 11 NA NA NA NA NA ...
##  $ OnTimeProsperPayments              : int  NA NA NA NA 11 NA NA NA NA NA ...
##  $ ProsperPaymentsLessThanOneMonthLate: int  NA NA NA NA 0 NA NA NA NA NA ...
##  $ ProsperPaymentsOneMonthPlusLate    : int  NA NA NA NA 0 NA NA NA NA NA ...
##  $ ProsperPrincipalBorrowed           : num  NA NA NA NA 11000 NA NA NA NA NA ...
##  $ ProsperPrincipalOutstanding        : num  NA NA NA NA 9948 ...
##  $ ScorexChangeAtTimeOfListing        : int  NA NA NA NA NA NA NA NA NA NA ...
##  $ LoanCurrentDaysDelinquent          : int  0 0 0 0 0 0 0 0 0 0 ...
##  $ LoanFirstDefaultedCycleNumber      : int  NA NA NA NA NA NA NA NA NA NA ...
##  $ LoanMonthsSinceOrigination         : int  78 0 86 16 6 3 11 10 3 3 ...
##  $ LoanNumber                         : int  19141 134815 6466 77296 102670 123257 88353 90051 121268 121268 ...
##  $ LoanOriginalAmount                 : int  9425 10000 3001 10000 15000 15000 3000 10000 10000 10000 ...
##  $ LoanOriginationDate                : Factor w/ 1873 levels "2005-11-15 00:00:00",..: 426 1866 260 1535 1757 1821 1649 1666 1813 1813 ...
##  $ LoanOriginationQuarter             : Factor w/ 33 levels "Q1 2006","Q1 2007",..: 18 8 2 32 24 33 16 16 33 33 ...
##  $ MemberKey                          : Factor w/ 90831 levels "00003397697413387CAF966",..: 11071 10302 33781 54939 19465 48037 60448 40951 26129 26129 ...
##  $ MonthlyLoanPayment                 : num  330 319 123 321 564 ...
##  $ LP_CustomerPayments                : num  11396 0 4187 5143 2820 ...
##  $ LP_CustomerPrincipalPayments       : num  9425 0 3001 4091 1563 ...
##  $ LP_InterestandFees                 : num  1971 0 1186 1052 1257 ...
##  $ LP_ServiceFees                     : num  -133.2 0 -24.2 -108 -60.3 ...
##  $ LP_CollectionFees                  : num  0 0 0 0 0 0 0 0 0 0 ...
##  $ LP_GrossPrincipalLoss              : num  0 0 0 0 0 0 0 0 0 0 ...
##  $ LP_NetPrincipalLoss                : num  0 0 0 0 0 0 0 0 0 0 ...
##  $ LP_NonPrincipalRecoverypayments    : num  0 0 0 0 0 0 0 0 0 0 ...
##  $ PercentFunded                      : num  1 1 1 1 1 1 1 1 1 1 ...
##  $ Recommendations                    : int  0 0 0 0 0 0 0 0 0 0 ...
##  $ InvestmentFromFriendsCount         : int  0 0 0 0 0 0 0 0 0 0 ...
##  $ InvestmentFromFriendsAmount        : num  0 0 0 0 0 0 0 0 0 0 ...
##  $ Investors                          : int  258 1 41 158 20 1 1 1 1 1 ...
```

## The first Qustion
The first question that needs to be asked is HOW LONG PEOPLE USUALLY OPT FOR LOAN? Let's answer this question with a histogram

![](EDA_Loan_files/figure-html/unnamed-chunk-4-1.png)<!-- -->

We can see that people don't really loan any amount for less than one year and the most popular loan amount is of 3 years although some people do choose for 5 years. Now lets assume something and check if it is correct or not. I assume that people who opted for 1 year would fail to repay their loan more as compared to the people who opted for 3 or 5 years. But is it true? So the next question is
DOES PEOPLE REPAY THE LOANS BETTER WHEN THEY ARE GIVEN MORE TIME?



## Plotting the trend of different customer types


![](EDA_Loan_files/figure-html/unnamed-chunk-6-1.png)<!-- -->

That's unusual because for **LoanStatus** of _Completed_, we see a trend but not in **LoanStatus** of _Defaulted_ though. Now just because some customer's loan status is not Completed, doesn't mean his/her loan status is Defaulted.

We can see that there is a trend in the of **LoanStatus** of _Completed_ and _Other_ but we see any trend in _Defaulted_ though. Now just because some customer's loan status is not Completed, doesn't mean his/her loan status is Defaulted. So let's explore the Defaulted section more.

The reason we are exploring this is because we want to find if BANKS SHOULD FOCUS ON CUSTOMERS OPTING LOANS FOR SMALLER TERMS OR NOT? AND HOW SOME OF THE MOST COMMON BORROWER LOANSTATUS VARIES FOR DIFFERENT LOAN TERMS? For this getting data of only two loan status won't be enough. So let's divide the customers into two groups

    1. Good Customer
    2. Bad Customer




But before that lets see the distribution of LonaStatus variable

![](EDA_Loan_files/figure-html/unnamed-chunk-8-1.png)<!-- -->

## The bigger Picture

![](EDA_Loan_files/figure-html/unnamed-chunk-9-1.png)<!-- -->

As we can that the short and long term prospects of the banks who issues the loan seems good because both in 1 and 5 year category, we see more number of good customers as compared to the 3 years. The number of good customers is however decreased a little from 1 year to 5 years but as compared to 3 years it is nothing. This may mean that banks should focus in long and short term customers as compared to medium term customers. But we should take this fact with a grain of slat because there might be other factors that may affect this trend. Only further exploration of the data would reveal that.

But before we move ahead, lets analyse the distribution of some of the features that might be useful for us in this data set. We would also remove some the outliers to better understand the features and may dive into some descriptive statistics too.

## Distribution for some continuous/categorical features

![](EDA_Loan_files/figure-html/unnamed-chunk-10-1.png)<!-- -->

## EstimatedEffectiveYield - A better measure for a successful Lender

![](EDA_Loan_files/figure-html/unnamed-chunk-11-1.png)<!-- -->

**EstimatedEffectiveYield** is said to be better estimate for the lenders than the interest rate because the interest includes _processing fees_, _uncollected interest due to borrower being chargedoff_. Plus it also doesn't include _late fines_. Hence EstimatedEffectiveYield takes account for all these things and it is thus a better measure. Above we are trying to see the distribution of the EstimatedEffectiveYield and we can see that it is multimodal. We see the most popular EstimatedEffectiveYield is around 0.3 while the mean is around 0.17 represented by the blue dotted line. The multimodal pattern shows that there are multiple EstimatedEffectiveYield that is popular. Strangely we can also see that the some customers have negative EstimatedEffectiveYield. This may mean a lot of things. This may mean that their BorrowerRate is a lot lower than their _service fee rate_ or these customer's _uncollected interest on chargeoff_ is lot more or they just never payed the late fee and payed back the loans along with the interest always on time.

## Does Lenders prefer borrowers with better Prosper Score ? 

Now lets see what is the distribution of EstimatedEffectiveYield depending on the different **ProsperScore**. This is important because we want to answer a question, i.e., IF LENDERS GET MORE EstimatedEffectiveYield IF THEY HAVE BETTER ProsperScore ?

We are using violin plot instead of box plot for this.

![](EDA_Loan_files/figure-html/unnamed-chunk-12-1.png)<!-- -->

Well this is interesting. We see an wonderful trend here. Here more score for the risk factor means better the borrower and lesser score for risk factor means poor prospects from the borrowers. We can see that for lower ProsperScore distribution of effective yield in a lot more than the higher ProsperScore. This may mean that lenders charges a variety of interest rate from the borrower with poor prospects as compared to borrowers with better prospect. We can also notice how median (represented by the black dot) is decreasing as ProsperScore is increasing. This may mean that lenders give more relaxations to borrowers with better ratings as compared to borrowers with poor rating. Does that mean lenders trust and like borrowers with better ProsperScore! Let's do a little more analysis to reveal it more. The reason we need more exploration on this is because EstimatedEffectiveYield includes more things such as late fine and doesn't include processing fee and others. So more EstimatedEffectiveYield for lesser ProsperScore borrowers may be due to high late fines because lesser ProsperScore borrowers are more prone to fail to repay their loan on time each month. So, Let's see if borrower's interest rate shows the same trend for each ProsperScore categories or not because interest rates doesn't include late fines. 


![](EDA_Loan_files/figure-html/unnamed-chunk-13-1.png)<!-- -->

Finally things are revealed much better now! We can clearly observe that for both _BorrowerAPR_ and _BorrowerRate_ which are metric for interest rates, we see a declining trend as the _ProsperScore_ is increasing. This justifies the fact even more that lenders somehow prefers to charge less for all the borrowers with better ProsperScore as compared to borrowers with inferior ProsperScore. Here food for thought is that is it moral too? Well I guess no amount of EDA can reveal it.

But are we missing the real question here? We are performing all these analysis on the Prosper loan data to answer several questions but what is the most important thing for a loan ? It's **BORROWERS** and what is the most important question related to borrowers? 

## Distribution of Listing Category

![](EDA_Loan_files/figure-html/unnamed-chunk-14-1.png)<!-- -->

The other section indicated by number 7 with more than 10000 of the borrowers would remain unknown. Why the loan reason would be unknown? Does it indicate any illegal reason to opt for loan! Let's explore this more. Let's see the Occupation and Employment status of Borrowers for all the loans falling into the _others_ section.

## Who are others??



<!--html_preserve--><div id="htmlwidget-3a5bd8e2a3e670b651f4" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-3a5bd8e2a3e670b651f4">{"x":{"filter":"top","filterHTML":"<tr>\n  <td data-type=\"factor\" style=\"vertical-align: top;\">\n    <div class=\"form-group has-feedback\" style=\"margin-bottom: auto;\">\n      <input type=\"search\" placeholder=\"All\" class=\"form-control\" style=\"width: 100%;\"/>\n      <span class=\"glyphicon glyphicon-remove-circle form-control-feedback\"><\/span>\n    <\/div>\n    <div style=\"width: 100%; display: none;\">\n      <select multiple=\"multiple\" style=\"width: 100%;\" data-options=\"[&quot;Employed&quot;,&quot;Full-time&quot;,&quot;Not employed&quot;,&quot;Other&quot;,&quot;Part-time&quot;,&quot;Retired&quot;,&quot;Self-employed&quot;]\"><\/select>\n    <\/div>\n  <\/td>\n  <td data-type=\"factor\" style=\"vertical-align: top;\">\n    <div class=\"form-group has-feedback\" style=\"margin-bottom: auto;\">\n      <input type=\"search\" placeholder=\"All\" class=\"form-control\" style=\"width: 100%;\"/>\n      <span class=\"glyphicon glyphicon-remove-circle form-control-feedback\"><\/span>\n    <\/div>\n    <div style=\"width: 100%; display: none;\">\n      <select multiple=\"multiple\" style=\"width: 100%;\" data-options=\"[&quot;&quot;,&quot;Administrative Assistant&quot;,&quot;Computer Programmer&quot;,&quot;Construction&quot;,&quot;Engineer - Electrical&quot;,&quot;Food Service&quot;,&quot;Investor&quot;,&quot;Nurse (RN)&quot;,&quot;Other&quot;,&quot;Professional&quot;,&quot;Sales - Commission&quot;,&quot;Sales - Retail&quot;,&quot;Student - College Graduate Student&quot;,&quot;Student - College Senior&quot;,&quot;Teacher&quot;]\"><\/select>\n    <\/div>\n  <\/td>\n  <td data-type=\"integer\" style=\"vertical-align: top;\">\n    <div class=\"form-group has-feedback\" style=\"margin-bottom: auto;\">\n      <input type=\"search\" placeholder=\"All\" class=\"form-control\" style=\"width: 100%;\"/>\n      <span class=\"glyphicon glyphicon-remove-circle form-control-feedback\"><\/span>\n    <\/div>\n    <div style=\"display: none; position: absolute; width: 200px;\">\n      <div data-min=\"2\" data-max=\"1579\"><\/div>\n      <span style=\"float: left;\"><\/span>\n      <span style=\"float: right;\"><\/span>\n    <\/div>\n  <\/td>\n<\/tr>","data":[["Employed","Employed","Employed","Employed","Employed","Full-time","Full-time","Full-time","Full-time","Full-time","Not employed","Other","Other","Part-time","Part-time","Part-time","Part-time","Part-time","Part-time","Part-time","Retired","Retired","Self-employed","Self-employed","Self-employed","Self-employed","Self-employed"],["Other","Professional","Administrative Assistant","Teacher","Computer Programmer","Other","Professional","Computer Programmer","Teacher","Administrative Assistant","Other","Other","","Other","Sales - Retail","Administrative Assistant","Food Service","Nurse (RN)","Student - College Graduate Student","Student - College Senior","Other","Engineer - Electrical","Other","Professional","Investor","Construction","Sales - Commission"],[1579,789,280,256,247,622,326,139,125,115,153,352,95,23,13,8,7,4,4,4,127,2,152,32,19,16,16]],"container":"<table class=\"stripe\">\n  <thead>\n    <tr>\n      <th>Employment Status<\/th>\n      <th>Occupation<\/th>\n      <th>Total<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"autoWidth":true,"columnDefs":[{"targets":[1,2],"searchable":false},{"className":"dt-right","targets":2}],"crosstalkOptions":{"key":null,"group":null},"order":[],"orderClasses":false,"orderCellsTop":true,"lengthMenu":[5,10,25,50,100]},"selection":{"mode":"multiple","selected":null,"target":"row"}},"evals":[],"jsHooks":[]}</script><!--/html_preserve-->


We can see some really strange things happening here. In fact there are so many strange things that I have to list them down
    
**Firstly** what is the difference between _Employed_ and _Full-time_?
    
**Secondly** there are too many others. The complete sample of the data is taken for those borrowers whose purpose for borrowing is _Others_. But there are _Others_ for _Occupation_ and _EmploymentStatus_ too. 

**Thirdly** how can someone be _Retired_ but still has _Occupation Others_ ?

**Lastly** there are some dubious borrowers in the _Others_ table. We can see that there are 352 cases where the borrowing reason, EmploymentStatus, Occupation all are _Others_ and 95 cases where _Occupation_ is left blank.
    
These above points, specially the last one says not all the burrower's information is revealed or in some cases they seemed to be fake too. I guess it is a partial dead end for us to see why people mention _Other_ as a reason while opting for loan.

Let's now move into something more computational. Let's first see after working for how many years, people like to opt for a loan? We can then move into some deeper level of analysis.

## Does experienced people opt for loan lesser ?

![](EDA_Loan_files/figure-html/unnamed-chunk-18-1.png)<!-- -->

## I was right ..:)

Well this was really interesting. We can see that our assumption was overall correct because the as people gain experience in their jobs, lesser they opt for the loans. This may be due the fact that as people gain experience their salary also increases and hence the lesser reason they find to opt for loans or the reason can be something different. We can also see in the right histogram of 95% quarterly, most people opt for loans when they have almost 2 years of experience. 

Lets explore it even more let's see the correlation between number of month a person has experience and the EstimatedEffectiveYield variable that we have explored earlier. The question that we want to explore - 
DOES LENDERS ASK FOR LESS INTEREST FORM THE BORROWERS WHO ARE MORE EXPERIENCED? This can be true because people with more job experience should have more potential to replay their loan better because they have higher paying jobs and hence their ProsperScore would be higher. And as we have seen that borrowers with better prosper score pay lesser to the lenders and lenders somehow prefer them.

![](EDA_Loan_files/figure-html/unnamed-chunk-19-1.png)<!-- -->

As it seems from the scatter plot that the pattern seems to have no correlation. It means our assumption was not correct. Borrowers with better **EmploymentStatusDuration** don't seem to get any special relaxation from lenders in terms of interest each month. This can be further confirmed by checking the _Perarson's correlation Coefficient_. We see that the correlation coefficient is almost 0 (-0.0233).


```
## 
## 	Pearson's product-moment correlation
## 
## data:  EmploymentStatusDuration/12 and EstimatedEffectiveYield
## t = -6.7924, df = 84832, p-value = 1.11e-11
## alternative hypothesis: true correlation is not equal to 0
## 95 percent confidence interval:
##  -0.03003902 -0.01658791
## sample estimates:
##         cor 
## -0.02331452
```

This also says that even though the true correlation is not true and alternative hypothesis is accepted, their is some **serious statistical evidence of significance**. But if we look into the CI, it is within the range of -0.03 to -0.016 which is very small. Good R value is said a value < -0.3 or value > 0.3. This value is definitely not that large. Judging from the context latest it is not. So we can say that there is **no practical significance.** Hence we can not tell with any confirmation that More Experienced Lenders end up paying Less/More interest to the Lenders.

## Other Correlations
![](EDA_Loan_files/figure-html/unnamed-chunk-21-1.png)<!-- -->


## How people loan for their Homes ?

Here we are going to explore the people for two category. 

    1. First those who are opting for loan to rennovation of home when they have a house.
    2. Second those who opt for home loans even though they don't have house.




**Now let's plot the data**

![](EDA_Loan_files/figure-html/unnamed-chunk-23-1.png)<!-- -->

## Are Investors partial to Borrowers with better rating ??

Here we visualizing an interesting trend. We are seeing for people with ProsperRating of _AA, A & B_, number of people opted for loan mentioning the reason for loan as **Home Improvement** but still has no home is more than the people who has home and opted for loan for Home Improvement and truly a home owner. But for people with poor rating, the trend in opposite and expected also. People who don't have any house should not get any loan mentioning the loan reason of House Improvement. These whole thing shows not only lenders give much preference to Rating over Verification and KYC (Know Your Customer) but this also shows irrespective of rating of borrowers, lenders font care much about loan reason as a whole. The following code proves it even more. We can see that there are not a single borrowers who mentioned their loan purpose to be Home Improvement when they didn't have their own house and their loan was not approved. That's a strong evidence to show that investors don't care much about how much borrowers fudge or fake their loan purpose.


```r
a <- loanData %>%
    filter(ListingCategory..numeric. == 2,
           LoanStatus == 'Cancelled')
print.numeric_version(dim(a)[0])
```

```
## <0 elements>
```
## What's up with the people having dubious income sources ?



![](EDA_Loan_files/figure-html/unnamed-chunk-26-1.png)<!-- -->

## Prosper rating system seems legit !!

Although we can't see any specific pattern among the dubious borrowers but we can see one thing very well. Overall borrowers with better ratings tends to be less dubious than borrowers with poor ratings. One more interesting thing is that the above bar chart does not include borrowers with _AA_ rating. It means that the best borrowers are really best and the prosper rating really works.

## Are Lenders greedy ?

I always wanted to do this. But from this dataset we can answer this question a lot of way. One of the way is to check if the lenders asked for money if the borrowers income was high. Let's see if the correlation is substantial.

![](EDA_Loan_files/figure-html/unnamed-chunk-27-1.png)<!-- -->


Here I am trying to see the relationship of _MonthlyLoanPayment_ with _StatedMonthlyIncome._ We can see from the above statterplot that most of the _MonthlyLoanPayment_ is distributed from 10 to 1000 and the _StatedMonthlyIncome_ is distributed from 100 to 30000. Both the scales are transformed in log scale and we can clearly observe two things, namely,
  
    
    1. There is definite a strong positive correlation 
    between monthly income and monthly loan amount.
    
    2. Cubic relationship seems a better fit that simple linear model.

## Are we sure that they are greedy ?

Now we can see that there was definitely a strong correlation between the two variables but are we sure? Let's find the **Correlation Coefficient** to analyse it more.




```
## 
## 	Pearson's product-moment correlation
## 
## data:  MonthlyLoanPayment and StatedMonthlyIncome
## t = 67.764, df = 113940, p-value < 2.2e-16
## alternative hypothesis: true correlation is not equal to 0
## 95 percent confidence interval:
##  0.1912423 0.2024055
## sample estimates:
##       cor 
## 0.1968303
```



Well we can't really say that there is a strong correlation looking at the value of R which is almost 0.2. Usually it is said to be of high statistical importance if it is more than 0.3 or less than -0.3. But we can see that the value is still acceptable with somewhat positive correlation with the population Conficence Interval being more than 0. The strong t-statistics of 67.76 and small p-value shows that the statistical significance of alternative hypothesis is very strong. But this can also be somewhat practical significance too, at least to be included in a linear model.

## Does Recommendations matter ??

Before we move ahead let's review the _Recommendations_ variable and understand it's impact and distribution. 

### Distribution of Recommendation
![](EDA_Loan_files/figure-html/unnamed-chunk-29-1.png)<!-- -->

![](EDA_Loan_files/figure-html/unnamed-chunk-30-1.png)<!-- -->

As we can see that people with _Above 20_ recommendations has the highest number of _MonthlyLoanPayment_ percentage as compared to any other group. But this still can't assure us that people with higher recommendations pay more loan each month. This question was relevant because we want to find out IF PEOPLE WITH MORE RECOMMENDATION ARE POWERFUL AND RICH ENOUGH TO PAY MORE LOAN MONTHLY? The answer is we can't be really sure.


## Let's predict the Monthly Loan Payment

![](EDA_Loan_files/figure-html/unnamed-chunk-31-1.png)<!-- -->


As we can the a very good linear realtionship here. Let's explore this even further. There are multiple number of models that we can create with different number of input or independent variables. Let's try to create a linear model and see how we can improve it.

![](EDA_Loan_files/figure-html/unnamed-chunk-32-1.png)<!-- -->


```
## 
## Call:
## lm(formula = MonthlyLoanPayment ~ LoanOriginalAmount, data = model)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -710.32  -33.57   -3.00   27.64 1528.86 
## 
## Coefficients:
##                     Estimate Std. Error t value Pr(>|t|)    
## (Intercept)        4.556e+01  4.716e-01   96.61   <2e-16 ***
## LoanOriginalAmount 2.708e-02  4.177e-05  648.33   <2e-16 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 74.23 on 77112 degrees of freedom
## Multiple R-squared:  0.845,	Adjusted R-squared:  0.845 
## F-statistic: 4.203e+05 on 1 and 77112 DF,  p-value: < 2.2e-16
```

_LoanOriginalAmount_ should be the most important factor to decide what would be the _MonthlyLoanPayment_. As we can see that the correlation has very good _Adjusted R-squared_ value of 0.845 or almost 85%. The _Residual Standard Error_ is however quite high of almost75 which indicates the average performance of the linear model. We can visualize how the residuals are spread from the above plot. Their distribution is quite high. So the bigger question is that can we improve this model. Improving the model would ensure the following things
    
    1. Higher Adjusted R-squared value
    2. Lower Residual Standard Error
    3. Less variation/ Less dispersed residual graph
    
The key to improve any model liner/non-linear is to increase the number of independent variables. The choice of independent variable should be very logical. We should not include the variable which are dependent on the predicting variable. The independent variables should be truly independent. Here are the following variables that are chosen to improve the model. 
    
    1. LoanOriginalAmount: This should be the most important one 
    because how much the borrower has to pay each month 
    should be dependent on the total amount that is loaned
    
    2. DebtToIncomeRatio: This is important because lenders may 
    ask more money each month who has a record of high DebtToIncomeRatio 
    because they are considered borrowers with poor prospect and 
    lenders might charge them more if giving loans
    
    3. ProsperRating..numeric.: This is obvious because the we have shown 
    already that lenders trust the prosper rating a lot over anything else 
    and hence borrowers with poor ratings should pay more each 
    month as compared to better ratings.
    
    4. Term: Term decides how long the borrower is opting for the loan 
    and hence longer the Term shorter should be monthly payment.
    
    5. LoanOriginationQuarter: Lenders may ask for different monthly loan payment 
    on different time of the year because of dynamic interest rate 
    and changing macro economic factors on different time of the year.

![](EDA_Loan_files/figure-html/unnamed-chunk-34-1.png)<!-- -->

We can see a lot less variation in the residual. Moreover when we summarize the fit2 for our improved model, we see that the value of _Residual standard error_ decreased a lot to almost 49 and _Adjusted R-squared_ increased to almost 94%. This was a huge jump from our previous model. Hence we can say that fit2 predicts the monthly loan amount better than the fit1 model. This also proves that _LoanOriginalAmount_ is not only the deciding factor of _MonthlyLoanPayment_. There are other factors too that contribute to this. From the ```summary(fit2)```, we observe that the slope values like below

    1. LoanOriginalAmount: 3.124e-02
    2. DebtToIncomeRatio:  3.211e+00
    3. ProsperRating..numeric.: -1.050e+01
    4. Term: -4.993e+00 

We can see that as we might have assumed, _LoanOriginalAmount_ & _DebtToIncomeRatio_ has positive slope which is obvious because if these two increase, lenders ask for more money from the borrowers. On the other hand, _Term_ has a negative slope which is logical because if term increases, monthly loan payment should decrease.

We can also see that the both maximum and minimum residual for our improved model is lesser than our previous model.

## Some Final Thoughts

Let's select 3 plots from what we have discussed and elaborate them bit further.

### What people loans for ?

![](EDA_Loan_files/figure-html/unnamed-chunk-35-1.png)<!-- -->

It is really strange that people took loans to reimburse loans/debts and lenders also issued loans to these people. Isn't is a bad idea to take loans to pay for loans? Aren't we falling into a vicious cycle? We can also see that Home Improvement is above Medical which may mean well insured population or negligence toward health.

### Does lenders prefer borrowers with better ProsperScore ?

![](EDA_Loan_files/figure-html/unnamed-chunk-36-1.png)<!-- -->

This depicts how we interest rates are affected by the Prosper Score for risk factor. As the score improves, the interest rate shows a declining treand visible from the black points. This indeed proves that the lenders like to charge less from borrowers with better prosper score.

### Correlation of MonthlyIncome vs MonthlyLoanPayment

![](EDA_Loan_files/figure-html/unnamed-chunk-37-1.png)<!-- -->

This created the base for the Linear regression model that was already discussed. This shows that _LoanOriginalAmount_ and _MonthlyLoanPayment_ has very good linear relationship for each _Term_. We have improved the model and by adding mutiple input variables and achieved a very good _Adjusted R squared_ value of almost 94% and a very low _Standard Residual Error_.

## Reflection

**Struggle** with this data set were many. I was at first intimidated by it seer size of number of rows. I honestly have never seen any CSV file which is this big and contains this many variables. However the real relief was the CSV file that contained the meaning of all the variables in the data set. But the biggest struggle that I faced in this data set was actually common in most of the data sets that contains this many variables. Some of the variables seems to have the same meaning for example _BorrowerAPR_, _BorrowerRate_, _LenderYield_, _EstimatedEffectiveYield_. These terms seemed to have similar meaning but not exactly the same. Now the was which one to include in our analysis and which is more important than other? Although with little bit more understanding I solved it but it took some time. Another struggle was to establish right combination of variables to create accurate linear regression model for minimum residual. This problem could have been solved using _Gradient Decend_ but because it being out of scope I had to try different combination manually. This also took some time.

**Successes** were achieved even after the above mentioned struggle because of some detailed analysis of the data set and the CSV file supplied that explains the variables in the data set. Linear Regression model's accuracy was checked by carefully taken the variables and then checking the _Adjusted R-squared_ values and the _Residual standard error_ and plotting the Residual standard error. By doing this I could actually improve the regression model substantially already discussed earlier.

Although some **ideas for future exploration** can improve this analysis substantially. I really think regression model can be improved further using _Gradient Decend_ to better approximate the slope and the intercept of the line. I also believe that is some information hidden inside the delinquency variables and late payment variables in _CurrentDelinquencies, AmountDelinquent, DelinquenciesLast7Years_ and _OnTimeProsperPayments, ProsperPaymentsLessThanOneMonthLate, ProsperPaymentsOneMonthPlusLate_ with respect the Monthly loan amount which can be explored further. 

However one thing is confirmed, Financial Data set is really intensive stuff.
