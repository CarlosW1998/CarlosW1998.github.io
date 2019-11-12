---
layout: default
---

# High School and Beyond analysis

First things first, for this analysis i chose the  hsb2 dataset, in this survey we have two hundred observations were randomly sampled from the High School and Beyond survey, a survey conducted on high school seniors by the National Center of Education Statistics.

And then, import the librarys for the analysis


```R
library(dplyr)
library(ggplot2)
library(tidyr)
```

After, import the dataset where they are stored


```R
hsb2 = read.csv("hsb2.csv")
```

So, i run the comands over the data


```R
str(hsb2)

glimpse(hsb2)
```

    'data.frame':	200 obs. of  11 variables:
     $ id     : int  70 121 86 141 172 113 50 11 84 48 ...
     $ gender : Factor w/ 2 levels "female","male": 2 1 2 2 2 2 2 2 2 2 ...
     $ race   : Factor w/ 4 levels "african american",..: 4 4 4 4 4 4 1 3 4 1 ...
     $ ses    : Factor w/ 3 levels "high","low","middle": 2 3 1 1 3 3 3 3 3 3 ...
     $ schtyp : Factor w/ 2 levels "private","public": 2 2 2 2 2 2 2 2 2 2 ...
     $ prog   : Factor w/ 3 levels "academic","general",..: 2 3 2 3 1 1 2 1 2 1 ...
     $ read   : int  57 68 44 63 47 44 50 34 63 57 ...
     $ write  : int  52 59 33 44 52 52 59 46 57 55 ...
     $ math   : int  41 53 54 47 57 51 42 45 54 52 ...
     $ science: int  47 63 58 53 53 63 53 39 58 50 ...
     $ socst  : int  57 61 31 56 61 61 61 36 51 51 ...
    Observations: 200
    Variables: 11
    $ id      [3m[90m<int>[39m[23m 70, 121, 86, 141, 172, 113, 50, 11, 84, 48, 75, 60, 95, 104, …
    $ gender  [3m[90m<fct>[39m[23m male, female, male, male, male, male, male, male, male, male,…
    $ race    [3m[90m<fct>[39m[23m white, white, white, white, white, white, african american, h…
    $ ses     [3m[90m<fct>[39m[23m low, middle, high, high, middle, middle, middle, middle, midd…
    $ schtyp  [3m[90m<fct>[39m[23m public, public, public, public, public, public, public, publi…
    $ prog    [3m[90m<fct>[39m[23m general, vocational, general, vocational, academic, academic,…
    $ read    [3m[90m<int>[39m[23m 57, 68, 44, 63, 47, 44, 50, 34, 63, 57, 60, 57, 73, 54, 45, 4…
    $ write   [3m[90m<int>[39m[23m 52, 59, 33, 44, 52, 52, 59, 46, 57, 55, 46, 65, 60, 63, 57, 4…
    $ math    [3m[90m<int>[39m[23m 41, 53, 54, 47, 57, 51, 42, 45, 54, 52, 51, 51, 71, 57, 50, 4…
    $ science [3m[90m<int>[39m[23m 47, 63, 58, 53, 53, 63, 53, 39, 58, 50, 53, 63, 61, 55, 31, 5…
    $ socst   [3m[90m<int>[39m[23m 57, 61, 31, 56, 61, 61, 61, 36, 51, 51, 61, 61, 71, 46, 56, 5…


This commands return a dataset summary, will output the information on one line for each basic structure, blimpse "It's a little like str applied to a data frame but it tries to show you as much data as possible".

This two funcitions tell us informations abaout the data like the number of samples in the data set, the number of  variables, the type of variables, and the begin of dataset.

We  have 200 examples in this sample, and 11 variables and two types of variables are observed int and factor.

We also can filter the variables on the dataset, with the below command.


```R
hsb2_public <- filter(hsb2, schtyp == "public")

hsb2_private <- hsb2 %>% filter(schtyp == "private")

table(hsb2_public$schtyp)

table(hsb2_private$schtyp)

```


    
    private  public 
          0     168 



    
    private  public 
         32       0 


The pipe operator use a simple idea, the result of the  expression in the left side is used like the first argument of the function in the right side.

Table function in R, performs categorical tabulation of data with the variable and its frequency.

So in the schtup variable we observe 168 times the variable is public and 32 times the variable is private.
