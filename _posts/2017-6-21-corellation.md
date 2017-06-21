---
layout: post
title: 'Practicle guide to Correlation measures'
title: Practicle guide to Correlation measures
published: true
read_time: 2m
excerpt: Completely free method to run keras, tensorflow in the cloud on high performance GPUs with support of running jupyter notebooks also. All you need is an email id and you get 100hrs of free use.
excerpt: General talk about different correlation measures and when to use what.
tags:
  - Deep Learning
  - Correlation
  - Kendall
  - Spearman
  - Pearson
---
## Different Corellation Measures  
Corellation measures are used to measure the degree of relationship between two variables. There are different kinds of corellation measures that can be used depending on the type of data and use case. Some common correlation measures are Pearson, Spearman and Kendall corellations. In this post I will try to explain beiefly what these do and when to use them. Formulas for these can be found easily elsewhere, Implementations are available in Pandas library.    
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
- Use when
    - The relationship is monotonic (either always increasing of always decreasing)
    - Order of values of a variable may be of interest




#### References  
[Minitab Express Support's page on correlations](http://support.minitab.com/en-us/minitab-express/1/help-and-how-to/modeling-statistics/regression/supporting-topics/basics/a-comparison-of-the-pearson-and-spearman-correlation-methods/ "MiniTab Express Support" )  
[StatisticsSolutions.com's page on Correlation](http://www.statisticssolutions.com/correlation-pearson-kendall-spearman/ "statisticssolutions.com")  
[Wikipedia - Pearson Correlation](https://en.wikipedia.org/wiki/Pearson_correlation_coefficient "Wikipedia - Pearson Correlation")  
[Wikipedia - Spearman Correlation](https://en.wikipedia.org/wiki/Spearman%27s_rank_correlation_coefficient "Wikipedia - Spearman Correlation")  

