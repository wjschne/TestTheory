

Normal and related distributions
========================================================
author: W. Joel Schneider
date: Psychology 442
transition: none
incremental:true
css: slides.css



The Central Limit Theorem
========================================================

The term *iid* means "independent and identically distributed."

* *Independent* means that the value of one variable has no conditional effect on the probability distribution of the other variable. As a consequence, the variables are uncorrelated.
* *Identically distributed* means that the variables have the same distribution.


$$S_n = \sum\limits_{i=1}^n {X_i}, \text{all}\, X_i \,\text{are}\, iid \, \text{and have means and variances.}$$

$$\lim_{n\to\infty} {S_n \sim N\left(n\mu_X,n\sigma_X^2\right)}$$

$$\lim_{n\to\infty} {\dfrac{S_n}{n} \sim N\left(\mu_X,\dfrac{\sigma_X^2}{n}\right)}$$



Chi-Square
=======================
title: false
incremental: false


### $\huge \chi^2$

![$\chi^2$ Added Together](Normal2Chi.gif)





Chi-Square
=======================
title: none
incremental: false

### $\huge \chi^2$

![$\chi^2$ Added Together](ChiSquareAdding.gif)




Chi-Square
=======================
title: none
incremental: false

### $\huge \chi^2$

Run this code in RStudio and manipulate the degrees of freedom with the slider.


```r
library(manipulate)
manipulate({
  x<-seq(round(qchisq(0.00001,df),2),
         round(qchisq(0.99999,df),2),0.1)
  y <- dchisq(x,df)
  x  <- x[is.finite(y)]
  y  <- y[is.finite(y)]
  par(mar=c(3,1,3,1),bty="n")
  plot(y~x,type="n",ylab="",xlab="",yaxt="n",
       main=bquote({chi^2} (italic(nu)== .(df))))
  polygon(c(min(x),x,max(x)),c(0,y,0),
          border="royalblue2",col="royalblue2")
  mtext(bquote(italic(atop(atop(mu == {nu == .(df)},
      {sigma^2=={2*nu==.(2*df)}}),
      atop(gamma[1]=={sqrt(8/nu)==.(round(sqrt(8/df),3))},
           gamma[2]=={12/nu==.(round(12/df,3))}))))
      ,4,las=1,adj = 1,cex=2)
  }, df=slider(1,1000,1,"\u03BD"))
```

Student's t Distribution
===========================
incremental: false

$$m=\dfrac{x_1+x_2+\dots+x_n}{n} \sim N\left(\mu,\dfrac{\sigma^2}{n}\right)$$

[$$s^2=\dfrac{\sum\limits_{i=1}^n {(x_i-m})^2}{n-1} \sim \sigma^2\dfrac{\chi^2(n-1)}{n-1} $$](https://onlinecourses.science.psu.edu/stat414/node/174)

$$t=\dfrac{m-\mu}{\sqrt{\dfrac{s^2}{n}}}=\dfrac{m-\mu}{\sqrt{\dfrac{\sigma^2\dfrac{\chi^2(n-1)}{n-1}}{n}}}=\dfrac{m-\mu}{\sqrt{\dfrac{\sigma^2}{n}\dfrac{\chi^2(n-1)}{n-1}}}=\dfrac{\dfrac{m-\mu}{\sqrt{\dfrac{\sigma^2}{n}}}}{\sqrt{\dfrac{\chi^2(n-1)}{n-1}}}=\dfrac{z}{\sqrt{\dfrac{\chi^2(df)}{df}}}$$

Student's t Distribution
===========================
title: false
incremental: false


```r
replicate(reps, mean(rnorm(n, mu, sigma)))
```

![plot of chunk DSM](Normal, chi, t, and F-figure/DSM-1.svg) 


F Distribution
=================

$${U_1\sim \chi^2(df_1)}, {U_2\sim \chi^2(df_2)}$$

$${F(df_1,df_2)=\dfrac{MS_b}{MS_w} = \frac{\frac{U_1}{df_1}}{\frac{U_1}{df_2}}}$$

![plot of chunk Fdist](Normal, chi, t, and F-figure/Fdist-1.svg) 

