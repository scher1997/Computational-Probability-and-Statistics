# Additional Hypothesis Tests {#ADDTESTS}

## Objectives

1) Conduct and interpret a goodness of fit test using both Pearson's chi-squared and randomization to evaluate the independence between two categorical variables. 

2) Explain how the chi-squared distribution relates to the normal distribution, where it is used, and how changing parameters impacts the shape of the distribution.   

3) Conduct and interpret a hypothesis test for equality of two means and equality of two variances using both permutation and the CLT.   
  
4) Know and check assumptions for the tests in the reading.  


## Introduction

The purpose of this chapter is to put all we learned in this block into perspective and then to also add a couple of new tests to demonstrate other statistical tests.

Remember that we have been using data to answer research questions. So far we can do this with hypothesis tests or confidence intervals. There is a close link between these two methods. The key ideas have been to generate a single number metric to use in answering our research question and then to obtain the sampling distribution of this metric. 

In obtaining the sampling distribution we used randomization as an approximation to permutation exact tests, probability models, mathematical models, and the bootstrap. Each of these had different assumptions and different areas where they could be applied. In some cases, several methods can be applied to the problem to get a sense of the robustness to the different assumptions. For example, if you run a randomization test and a test using the CLT and they both give you similar results, you can feel better about your decision.

Finding a single number metric to answer our research question can be difficult. For example, in the homework for last chapter, we wanted to determine if the prices of books at a campus bookstore were different from Amazon's prices. The metric we decided to use was the mean of the differences in prices. But is this the best way to answer the question? This metric has been used historically because of the need to use the $t$ distribution. However, there are other ways in which the prices of books can differ. Jack Welch was the CEO of GE for years and he made the claim that customers don't care about average but they do care about variability. The average temperature setting of your GE refrigerator could be off and you would adapt. However if the temperature had great variability, then you would be upset. So maybe metrics that incorporate variability might be good. In our bootstrap notes, we looked at the ages of males and females in the HELP study. In using a randomization permutation test, we assumed there was no difference in the distribution of ages between males and females. However, in the alternative we measured the difference in the distributions using only means. The means of these two populations could be equal but the distributions differ in other ways, for example variability. We could conduct a separate test for variances but we have to be careful about multiple comparisons because in that case the Type 1 error is inflated.

We also learned that the use of the information in the data impacts the power of the test. In the golf ball example, when we used range as our metric, we did not have the same power as looking at the differences from expected values under the null hypothesis. There is some mathematical theory that leads to better estimators, they are called likelihood ratio tests, but this is beyond the scope of the book. What you can do is create a simulation where you simulate data from the alternative hypothesis and then measure the power. This will give you a sense of the quality of your metric. We only briefly looked at measuring power an earlier chapter and will not go further into this idea in this chapter.  

We will finish this block by examining problems with two variables. In the first case they will both be categorical but at least one of the categorical variables has more than two levels. In the second case, we will examine two variables where one is numeric and the other categorical. The categorical variable has more than two levels.


## Other distribution for estimators

In Chapter \@ref(HYPTESTCLT), we discussed the $t$ distribution, a different sampling distribution that is based on the CLT or normality assumption. In theoretical statistics, we often mathematically derive the sampling distribution by obtaining a sampling statistic, determining the distribution of that statistic under certain conditions, and using that information to make a statement about the population parameter. We now discuss another commonly used sampling distribution: the chi-squared distribution.  


### Chi-squared

Recall that the central limit theorem tells us that for reasonably large sample sizes, $\bar{X}\overset{approx}{\sim}\textsf{Norm}(\mu,\sigma/\sqrt{n})$. However, this expression involves two unknowns: $\mu$ and $\sigma$. In the case of binary data, population variance is a function of population proportion ($\Var(X)=\pi(1-\pi)$), so there is really just one unknown. In the case of continuous data, the standard deviation would need to be estimated. 

Let $S^2$ be defined as:  

$$
S^2={\sum (X_i-\bar{X})^2\over n-1}
$$

Recall that this is an unbiased estimate for $\sigma^2$. The sampling distribution of $S^2$ can be found using the following lemma.

>Lemma: Let $X_1,X_2,...,X_n$ be an iid sequence of random variables from a normal population with mean $\mu$ and standard deviation $\sigma$. Then,  
$$
{(n-1)S^2\over \sigma^2}\sim \textsf{Chisq}(n-1)
$$

The $\textsf{Chisq}(n-1)$ distribution is read as the "chi-squared" distribution ("chi" is pronounced "kye"). This can also be written as $\chi^2 (n-1)$. The chi-squared distribution has one parameter: degrees of freedom. The chi-squared distribution is used in other contexts such as goodness of fit problems like the golf ball example from last lesson, we will discuss this particular application in a later chapter.   

The proof of this lemma is outside the scope of this book, but it is not terribly complicated. It follows from the fact that the sum of $n$ squared random variables, each with the standard normal distribution, follows the chi-squared distribution with $n$ degrees of freedom. 

This lemma can be used to draw inferences about $\sigma^2$. For a particular value of $\sigma^2$, we know how $S^2$ should behave. So, for a particular value of $S^2$, we can figure out reasonable values of $\sigma^2$. 

In practice, one rarely estimates $\sigma$ for the purpose of inferring on $\sigma$. Typically, we are interested in estimating $\mu$ and we need to account for the added uncertainty in estimating $\sigma$ as well. That is what we will discuss in the next section.


### Important Note  

Just like for the $t$ distribution, the lemma above assumed that each $X_i$ in the sequence of random variables was *normally* distributed. While the central limit theorem has no such normality assumption, the distribution of the chi-square statistic is subject to the distribution of the underlying population. With large enough expected counts, this assumption is not necessary. Again, there is no magic number, but some resources state that no expected count should be less than one and no more than 20% of the expected counts should be less than five. 

One advantage of simulation-based inference methods is that these methods do not rely on any such distributional assumptions. However, the simulation-based methods may have smaller power for the same sample size.


## Categorical data

It is worth spending some time on common approaches to categorical data that you may come across. We have already dealt with categorical data to some extent in this course. We have performed hypothesis tests and built confidence intervals for $\pi$, the population proportion of "success" in binary cases (for example, support for a local measure in a vote). This problem had a single variable. Also, the golf ball example involved counts of four types of golf ball. This is considered categorical data because each observation is characterized by a qualitative value (number on the ball). The data are summarized by counting how many balls in a sample belong to each type. This again was a single variable. 

In another scenario, suppose we are presented with two qualitative variables and would like to know if they are independent. For example, we have discussed methods for determining whether a coin could be fair. What if we wanted to know whether flipping the coin during the day or night changes the fairness of the coin? In this case, we have two categorical variables with two levels each: result of coin flip (heads vs tails) and time of day (day vs night). We have solved this type of problem by looking at a difference in probabilities of success using randomization and mathematically derived solutions, CLT. We also used a hypergeometric distribution to obtain an exact p-value. 

We will next explore a scenario that involves categorical data with two variables but where at least one variable has more than two levels. However, note that we are only merely scratching the surface in our studies. You could take an entire course on statistical methods for categorical data. This book is giving you a solid foundation to learn more advanced methods. 

### Health evaluation and linkage to primary care  

The Health Evaluation and Linkage to Primary Care (HELP) study was a clinical trial for adult inpatients recruited from a detoxification unit. Patients with no primary care physician were randomized to receive a multidisciplinary assessment and a brief motivational intervention or usual care, with the goal of linking them to primary medical care.  

The `HELPrct` data set is available in the **mosaicData** package. We are interested in whether there are differences between males and females, particularly in the variable `substance`, the primary substance of abuse. 

#### REMOVE OR EDIT THIS - INTERESTED IN DIFF OF MEANS IN CH 25 BOOTSTRAP ####


```r
data("HELPrct")
```


```r
HELP_sub <- HELPrct %>%
  select(age,sex)
```


```r
favstats(age~sex,data=HELP_sub)
```

```
##      sex min Q1 median   Q3 max     mean       sd   n missing
## 1 female  21 31     35 40.5  58 36.25234 7.584858 107       0
## 2   male  19 30     35 40.0  60 35.46821 7.750110 346       0
```


```r
HELP_sub %>%
  gf_boxplot(age~sex) %>%
  gf_theme(theme_classic()) %>%
  gf_labs(x="Gender",y="Age (years)")
```

<div class="figure">
<img src="22-Additional-Hypothesis-Tests_files/figure-html/box232-fig-1.png" alt="The distribution of age in the HELP study by gender." width="672" />
<p class="caption">(\#fig:box232-fig)The distribution of age in the HELP study by gender.</p>
</div>



```r
HELP_sub %>%
  gf_dhistogram(~age|sex,fill="cyan",color="black") %>%
  gf_theme(theme_classic()) %>%
  gf_labs(x="Age",y="")
```

<div class="figure">
<img src="22-Additional-Hypothesis-Tests_files/figure-html/hist232-fig-1.png" alt="The distribution of age in the HELP study by gender." width="672" />
<p class="caption">(\#fig:hist232-fig)The distribution of age in the HELP study by gender.</p>
</div>


Figures \@ref(fig:box232-fig) and \@ref(fig:hist232-fig) indicate there might be a slight difference in the means, but is it statistically significant?

#### Age and Sex example ends here #### 

There are three substances: alcohol, cocaine, and heroin. We’d like to know if there is evidence that the proportions of use differ for males and females. In our data set, we observe modest differences.


```r
tally(substance ~ sex, data = HELPrct, format = "prop", margins = TRUE)
```

```
##          sex
## substance    female      male
##   alcohol 0.3364486 0.4075145
##   cocaine 0.3831776 0.3208092
##   heroin  0.2803738 0.2716763
##   Total   1.0000000 1.0000000
```

But we need a test statistic to determine if there is a difference in substance of abuse between males and females.


### Test statistic  

To help us develop and understand a test statistic, let's simplify and use a simple theoretical example. 

Suppose we have a 2 x 2 contingency table like the one below.  

$$
\begin{array}{lcc}
 & \mbox{Response 1} & \mbox{Response 2} \\
 \mbox{Group 1} & n_{11} & n_{12} \\
 \mbox{Group 2} & n_{21} & n_{22} 
\end{array}
$$

If our null hypothesis is that the two variables are independent, a classical test statistic used is the Pearson chi-squared test statistic ($X^2$). This is similar to the one we used in our golf ball example. Let $e_{ij}$ be the expected count in the $i$th row and $j$th column under the null hypothesis, then the test statistic is:  

$$
X^2=\sum_{i=1}^2 \sum_{j=1}^2 {(n_{ij}-e_{ij})^2\over e_{ij}}
$$

But how do we find $e_{ij}$? What do we expect the count to be under $H_0$? To find this, we recognize that under $H_0$ (independence), a joint probability is equal to the product of the marginal probabilities. Let $\pi_{ij}$ be the probability of an outcome appearing in row $i$ and column $j$. In the absence of any other information, our best guess at $\pi_{ij}$ is $\hat{\pi}_{ij}={n_{ij}\over n}$, where $n$ is the total sample size. But under the null hypothesis we have the assumption of independence, thus $\pi_{ij}=\pi_{i+}\pi_{+j}$ where $\pi_{i+}$ represents the total probability of ending up in row $i$ and $\pi_{+j}$ represents the total probability of ending up in column $j$. Note that $\pi_{i+}$ is estimated by $\hat{\pi}_{i+}$ and  

$$
\hat{\pi}_{i+}={n_{i+}\over n}
$$
Thus for our simple 2 x 2 example, we have: 

$$
\hat{\pi}_{i+}={n_{i+}\over n}={n_{i1}+n_{i2}\over n}
$$

And for Group 1 we would have:

$$
\hat{\pi}_{1+}={n_{1+}\over n}={n_{11}+n_{12}\over n}
$$

So, under $H_0$, our best guess for $\pi_{ij}$ is:  

$$
\hat{\pi}_{ij}=\hat{\pi}_{i+}\hat{\pi}_{+j}={n_{i+}\over n}{n_{+j}\over n} = {n_{i1}+n_{i2}\over n}{n_{1j}+n_{2j}\over n}
$$

Continuing, under $H_0$ the expected cell count is: 

$$
e_{ij}=n\hat{\pi}_{ij}=n{n_{i+}\over n}{n_{+j}\over n}={n_{i+}n_{+j}\over n}
$$


### Extension to larger tables

The advantage of using the Pearson chi-squared is that it can be extended to larger **contingency tables**, the name given to these tables of multiple categorical variables. Suppose we are comparing two categorical variables, one with $r$ levels and the other with $c$ levels. Then,
$$
X^2=\sum_{i=1}^r \sum_{j=1}^c {(n_{ij}-e_{ij})^2\over e_{ij}}
$$

Under the null hypothesis of independence, the $X^2$ test statistic follows the chi-squared distribution with $(r-1)(c-1)$ degrees of freedom. 


#### Assumptions reiterated

Note that to use this test statistic, the expected cell counts must be reasonably large. In fact, no $e_{ij}$ should be less than 1 and no more than 20% of the $e_{ij}$'s should be less than 5. If this occurs, you should combine cells or look for a different test. 

This may all look too abstract, so let's break it down with an example. 


### Test statistic for the HELP example

#### REWRITE THE FOLLOWING WITH THE HELP DATA AND OMIT THE COIN FLIP EXAMPLE #### 


Suppose we flip a coin 40 times during the day and 40 times at night and obtain the results below. 

$$
\begin{array}{lcc}
 & \mbox{Heads} & \mbox{Tails} \\
 \mbox{Day} & 22 & 18 \\
 \mbox{Night} & 17 & 23 
\end{array}
$$

To find the Pearson chi-squared ($X^2$), we need to figure out the expected value under $H_0$. Recall that under $H_0$ the two variables are independent. It's helpful to add the row and column totals prior to finding expected counts: 

$$
\begin{array}{lccc}
 & \mbox{Heads} & \mbox{Tails} & \mbox{Row Total}\\
 \mbox{Day} & 22 & 18  & 40\\
 \mbox{Night} & 17 & 23 & 40 \\
 \mbox{Column Total} & 39 & 41 & 80
\end{array}
$$

Thus under independence, expected count is equal to the row sum multiplied by the column sum divided by the overall sum. So, 

$$
e_{11} = {40*39\over 80}= 19.5
$$

Continuing in this fashion yields the following table of expected counts: 

$$
\begin{array}{lcc}
 & \mbox{Heads} & \mbox{Tails} \\
 \mbox{Day} & 19.5 & 20.5 \\
 \mbox{Night} & 19.5 & 20.5 
\end{array}
$$

Now we can find $X^2$: 

$$
X^2= {(22-19.5)^2\over 19.5}+{(17-19.5)^2\over 19.5}+{(18-20.5)^2\over 20.5}+{(23-20.5)^2\over 20.5} 
$$

As you can probably tell, $X^2$ is essentially comparing the observed counts with the expected counts under $H_0$. The larger the difference between observed and expected, the larger the value of $X^2$. It is normalized by dividing by the expected counts since more data in a cell leads to a larger contribution to the sum. Under $H_0$, this statistic follows the chi-squared distribution with $(R-1)(C-1)$, in this case 1, degrees of freedom ($R$ is the number of rows and $C$ is the number of columns). 


### Calculate the p-value  

To find the Pearson chi-squared statistic ($X^2$) and corresponding p-value from the chi-squared distribution in `R` use the following code: 


```r
e<-c(19.5,19.5,20.5,20.5)
o<-c(22,17,18,23)
x2<-sum(((o-e)^2)/e)

x2
```

```
## [1] 1.250782
```


```r
1-pchisq(x2,1)
```

```
## [1] 0.2634032
```

Note that the chi-squared test statistic is a sum of squared differences. Thus its distribution, a chi-squared, is skewed right and bounded on the left at zero. A departure from the null hypothesis means a value further in the right tail of the distribution. This is why we use one minus the CDF in the calculation of the p-value.

Again, the $p$-value suggests there is not enough evidence to say these two variables are dependent.

Of course there is a built in function in `R` that will make the calculations easier. It is `chisq.test()`.


```r
coin <- tibble(time = c(rep("Day",40),rep("Night",40)),
               result = c(rep(c("Heads","Tails"),c(22,18)),rep(c("Heads","Tails"),c(17,23))))
```


```r
tally(~time+result,data=coin)
```

```
##        result
## time    Heads Tails
##   Day      22    18
##   Night    17    23
```


```r
chisq.test(tally(~time+result,data=coin),correct = FALSE)
```

```
## 
## 	Pearson's Chi-squared test
## 
## data:  tally(~time + result, data = coin)
## X-squared = 1.2508, df = 1, p-value = 0.2634
```

If you just want the test statistic, which we will for permutation tests, then use:


```r
chisq(~time+result,data=coin)
```

```
## X.squared 
##  1.250782
```


### Permutation test

We will complete our analysis of the HELP data first using a randomization, approximate permutation, test.

First let's write the hypotheses:

$H_0$: The variables sex and substance are independent.  
$H_a$: The variables sex and substance are dependent.  

We will use the chi-squared test statistic as our test statistic. We could use a different test statistic such as using the absolute value function instead of the square function but then we would need to write a custom function.

First, let's get the observed value for the test statistic:


```r
obs <- chisq(substance~sex,data=HELPrct)
obs
```

```
## X.squared 
##  2.026361
```

Next we will use a permutation randomization process to find the sampling distribution of our test statistics.


```r
set.seed(2720)
results <- do(1000)*chisq(substance~shuffle(sex),data=HELPrct)
```

Figure \@ref(fig:hist241-fig) is a visual summary of the results which helps us to gain some intuition about the p-value. We also plot the theoretical chi-squared distribution as a dark blue overlay.


```r
results %>%
  gf_dhistogram(~X.squared,fill="cyan",color="black") %>%
  gf_vline(xintercept = obs,color="red") %>%
  gf_theme(theme_classic()) %>%
  gf_dist("chisq",df=2,color="darkblue") %>%
  gf_labs(title="Sampling distribution of chi-squared test statistic",
          subtitle="For the variables sex and substance in the HELPrct data set",
          x="Test statistic")
```

<div class="figure">
<img src="22-Additional-Hypothesis-Tests_files/figure-html/hist241-fig-1.png" alt="Sampling distribution of chi-squared statistic from randomization test." width="672" />
<p class="caption">(\#fig:hist241-fig)Sampling distribution of chi-squared statistic from randomization test.</p>
</div>

We find the p-value using `prop1()`.


```r
prop1((~X.squared>=obs),data=results)
```

```
## prop_TRUE 
## 0.3536464
```

We don't double this value because the chi-squared is a one sided test due to the fact that we squared the differences.

Based on this p-value, we fail to reject the hypothesis that the variables are independent.


### Chi-squared test in `R`

We will jump straight to using the function `chisq.test()`.


```r
chisq.test(tally(substance~sex,data=HELPrct))
```

```
## 
## 	Pearson's Chi-squared test
## 
## data:  tally(substance ~ sex, data = HELPrct)
## X-squared = 2.0264, df = 2, p-value = 0.3631
```

We get a p-value very close to the one from the randomization permutation test. Remember in the randomization test we shuffled the variable `sex` over many replications and calculated a value for the test statistic for each replication. We did this shuffling because the null hypothesis assumed independence of the two variables. This process led to an empirical estimate of the sampling distribution, the gray histogram in the previous graph. In this section, under the null hypothesis and the appropriate assumptions, the sampling distribution is a chi-squared, the blue line in the previous graph. We used it to calculate the p-value directly.

Notice that if the null hypothesis is true, the test statistic has the minimum value of zero. We can't use a bootstrap confidence interval on this problem because zero will never be in the interval. It can only be on the edge of an interval.


## Numerical data 

#### CONVERT TO A TWO SAMPLE T-TEST #### 




Sometimes we want to compare means across many groups. In this case we have two variables where one is continuous and the other categorical. We might initially think to do pairwise comparisons, two sample t-tests, as a solution; for example, if there were three groups, we might be tempted to compare the first mean with the second, then with the third, and then finally compare the second and third means for a total of three comparisons. However, this strategy can be treacherous. If we have many groups and do many comparisons, it is likely that we will eventually find a difference just by chance, even if there is no difference in the populations.

In this section, we will learn a new method called **analysis of variance** (ANOVA) and a new test statistic called $F$. ANOVA uses a single hypothesis test to check whether the means across many groups are equal. The hypotheses are:

$H_0$: The mean outcome is the same across all groups. In statistical notation, $\mu_1 = \mu_2 = \cdots = \mu_k$ where $\mu_i$ represents the mean of the outcome for observations in category $i$.  
$H_A$: At least one mean is different.  
  
Generally we must check three conditions on the data before performing ANOVA with the $F$ distribution:

i. the observations are independent within and across groups,  
ii. the data within each group are nearly normal, and  
iii. the variability across the groups is about equal.  

When these three conditions are met, we may perform an ANOVA to determine whether the data provide strong evidence against the null hypothesis that all the $\mu_i$ are equal.


### MLB batting performance

We would like to discern whether there are real differences between the batting performance of baseball players according to their position: outfielder (`OF`), infielder (`IF`), designated hitter (`DH`), and catcher (`C`). We will use a data set `mlbbat10` from the **openintro** package but we saved it is in the file `mlb_obp.csv` which has been modified from the original data set to include only those with more than 200 at bats. The batting performance will be measured with the on-base percentage. The on-base percentage roughly represents the fraction of the time a player successfully gets on base or hits a home run.

Read the data into `R`.


```r
mlb_obp <- read_csv("data/mlb_obp.csv")
```

Let's review our data:


```r
inspect(mlb_obp)
```

```
## 
## categorical variables:  
##       name     class levels   n missing
## 1 position character      4 327       0
##                                    distribution
## 1 IF (47.1%), OF (36.7%), C (11.9%) ...        
## 
## quantitative variables:  
##      name   class   min    Q1 median     Q3   max     mean         sd   n
## ...1  obp numeric 0.174 0.309  0.331 0.3545 0.437 0.332159 0.03570249 327
##      missing
## ...1       0
```

Next change the variable `position` to a factor to give us greater control.


```r
mlb_obp <- mlb_obp %>%
  mutate(position=as.factor(position))
```


```r
favstats(obp~position,data=mlb_obp)
```

```
##   position   min      Q1 median      Q3   max      mean         sd   n missing
## 1        C 0.219 0.30000 0.3180 0.35700 0.405 0.3226154 0.04513175  39       0
## 2       DH 0.287 0.31625 0.3525 0.36950 0.412 0.3477857 0.03603669  14       0
## 3       IF 0.174 0.30800 0.3270 0.35275 0.437 0.3315260 0.03709504 154       0
## 4       OF 0.265 0.31475 0.3345 0.35300 0.411 0.3342500 0.02944394 120       0
```

The means for each group are pretty close to each other.

> **Exercise**:
The null hypothesis under consideration is the following: $\mu_{OF} = \mu_{IF} = \mu_{DH} = \mu_{C}$.
Write the null and corresponding alternative hypotheses in plain language.^[$H_0$: The average on-base percentage is equal across the four positions. $H_A$: The average on-base percentage varies across some (or all) groups.]

If we have all the data for the 2010 season, why do we need a hypothesis test? What is the population of interest?

If we are only making decisions or claims about the 2010 season, we do not need hypothesis testing. We can just use summary statistics. However, if we want to generalize to other years or other leagues, then we would need a hypothesis test. 

> **Exercise**:  
Construct side-by-side boxplots.

Figure \@ref(fig:box241-fig) is the side-by-side boxplots. 


```r
mlb_obp %>%
  gf_boxplot(obp~position) %>%
  gf_labs(x="Position Played",y="On Base Percentage") %>%
  gf_theme(theme_bw()) %>%
  gf_labs(title="Comparison of OBP for different positions")
```

<div class="figure">
<img src="22-Additional-Hypothesis-Tests_files/figure-html/box241-fig-1.png" alt="Boxplots of on base percentage by position played." width="672" />
<p class="caption">(\#fig:box241-fig)Boxplots of on base percentage by position played.</p>
</div>

The largest difference between the sample means is between the designated hitter and the catcher positions. Consider again the original hypotheses:  

$H_0$: $\mu_{OF} = \mu_{IF} = \mu_{DH} = \mu_{C}$  
$H_A$: The average on-base percentage ($\mu_i$) varies across some (or all) groups.  


#### ADD PERMUTATION TEST #### 


Why might it be inappropriate to run the test by simply estimating whether the difference of $\mu_{DH}$ and $\mu_{C}$ is statistically significant at a 0.05 significance level?  The primary issue here is that we are inspecting the data before picking the groups that will be compared. It is inappropriate to examine all data by eye (informal testing) and only afterwards decide which parts to formally test. This is called **data snooping** or **data fishing**. Naturally we would pick the groups with the large differences for the formal test, leading to an inflation in the Type 1 Error rate. To understand this better, let's consider a slightly different problem.

Suppose we are to measure the aptitude for students in 20 classes in a large elementary school at the beginning of the year. In this school, all students are randomly assigned to classrooms, so any differences we observe between the classes at the start of the year are completely due to chance. However, with so many groups, we will probably observe a few groups that look rather different from each other. If we select only these classes that look so different, we will probably make the wrong conclusion that the assignment wasn't random. While we might only formally test differences for a few pairs of classes, we informally evaluated the other classes by eye before choosing the most extreme cases for a comparison.

In the next chapter, we will learn how to use the $F$ statistic and ANOVA to test whether observed differences in means could have happened just by chance even if there was no difference in the respective population means.



## Homework Problems

1. Golf balls   

Repeat the analysis of the golf ball problem from earlier in the book.


a. Load the data and tally the data into a table. The data is in `golf_balls.csv`.   

b. Using the function `chisq.test()`, conduct a hypothesis test of equally likely distribution of balls. You may have to read the help menu for `chisq.test()`.   

c. Repeat part b, but assume balls with the numbers 1 and 2 occur 30\% of the time and balls with 3 and 4 occur 20\% of the time.  


2. Test of variance

    We have not performed a test of variance so we will create our own.

a. Using the MLB from the reading, subset on `IF` and `OF`.   

b. Create a side-by-side boxplot.  

    The hypotheses are:  

$H_0$: $\sigma^2_{IF}=\sigma^2_{OF}$. There is no difference in the variance of on base percentage for infielders and outfielders.   
$H_A$: $\sigma^2_{IF}\neq \sigma^2_{OF}$. There is a difference in variances.
 
c. Use the differences in sample standard deviations as your test statistic. Using a permutation test, find the p-value and discuss your decision.   

#### REMOVE THIS??? ####

d. Create a bootstrap distribution of the differences in sample standard deviations, and report a 95\% confidence interval. Compare with part d.


3. Exploration of the chi-squared and $t$ distributions. 

a. In `R`, plot the pdf of a random variable with the chi-squared distribution with 1 degree of freedom. On the same plot, include the pdfs with degrees of freedom of 5, 10 and 50. Describe how the behavior of the pdf changes with increasing degrees of freedom.   

b. Repeat part (a) with the $t$ distribution. Add the pdf of a standard normal random variable as well. What do you notice? 


 