# Loading-saving-and-describing-data-
ANA 515

---
title: "ANA 515 Assignment 2"
author: "Zhiying Chen"
date: "6/18/2022"
output:
  html_document: default
---

#This dataset consists of several variables that measures the fatalities caused by accident for different ailines: the name of the airline, Available seat kilometers flown very week, incidents, fatal incidents and fatalities. Incidents, fatal incidents and fatalities are broke into two time period, 85-99 and 00-14. The data was collected from the Bureau of Transportation Statistics. It is a csv file. If it is in a flat file, It is delimited and the delimiter is comma.


```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```

## R Markdown

``` {r, echo = FALSE}
#Note, Each gray box below is a code chunk. You need to insert a code chunk and put your R code in it. By setting echo = FALSE. this comment and any code will not show in my output document. If it were TRUE, the comment and code would appear. 
```

``` {r, echo = FALSE}
#install.packages("tidyverse") 
#install.packages("knitr")
#install.packages("readr")

library("tidyverse")
library("knitr")
library("readr")
``` 

```{r, echo = FALSE}
#The include = FALSE function hides both the code and output in my output document

#You need to install these packages first to be able to use the functions within them. You can install them from the Tools tab or write a new code chunk: install.packages("package_name").

url <- "https://raw.githubusercontent.com/fivethirtyeight/data/master/airline-safety/airline-safety.csv"
air_safety <- read.csv(url)

#I loaded readr to use the read_csv function which reads the csv file data.

```

```{r, echo = FALSE}

se_accident <- air_safety

names(se_accident)[names(se_accident) == "airline"] <- "airline_name"
names(se_accident)[names(se_accident) == "avail_seat_km_per_week"] <- "avail_seat"
names(se_accident)[names(se_accident) == "fatalities_85_99"] <- "num_fatalities_85_99"
names(se_accident)[names(se_accident) == "fatalities_00_14"] <- "num_fatalities_00_14"

colnames(se_accident)
```

This dataframe has `r nrow(se_accident)` rows and `r ncol(se_accident)` columns. The names of the columns and a brief description of each are in the table below

``` {r}
object <- c(colnames(se_accident))
description <- c("name of airline", "availablt seats/km/week","number of incidents in 85-99","number of fatal incidents in 85-99", "number of fatalities in 85-99", "number of incidents in 00-14","number of fatal incidents in 00-14", "number of fatalities in 00-14")
introduction <- data.frame(object, description)
introduction
knitr::kable(introduction,"pipe")
```


```{r}
accident0014 <- se_accident[c(6:8)]
sum_ac_00_14 <- summary(accident0014)
sum_ac_00_14
```
