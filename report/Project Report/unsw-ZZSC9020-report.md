---
title: "A Data Science Approach to Forecasting Electricity Demand in NSW, Australia"
team: "D"
session: Hex 3, 2021
coursecode: MATH0000
author: 
  - "Baheerathan Gnanasundram, "
  - "Matthew Seery, "
  - "Mohammad Ahsan Ullah, " 
  - "Rahul Lobo." 
date: "15/06/2021"
Acknowledgements: 
  - "All thanks must go to our families and university professors who have guided us through this Capstone Project. Without them this would not be possible."

Abstract: "Forecasting electricity demand is an important requirement as there are now more interested stakeholders associated with the generation and distribution of this service. Traditionally electricity demand was just the concern of governments. However, this has now been extended to market bodies and owners and operators of the underlying infrastructure required for this service. Forecasting accurate energy demand not only supports network infrastructure, but also aides investment decisions about power generation. It is of thus of interest to a variety of stakeholders including power utilities, energy policymakers, and private investors just to name a few. This study aims to demonstrate how neural network (specifically LSTM neural networks) can be used to accurately forecast short-term energy demand. The focus will be on attributes such as temperature, month of the year, day of the week and time of the day as well as how past time lags can be used to predict future demand values. It is envisaged that the results of this study will provide useful insights for governments and market bodies to assist in the rules, policies and pricing that are invoked on the energy sector. Additionally, the businesses operating in this sector can use this information to guide their decision-making regarding electricity generation and distribution, as well as for the purpose of price benchmarking."
output:
  pdf_document:
    template: template.tex
    md_extensions: +raw_attribute
    keep_md: true 
    keep_tex: true 
    pandoc_args:
    - --top-level-division="chapter"
    toc: true
    toc_depth: 1
    number_sections: true
---




# Introduction {.label:s-intro}

Towards the end of the 20th century, countries throughout the world began moving away from regulated government-controlled energy supply to a deregulated sector influenced by market forces \cite{Catalao2007}. This means that forecasting for electricity demands is essential information required beyond previously regulated governmental structures. It is now required by the market bodies working in the sector and private industries who invest in the generation and distribution of electricity. In turn, this aids in better rules, policies, and pricing in the energy sector. However, for this study, the focus will primarily be on short-term forecasting as this can greatly aid vested parties concerned in maximising profits and cutting costs.

\bigskip

Temperature plays a significant role in electricity demand. This is because heating is utilised more by customers in the cooler months while cooling is required for the hottest months of the year. For that reason, temperature is an essential attribute that will be investigated in this study. However, temperature does not account for other factors such as humidity or varying electricity usage patterns associated with specific days of the weeks. For example, a temperature of 25 degrees in Spring may not lead to as much usage of air conditioning as a humid day in Summer with the same temperature. Additionally, the rate of usage of electricity will inevitably vary between weekdays, weekends, and public holidays due to the varying ratios of usage between business and residential customers. Therefore, the month of the year, day of the week and time of day will also be examined in this study.

# Literature Review

There have been various studies undertaken where more traditional statistical methods such as multiple linear regression (MLR) have been utilised to predict demand \cite{Mohamed2005}. However, in more recent times there has been greater focus on the use of neural networks to help solve the problem of forecasting demand  \cite{Gonzalez2008}. The advantage of neural networks is they are very suitable for determining non-linear relationships   \cite{Gonzalez2008} and have been widely used for short-term demand forecasting \cite{Ciulla2019}. They are also very flexible and easy to configure when dealing with time-series data \cite{Carmona2002}. For neural networks, monthly values have been a popular unit of measure and this is particularly true when short-term forecasting of demand has been employed  \cite{Carmona2002}. However, this proposed solution differs because the focus will be on intervals shorter than even a day as this is of greater interest to the client. Nevertheless, the month of the year will still be considered as an input factor for the model for its potential to distinguish factors such as humidity that are not fully explained by temperature alone. Another distinguishing factor for this study will be the emphasis on the day of the week where each record will be categorised as either a weekday, weekend, or public holiday.

\bigskip

Up until the time of writing, the majority of deep learning models being appliied to energy forecasting fall under the subset of three major ways \cite{Kumar2013}. These are: A feed forward neural network (FFNN)/Multi Layer Perceptron (MLP) through the process of increasing the number of hidden layers, some form of recurrence through a recurrent neural network (RNN), long-short term memory (LSTM) or gated recurrent unit (GRU), or through sequentially combining different types of algorithms into an overall structure. In 2020, Xue et al. contrasted these different approaches in order to forecast the heating demand of a district system \cite{Xue2020}. Their experiments showed that the LSTM models were among the highest-performing models tested for. 

\bigskip

When applied to natural gas forecasting, a close relative to electricity demand, RNN models have proven to be useful in prediction. Wei et al. (2019) explored the application of LSTM for forecasting natural gas consumption of four cities \cite{Xue2020}. In addition, LSTM models used for forecasting were compared with other model techniques, including multiple linear regression, feed-forward neural networks, and a support vector regression in this study. The authors’ rigorous testing demonstrated that LSTM models achieved a greater accuracy than the other data-driven models. It appears that RNN and LSTM  models have formed the majority of accurate forecasting implementations to date, with other machine learning techniques such as SVMs performing as well as, but not better than RNN and LSTM based models. An example of this is demonstrated by Amarasignhe et al. (2017), who contrasted the deep learning techniques of a Convolutional Neural Network (CNN) and LSTM, against a traditional machine learning technique (SVM) in order to forecast the energy demand of a building. This forecast  was for a time period of sixty hours ahead and used 4 years of training data \cite{Amarasinghe2016}. Their experiments proved that the deep learning based forecasting models obtained less forecasting error when compared with standard machine learning-based techniques; in particular, the LSTM obtained the smallest error. 

\bigskip

Due to the significance of the LSTM accuracy across a variety of these studies, it will form the basis of this analysis.

# Material and Methods

## Software

R and Python of course are great software for Data Science. Sometimes, you might want to use `bash` utilities such as `awk` or `sed`.

Of course, to ensure reproducibility, you should use something like `Git` and RMarkdown (or a Jupyter Notebook). Do **not** use Word!

## Description of the Data

How are the data stored? What are the sizes of the data files? How many files? etc.

## Pre-processing Steps

What did you have to do to transform the data so that they become useable?

## Data Cleaning

How did you deal with missing data? etc. 

## Assumptions

What assumptions are you making on the data?

## Modelling Methods

# Exploratory Data Analysis

This is where you explore your data using histograms, scatterplots, boxplots, numerical summaries, etc.

## Using R {.fragile}


```r
boxplot(cars, col = c("#5975a4", "#cc8963"))
```

![](unsw-ZZSC9020-report_files/figure-latex/unnamed-chunk-1-1.pdf)<!-- --> 

## Using Python {.fragile}

See https://cran.r-project.org/web/packages/reticulate/vignettes/r_markdown.html for more details.

\bigskip

You need to install the R package `reticulate`.


```python
print("Python can be used with MATHxxxx!")
```

```
## Python can be used with MATHxxxx!
```

```python
import sys
print(sys.version)
```

```
## 3.6.12 |Anaconda, Inc.| (default, Sep  9 2020, 00:29:25) [MSC v.1916 64 bit (AMD64)]
```



```python
import numpy as np
np.random.seed(1)
np.random.normal(0.0, 1.0, size=10)
```

```
## array([ 1.62434536, -0.61175641, -0.52817175, -1.07296862,  0.86540763,
##        -2.3015387 ,  1.74481176, -0.7612069 ,  0.3190391 , -0.24937038])
```


```python
import pandas as pd
import matplotlib.pyplot as plt
df=pd.DataFrame([[1, 2], [3, 4], [4, 3], [2, 3]])
fig = plt.figure(figsize=(4, 4))
for i in df.columns:
    ax=plt.subplot(2,1,i+1) 
    df[[i]].plot(ax=ax)
    print(i)
```

```
## <AxesSubplot:>
## 0
## <AxesSubplot:>
## 1
```

```python
plt.show()
```

![](unsw-ZZSC9020-report_files/figure-latex/unnamed-chunk-2-1.pdf)<!-- --> 


# Analysis and Results

## A First Model

Having a very simple model is always good so that you can benchmark any result you would obtain with a more elaborate model.

\bigskip

For example, one can use the linear regression model

$$
Y_i = \beta_0 + \beta_1 x_{1i} + \cdots \beta_p x_{pi} + \epsilon_i, \qquad i=1,\ldots,n.
$$
where it is assumed that the $\epsilon_i$'s are i.i.d.\ $N(0,1)$.

# Discussion

Put the results you got in the previous chapter in perspective with respect to the problem studied.

# Conclusion and Further Issues {.label:ccl}

What are the main conclusions? What are your recommendations for the "client"? What further analysis could be done in the future?

A figure:

\begin{figure}[H]
\includegraphics{unsw-logo.png}
\caption{A caption}\label{myfigure}
\end{figure}

In the text, see Figure \ref{myfigure}.

---
# References
---

\bibliographystyle{elsarticle-num}
\bibliography{references}

# Appendix {-}

## **Codes** {-}

Add you codes here.

## **Tables** {-}

If you have tables, you can add them here.

Use https://www.tablesgenerator.com/markdown_tables to crete very simple markdown tables, otherwise use \LaTeX.

| Tables   |      Are      |  Cool |
|----------|:-------------:|------:|
| col 1 is |  left-aligned | $1600 |
| col 2 is |    centered   |   $12 |
| col 3 is | right-aligned |    $1 |


