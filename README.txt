This is the documentation for Tausworth5.ipynb, a Jupiter Notebook that simulates the properties of the Tausworthe pseudo-random number generator. The author is Charlie Kramer (https://github.com/Charlie-Kramer). This code, along with some helper code and the associated paper on the Tausworthe generator, is available at https://github.com/Charlie-Kramer/tausworthe

The notebook was run in Jupyter Notebook under Python 3.9. It uses these packages:

NumPy 1.21.5
SciPy 1.9.1
Pandas1.4.4
Matplotlib 3.5.2
Statsmodels 0.13.2
random (inbuilt)

The notebook contains the following routines:

make_u(q,r,el,n).  Given the desired parameters, this routine returns the corresponding Tausworthe series as a list. 

gen_norm(u). This applies the Box-Muller transformation to u, splitting it into two series u1,u2, transforming them into z1, z2, and returning the two z series appended to one another as a list.

make_graphs(u,nbins). Given a series u and number of bins (for the histogram), this routine draws figures 1-5 in the paper.

do_tests(u,nbins). Given the series u and the number of bins for the uniformity chi-square test, this routine applies the battery of tests for uniformity and independence, returning a dictionary with the value of each statistic and its corresponding p-value

The third cell performs the two-level tests; set the number of tests and desired length. It writes the results to a set of lists denoted [testname]_p and saves them to a csv file for later analysis. The fourth cell plots these results.

The final cell performs random draws from parameter sets for primitive trinomials, generates corresponding series, and performs chi-squared goodness of fit tests on each, which are then plotted on a histogram.

HOW TO GENERATE THE RESULTS IN THE PAPER

1. Start by generating a series of uniform random numbers. First, in Cell 1, choose the recurrence parameters q and r and the word size el (corresponding to p, q, and el in the paper), along with the number of PRNs you want (n), the number of lags for the autocorrelation function test (nlag), and the number of bins for the histogram. Go to the part labeled 'set parameters here'. Then run the routine make_u() with the corresponding parameters--it returns a list of n uniform PRNs. You can alter the seed in the routine set_seed().

2. Make the initial set of charts using make_graphs() (also in Cell 1). This produces Figures 1-5 in the paper.

3. Run the suite of one-level tests. Run Cell 2, which runs the routine do_tests(). It outputs a dictionary with test results (statistics and p-values).

4. Run two-level tests; see Cell 3. Here, set the number of tests (ntests) and the total length n of the generated series (the length per tests times the number of tests), along with the number of lags for the Ljung-Box test. The results are saved to a Pandas data frame and .csv file for offline analysis.

5. Chart the two-level test results--run Cell 4 (this produces Figure 6 in the paper).  

6. Cell 5 runs the tests over randomized choice of parameterization of the recurrence relation, selecting from primitive trinomials. This produces Figure 7 in the paper. (See my GitHub repo for the code that extracts and cleans the table from the original PDF)