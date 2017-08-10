# Reproducible Research: Peer Assessment 1




## Loading and preprocessing the data

First load graphics libraries, 


```r
# load graphics library
library(ggplot2)
```

Unzip data  and read it in data.frame


```r
# Unzip archive
unzip("activity.zip")

# Read base data into a data frame.
baseData <- read.csv("activity.csv")
```

Check the structure of baseData.


```r
str(baseData)
```

```
## 'data.frame':	17568 obs. of  3 variables:
##  $ steps   : int  NA NA NA NA NA NA NA NA NA NA ...
##  $ date    : Factor w/ 61 levels "2012-10-01","2012-10-02",..: 1 1 1 1 1 1 1 1 1 1 ...
##  $ interval: int  0 5 10 15 20 25 30 35 40 45 ...
```


## What is mean total number of steps taken per day?

To calculate mean of total number of steps taken per day, first aggregate steps based on dates .


```r
# Aggregate the number of steps (excluding number of steps)

totalSteps <- tapply(X = baseData$steps,INDEX = baseData$date,FUN = sum , na.rm =TRUE )
```

Next step draw the histograph.



```r
qplot(x = totalSteps , binwidth=1000 , xlab="total number of steps", main ="total number of steps taken each day" )
```

![](PA1_template_files/figure-html/hist_steps-1.png)<!-- -->

Calculate and report the mean and median of the total number of steps taken per day.


```r
stepsByDayMean <- mean(totalSteps )
stepsByDayMedian <- median(totalSteps )
```

The *mean* is 9354.2295082 and *median* is 10395

## What is the average daily activity pattern?



## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
