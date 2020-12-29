[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

Exercise 5.1 In the BRFSS (see Section 5.4), the distribution of heights is roughly normal with parameters µ = 178 cm and σ = 7.7 cm for men, and µ = 163 cm and σ = 7.3 cm for women. In order to join Blue Man Group, you have to be male between 5’10” and 6’1” (see http://bluemancasting.com). What percentage of the U.S. male population is in this range? Hint: use scipy.stats.norm.cdf.

First scipy.stats needs to be imported so that scipy.stats.norm can be used as a representations of a normal distribution. I ignored the normal parameters for women since only men can be members of the blue men group and used the provided male parameters to create variables mu and sigma to define loc and scale of my normal distribution. I made a note of my parameters being in centimeters to make sure future data was using the same type of measurement.

---

    import scipy.stats
    mu=178
    sigma=7.7
    ## mu and sigma are in cm
    dist= scipy.stats.norm(loc=mu,scale=sigma)
    type(dist)
    
---

Type(dist) shows that dist is a frozen random variable meaning it can compute its mean and standard deviation, which should and did equal mu and sigma respectively. It can also evalute the CDF of dist, which can be used to determine how many people are are more than a single standard deviation below the mean, in this case about 16%.

---

    dist.mean()
    dist.std()
    dist.cdf(mu-sigma)
    
---

I was then asked to determine how mny people are between 5'10" and 6'1", this is where my earlier note of mu and sigma being in cm came in handy indicating I need to convert these feet and inches height values into centimeters. 5'10" became 177.8 cm and 6'1" became 185.4 cm. I created variable low which showed the portion of the population that was 177.8 cm tall or shorter which was approximating 48.96%, and variable high which showed the portion of the population that was 185.4 cm tall or shorter which was approximately 83.17%. I then subtracted low from high to determine the portion of the population that was between the heights of 177.8 cm and 185.4 cm which was approximately 34.21%.

---

    low=dist.cdf(177.8)
    high=dist.cdf(185.4)
    low, high, high-low
    
---