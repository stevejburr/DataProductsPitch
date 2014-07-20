---
title       : Developing Data Products
subtitle    : Course Project - Reproducible Pitch Presentation
author      : Steve Burr
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     :       #{tomorrow} 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : standalone # {standalone, draft}
knit        : slidify::knit2slides
--- 

## Introduction

- Ever been stuck about what movie to watch tonight?  

- Know what type of film you want but not which title?  

- Got a limitted amount of time and need to find something to fit?    


   
### This app is for you!

--- 

## What does it do?

- Uses film ratings from IMBD (found in the R package ggplot2)  

- User can filter films by:
    1. Genre
    2. Min/Max Length
    3. Min/Max Rating
    4. The number of required ratings  
    
- A graphical representation of the top 10 films meeting the requirements is plotted

---

## More detail

- The plot uses rCharts / Highcharts - it's possible to mouse over to find out which title the point represents  

- Points are sized based on the number of ratings and positioned in space based on average rating and estimated number of people who rated it 10/10  



---
## Example calculation of number of 10/10s estimate

- The column r10 gives the percentile of people who gave a 10  

- By multiplying this by the total number of votes, we can calculate the number of 10s  

- This can identify if films score a lot of 10s as well as a lot of lower scores to end up at their average



```r
require(ggplot2)
```

```
## Loading required package: ggplot2
```

```r
DT <- subset(movies, title == "Matrix, The")
DT$Estimated10s<-(DT$r10/100)*(DT$votes)
DT$Estimated10s
```

```
## [1] 49629
```


