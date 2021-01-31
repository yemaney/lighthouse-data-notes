# Basic Statistics

## Bayes Theorem
        P(A | B) = P(B | A) * P(A) / P(B)


---
## Hypothesis Testing
- Assume, after data is standardize, that there id `no difference with the sample mean and the population mean`
    - mean_p = 0
    - mean_s = 0
- chose a significance level `alpha` 
- Do `T-test or Z-test` 
- identify the propability of getting the sample mean or anything more extreme, given the assumptions
    - this is the `p-value`
- if  `p < alpha` then the findings are significant, reject the null hypothesis
- if `p > alpha` then the findings are not unlikely and we don't reject the null hypothesis

---
### Central Limit Theorem 

The central limit theorem states that if you have a population with mean `μ` and standard deviation `σ` and take `sufficiently large random samples `from the population with replacement , then the `distribution of the sample means will be approximately normally` distributed.

- even if the original distribution isn't normal itself, it's sampling distribution will be normal