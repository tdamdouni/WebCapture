# Quantile Regression (Home Made)

_Captured: 2018-07-19 at 19:07 from [dzone.com](https://dzone.com/articles/quantile-regression-home-made?edition=385254&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=big%20data%202018-07-19)_

[Hortonworks Sandbox](https://dzone.com/go?i=285437&u=https%3A%2F%2Fhortonworks.com%2Fproducts%2Fsandbox%2F%3Futm_campaign%3Ddzonepre%2Fpostroll%26utm_medium%3Ddisplay%26apos%3B%26utm_source%3Ddzone%26utm_id%3D2216633) for HDP and HDF is your chance to get started on learning, developing, testing and trying out new features. Each [download](https://dzone.com/go?i=285437&u=https%3A%2F%2Fhortonworks.com%2Fproducts%2Fsandbox%2F%3Futm_campaign%3Ddzonepre%2Fpostroll%26utm_medium%3Ddisplay%26apos%3B%26utm_source%3Ddzone%26utm_id%3D2216633) comes preconfigured with interactive tutorials, sample data and developments from the Apache community.

After my [series of posts](https://freakonometrics.hypotheses.org/category/r/from-scatch) on classification algorithms, it's time to get back to R, this time for quantile regression. Yes, I still want to get a better understanding of optimization routines in R. Before looking at the quantile regression, let us compute the median, or the quantile, from a sample.

## Median

Consider a sample {y1,⋯,yn}. To compute the median, solve:

![Image title](https://dzone.com/storage/temp/9747076-screen-shot-2018-07-13-at-41844-pm.png)

which can be solved using linear programming techniques. More precisely, this problem is equivalent to

ai,bi≥0 and yi−μ=ai−bi, ∀i=1,⋯,n.

To illustrate, consider a sample from a lognormal distribution,

For the optimization problem, use the matrix form, with 3n constraints, and 2n+1 parameters:
    
    
    A2 = cbind(diag(n), -diag(n), 1)
    
    
    r = lp("min", c(rep(1,2*n),0),
    
    
    rbind(A1, A2),c(rep(">=", 2*n), rep("=", n)), c(rep(0,2*n), y))

It looks like it's working well…

## Quantile

Of course, we can adapt our previous code for quantiles:

The linear program is now

![Image title](https://dzone.com/storage/temp/9747081-screen-shot-2018-07-13-at-42146-pm.png)

with ai,bi≥0 and yi−μ=ai−bi, ∀i=1,⋯,n. The R code is now:
    
    
    A1 = cbind(diag(2*n),0) 
    
    
    A2 = cbind(diag(n), -diag(n), 1)
    
    
    r = lp("min", c(rep(tau,n),rep(1-tau,n),0),
    
    
    rbind(A1, A2),c(rep(">=", 2*n), rep("=", n)), c(rep(0,2*n), y))

So far so good…

## Quantile Regression (Simple)

Consider the following dataset, with rents of flats in a major German city, as a function of the surface, the year of construction, etc.
    
    
    base=read.table("http://freakonometrics.free.fr/rent98_00.txt",header=TRUE)

The linear program for the quantile regression is now

![Image title](https://dzone.com/storage/temp/9747085-screen-shot-2018-07-13-at-42259-pm.png)

with ai,bi≥0 and

yi−[β0τ+β1τxi]=ai−bi

∀i=1,⋯,n. So use here
    
    
    A1 = cbind(diag(2*n), 0,0) 
    
    
    A2 = cbind(diag(n), -diag(n), X) 
    
    
           c(rep(tau,n), rep(1-tau,n),0,0), rbind(A1, A2),
    
    
           c(rep(">=", 2*n), rep("=", n)), c(rep(0,2*n), y)) 

Of course, we can use an R function to fit that model:
    
    
    rq(rent_euro~area, tau=tau, data=base)

Here again, it seems to work quite well. We can use a different probability level, of course, and get a plot.
    
    
    plot(base$area,base$rent_euro,xlab=expression(paste("surface (",m^2,")")),
    
    
         ylab="rent (euros/month)",col=rgb(0,0,1,.4),cex=.5)
    
    
    yr=r$solution[2*n+1]+r$solution[2*n+2]*sf
    
    
    lines(sf,yr,lwd=2,col="blue")
    
    
           c(rep(tau,n), rep(1-tau,n),0,0), rbind(A1, A2),
    
    
           c(rep(">=", 2*n), rep("=", n)), c(rep(0,2*n), y)) 
    
    
    yr=r$solution[2*n+1]+r$solution[2*n+2]*sf
    
    
    lines(sf,yr,lwd=2,col="blue")

![](https://freakonometrics.hypotheses.org/files/2018/06/Capture-d%E2%80%99e%CC%81cran-2018-06-14-a%CC%80-21.12.34.png)

## Quantile Regression (Multiple)

Now that we understand how to run the optimization program with one covariate, why not try with two? For instance, let us see if we can explain the rent of a flat as a (linear) function of the surface and the age of the building.
    
    
    X = cbind( 1, base$area, base$yearc )
    
    
    A1 = cbind(diag(2*n), 0,0,0) 
    
    
    A2 = cbind(diag(n), -diag(n), X) 
    
    
           c(rep(tau,n), rep(1-tau,n),0,0,0), rbind(A1, A2),
    
    
           c(rep(">=", 2*n), rep("=", n)), c(rep(0,2*n), y)) 

Unfortunately, this time, it is not working well…
    
    
    rq(rent_euro~area+yearc, tau=tau, data=base)

Results are quite different. And, actually, another technique can confirm the latter ([IRLS](https://en.wikipedia.org/wiki/Iteratively_reweighted_least_squares) - Iteratively Reweighted Least Squares)
    
    
    eps = residuals(lm(rent_euro~area+yearc, data=base))
    
    
      reg = lm(rent_euro~area+yearc, data=base, weights=(tau*(eps&gt;0)+(1-tau)*(eps&lt;0))/abs(eps))

I could not figure out what went wrong with the linear program. Not only are the coefficients very different, but so are the predictions:
    
    
    yr = r$solution[2*n+1]+r$solution[2*n+2]*base$area+r$solution[2*n+3]*base$yearc
    
    
    abline(a=0,b=1,lty=2,col="red")

![](https://freakonometrics.hypotheses.org/files/2018/06/Capture-d%E2%80%99e%CC%81cran-2018-06-14-a%CC%80-21.22.06.png)

It's now time to investigate….

[Hortonworks Community Connection (HCC)](https://dzone.com/go?i=293443&u=https%3A%2F%2Fcommunity.hortonworks.com%2Findex.html%3Futm_campaign%3Ddzonepre%2Fpostrollv2%26utm_medium%3D3rd-party-resource%26utm_source%3Ddzone%26utm_id%3D2307295) is an online collaboration destination for developers, DevOps, customers and partners to get answers to questions, collaborate on technical articles and share code examples from GitHub. [Join the discussion.](https://dzone.com/go?i=293443&u=https%3A%2F%2Fcommunity.hortonworks.com%2Findex.html%3Futm_campaign%3Ddzonepre%2Fpostrollv2%26utm_medium%3D3rd-party-resource%26utm_source%3Ddzone%26utm_id%3D2307295)
