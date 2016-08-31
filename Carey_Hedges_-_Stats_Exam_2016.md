Exam 2016
================
Carey Hedges (751546)

Question 1 - Body Temperature and Resting Heart Rate
====================================================

Temperature is interval continuous data and heart rate is discrete numerical data. The gender data is nominal data.

The hypotheses are:

Ho: Relations between body temperature and heart rate are sex independent. H1: Relations between body temperature and heart rate are sex dependent.

A correlation and linear regression analysis should be used to establish if the temperature and heart rate are related in both male and female populations independently.

The assumptions underlying a linear regression are:

1.  A trend exists between heart rate and body temperature.
2.  Observations are independent of one another.
3.  Measurements of the independent variable have been made correctly.
4.  Residuals are normally distributed and are homoskedastic (same variance).

Assumptions underlying Pearson's correlation analyses (as used here) are:

1.  Data should be interval or ratio data.
2.  Data should have a linear relationship.
3.  Data should not have any outliers or pivot points.
4.  Variables should both be approximately normally distributed.

These tests shouyld indicate if there is a relation between temperature and resting heart rate in different genders.

``` r
library(knitr)
library(dplyr)
```

    ## Warning: package 'dplyr' was built under R version 3.3.1

    ## 
    ## Attaching package: 'dplyr'

    ## The following objects are masked from 'package:stats':
    ## 
    ##     filter, lag

    ## The following objects are masked from 'package:base':
    ## 
    ##     intersect, setdiff, setequal, union

``` r
#Instruct R Studio to read the excel spreadsheet

 A <- read.csv('C:/Users/Carey Hedges/Desktop/Stats - Exam/question1.csv')
 A
```

    ##     body_temperature male female
    ## 1               35.7   70     NA
    ## 2               35.8   NA     69
    ## 3               35.9   71     NA
    ## 4               35.9   NA     62
    ## 5               36.0   NA     75
    ## 6               36.1   74     NA
    ## 7               36.1   80     NA
    ## 8               36.2   73     NA
    ## 9               36.2   75     NA
    ## 10              36.2   82     NA
    ## 11              36.2   64     NA
    ## 12              36.2   NA     66
    ## 13              36.2   NA     68
    ## 14              36.3   69     NA
    ## 15              36.3   70     NA
    ## 16              36.3   68     NA
    ## 17              36.3   72     NA
    ## 18              36.3   78     NA
    ## 19              36.3   NA     57
    ## 20              36.4   70     NA
    ## 21              36.4   75     NA
    ## 22              36.4   74     NA
    ## 23              36.4   69     NA
    ## 24              36.4   73     NA
    ## 25              36.4   NA     61
    ## 26              36.5   77     NA
    ## 27              36.5   NA     84
    ## 28              36.5   NA     61
    ## 29              36.6   58     NA
    ## 30              36.6   73     NA
    ## 31              36.6   65     NA
    ## 32              36.6   74     NA
    ## 33              36.6   76     NA
    ## 34              36.6   72     NA
    ## 35              36.6   NA     77
    ## 36              36.6   NA     62
    ## 37              36.6   NA     71
    ## 38              36.6   NA     68
    ## 39              36.6   NA     69
    ## 40              36.6   NA     79
    ## 41              36.7   78     NA
    ## 42              36.7   71     NA
    ## 43              36.7   74     NA
    ## 44              36.7   67     NA
    ## 45              36.7   64     NA
    ## 46              36.7   78     NA
    ## 47              36.7   73     NA
    ## 48              36.7   67     NA
    ## 49              36.7   NA     76
    ## 50              36.7   NA     87
    ## 51              36.7   NA     78
    ## 52              36.7   NA     73
    ## 53              36.7   NA     89
    ## 54              36.7   NA     81
    ## 55              36.8   66     NA
    ## 56              36.8   64     NA
    ## 57              36.8   71     NA
    ## 58              36.8   72     NA
    ## 59              36.8   86     NA
    ## 60              36.8   72     NA
    ## 61              36.8   NA     73
    ## 62              36.8   NA     64
    ## 63              36.8   NA     65
    ## 64              36.8   NA     73
    ## 65              36.8   NA     69
    ## 66              36.8   NA     57
    ## 67              36.8   NA     79
    ## 68              36.8   NA     78
    ## 69              36.8   NA     80
    ## 70              36.9   68     NA
    ## 71              36.9   70     NA
    ## 72              36.9   82     NA
    ## 73              36.9   84     NA
    ## 74              36.9   68     NA
    ## 75              36.9   71     NA
    ## 76              36.9   NA     79
    ## 77              36.9   NA     81
    ## 78              36.9   NA     73
    ## 79              36.9   NA     74
    ## 80              36.9   NA     84
    ## 81              36.9   NA     83
    ## 82              37.0   77     NA
    ## 83              37.0   78     NA
    ## 84              37.0   83     NA
    ## 85              37.0   66     NA
    ## 86              37.0   70     NA
    ## 87              37.0   82     NA
    ## 88              37.0   NA     82
    ## 89              37.0   NA     85
    ## 90              37.0   NA     86
    ## 91              37.0   NA     77
    ## 92              37.1   73     NA
    ## 93              37.1   78     NA
    ## 94              37.1   78     NA
    ## 95              37.1   81     NA
    ## 96              37.1   78     NA
    ## 97              37.1   NA     72
    ## 98              37.1   NA     79
    ## 99              37.1   NA     59
    ## 100             37.1   NA     64
    ## 101             37.1   NA     65
    ## 102             37.1   NA     82
    ## 103             37.1   NA     64
    ## 104             37.1   NA     70
    ## 105             37.1   NA     83
    ## 106             37.1   NA     89
    ## 107             37.1   NA     69
    ## 108             37.1   NA     73
    ## 109             37.1   NA     84
    ## 110             37.2   80     NA
    ## 111             37.2   75     NA
    ## 112             37.2   79     NA
    ## 113             37.2   81     NA
    ## 114             37.2   NA     76
    ## 115             37.2   NA     79
    ## 116             37.2   NA     81
    ## 117             37.3   71     NA
    ## 118             37.3   83     NA
    ## 119             37.3   NA     80
    ## 120             37.3   NA     74
    ## 121             37.3   NA     77
    ## 122             37.3   NA     66
    ## 123             37.4   63     NA
    ## 124             37.4   70     NA
    ## 125             37.4   NA     68
    ## 126             37.4   NA     77
    ## 127             37.5   75     NA
    ## 128             37.7   NA     79
    ## 129             37.8   NA     78
    ## 130             38.2   NA     77

``` r
#Gain a holistic overview of the dataset
 
 summary(A)
```

    ##  body_temperature      male           female     
    ##  Min.   :35.70    Min.   :58.00   Min.   :57.00  
    ##  1st Qu.:36.60    1st Qu.:70.00   1st Qu.:68.00  
    ##  Median :36.80    Median :73.00   Median :76.00  
    ##  Mean   :36.81    Mean   :73.37   Mean   :74.15  
    ##  3rd Qu.:37.10    3rd Qu.:78.00   3rd Qu.:80.00  
    ##  Max.   :38.20    Max.   :86.00   Max.   :89.00  
    ##                   NA's   :65      NA's   :65

``` r
 head(A)
```

    ##   body_temperature male female
    ## 1             35.7   70     NA
    ## 2             35.8   NA     69
    ## 3             35.9   71     NA
    ## 4             35.9   NA     62
    ## 5             36.0   NA     75
    ## 6             36.1   74     NA

``` r
 colnames(A)
```

    ## [1] "body_temperature" "male"             "female"

``` r
 tail(A)
```

    ##     body_temperature male female
    ## 125             37.4   NA     68
    ## 126             37.4   NA     77
    ## 127             37.5   75     NA
    ## 128             37.7   NA     79
    ## 129             37.8   NA     78
    ## 130             38.2   NA     77

``` r
#Isolate male data 
 
AM <- A [,-3]
AM
```

    ##     body_temperature male
    ## 1               35.7   70
    ## 2               35.8   NA
    ## 3               35.9   71
    ## 4               35.9   NA
    ## 5               36.0   NA
    ## 6               36.1   74
    ## 7               36.1   80
    ## 8               36.2   73
    ## 9               36.2   75
    ## 10              36.2   82
    ## 11              36.2   64
    ## 12              36.2   NA
    ## 13              36.2   NA
    ## 14              36.3   69
    ## 15              36.3   70
    ## 16              36.3   68
    ## 17              36.3   72
    ## 18              36.3   78
    ## 19              36.3   NA
    ## 20              36.4   70
    ## 21              36.4   75
    ## 22              36.4   74
    ## 23              36.4   69
    ## 24              36.4   73
    ## 25              36.4   NA
    ## 26              36.5   77
    ## 27              36.5   NA
    ## 28              36.5   NA
    ## 29              36.6   58
    ## 30              36.6   73
    ## 31              36.6   65
    ## 32              36.6   74
    ## 33              36.6   76
    ## 34              36.6   72
    ## 35              36.6   NA
    ## 36              36.6   NA
    ## 37              36.6   NA
    ## 38              36.6   NA
    ## 39              36.6   NA
    ## 40              36.6   NA
    ## 41              36.7   78
    ## 42              36.7   71
    ## 43              36.7   74
    ## 44              36.7   67
    ## 45              36.7   64
    ## 46              36.7   78
    ## 47              36.7   73
    ## 48              36.7   67
    ## 49              36.7   NA
    ## 50              36.7   NA
    ## 51              36.7   NA
    ## 52              36.7   NA
    ## 53              36.7   NA
    ## 54              36.7   NA
    ## 55              36.8   66
    ## 56              36.8   64
    ## 57              36.8   71
    ## 58              36.8   72
    ## 59              36.8   86
    ## 60              36.8   72
    ## 61              36.8   NA
    ## 62              36.8   NA
    ## 63              36.8   NA
    ## 64              36.8   NA
    ## 65              36.8   NA
    ## 66              36.8   NA
    ## 67              36.8   NA
    ## 68              36.8   NA
    ## 69              36.8   NA
    ## 70              36.9   68
    ## 71              36.9   70
    ## 72              36.9   82
    ## 73              36.9   84
    ## 74              36.9   68
    ## 75              36.9   71
    ## 76              36.9   NA
    ## 77              36.9   NA
    ## 78              36.9   NA
    ## 79              36.9   NA
    ## 80              36.9   NA
    ## 81              36.9   NA
    ## 82              37.0   77
    ## 83              37.0   78
    ## 84              37.0   83
    ## 85              37.0   66
    ## 86              37.0   70
    ## 87              37.0   82
    ## 88              37.0   NA
    ## 89              37.0   NA
    ## 90              37.0   NA
    ## 91              37.0   NA
    ## 92              37.1   73
    ## 93              37.1   78
    ## 94              37.1   78
    ## 95              37.1   81
    ## 96              37.1   78
    ## 97              37.1   NA
    ## 98              37.1   NA
    ## 99              37.1   NA
    ## 100             37.1   NA
    ## 101             37.1   NA
    ## 102             37.1   NA
    ## 103             37.1   NA
    ## 104             37.1   NA
    ## 105             37.1   NA
    ## 106             37.1   NA
    ## 107             37.1   NA
    ## 108             37.1   NA
    ## 109             37.1   NA
    ## 110             37.2   80
    ## 111             37.2   75
    ## 112             37.2   79
    ## 113             37.2   81
    ## 114             37.2   NA
    ## 115             37.2   NA
    ## 116             37.2   NA
    ## 117             37.3   71
    ## 118             37.3   83
    ## 119             37.3   NA
    ## 120             37.3   NA
    ## 121             37.3   NA
    ## 122             37.3   NA
    ## 123             37.4   63
    ## 124             37.4   70
    ## 125             37.4   NA
    ## 126             37.4   NA
    ## 127             37.5   75
    ## 128             37.7   NA
    ## 129             37.8   NA
    ## 130             38.2   NA

``` r
#Isolate female data

AF <- A [,-2]
AF
```

    ##     body_temperature female
    ## 1               35.7     NA
    ## 2               35.8     69
    ## 3               35.9     NA
    ## 4               35.9     62
    ## 5               36.0     75
    ## 6               36.1     NA
    ## 7               36.1     NA
    ## 8               36.2     NA
    ## 9               36.2     NA
    ## 10              36.2     NA
    ## 11              36.2     NA
    ## 12              36.2     66
    ## 13              36.2     68
    ## 14              36.3     NA
    ## 15              36.3     NA
    ## 16              36.3     NA
    ## 17              36.3     NA
    ## 18              36.3     NA
    ## 19              36.3     57
    ## 20              36.4     NA
    ## 21              36.4     NA
    ## 22              36.4     NA
    ## 23              36.4     NA
    ## 24              36.4     NA
    ## 25              36.4     61
    ## 26              36.5     NA
    ## 27              36.5     84
    ## 28              36.5     61
    ## 29              36.6     NA
    ## 30              36.6     NA
    ## 31              36.6     NA
    ## 32              36.6     NA
    ## 33              36.6     NA
    ## 34              36.6     NA
    ## 35              36.6     77
    ## 36              36.6     62
    ## 37              36.6     71
    ## 38              36.6     68
    ## 39              36.6     69
    ## 40              36.6     79
    ## 41              36.7     NA
    ## 42              36.7     NA
    ## 43              36.7     NA
    ## 44              36.7     NA
    ## 45              36.7     NA
    ## 46              36.7     NA
    ## 47              36.7     NA
    ## 48              36.7     NA
    ## 49              36.7     76
    ## 50              36.7     87
    ## 51              36.7     78
    ## 52              36.7     73
    ## 53              36.7     89
    ## 54              36.7     81
    ## 55              36.8     NA
    ## 56              36.8     NA
    ## 57              36.8     NA
    ## 58              36.8     NA
    ## 59              36.8     NA
    ## 60              36.8     NA
    ## 61              36.8     73
    ## 62              36.8     64
    ## 63              36.8     65
    ## 64              36.8     73
    ## 65              36.8     69
    ## 66              36.8     57
    ## 67              36.8     79
    ## 68              36.8     78
    ## 69              36.8     80
    ## 70              36.9     NA
    ## 71              36.9     NA
    ## 72              36.9     NA
    ## 73              36.9     NA
    ## 74              36.9     NA
    ## 75              36.9     NA
    ## 76              36.9     79
    ## 77              36.9     81
    ## 78              36.9     73
    ## 79              36.9     74
    ## 80              36.9     84
    ## 81              36.9     83
    ## 82              37.0     NA
    ## 83              37.0     NA
    ## 84              37.0     NA
    ## 85              37.0     NA
    ## 86              37.0     NA
    ## 87              37.0     NA
    ## 88              37.0     82
    ## 89              37.0     85
    ## 90              37.0     86
    ## 91              37.0     77
    ## 92              37.1     NA
    ## 93              37.1     NA
    ## 94              37.1     NA
    ## 95              37.1     NA
    ## 96              37.1     NA
    ## 97              37.1     72
    ## 98              37.1     79
    ## 99              37.1     59
    ## 100             37.1     64
    ## 101             37.1     65
    ## 102             37.1     82
    ## 103             37.1     64
    ## 104             37.1     70
    ## 105             37.1     83
    ## 106             37.1     89
    ## 107             37.1     69
    ## 108             37.1     73
    ## 109             37.1     84
    ## 110             37.2     NA
    ## 111             37.2     NA
    ## 112             37.2     NA
    ## 113             37.2     NA
    ## 114             37.2     76
    ## 115             37.2     79
    ## 116             37.2     81
    ## 117             37.3     NA
    ## 118             37.3     NA
    ## 119             37.3     80
    ## 120             37.3     74
    ## 121             37.3     77
    ## 122             37.3     66
    ## 123             37.4     NA
    ## 124             37.4     NA
    ## 125             37.4     68
    ## 126             37.4     77
    ## 127             37.5     NA
    ## 128             37.7     79
    ## 129             37.8     78
    ## 130             38.2     77

``` r
#Plot data to visualise, and run linear model to assess if the data are correlated.

#Plot of male data

plot(AM$body_temperature, AM$male, 
     main = "Heart Rate versus Body Temperature for Male Subjects",
     xlab = "Body Temperature",
     ylab = "Resting Heart Rate")
```

<img src="./figures/question 1-1.png" style="display: block; margin: auto;" />

``` r
LAM <- lm(AM)
summary(LAM)
```

    ## 
    ## Call:
    ## lm(formula = AM)
    ## 
    ## Residuals:
    ##      Min       1Q   Median       3Q      Max 
    ## -0.98425 -0.28425  0.05305  0.24062  0.80280 
    ## 
    ## Coefficients:
    ##              Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept) 35.813752   0.601771  59.514   <2e-16 ***
    ## male         0.012436   0.008176   1.521    0.133    
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 0.3843 on 63 degrees of freedom
    ##   (65 observations deleted due to missingness)
    ## Multiple R-squared:  0.03542,    Adjusted R-squared:  0.02011 
    ## F-statistic: 2.313 on 1 and 63 DF,  p-value: 0.1333

``` r
#As the male data has no linear relationship, a correlation cannot be performed.

#Plot of female data

plot(AF$body_temperature, AF$female, 
     main = "Heart Rate versus Body Temperature for Female Subjects",
     xlab = "Body Temperature",
     ylab = "Resting Heart Rate")
```

<img src="./figures/question 1-2.png" style="display: block; margin: auto;" />

``` r
LAF <- lm(AF)
summary(LAF)
```

    ## 
    ## Call:
    ## lm(formula = AF)
    ## 
    ## Residuals:
    ##      Min       1Q   Median       3Q      Max 
    ## -1.01469 -0.21469 -0.01469  0.24192  1.26961 
    ## 
    ## Coefficients:
    ##              Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept) 35.816769   0.458825  78.062   <2e-16 ***
    ## female       0.014463   0.006151   2.351   0.0219 *  
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 0.3989 on 63 degrees of freedom
    ##   (65 observations deleted due to missingness)
    ## Multiple R-squared:  0.08066,    Adjusted R-squared:  0.06607 
    ## F-statistic: 5.528 on 1 and 63 DF,  p-value: 0.02186

``` r
CAF <- cor.test(AF$body_temperature, AF$female, method = "pearson")
CAF
```

    ## 
    ##  Pearson's product-moment correlation
    ## 
    ## data:  AF$body_temperature and AF$female
    ## t = 2.3511, df = 63, p-value = 0.02186
    ## alternative hypothesis: true correlation is not equal to 0
    ## 95 percent confidence interval:
    ##  0.04310142 0.49371392
    ## sample estimates:
    ##       cor 
    ## 0.2840149

``` r
#You are required to check that the data is homoskedatic.  Male data is not linear so only female data is used here.

qqnorm(LAF$residuals) 
qqline(LAF$residuals)
```

<img src="./figures/question 1-3.png" style="display: block; margin: auto;" />

Data analysis indicates that there is no linear relationship between the heart rate and body temperature of male subjects, b|= 0.1244, t(63)=1.521, p = 0.1333. There is a weak positive linear relationship (r=0.2840, p=0.02186) between the body temperature and heart rate in females b|= 0.1445, t(63)=2.351, p=0.0219, R<sup>2</sup> = 0.08066 (adjusted R<sup>2</sup> = 0.06607), F(1, 63) = 5.528, p=0.02186. The data from the female population are homoskedastic and do not vialate the basic assumptions of linear regression analyses. This validates the linear model in the female group.

These data indicate that body temperature and heart rate are sex dependent and females with higher resting heart rates will have higher oral body temperature. This inference would be sound for all body temperatures between 35.70 degrees celcius and 38.20 degrees celcius.

Question 2 - Intoxicated Ataxia
===============================

The all of the data variables (that is, left hand, right hand, males, female, line left, line right) are categorical nominal data.

The hypotheses are:

Ho: Handedness does not affect body position and limb favouring in intoxicated subjects. H1: Handedness does affect body position and limb favouring in intoxicated subjects.

A Fisher's exact test will be used to evaluate if handedness affects body position in intoxicated subjects.

The assumptions underlying a Fischer's exact test are :

1.  Values are independent of one another
2.  Sampling is random
3.  Observed frequencies are approximated by normal distribution
4.  Expected values should be 5 or greater in all cells

``` r
library(knitr)
library(dplyr)

#Get R to read the excel spreadsheet

B <- read.csv('C:/Users/Carey Hedges/Desktop/Stats - Exam/question2.csv')
B
```

    ##      id sex handedness first_stumble final_position
    ## 1     1   1          1             1              1
    ## 2     2   1          1             1              1
    ## 3     3   0          1             1              1
    ## 4     4   1          1             1              0
    ## 5     5   1          1             0              0
    ## 6     6   1          0             0              1
    ## 7     7   0          0             0              0
    ## 8     8   0          0             0              0
    ## 9     9   1          0             1              1
    ## 10   10   0          0             0              0
    ## 11   11   0          1             1              1
    ## 12   12   1          1             1              0
    ## 13   13   0          1             0              1
    ## 14   14   0          1             0              0
    ## 15   15   1          1             0              1
    ## 16   16   0          0             1              1
    ## 17   17   0          0             0              0
    ## 18   18   0          0             1              1
    ## 19   19   0          0             0              1
    ## 20   20   1          0             1              0
    ## 21   21   0          1             1              0
    ## 22   22   1          1             1              0
    ## 23   23   1          1             0              0
    ## 24   24   1          1             1              1
    ## 25   25   1          1             0              1
    ## 26   26   0          0             0              0
    ## 27   27   0          0             0              0
    ## 28   28   1          0             0              1
    ## 29   29   0          0             1              1
    ## 30   30   1          0             0              1
    ## 31   31   1          1             1              1
    ## 32   32   1          1             1              1
    ## 33   33   1          1             1              0
    ## 34   34   0          1             1              1
    ## 35   35   0          1             1              1
    ## 36   36   0          0             1              0
    ## 37   37   0          0             1              1
    ## 38   38   1          0             0              0
    ## 39   39   0          0             0              1
    ## 40   40   0          0             0              1
    ## 41   41   0          1             1              1
    ## 42   42   0          1             1              1
    ## 43   43   0          1             1              1
    ## 44   44   0          1             0              1
    ## 45   45   0          1             0              0
    ## 46   46   0          0             0              0
    ## 47   47   0          0             1              1
    ## 48   48   0          0             0              1
    ## 49   49   0          0             0              0
    ## 50   50   0          0             0              0
    ## 51   51   0          1             1              1
    ## 52   52   1          1             1              1
    ## 53   53   0          1             0              1
    ## 54   54   0          1             1              1
    ## 55   55   1          1             1              1
    ## 56   56   1          0             0              0
    ## 57   57   1          0             1              0
    ## 58   58   0          0             0              0
    ## 59   59   1          0             0              0
    ## 60   60   0          0             1              1
    ## 61   61   0          1             1              0
    ## 62   62   1          1             1              0
    ## 63   63   1          1             1              0
    ## 64   64   0          1             0              0
    ## 65   65   1          1             1              1
    ## 66   66   1          0             1              1
    ## 67   67   1          0             0              1
    ## 68   68   1          0             0              1
    ## 69   69   0          0             0              0
    ## 70   70   0          0             0              1
    ## 71   71   0          1             1              0
    ## 72   72   1          1             1              1
    ## 73   73   0          1             1              1
    ## 74   74   1          1             1              0
    ## 75   75   1          0             0              1
    ## 76   76   0          0             0              0
    ## 77   77   1          0             0              0
    ## 78   78   0          0             0              0
    ## 79   79   1          1             1              1
    ## 80   80   0          1             1              0
    ## 81   81   0          1             1              1
    ## 82   82   1          0             0              0
    ## 83   83   1          0             0              0
    ## 84   84   1          0             0              1
    ## 85   85   0          1             1              1
    ## 86   86   1          1             1              0
    ## 87   87   0          1             0              1
    ## 88   88   0          1             0              0
    ## 89   89   1          1             0              1
    ## 90   90   0          0             1              1
    ## 91   91   0          0             0              0
    ## 92   92   0          0             1              1
    ## 93   93   0          0             0              1
    ## 94   94   1          0             1              0
    ## 95   95   0          1             1              0
    ## 96   96   1          1             1              0
    ## 97   97   1          1             0              0
    ## 98   98   1          1             1              1
    ## 99   99   1          1             0              1
    ## 100 100   0          0             0              0
    ## 101 101   0          0             0              0
    ## 102 102   1          0             0              1
    ## 103 103   0          0             1              1
    ## 104 104   1          0             0              1
    ## 105 105   1          1             1              1
    ## 106 106   1          1             1              1
    ## 107 107   1          1             1              0
    ## 108 108   0          1             1              1
    ## 109 109   0          1             1              1
    ## 110 110   0          0             1              0
    ## 111 111   0          0             1              1
    ## 112 112   1          0             0              0
    ## 113 113   0          0             0              1
    ## 114 114   0          0             0              1
    ## 115 115   1          1             1              1
    ## 116 116   1          1             1              1
    ## 117 117   0          1             1              1
    ## 118 118   1          1             1              0
    ## 119 119   1          1             0              0
    ## 120 120   1          0             0              1
    ## 121 121   0          0             0              0
    ## 122 122   0          0             0              0
    ## 123 123   1          0             1              1
    ## 124 124   0          0             0              0
    ## 125 125   0          1             1              1
    ## 126 126   0          1             1              1
    ## 127 127   0          1             1              1
    ## 128 128   0          1             0              1
    ## 129 129   0          1             0              0
    ## 130 130   0          0             0              0
    ## 131 131   0          0             1              1
    ## 132 132   0          0             0              1
    ## 133 133   0          0             0              0
    ## 134 134   0          0             0              0
    ## 135 135   1          1             1              1
    ## 136 136   1          1             0              1
    ## 137 137   1          1             0              1
    ## 138 138   0          0             0              1
    ## 139 139   1          0             0              0
    ## 140 140   0          0             1              0
    ## 141 141   1          0             1              1
    ## 142 142   1          1             1              0
    ## 143 143   1          1             0              1
    ## 144 144   1          1             1              1
    ## 145 145   1          1             0              0
    ## 146 146   0          1             1              1
    ## 147 147   0          0             0              1
    ## 148 148   1          0             0              0
    ## 149 149   1          0             1              0
    ## 150 150   0          0             0              0
    ## 151 151   0          0             0              0

``` r
#All values that are measured need to correspond to the subject.  The data is grouped by the subject identification to ensure that all values for one individual are analysed as such.

B1 <- group_by(B, id)
B1
```

    ## Source: local data frame [151 x 5]
    ## Groups: id [151]
    ## 
    ##       id   sex handedness first_stumble final_position
    ##    (int) (int)      (int)         (int)          (int)
    ## 1      1     1          1             1              1
    ## 2      2     1          1             1              1
    ## 3      3     0          1             1              1
    ## 4      4     1          1             1              0
    ## 5      5     1          1             0              0
    ## 6      6     1          0             0              1
    ## 7      7     0          0             0              0
    ## 8      8     0          0             0              0
    ## 9      9     1          0             1              1
    ## 10    10     0          0             0              0
    ## ..   ...   ...        ...           ...            ...

``` r
#We are not concerned with gender in this instance, as such, we exclude sex from the analysis.

B2 <- B1[,-2]
B2
```

    ## Source: local data frame [151 x 4]
    ## Groups: id [151]
    ## 
    ##       id handedness first_stumble final_position
    ##    (int)      (int)         (int)          (int)
    ## 1      1          1             1              1
    ## 2      2          1             1              1
    ## 3      3          1             1              1
    ## 4      4          1             1              0
    ## 5      5          1             0              0
    ## 6      6          0             0              1
    ## 7      7          0             0              0
    ## 8      8          0             0              0
    ## 9      9          0             1              1
    ## 10    10          0             0              0
    ## ..   ...        ...           ...            ...

``` r
#Tabulate data in order to run tests

B3 <- xtabs(handedness~first_stumble + final_position, data = B2)
B3
```

    ##              final_position
    ## first_stumble  0  1
    ##             0 10 12
    ##             1 17 36

``` r
plot(B3, 
     main="Handedness and Line Position and First Stumble", 
     xlab = "First Stumble",
     ylab = "Final Postion", 
     col = c("Orange", "Red"))
```

<img src="./figures/question 2-1.png" style="display: block; margin: auto;" />

``` r
#Table is a 2X2 table and the Fisher's test gives the exact p-value.

fisher.test(B3)
```

    ## 
    ##  Fisher's Exact Test for Count Data
    ## 
    ## data:  B3
    ## p-value = 0.3002
    ## alternative hypothesis: true odds ratio is not equal to 1
    ## 95 percent confidence interval:
    ##  0.5575872 5.4756693
    ## sample estimates:
    ## odds ratio 
    ##   1.750917

Results indicate that there is no link between handedness and markers of ataxic walking in intoxicated subjects (p=0.3002, CI(0.5576, 5.4757)).

Question 3 - Amateur Runner
===========================

The data is numerical interval data.

The hypotheses are:

Ho: The runner cannot predict her running time over her standard distance. H1: The runner can presict her running time over a standard distance.

A test for correlation and linear regression will be used to evaluate whether or not there is good predictive value in the measurements that she currently has.

The assumptions underlying the linear regression test are:

1.  A trend exists between running time and calories consumed.
2.  Observations are independent of one another.
3.  Measurements of the independent variable have been made correctly.
4.  Residuals are normally distributed and are homoskedastic (same variance).

Assumptions underlying Pearson's correlation analyses (as used here) are:

1.  Data should be interval or ratio data.
2.  Data should have a linear relationship.
3.  Data should not have any outliers or pivot points.
4.  Variables should both be approximately normally distributed.

``` r
#Tell R to read the excel spread sheet

C <- read.csv('C:/Users/Carey Hedges/Desktop/Stats - Exam/question3.csv')
C
```

    ##    run time calories
    ## 1    1 2169      319
    ## 2    2 1986      384
    ## 3    3 1979      398
    ## 4    4 1937      359
    ## 5    5 2093      366
    ## 6    6 1924      388
    ## 7    7 1949      411
    ## 8    8 1879      423
    ## 9    9 2106      373
    ## 10  10 2019      418
    ## 11  11 1957      446
    ## 12  12 1926      400
    ## 13  13 2134      347
    ## 14  14 2174      334
    ## 15  15 2088      378
    ## 16  16 1903      368
    ## 17  17 2146      320
    ## 18  18 2059      326
    ## 19  19 2057      302

``` r
#Get an holistic overview of the data

summary(C)
```

    ##       run            time         calories    
    ##  Min.   : 1.0   Min.   :1879   Min.   :302.0  
    ##  1st Qu.: 5.5   1st Qu.:1943   1st Qu.:340.5  
    ##  Median :10.0   Median :2019   Median :373.0  
    ##  Mean   :10.0   Mean   :2026   Mean   :371.6  
    ##  3rd Qu.:14.5   3rd Qu.:2100   3rd Qu.:399.0  
    ##  Max.   :19.0   Max.   :2174   Max.   :446.0

``` r
head(C)
```

    ##   run time calories
    ## 1   1 2169      319
    ## 2   2 1986      384
    ## 3   3 1979      398
    ## 4   4 1937      359
    ## 5   5 2093      366
    ## 6   6 1924      388

``` r
tail(C)
```

    ##    run time calories
    ## 14  14 2174      334
    ## 15  15 2088      378
    ## 16  16 1903      368
    ## 17  17 2146      320
    ## 18  18 2059      326
    ## 19  19 2057      302

``` r
plot(C$time, C$calories, 
     main = "Calories Consumed versus Time Run", 
     ylab = "Calories Consumed (cal)",
     xlab = "Time (s)")
```

<img src="./figures/question 3-1.png" style="display: block; margin: auto;" />

``` r
#Visual analysis suggests a possible linear regression model exists

#Remove the run column

C1 <- C[,-1]
C1
```

    ##    time calories
    ## 1  2169      319
    ## 2  1986      384
    ## 3  1979      398
    ## 4  1937      359
    ## 5  2093      366
    ## 6  1924      388
    ## 7  1949      411
    ## 8  1879      423
    ## 9  2106      373
    ## 10 2019      418
    ## 11 1957      446
    ## 12 1926      400
    ## 13 2134      347
    ## 14 2174      334
    ## 15 2088      378
    ## 16 1903      368
    ## 17 2146      320
    ## 18 2059      326
    ## 19 2057      302

``` r
#Evaulate if there is a linear model that exists.

LMC <- lm(C1)
summary(LMC)
```

    ## 
    ## Call:
    ## lm(formula = C1)
    ## 
    ## Residuals:
    ##      Min       1Q   Median       3Q      Max 
    ## -128.343  -58.148   -3.588   63.468   87.402 
    ## 
    ## Coefficients:
    ##              Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept) 2629.4011   160.9786  16.334 7.95e-12 ***
    ## calories      -1.6252     0.4309  -3.772  0.00152 ** 
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 72.65 on 17 degrees of freedom
    ## Multiple R-squared:  0.4556, Adjusted R-squared:  0.4235 
    ## F-statistic: 14.22 on 1 and 17 DF,  p-value: 0.001522

``` r
#A linear regression is present, perhaps a correlation exists.  I have used a Pearson's test as there are no outliers or influence points identified in the data set

cor.test(C$time, C$calories, method = "pearson")
```

    ## 
    ##  Pearson's product-moment correlation
    ## 
    ## data:  C$time and C$calories
    ## t = -3.7715, df = 17, p-value = 0.001522
    ## alternative hypothesis: true correlation is not equal to 0
    ## 95 percent confidence interval:
    ##  -0.8642170 -0.3183295
    ## sample estimates:
    ##        cor 
    ## -0.6749491

``` r
#Check that the underlying assumptions of the tests have not been violated

#Residuals Check

qqnorm(LMC$residuals)
qqline(LMC$residuals)
```

<img src="./figures/question 3-2.png" style="display: block; margin: auto;" />

``` r
#Hetereoskedacity check

plot(x = LMC$fitted, y = LMC$residuals,
     main = "Standard Deviation Across Measures",
     xlab = 'Fitted Values', 
     ylab = 'Residual Values')
abline(h=0, col = "gray")
```

<img src="./figures/question 3-3.png" style="display: block; margin: auto;" />

Data indicates that the runner can predict the number of calories that she burns if she looks at her running time. Running time and calories burned are inversely correlated (r=-0.6749, p=0.001522) and have a fairly strong negative association. A linear model of the data is given by b|,-1.6252 t(17)=-3.772, p=0.001522 and R<sup>2</sup>= 0.4556, F(1,17)=14.22, p=0.001522.

This indicates that the runner could predict her calories that she burns when the time she runs falls between 1879 and 2174 seconds.

Extrapolation of data in this model is bad methodology. If the runner were to predict her calories consumed in 30 minutes this would correlate to 1800 seconds that lies outside this model and reduces that models ability to accurately predict her calorie loss over that time. However, crudely, extrapolation would indicate that caloric consumption is going to be close to or greater than 466cal and is extrapolated by this model to be 510.3379 calories ((-1.6252\*y)+2629.4011=1800).

Question 4 - Publishable Graphs
===============================

``` r
#Copy pasted data from word document.

foo <- rnorm(10000, mean = 60, sd = 3) # final mark
bar <- rnorm(10000, mean = 68, sd = 5) # project mark
baz <- rep(seq(from = 1997, to = 2006), each = 1) # years

year <- sample(baz, 150, replace = TRUE,
               prob = c(0.05, 0.05, 0.08, 0.08, 
                          0.1, 0.13, 0.14, 0.13, 0.12, 0.12))
project_mark <- sample(bar, 150, replace = TRUE)
final_mark <- sample(foo, 150, replace = TRUE)

plot_data <- data_frame(year = year,
                        project_mark = round(project_mark, 1),
                        final_mark = round(final_mark, 1)) %>%arrange(year)

#Visualise the data briefly.  As we are only assessing the 

summary(foo)
```

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ##   46.93   57.98   60.02   60.01   62.03   71.51

``` r
summary(bar)
```

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ##   49.33   64.59   68.05   67.99   71.40   88.38

``` r
#Plotted data adding a title, x and y axis labels and different limits for more space on the graph.

plot(bar, foo,
     main = "Relationship between Final Marks and Project Marks",
     xlab = "Project Mark (%)",
    ylab = "Final Mark (%)", 
    ylim = (c(45, 80)), 
    xlim = (c(45, 90)))
```

<img src="./figures/r question 4-1.pdf" style="display: block; margin: auto;" />

``` r
#r and p values should always be quoted on the graph.  I have run a correlation test to obtain an r value to place on the graph.

cor.test(bar, foo, method = "pearson")
```

    ## 
    ##  Pearson's product-moment correlation
    ## 
    ## data:  bar and foo
    ## t = 0.21504, df = 9998, p-value = 0.8297
    ## alternative hypothesis: true correlation is not equal to 0
    ## 95 percent confidence interval:
    ##  -0.01745024  0.02174972
    ## sample estimates:
    ##         cor 
    ## 0.002150569

There is a large density of points ontop of one another. Extending the axes on to include zero and 100 make it very difficult to see what is happening in the figure. Thus, I have shifted the default settings to incorperate a small amount of space around the points plotted on the axes.
