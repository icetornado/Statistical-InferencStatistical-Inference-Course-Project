# Statistical Inference Course Project - Part 2
Trieu Tran  
September 21, 2015  

## Synopsis
This is the second part of the course project for the statistical inference class. The goal of this project is conducting some basic inferential data analysis on the "ToothGrowth"" data of R datasets package. The following is step-by-step execution and conlusion drawing from the analysis.

## Loading data

```r
library(datasets)
library(ggplot2)
data("ToothGrowth")

## checking existence of a folder named "figure", if not then creating one to store plot figures
figureDir <- 'figure'
if (!file.exists(figureDir)){
    dir.create(figureDir)
} 

str(ToothGrowth)
```
## Summary about data
"ToothGrowth" data is a set of 60 observations of 3 variables which are: 

- len - length of odontoblasts cell in each of 10 guinea pigs 

- supp - factor with two levels (OC, VC) to indicate delivery method of vitamin C supplement (Orange Juice - OC or ascorbic acid - VC)

- dose - dose of vitamin C supplements at three levels (0.5, 1 and 2 mg/day)

Read more about the dataset: [https://stat.ethz.ch/R-manual/R-devel/library/datasets/html/ToothGrowth.html](https://stat.ethz.ch/R-manual/R-devel/library/datasets/html/ToothGrowth.html)


```r
## plotting boxplots
p <- ggplot(ToothGrowth, aes(x = supp, y = len))
p <- p + geom_boxplot(aes(fill = supp)) 
p <- p + labs(x = "Supplement", y = "Odontoblasts Cell Length")
p <- p + scale_fill_discrete(name="Delivery Methods",
                         breaks=c("OJ", "VC"),
                         labels=c("Orange Juice", "Vitamin C"))
## save plot to a file
ggsave(file.path(figureDir, "plot2-1.png"), width=6.4, height=4.8, dpi=124)
```
![](figure/plot2-1.png)

## Confident interval and hypothesis tests 
