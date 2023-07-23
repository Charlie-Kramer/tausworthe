# tausworthe
Simulates the properties of the Tausworthe pseudo-random number generator based on the trinomial recurrence $x_i=x_{i-p} + x_{i-q} mod 2$  (see the pdf of the paper in this repo).

The main code notebook (tausworth5) was run in Jupyter Notebook under Python 3.9. It uses these packages:

NumPy 1.21.5
SciPy 1.9.1
Pandas1.4.4
Matplotlib 3.5.2
Statsmodels 0.13.2
random (inbuilt)

The notebook contains the following routines:

make_u(q,r,el,n).  Given the desired parameters, this routine returns the corresponding Tausworthe series as a list. 

gen_norm(u). This applies the Box-Muller transformation to u.

make_graphs(u,nbins). Given a series u and number of bins (for the histogram), this routine draws figures 1-5 in the paper.

do_tests(u,nbins). Given the series u and the number of bins for the uniformity chi-square test, this routine applies the battery of tests for uniformity and independence, returning a dictionary with the value of each statistic and its corresponding p-value

The third cell performs the two-level tests; set the number of tests and desired length. It writes the results to a set of lists denoted [testname]_p and saves them to a csv file for later analysis. The fourth cell plots these results

The final cell performs random draws from the parameter sets, generates corresponding series, and performs chi-squared goodness of fit tests on each, which are then plotted on a histogram.

Also included is a notedbook that reads the parameters for primitive trinomials entabulated in Zierler and Brillhart's 1968 paper in Information and Control. 

