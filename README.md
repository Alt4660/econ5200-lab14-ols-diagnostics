# OLS Diagnostics: Robust and Clustered Standard Errors

## Objective

I tested how well classical, HC3 and firm-clustered standard errors hold up in OLS when errors are heteroskedastic or correlated within firms, and I checked an AI-written standard-error function against statsmodels.

## Methodology

- I measured how often a nominal 95% confidence interval for the slope contains the true slope, comparing classical and HC3 standard errors when the errors are heteroskedastic.
- I repeated the coverage check with errors shared within 40 firms, comparing HC3 standard errors with standard errors clustered by firm.
- I looked for three planted rows using leverage, studentised residuals and Cook's distance.
- I measured how much one of the planted rows moved the estimated slope.
- I wrote my own prompt asking an AI for a table of standard errors, and ran two rounds of it.
- I checked all 18 numbers from each round against statsmodels. I also ran each round's function on a copy of the data with every column renamed, to see whether the result depended on column names.

## Key Findings

**Coverage with heteroskedastic errors**
- Classical standard errors gave 92.4% coverage.
- HC3 standard errors gave 94.4%, closer to the nominal 95%.

**Coverage with errors shared within 40 firms**
- HC3 standard errors gave 50.3%, so they did not account for the within-firm correlation.
- Clustering by firm gave 93.7%.

**Planted rows**
- Leverage, studentised residuals and Cook's distance together found all three planted rows.
- One of them moved the slope from 1.4927 to 1.4468.

**AI-generated standard-error table**
- Round 1: the function matched all 18 numbers, and also 18 of 18 on the copy with renamed columns.
- Round 2: the function matched only 12 of 18, because 6 intercept values were missing. It also matched 12 of 18 on the renamed copy.
