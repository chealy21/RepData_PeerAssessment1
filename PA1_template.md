---
title: "Reproducible Research: Peer Assessment 1"
output: 
  html_document:
    keep_md: yes
---
## Loading necessary libraries

```r
suppressPackageStartupMessages(library(dplyr))
suppressPackageStartupMessages(library(lattice))
```

## Display figure information

```r
knitr::opts_chunk$set(fig.width=12, fig.height=8, fig.path='Figs/',
                      echo=FALSE, warning=FALSE, message=FALSE)
```

## Loading and preprocessing the data

```r
unzip("activity.zip")
dat<-read.csv("activity.csv",header=TRUE)



totalsteps<- dat %>% group_by(date) %>% summarize(steps=sum(steps, na.rm=TRUE))

hist(totalsteps$steps, main="Histogram of Total Steps per Day", xlab="Total Steps")
```

![](Figs/unnamed-chunk-3-1.png)<!-- -->



## What is mean total number of steps taken per day?


The mean total steps per day is 9354.2295082, and the mediean total steps per day is 10395.

## What is the average daily activity pattern?
![](Figs/unnamed-chunk-5-1.png)<!-- -->

The maximum average steps of 206.1698113 occur during interval 835.


## Imputing missing values

The total number of observations missing steps is 2304.

The mean steps for that interval was used to fill in the missing values. To do this, I joined the mean steps per interval to the main data frame, and substituting the mean steps per interval into the missing value using a subset function. 
![](Figs/unnamed-chunk-7-1.png)<!-- -->
The mean total number of steps is 1.0766189\times 10^{4} and the median total number of steps is 1.0766189\times 10^{4}. The difference between the mean steps is 1411.959171. The difference between the median steps is 371.1886792.


## Are there differences in activity patterns between weekdays and weekends?
![](Figs/unnamed-chunk-8-1.png)<!-- -->
