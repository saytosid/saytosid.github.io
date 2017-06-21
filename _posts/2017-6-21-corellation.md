---
layout: post
title: 'Practicle guide to Correlation measures'
title: Practicle guide to Correlation measures
published: true
read_time: 2m
excerpt: Completely free method to run keras, tensorflow in the cloud on high performance GPUs with support of running jupyter notebooks also. All you need is an email id and you get 100hrs of free use.
excerpt: General talk about different correlation measures and when to use what. Compared Spearman, Pearson and Kendall correlation measures.
tags:
  - Deep Learning
  - Correlation
  - Kendall
  - Spearman
  - Pearson
---
###TLDR  
Use Kendall for most cases its the best option.  

## Corellation Measure  
Corellation measure is used to measure the degree of relationship between two variables. There are different kinds of corellation measures that can be used depending on the type of data and use case. Some common correlation measures are Pearson, Spearman and Kendall corellations. In this post I will try to explain beiefly what these do and when to use them. Formulas for these can be found easily elsewhere, Implementations are available in Pandas library.    
### Pearson  
Can compute degree of relationship between two variables however it assumes that data is Linear and Homoscedastic.  
- Linearity: X,Y are linear if, graph of X,Y is a straight line  
- Homoscedasticity: X,Y are homoscedastic if they come from some Gaussian distribution.  

What does that mean? Well to put it in simple practical points.
- Use when
    - Data appears to have a simple linear relationship(If it has).
    - Data is stationary (Mean, Variances, etc. dont change)
    - Data appears to be normally distributed around a mean point with some variance.
        - There are tests available to find out weather data is coming from a normal distribution.
- Dont use when
    - Data is non stationary
    - Data is not linearly related
- It will give some readings if you use it for non linear, non gaussian data but those wont be reliable indicators of corellations.

### Spearman Corellation  
It is a more robust correlation measure as it does not assume anything about the distribution of the data. However it only looks for monotonic relationships, and is generally suited for ordinal variables. eg: Finding the relationship betweeen the order of students who finish a race with the amount of hours they practice.  
Note that this captures only the monotonic relationships, as can be seen in Fig 1 however it cannot capture non monotonically related variables as in Fig 2.  
![Monotonic relationship captured by Spearman coeff.]({{site.baseurl}}/images/correlation/monotonic_spearman.png)  
Fig 1: Spearman coeff = 1  
![Monotonic relationship captured by Spearman coeff.]({{site.baseurl}}/images/correlation/zero_spearman.png)  
Fig 2: Spearman coeff = 0  
Note: Spearman correlation is good for finding out weather two variables are independent or not, however when they are not independent it doesnt convey much information.
- Use when
    - The relationship is monotonic (either always increasing of always decreasing)
    - Order of values of a variable may be of interest (Spearman rho)

### Kendall Correlation  
Kendall correlation does not assume anything about the distribution of the data like Spearman. Spearman has a flaw it is good to find weather there is monotonic dependence or not, if there is monotonic dependence the value is difficult to interpret. Kendall on the other hand can quantify the strength of dependence between variables.  
Kendall is the best correlation measure as it is non parametric (Doesnt assume distribution of the data), and can be used to establish weather two variables are dependent or not and how much (if they are dependent).  

#### References  
[Minitab Express Support's page on correlations](http://support.minitab.com/en-us/minitab-express/1/help-and-how-to/modeling-statistics/regression/supporting-topics/basics/a-comparison-of-the-pearson-and-spearman-correlation-methods/ "MiniTab Express Support" )  
[Statisticssolutions.com's page on Correlation](http://www.statisticssolutions.com/correlation-pearson-kendall-spearman/ "statisticssolutions.com")  
[Wikipedia - Pearson Correlation](https://en.wikipedia.org/wiki/Pearson_correlation_coefficient "Wikipedia - Pearson Correlation")  
[Wikipedia - Spearman Correlation](https://en.wikipedia.org/wiki/Spearman%27s_rank_correlation_coefficient "Wikipedia - Spearman Correlation")  
[Statsdirect - Kendall Correlation](http://www.statsdirect.com/help/nonparametric_methods/kendall_correlation.htm)  
[Wikipedia - Kendall Correlation](https://en.wikipedia.org/wiki/Kendall_rank_correlation_coefficient)  
