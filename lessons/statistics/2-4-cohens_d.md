[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

Exercise 4   Using the variable totalwgt_lb, investigate whether first babies are lighter or heavier than others. Compute Cohen’s d to quantify the difference between the groups. How does it compare to the difference in pregnancy length?

Using the firsts and others groupings established previously in the chapter I first determined the mean total weight in pounds for first babies and all other babies.
...

    firsts = live[live.birthord == 1]
    others = live[live.birthord != 1]
    firsts.totalwgt_lb.mean(), others.totalwgt_lb.mean()

This gave (7.201094430437772, 7.325855614973262) as the resulting means, indicating an approximate 0.125 lbs difference between first born babies and all others, with all other babies averaging the heavier weight. I then used the provided function for the Cohen effect size to quantify the difference between the first born baby weights and the weights of all other babies. I did not modify the provided function or write it in my own code as the provided code was incredibly easy to read and understand as well as already used the types of variable names I typically would also use. 
...

    def CohenEffectSize(group1, group2):
    """Computes Cohen's effect size for two groups.
    
    group1: Series or DataFrame
    group2: Series or DataFrame
    
    returns: float if the arguments are Series;
             Series if the arguments are DataFrames
    """
    diff = group1.mean() - group2.mean()

    var1 = group1.var()
    var2 = group2.var()
    n1, n2 = len(group1), len(group2)

    pooled_var = (n1 * var1 + n2 * var2) / (n1 + n2)
    d = diff / np.sqrt(pooled_var)
    return d
    
    CohenEffectSize(firsts.totalwgt_lb, others.totalwgt_lb)

This gave an effect size of approximately -0.089 standard deviations which according to the linked wikipedia article on Cohen's d is categorized as being a very small effect size. The pregnancy length difference between first babies and all other babies had a mean difference of 0.079 weeks and a cohen effect size difference of 0.029 standard deviations. While total weight has a larger effect size than pregnancy length both effect sizes are still well within that very small effect size category. 