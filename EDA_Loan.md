# Prosper Loan Data Analysis
Mayukh Sarkar  








## The first Qustion
The first question that needs to be asked is HOW LONG PEOPLE USUALLY OPT FOR LOAN? Let's answer this question with a histogram

![](EDA_Loan_files/figure-html/unnamed-chunk-3-1.png)<!-- -->

We can see that people don't really loan any amount for less than one year and the most popular loan amount is of 3 years although some people do choose for 5 years. Now lets assume something and check if it is correct or not. I assume that people who opted for 1 year would fail to repay their loan more as compared to the people who opted for 3 or 5 years. But is it true? So the next question is
DOES PEOPLE REPAY THE LOANS BETTER WHEN THEY ARE GIVEN MORE TIME?



## Plotting the trend of different customer types


![](EDA_Loan_files/figure-html/unnamed-chunk-5-1.png)<!-- -->

That's unusual because for **LoanStatus** of _Completed_, we see a trend but not in **LoanStatus** of _Defaulted_ though. Now just because some customer's loan status is not Completed, doesn't mean his/her loan status is Defaulted.
The reason we are exploring this is because we want to find if BANKS SHOULD FOCUS ON CUSTOMERS OPTING LOANS FOR SMALLER TERMS OR NOT? For this getting data of only two loan status won't be enough. So let's divide the customers into two groups

    1. Good Customer
    2. Bad Customer




## The bigger Picture

![](EDA_Loan_files/figure-html/unnamed-chunk-7-1.png)<!-- -->

As we can that the short and long term prospects of the banks who issues the loan seems good because both in 1 and 5 year category, we see more number of good customers as compared to the 3 years. The number of good customers is however decreased a little from 1 year to 5 years but as compared to 3 years it is nothing. This may mean that banks should focus in long and short term customers as compared to medium term customers. But we should take this fact with a grain of slat because there might be other factors that may affect this trend. Only further exploration of the data would reveal that.

But before we move ahead, lets analyse the distribution of some of the features that might be useful for us in this dataset. We would also remove some the outliers to better understand the features and may dive into some descriptive statistics too.

## Distribution for some continuous/categorical features

![](EDA_Loan_files/figure-html/unnamed-chunk-8-1.png)<!-- -->

## EstimatedEffectiveYield - A better measure for a successful Lender

![](EDA_Loan_files/figure-html/unnamed-chunk-9-1.png)<!-- -->

**EstimatedEffectiveYield** is said to be better estimate for the lenders than the interest rate because the interest includes _processing fees_, _uncollected interest due to borrower being chargedoff_. Plus it also doesn't include _late fines_. Hence EstimatedEffectiveYield takes account for all these things and it is thus a better measure. Above we are trying to see the distribution of the EstimatedEffectiveYield and we can see that it is multimodal. We see the most popular EstimatedEffectiveYield is around 0.3 while the mean is around 0.17 represented by the blue dotted line. The multimodal pattern shows that there are multiple EstimatedEffectiveYield that is popular. Strangely we can also see that the some customers have negative EstimatedEffectiveYield. This may mean a lot of things. This may mean that their BorrowerRate is a lot lower than their _service fee rate_ or these customer's _uncollected interest on chargeoff_ is lot more or they just never payed the late fee and payed back the loans along with the interest always on time.

## Does Lenders prefer borrowers with better Prosper Score ? 

Now lets see what is the distribution of EstimatedEffectiveYield depending on the different **ProsperScore**. This is important because we want to answer a question, i.e., IF LENDERS GET MORE EstimatedEffectiveYield IF THEY HAVE BETTER ProsperScore ?

We are using violin plot instead of box plot for this.

![](EDA_Loan_files/figure-html/unnamed-chunk-10-1.png)<!-- -->

Well this is interesting. We see an wonderful trend here. Here more score for the risk factor means better the borrower and lesser score for risk factor means poor prospects from the borrowers. We can see that for lower ProsperScore distribution of effective yield in a lot more than the higher ProsperScore. This may mean that lenders charges a variety of interest rate from the borrower with poor prospects as compared to borrowers with better prospect. We can also notice how median (represented by the black dot) is decreasing as ProsperScore is increasing. This may mean that lenders give more relaxations to borrowers with better ratings as compared to borrowers with poor rating. Does that mean lenders trust and like borrowers with better ProsperScore! Let's do a little more analysis to reveal it more. The reason we need more exploration on this is because EstimatedEffectiveYield includes more things such as late fine and doesn't include processing fee and others. So more EstimatedEffectiveYield for lesser ProsperScore borrowers may be due to high late fines because lesser ProsperScore borrowers are more prone to fail to repay their loan on time each month. So, Let's see if borrower's interest rate shows the same trend for each ProsperScore categories or not because interest rates doesn't include late fines. 


![](EDA_Loan_files/figure-html/unnamed-chunk-11-1.png)<!-- -->

Finally things are revealed much better now! We can clearly observe that for both _BorrowerAPR_ and _BorrowerRate_ which are metric for interest rates, we see a declining trend as the _ProsperScore_ is increasing. This justifies the fact even more that lenders somehow prefers to charge less for all the borrowers with better ProsperScore as compared to borrowers with inferior ProsperScore. Here food for thought is that is it moral too? Well I guess no amount of EDA can reveal it.

But are we missing the real question here? We are performing all these analysis on the Prosper loan data to answer several questions but what is the most important thing for a loan ? It's **BORROWERS** and what is the most important question related to borrowers? 

## What people want loans for?
![](EDA_Loan_files/figure-html/unnamed-chunk-12-1.png)<!-- -->

## Loan for Loans !!

It is really strange that people took loans to reimburse loans/debts and lenders also issued loans to these people. Isn't is a bad idea to take laons to pay for loans? Aren't we falling into a vicious cycle? We can also see that Home Inprovement is above Medical which may mean well insured population or negligence toward health. The other section with more than 10% of the loans would remain unknown. Why the loan reason would be unknown? Does it indicate any illegal reason to opt for loan! Let's explore this more. Let's see the Occupation and Employment status of Borrowers for all the loans falling into the _others_ section.

## Who are others??




\begin{table}[!htb]
    \begin{minipage}{.5\linewidth}
      \caption{ Employed }
      \centering 
\begin{tabular}{lr}
\toprule
Occupation & n\\
\midrule
Other & 1579\\
Professional & 789\\
Administrative Assistant & 280\\
Teacher & 256\\
Computer Programmer & 247\\
\bottomrule
\end{tabular} \end{minipage}%
    \begin{minipage}{.5\linewidth}
      \centering
        \caption{ Full-time } 
\begin{tabular}{lr}
\toprule
Occupation & n\\
\midrule
Other & 622\\
Professional & 326\\
Computer Programmer & 139\\
Teacher & 125\\
Administrative Assistant & 115\\
\bottomrule
\end{tabular} \end{minipage}
    \begin{minipage}{.5\linewidth}
      \centering
        \caption{ Part-time } 
\begin{tabular}{lr}
\toprule
Occupation & n\\
\midrule
Other & 23\\
Sales - Retail & 13\\
Administrative Assistant & 8\\
Food Service & 7\\
Nurse (RN) & 4\\
\addlinespace
Student - College Graduate Student & 4\\
Student - College Senior & 4\\
\bottomrule
\end{tabular} \end{minipage}%
    \begin{minipage}{.5\linewidth}
      \centering
        \caption{ Self-employed } 
\begin{tabular}{lr}
\toprule
Occupation & n\\
\midrule
Other & 152\\
Professional & 32\\
Investor & 19\\
Construction & 16\\
Sales - Commission & 16\\
\bottomrule
\end{tabular} \end{minipage}
    \centering
    \begin{minipage}{.5\linewidth}
      \centering
        \caption{ Others } 
\begin{tabular}{llr}
\toprule
EmploymentStatus & Occupation & n\\
\midrule
Other & Other & 352\\
Other &  & 95\\
Retired & Other & 127\\
Retired & Engineer - Electrical & 2\\
\bottomrule
\end{tabular} \end{minipage}
\end{table}

We can see some really strange things happening here. In fact there are so many strange things that I have to list them down
    
**Firstly** what is the difference between _Employed_ and _Full-time_?
    
**Secondly** there are too many others. The complete sample of the data is taken for those borrowers whose purpose for borrowing is _Others_. But there are _Others_ for _Occupation_ and _EmploymentStatus_ too. 

**Thirdly** how can someone be _Retired_ but still has _Occupation Others_ ?

**Lastly** there are some dubious borrowes in the _Others_ table. We can see that there are 352 cases where the borrowing reason, EmploymentStatus, Occupation all are _Others_ and 95 cases where _Occupation_ is left blank.
    
These above points, specially the last one says not all the bowrrower's information is revealed or in some cases they seemed to be fake too. I guess it is a partial dead end for us to see why people mention _Other_ as a reason while opting for loan.

Let's now move into something more computational. Let's first see after working for how many yaers, people like to opt for a loan? We can then move into some deeper level of analysis.

## Does experienced people opt for loan lesser ?

![](EDA_Loan_files/figure-html/unnamed-chunk-16-1.png)<!-- -->

## I was right ..:)

Well this was really intersting. We can see that our assumption was overall correct because the as people gain experience in their jobs, lesser they opt for the loans. This may be due the fact that as people gain experinece their salary also increases and hence the lesser reason they find to opt for loans or the reason can be something different. We can also see in the right histogram of 95% quartile, most people opt for loans when they have almost 2 years of experience. 

Lets explore it even more let's see the correlation between number of month a person has expericence and the EstimatedEffectiveYield variable that we have explored earlier. The question that we want to explore - 
DOES LENDERS ASK FOR LESS INTEREST FORM THE BORROWERS WHO ARE MORE EXPERIENCED? This can be true because people with more job experience should have more potential to replay their loan better because they have higher paying jobs and hence their ProsperScore would be higher. And as we have seen that borrowers with better prosper score pay lesser to the lenders and lenders somehow prefer them.

![](EDA_Loan_files/figure-html/unnamed-chunk-17-1.png)<!-- -->

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

This also says that even though the true correlation is not ture and alternative hypothesis is accepted, their is some **serious statistical evidence of significance**. But if we look into the CI, it is within the range of -0.03 to -0.016 which is very small. Good R value is said a value < -0.3 or value > 0.3. This value is definitely not that large. Judging from the context atlest it is not. So we can say that there is **no practical significance.** Hence we can not tell with any confirmation that More Exprerienced Lenders end up paying Less/More interest to the Lenders.

## Other Correlations
![](EDA_Loan_files/figure-html/unnamed-chunk-19-1.png)<!-- -->


## How people loan for their Homes ?

Here we are going to explore the people for two category. 

    1. First those who are opting for loan to rennovation of home when they have a house.
    2. Second those who opt for home loans even though they don't have house.




**Now let's plot the data**

![](EDA_Loan_files/figure-html/unnamed-chunk-21-1.png)<!-- -->

## Are Investors partial to Borrowers with better rating ??

Here we visualizing an interesting trend. We are seeing for people with ProsperRating of _AA, A & B_, number of people opted for loan mentioning the reason for laon as **Home Improvement** but still has no home is more than the people who has home and opted for loan for Home Improvement and truly a home owner. But for people with poor rating, the trend in opposite and expected also. People who don't have any house should not get any loan mentioning the loan reason of House Improvement. These whole thing shows not only lenders give much preference to Rating over Verification and KYC (Know Your Customer) but this also shows irrespective of rating of borrowers, lenders dont care much about laon reason as a whole. The following code proves it even more. We can see that there are not a single borrowers who mentioned their loan purpose to be Home Improvement when they didn't have their own house and their loan was not approved. That's a strong evidence to show that investors don't care much about how much borrowers fudge or fake their loan purpose.


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



![](EDA_Loan_files/figure-html/unnamed-chunk-24-1.png)<!-- -->

## Prosper rating system seems legit !!

Although we can't see any specific pattern among the dubious borrowers but we can see one thing very well. Overall borrowers with better ratings tends to be less dubious than borrowers with poor ratings. One more interesting thing is that the above barchart does not inlude borrowers with _AA_ rating. It means that the best borrowers are really best and the prosper rating really works.

## Are Lenders greedy ?

I always wanted to do this. But from this dataset we can answer this question a lot of way. One of the way is to check if the lenders asked for money if the borrowers income was high. Let's see if the correlation is substantial.

![](EDA_Loan_files/figure-html/unnamed-chunk-25-1.png)<!-- -->


Here I am trying to see the relationship of _MonthlyLoanPayment_ with _StatedMonthlyIncome._ We can see from the above statterplot that most of the _MonthlyLoanPayment_ is distribued from 10 to 1000 and the _StatedMonthlyIncome_ is distributed from 100 to 30000. Both the scales are transformed in log scale and we can clearly observe two things, namely,
  
    
    1. There is defineite a strong positive correlation 
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



Well we can't really say that there is a strong correlation looking at the value of R which is almost 0.2. Usually it is said to be of high statistical importance if it is more than 0.3 or less than -0.3. But we can see that the value is still accpeptable with somewhat positive correlation with the population Conficence Interval being more than 0. The strong t-statistics of 67.76 and small p-value shows that the statistical significance of alternative hypothesis is very strong. But this can also be somewhat practical significance too, atleast to be included in a linear model.



![](EDA_Loan_files/figure-html/unnamed-chunk-27-1.png)<!-- -->

As we can see that people with _Above 20_ recommendations has the highest number of _MonthlyLoanPayment_ percentage as compared to any other group. But this still can't assure us that people with higher recommendations pay more loan each month. This question was relevant because we want to find out IF PEOPLE WITH MORE RECOMMENDATION ARE POWERFUL AND RICH ENOUGH TO PAY MORE LOAN MONTHLY? The answer is we can't be really sure.


## Let's predict the Monthly Loan Payment

There are multiple number of models that we can create with different number of input or independent variables. Let's try to create a linear model and see how we can improve it.

![](EDA_Loan_files/figure-html/unnamed-chunk-28-1.png)<!-- -->


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

_LoanOriginalAmount_ should be the most important factor to decide what would be the _MonthlyLoanPayment_. As we can see that the correlation has very good _Adjusted R-squared_ value of 0.845 or almost 85%. The _Residual Standard Error_ is however quite high of almost75 which indicates the average performace of the linear model. We can visualise how the residuals are spread from the above plot. Their distribution is quite high. So the bigger question is that can we improve this model. Improving the model would ensure the following things
    
    1. Higher Adjusted R-squared value
    2. Lower Residual Standard Error
    3. Less variation/ Less dispersed residual graph
    
The key to improve any model liner/non-linear is to increase the number of independent variables. The choice of independent variable should be very logical. We should not include the variable which are dependent on the predicting variable. The independent variables should be truly independent. Here are the following variables that are choosen to improve the model. 
    
    1. LoanOriginalAmount: This should be the most important one 
    because how much the borrower has to pay each month 
    should be dependent on the total amount that is loaned
    
    2. DebtToIncomeRatio: This is important because lenders may 
    ask more money each month who has a record of high DebtToIncomeRatio 
    because they are considered borrowers with poor prospect and 
    lenders might charge them more if giving lonas
    
    3. ProsperRating..numeric.: This is obvious because the we have shown 
    already that lenders trust the prosper rating a lot over anything else 
    and hence borrowers with poor ratings should pay more each 
    month as compared to better ratings.
    
    4. Term: Term decides how long the borrower is opting for the loan 
    and hence longer the Term shorter should be monthly payment.
    
    5. LoanOriginationQuarter: Lenders may ask for different monthly loan payment 
    on different time of the year because of dynamic interest rate 
    and changing macro economic factors on different time of the year.

![](EDA_Loan_files/figure-html/unnamed-chunk-30-1.png)<!-- -->

We can see a lot less variation in the residual. Moreover when we summarize the fit2 for our improved model, we see that the value of _Residual standard error_ decreased a lot to almost 49 and _Adjusted R-squared_ incresed to almost 94%. This was a huge jump from our previous model. Hence we can say that fit2 predicts the monthly loan amount better than the fit1 model. This also proves that _LoanOriginalAmount_ is not only the deciding factor of _MonthlyLoanPayment_. There are other factors too that contribute to this. From the ```summary(fit2)```, we observe that the slope values like below

    1. LoanOriginalAmount: 3.124e-02
    2. DebtToIncomeRatio:  3.211e+00
    3. ProsperRating..numeric.: -1.050e+01
    4. Term: -4.993e+00 

We can see that as we might have assumed, _LoanOriginalAmount_ & _DebtToIncomeRatio_ has positive solpe which is obvious because if these two increse, lenders ask for more money from the borrowers. On the other hand, _Term_ has a negative slope which is logical because if term increses, monthly loan payment should decrease.

We can also see that the both maximum and minimum residual for our improved model is lesser than our previous model.

## Some Final Thoughts

Let's select 3 plots from what we have discussed and elaborate them bit further.

### Term's distribution for each Prosper Category

![](EDA_Loan_files/figure-html/unnamed-chunk-31-1.png)<!-- -->

As we can see the above mentioned plot is extension of the first plot of the histogram of different terms. Now it is split over serveral important variables. Firstly we are distributing it by each borrower category to see if there is any change in the pattern of loan terms for different type of borrowers. We can see along all the borrower types, 3 years is the most common borrowing year as we have already seen. We can see that people with _AA_ rank loan very less, while people of _C_ and _D_ category seems to loan most and all of their most poplular loan amount is 3 years. Moreover row-wise we split the plot in 2 sections namely, _True and False_ indcating Houseowner or not. We can see a lot more loan for houseowners with _AA_ and _A_ category while for others no houseowners seems to loan same or even more for low rating borrowers than houseowners. This may indicate that wheather a borrower would get more loan or not is dependent on the fact that they own their own house or not but only for high ranking borrowers. For low ranking borrowers, owning their own house doesn't affect much.

### EstimatedEffectiveYield variation on Employment type

![](EDA_Loan_files/figure-html/unnamed-chunk-32-1.png)<!-- -->

EstimatedEffectiveYield is measusred here which is the extention of the 5th plot of distribution EstimatedEffectiveYield for all ProsperScores. We found that as prosper socre increses, lenders seemed to demand comparatively lesser than the borrowers with poor ProsperScore. Now we would see how this varies with the profession of the borrowers. We see _Not employed_ people tends to have very less variation along all the prosperscore ranges. This may be due to the fact that they are not employed and hence return form them is kept fixed. We see almost the same pattern in the _Self-employed_ people. We see on the other hand a lot of variation in _Full-time_ and _Retired_ category. Probably because there are scopes of different level of returns from them. _Self-employed_ is somehow moderate as it should be because of its limited return values from them while _Employed_ remained to be strange because if it's amibuity with _Full-time_ as discussed. Overall we see a lot of ups and downs for the lenders' return if the borrowers are retired or full time as compared to others.

### Correlation of MonthlyIncome vs MonthlyLoanPayment

![](EDA_Loan_files/figure-html/unnamed-chunk-33-1.png)<!-- -->

This plot talks about so much and it is hard to talk about all of these. The color is by houseownership while the rows are split by verifiable income or not and columns are as usual borrowers' rating. We are trying to find the correlation of monthly income vs monthly loan payment. The cubic line fits in almost all of them and we see both the geom smoothing lines are following each other nicely. This means weather a borrower owns a house or not is not much of importance for the correlation. But we definitely see a more linear relationship for all the categories for the borrowers having verifiable income as compared to non verifiable income. This means that if income is verified, then their is a linear change in monthly loan payment and monthly income as compared non verifiable income borrowers. We also see that for borrowers with verifiable income the relation goes from linear to cubic as the rating of the borrowers goes down.


## Reflection

**Struggle** with this dataset were many. I was at first intimidated by it seer size of number of rows. I honestly have never seen any CSV file which is this big and contains this many variables. However the real relief was the CSV file that contained the meaing of all the variables in the dataset. But the biggest struggke that I faced in this dataset was actually common in most of the datasets that contains this many variables. Some of the variables seems to ahve the same meaning for example _BorrowerAPR_, _BorrowerRate_, _LenderYield_, _EstimatedEffectiveYield_. These terms seemed to have similar meaning but not exactly the same. Now the was which one to include in our analysis and which is more inportant than other? Although with little bit more understanding I solved it but it took some time. Another struggle was to establish right combination of variables to create accurate linear regression model for minimum residual. This problem could have been solved using _Gradient Decend_ but beacuse it being out of scope I had to try different combination manually. This also took some time.

**Successes** were achieved even after the above mentioned struggle because of some detailed analysis of the dataset and the CSV file supplied that expalins the variables in the dataset. Linear Regression model's accuracy was checked by carefully taken the variables and then checking the _Adjusted R-squared_ values and the _Residual standard error_ and plotting the Residual standard error. By doing this I could actually improve the regression model substantially already discussed earlier.

Although some **ideas for future exploration** can improve this analysis substantially. I really think regrssion model can be improved further using _Gradient Decend_ to better approximate the solope and the intercept of the line. I also believe that is some information hidden inside the delinquency variables and late payment variables in _CurrentDelinquencies, AmountDelinquent, DelinquenciesLast7Years_ and _OnTimeProsperPayments, ProsperPaymentsLessThanOneMonthLate, ProsperPaymentsOneMonthPlusLate_ with respect the Monthly loan amount which can be explored further. 

However one thing is confirmed, Financial Dataset is really intensive stuff.
