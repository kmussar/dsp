# Statistics

# Table of Contents

[1. Introduction](#section-a)  
[2. Why We Are Using Think Stats](#section-b)  
[3. Instructions for Cloning the Repo](#section-c)  
[4. Required Exercises](#section-d)  
[5. Optional Exercises](#section-e)  
[6. Recommended Reading](#section-f)  
[7. Resources](#section-g)

## <a name="section-a"></a>1.  Introduction

[<img src="img/think_stats.jpg" title="Think Stats"/>](http://greenteapress.com/thinkstats2/)

Use Allen Downey's [Think Stats (second edition)](http://greenteapress.com/thinkstats2/) book for getting up to speed with core ideas in statistics and how to approach them programmatically. This book is available online, or you can buy a paper copy if you would like.

Use this book as a reference when answering the 6 required statistics questions below.  The Think Stats book is approximately 200 pages in length.  **It is recommended that you read the entire book, particularly if you are less familiar with introductory statistical concepts.**

Complete the following exercises along with the questions in this file. Some can be solved using code provided with the book. The preface of Think Stats [explains](http://greenteapress.com/thinkstats2/html/thinkstats2001.html#toc2) how to use the code.  

Communicate the problem, how you solved it, and the solution, within each of the following [markdown](https://guides.github.com/features/mastering-markdown/) files. (You can include code blocks and images within markdown.)

## <a name="section-b"></a>2.  Why We Are Using Think Stats 

The stats exercises have been chosen to introduce/solidify some relevant statistical concepts related to data science.  The solutions for these exercises are available in the [ThinkStats repository on GitHub](https://github.com/AllenDowney/ThinkStats2).  You should focus on understanding the statistical concepts, python programming and interpreting the results.  If you are stuck, review the solutions and recode the python in a way that is more understandable to you. 

For example, in the first exercise, the author has already written a function to compute Cohen's D.  **You could import it, or you could write your own code to practice python and develop a deeper understanding of the concept.** 

Think Stats uses a higher degree of python complexity from the python tutorials and introductions to python concepts, and that is intentional to prepare you for the bootcamp.  

**One of the skills to learn here is to understand other people’s code.  And this author is quite experienced, so it’s good to learn how functions and imports work.**

---

## <a name="section-c"></a>3.  Instructions for Cloning the Repo 
Using the [code referenced in the book](https://github.com/AllenDowney/ThinkStats2), follow the step-by-step instructions below.  

**Step 1. Create a directory on your computer where you will do the prework.  Below is an example:**

```
(Mac):      /Users/yourname/ds/metis/metisgh/prework  
(Windows):  C:/ds/metis/metisgh/prework
```

**Step 2. cd into the prework directory.  Use GitHub to pull this repo to your computer.**

```
$ git clone https://github.com/AllenDowney/ThinkStats2.git
```

**Step 3.  Put your ipython notebook or python code files in this directory (that way, it can pull the needed dependencies):**

```
(Mac):     /Users/yourname/ds/metis/metisgh/prework/ThinkStats2/code  
(Windows):  C:/ds/metis/metisgh/prework/ThinkStats2/code
```

---


## <a name="section-d"></a>4.  Required Exercises

*Include your Python code, results and explanation (where applicable).*


### Q1. [Think Stats Chapter 2 Exercise 4](statistics/2-4-cohens_d.md) (effect size of Cohen's d)  
Cohen's D is an example of effect size.  Other examples of effect size are:  correlation between two variables, mean difference, regression coefficients and standardized test statistics such as: t, Z, F, etc. In this example, you will compute Cohen's D to quantify (or measure) the difference between two groups of data.   

    others.totalwgt_lb.mean() - firsts.totalwgt_lb.mean()
First babies are on average 0.12 pounds lighter than others. 
    
    CohenEffectSize(firsts.totalwgt_lb, others.totalwgt_lb)
This difference is about 0.09 standard deviations - which is very small. 
We can reasonably conclude that there is not much difference between the weights of first babies and other order babies. 

See [ipython file](https://github.com/kmussar/ThinkStats2/blob/master/code/chap02ex_KM.ipynb) for my code in context.

>You will see effect size again and again in results of algorithms that are run in data science.  For instance, in the bootcamp, when you run a regression analysis, you will recognize the t-statistic as an example of effect size.
> - Metis

---
### Q2. [Think Stats Chapter 3 Exercise 1](statistics/3-1-actual_biased.md) (actual vs. biased)
This problem presents a robust example of actual vs biased data.  As a data scientist, it will be important to examine not only the data that is available, but also the data that may be missing but highly relevant.  You will see how the absence of this relevant data will bias a dataset, its distribution, and ultimately, its statistical interpretation.

Excercise: Use the column numkdhh in the nsfg dataset to construct the actual and biased distributions for the number of children under 18 in the households of respondents. Also plot these and compute their means. 

    pmf = thinkstats2.Pmf(resp.numkdhh, label='numkdhh')
    biased = BiasPmf(pmf, label='biased')
    thinkplot.PrePlot(2)
    thinkplot.Pmfs([pmf,biased])
    thinkplot.Config(xlabel='Number of Children', ylabel='PMF')
The biased data does not include any households without children. This makes sense since if children are being asked about their households, households without children can, by definition, not be represented in the survey. 

![Image of unbiased PMF](https://github.com/kmussar/ThinkStats2/blob/master/code/ch3ex1_pmf.png)
![Image of both biased and unbiased PMF](https://github.com/kmussar/ThinkStats2/blob/master/code/ch3ex1_both.png)

Computing their means:
Note: .Mean() works in this file but I beleive the standard python function for mean is .mean() which does not work. Is .Mean() a function specific to thinkstats2? 
    
    pmf.Mean()
    biased.Mean()
The unbiased mean is 1.0 children/household, wherease the biased mean is 2.4 children/household. 
See my [iPython notebook](https://github.com/kmussar/ThinkStats2/blob/master/code/chap03ex-KM.ipynb) for my code in context. 

---

### Q3. [Think Stats Chapter 4 Exercise 2](statistics/4-2-random_dist.md) (random distribution)  
This questions asks you to examine the function that produces random numbers.  Is it really random?  A good way to test that is to examine the pmf and cdf of the list of random numbers and visualize the distribution.  If you're not sure what pmf is, read more about it in Chapter 3.  

    random_numbers = np.random.random(1000)
    random_numbers
    # plot PMF
    thinkplot.Pmf(thinkstats2.Pmf(random_numbers),linewidth=0.1)
    thinkplot.Config(xlabel='Weight (pounds)', ylabel='PMF')
    
    # Plot CDF
    thinkplot.Cdf(thinkstats2.Cdf(random_numbers, label='randomly generated numbers'))
    thinkplot.Config(xlabel='Birth weight (pounds)', ylabel='CDF')
    
![Image of PMF](https://github.com/kmussar/ThinkStats2/blob/master/code/ch4ex2_pmf.png)
![Image of CDF](https://github.com/kmussar/ThinkStats2/blob/master/code/ch4ex2_cdf.png)

Yes, both the PMF and CDF show that randomly generated numbers do indeed have an even distribution. 

However, this seems completely unrelated to birth weight. It looks like all of the randomy generated values are between 0 and 1 while that does not make any sense for birth weight. 

Perhaps a better way of looking at this would be to randomly generate values between the min and max birth weight and compare that distribution (should be even) to the observed distribution.

See my [iPython notebook](https://github.com/kmussar/ThinkStats2/blob/master/code/chap04ex-KM.ipynb) for my code in context.

---
### Q4. [Think Stats Chapter 5 Exercise 1](statistics/5-1-blue_men.md) (normal distribution of blue men)
This is a classic example of hypothesis testing using the normal distribution.  The effect size used here is the Z-statistic. 
In the BRFSS (see Section 5.4), the distribution of heights is roughly normal with parameters µ = 178 cm and σ = 7.7 cm for men, and µ = 163 cm and σ = 7.3 cm for women. 
In order to join Blue Man Group, you have to be male between 5’10” and 6’1” (see http://bluemancasting.com). What percentage of the U.S. male population is in this range? Hint: use scipy.stats.norm.cdf. 
    
    #imports    
    import scipy.stats
    
    #given information
    mu = 178
    sigma = 7.7
    
    # compute distribution (using normal distribution as instructed) 
    dist = scipy.stats.norm(loc=mu, scale=sigma)
    
    # define limits of population we're looking at 
    low = dist.cdf(177.8)    # 5'10"
    high = dist.cdf(185.4)   # 6'1"
    low, high, high-low
    # output: (0.48963902786483265, 0.8317337108107857, 0.3420946829459531)
   
 34.2% of the population is between 5'10 and 6'1 
 This seems high. Maybe if it's just men, but with women included I'd expect this to be lower. 
 
 [iPython notebook](https://github.com/kmussar/ThinkStats2/blob/master/code/chap05ex-KM.ipynb) for context. 

---

### Q5. Bayesian (Elvis Presley twin) 

Bayes' Theorem is an important tool in understanding what we really know, given evidence of other information we have, in a quantitative way.  It helps incorporate conditional probabilities into our conclusions.

Elvis Presley had a twin brother who died at birth.  What is the probability that Elvis was an identical twin? Assume we observe the following probabilities in the population: fraternal twin is 1/125 and identical twin is 1/300.  

To answer this one, you need some background information: According to the Wikipedia article on twins:  ``Twins are estimated to be approximately 1.9% of the world population, with monozygotic twins making up 0.2% of the total---and 8% of all twins.''

The 2 possibilities are: 
A: Elvis's brother was identical (identical birth event) 
B: Elvis's brother was fraternal (fraternal twin event) 

Probability that Elvis's brother was identical = P(A) = P(identical twins) P(identical twins that are both boys) = (1/300) (1/2) = (1/600)

Probability that Elvis's brother was fraternal = P(B) = P(fraternal twins) P(fraternal twins that are both boys) = (1/125) (1/4) = (1/500)

P(identical & boy) = P(A) / (P(A) + P(B)) = (1/600) / (1/600 + 1/500) = 5/11 = 45% 

#### So, it is 45% likely that Elvis's brother was identical. 

---

### Q6. Bayesian &amp; Frequentist Comparison  
How do frequentist and Bayesian statistics compare?

These are both approaches for computing probabilities of events. Frequentist statistics focuses only on repeatable random events with an infinite number of potential events (such as coin tosses), but do not deal with forcasting or predicting the likelihood of single events (such as election results). Bayesian statistics, however, can be applied more broadly to single events as they use piror probabilities to inform the likelihood of the probability you would like to predict. Bayesian statistics alow you to mathematically compute the probability of one event, given another event. 

---

## <a name="section-e"></a>5.  Optional Exercises

The following exercises are optional, but we highly encourage you to complete them if you have the time.

### Q7. [Think Stats Chapter 7 Exercise 1](statistics/7-1-weight_vs_age.md) (correlation of weight vs. age)
In this exercise, you will compute the effect size of correlation.  Correlation measures the relationship of two variables, and data science is about exploring relationships in data.    

### Q8. [Think Stats Chapter 8 Exercise 2](statistics/8-2-sampling_dist.md) (sampling distribution)
In the theoretical world, all data related to an experiment or a scientific problem would be available.  In the real world, some subset of that data is available.  This exercise asks you to take samples from an exponential distribution and examine how the standard error and confidence intervals vary with the sample size.

### Q9. [Think Stats Chapter 6 Exercise 1](statistics/6-1-household_income.md) (skewness of household income)
### Q10. [Think Stats Chapter 8 Exercise 3](statistics/8-3-scoring.md) (scoring)
### Q11. [Think Stats Chapter 9 Exercise 2](statistics/9-2-resampling.md) (resampling)

---

## <a name="section-f"></a>6.  Recommended Reading

Read Allen Downey's [Think Bayes](http://greenteapress.com/thinkbayes/) book.  It is available online for free, or you can buy a paper copy if you would like.

[<img src="img/think_bayes.png" title="Think Bayes"/>](http://greenteapress.com/thinkbayes/) 

---

## <a name="section-g"></a>7.  More Resources

Some people enjoy video content such as Khan Academy's [Probability and Statistics](https://www.khanacademy.org/math/probability) or the much longer and more in-depth Harvard [Statistics 110](https://www.youtube.com/playlist?list=PL2SOU6wwxB0uwwH80KTQ6ht66KWxbzTIo). You might also be interested in the book [Statistics Done Wrong](http://www.statisticsdonewrong.com/) or a very short [overview](http://schoolofdata.org/handbook/courses/the-math-you-need-to-start/) from School of Data.
