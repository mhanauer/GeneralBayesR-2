# GeneralBayesR-2
---
title: "GeneralBayesR^2Explaination"
output: html_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```

We need to create variables for y and each x for the test run.  Then we need to create zbeta's for the test run as well.  Then we need to bring the correlation toegether in a matrix and multiply them by each of the beta's and then sum them.
```{r}
y = rnorm(10)
x = rnorm(10)
x2 = rnorm(10)
x3 = rnorm(10)
zbeta1 = -.0008
zbeta2 = -.071
zbeta3 = .035

YcorX1 = cor( y , x ) # correlation of y with each x predictor
YcorX2 = cor( y , x2 ) # correlation of y with each x predictor
YcorX3 = cor( y , x3 ) # correlation of y with each x predictor
YcorAll = c(YcorX1, YcorX2, YcorX3)

# So zbeta1 is the beta for one of them and want to times that by the correlation between the x value and the y-value.  For the multivariate version it must be 

RsqZbeta1 = zbeta1 %*% matrix(YcorAll, nrow=1)
RsqZbeta2 = zbeta2 %*% matrix( YcorAll, nrow=1)
RsqZbeta3 = zbeta3 %*% matrix( YcorAll, nrow=1)
RsqAllBetas = sum(RsqZbeta1, RsqZbeta2, RsqZbeta3); RsqAllBetas

```
Rsq = zbeta %*% matrix( YcorX , ncol=1 ) = There must be one zbeta for each variable, because it is rows times columns that makes the matrix multiplication work.  In my version each of the variables is seperate not in one therefore, I need to 
