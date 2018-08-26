# Convex Regression Model

_Captured: 2018-07-14 at 14:25 from [dzone.com](https://dzone.com/articles/convex-regression-model?edition=385238&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=big%20data%202018-07-14)_

[Hortonworks Sandbox](https://dzone.com/go?i=285437&u=https%3A%2F%2Fhortonworks.com%2Fproducts%2Fsandbox%2F%3Futm_campaign%3Ddzonepre%2Fpostroll%26utm_medium%3Ddisplay%26apos%3B%26utm_source%3Ddzone%26utm_id%3D2216633) for HDP and HDF is your chance to get started on learning, developing, testing and trying out new features. Each [download](https://dzone.com/go?i=285437&u=https%3A%2F%2Fhortonworks.com%2Fproducts%2Fsandbox%2F%3Futm_campaign%3Ddzonepre%2Fpostroll%26utm_medium%3Ddisplay%26apos%3B%26utm_source%3Ddzone%26utm_id%3D2216633) comes preconfigured with interactive tutorials, sample data and developments from the Apache community.

This morning during the lecture on nonlinear regression, I mentioned (very) briefly the case of convex regression. Since I forgot to mention the codes in R, I will publish them here. Assume that yi=m(xi)+εi where m:Rd->R is some convex function.

Then m is convex if and only if ∀x1,x2∈Rd, ∀t∈[0,1],

[Hidreth (1954)](https://www.jstor.org/stable/2281132?seq=1#page_scan_tab_contents) proved that if

![Image title](https://dzone.com/storage/temp/9690953-screen-shot-2018-07-06-at-13840-pm.png)

then θ⋆=(m⋆(x1),⋯,m⋆(xn)) is unique.

Let y=θ+ε, then

where

I.e. θ⋆ is the projection of \mathbf{y}y onto the (closed) convex cone \mathcal{K}K. The projection theorem gives existence and unicity.

For convenience, in the application, we will consider the real-valued case, m:R->R, i.e. yi=m(xi)+εi. Assume that observations are ordered x1≤x2≤⋯≤xn. Here

![Image title](https://dzone.com/storage/temp/9690957-screen-shot-2018-07-06-at-13947-pm.png)

Hence, quadratic program with n−2 linear constraints.

m⋆ is a piecewise linear function (interpolation of consecutive pairs (xi,θi⋆)).

If m is differentiable, m is convex if

More generally, if m is convex, then there exists ξx∈Rn such that

ξx is a subgradient of m at x. And then

![Image title](https://dzone.com/storage/temp/9690964-screen-shot-2018-07-06-at-14057-pm.png)

Hence, θ⋆ is solution of

![Image title](https://dzone.com/storage/temp/9690966-screen-shot-2018-07-06-at-14124-pm.png)

and ξ1,⋯,ξn∈Rn. Now, to do it for real, use [cobs](https://cran.r-project.org/web/packages/cobs/index.html) package for constrained (b)splines regression,

To get a convex regression, use

![](https://f-origin.hypotheses.org/wp-content/blogs.dir/253/files/2018/07/convex1.png)

> _Here we can get the values of the knots_
    
    
    Call:  conreg(x = x, y = y, convex = TRUE) 
    
    
    Convex regression: From 19 separated x-values, using 5 inner knots,

and actually, if we use them in a linear-spline regression, we get the same output here
    
    
    reg = lm(dist~bs(speed,degree=1,knots=c(4,7,8,9,,20,23,25)),data=cars)
    
    
    v = predict(reg,newdata=data.frame(speed=u))
    
    
    lines(u,v,col="green")

Let us add vertical lines for the knots

![](https://f-origin.hypotheses.org/wp-content/blogs.dir/253/files/2018/07/convex2.png)

[Hortonworks Community Connection (HCC)](https://dzone.com/go?i=293443&u=https%3A%2F%2Fcommunity.hortonworks.com%2Findex.html%3Futm_campaign%3Ddzonepre%2Fpostrollv2%26utm_medium%3D3rd-party-resource%26utm_source%3Ddzone%26utm_id%3D2307295) is an online collaboration destination for developers, DevOps, customers and partners to get answers to questions, collaborate on technical articles and share code examples from GitHub. [Join the discussion.](https://dzone.com/go?i=293443&u=https%3A%2F%2Fcommunity.hortonworks.com%2Findex.html%3Futm_campaign%3Ddzonepre%2Fpostrollv2%26utm_medium%3D3rd-party-resource%26utm_source%3Ddzone%26utm_id%3D2307295)
