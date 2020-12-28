[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

Exercise 3.1 Something like the class size paradox appears if you survey
children and ask how many children are in their family. Families with many
children are more likely to appear in your sample, and families with no children have no chance to be in the sample.Use the NSFG respondent variable NUMKDHH to construct the actual distribution for the number of children under 18 in the household.Now compute the biased distribution we would see if we surveyed the childrenand asked them how many children under 18 (including themselves) are intheir household.
Plot the actual and biased distributions, and compute their means. As astarting place, you can use chap03ex.ipynb.

I first took the NSFG respondent variable numkdhh and converted it into a Pmf object using the Pmf class from thinkstats2 under the variable name pmf. The PMF function maps each value to its probability creating value:item pairs. I then used thinkplot to plot Pmf as a step function and labeled each axis.

---

    resp=nsfg.ReadFemResp()
    pmf=thinkstats2.Pmf(resp.numkdhh, label='numkdhh')
    thinkplot.Pmf(pmf)
    thinkplot.Config(xlabel="Number of Children",ylabel="PMF")
    ![Unbiased distribution of number of children under 18 per household](../StatsImages/ch3ex1.png)
---

