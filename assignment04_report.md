# Assignment 04 Interpretation Memo

**Student Name:** Luna Wolfe
**Date:** 2/15/26
**Assignment:** REIT Annual Returns and Predictors (Simple Linear Regression)

---

## 1. Regression Overview

You estimated **three** simple OLS regressions of REIT *annual* returns on different predictors:

| Model | Y Variable | X Variable | Interpretation Focus |
|-------|------------|------------|----------------------|
| 1 | ret (annual) | div12m_me | Dividend yield |
| 2 | ret (annual) | prime_rate | Interest rate sensitivity |
| 3 | ret (annual) | ffo_at_reit | FFO to assets (fundamental performance) |

For each model, summarize the key results in the sections below.

---

## 2. Coefficient Comparison (All Three Regressions)

**Model 1: ret ~ div12m_me**    
- Intercept (β₀): [0.1082] (SE: [0.006] , p-value: [0.000])
- Slope (β₁): [-0.0687] (SE: 0.032, p-value: [0.035])
- R²: [0.002] normal and 0.001 adj | N: [2527]

**Model 2: ret ~ prime_rate**
- Intercept (β₀): [0.1998] (SE: [0.016], p-value: [0.000])
- Slope (β₁): [-.0194] (SE: [0.003], p-value: [0.000])
- R²: [0.016] | N: [2527]
**Model 3: ret ~ ffo_at_reit**
- Intercept (β₀): [0.0973] (SE: [0.009], p-value: [0.000])
- Slope (β₁): [0.5770] (SE: [0.567], p-value: [0.309])
- R²: [0.000] | N: [2518]

*Note: Model 3 may have fewer observations if ffo_at_reit has missing values; statsmodels drops those rows.*

---

## 3. Slope Interpretation (Economic Units)

**Dividend Yield (div12m_me):**
- A 1 percentage point increase in dividend yield (12-month dividends / market equity) is associated with a [slope value] change in annual return.
- The slope was -.0678  indicating a negative trajectory of 6.78% in annual return as the dividend yield increses by 1%. I can see that the relationship between dividends and annual return is inverse, because as the dividends go up the annual return is much more likely to trend down with some outliars. So according to the model with each 2% increse in dividends, the annual return decreases by 6.7%.

**Prime Loan Rate (prime_rate):**
- A 1 percentage point increase in the year-end prime rate is associated with a [slope value] change in annual return.
- I am quite lost on this one, the slope is -0.0194 meaning that as the prime rate increses by 1% the annual return decreases by 1.94%. The strange thing is the way the datapoints settle on the graph, in long verticle lines similar to a boxplot. The strongest and highest placed plot cluster lines seem to be around 5% on the prime rate axis. I am unsure what causes this behavior but it is interesting to see how the data clusters dont consistantly trend upwards or downwards in overall placement. 

**FFO to Assets (ffo_at_reit):**
- A 1 unit increase in FFO/Assets (fundamental performance) is associated with a [slope value] change in annual return.
- The slope is .5770  which is our only positive slope out of these models. It means that with every 1% increse in ffo/assets the return increses by 57.7% which is a very high slope and does not seem consistant with the scatterplot. 


---

## 4. Statistical Significance

For each slope, at the 5% significance level:
- **div12m_me:** [Significant] — P (0.035 ) is less than .05, so we reject null and consider it significant. 
- **prime_rate:** [Significant] — p (0.00) is less than .05 so it is significant. 
- **ffo_at_reit:** [Not significant] — p (.309) is more than 0.05 so we accept null and consideer it not significant.

**Which predictor has the strongest statistical evidence of a relationship with annual returns?** I feel like the prime rate has the lowest p value and the highest r^2 number so I beleive it has the strongest evidence of a relationship. I am concerned though because .10-.30 is a normal r^2 for cross sectional data but these regressions have r^2 values that are less than that. 

---

## 5. Model Fit (R-squared)

Compare R² across the three models:
- The highest r^2 is attributed to the prime rate model at 0.016 where the closer it is to 1 the better the fit is. Cross sectional data like this should have an r^2 of .10 to.30. The other models have 0.002 (div) and 0.000 (ffo). I do not think this is a good sign for the goodness of fit of these regressions but it is hard to tell how we could improve this number. I am surprised that the one with the highest r also was the hardest for me to interpret. 

---

## 6. Omitted Variables

By using only one predictor at a time, we might be omitting:
- [ret]: [Ret measures the momentum of an investment, more speficially if the investment return will keep moving in its current direction (up or down) and could be helpful in finding corralations between the ret and the return, and which investments do better and why.]
- [ret12]: [Ret12 is similar to ret but speficially for 12 month rerturns which could pair nicely with the 12 month returns of dividends, I think there could be an interesting coralation there.]
- [1nmcap]: [1 net multiplier cap is a header related to the size of the return one can get. It strongly relates to annual return and probably should have been included in one of these regressions. Caps are hard for me to understand but from what I can tell the larger the cap, the larger your return should be so it would be cricial data when analyzing annual return.]

**Potential bias:** If omitted variables are correlated with both the X variable and ret, our slope estimates may be biased. [Brief discussion of direction if possible]
It can be hard to avoid bias in testing like this because you do not want overlapping variables or it can skew the results and cause there to be a lot of bias. If too variables are slightly overlapping it can throw off the regression because parts of the data will be double counted in a way, causing our outputs to be off, like r^2, SE, slope, and others. 
---

## 7. Summary and Next Steps

**Key Takeaway:**
[The predictor with the best stats was Prime_Rate, where the prime rate explains 1.6% of annual returns. It is both practically and statistically important because the p value is 0.00 and the slope shows that with every 1% increse in prime rates the annual return decreases by 1.94%. The other two regressions had some issues but I found that despite only 0.2% of the returns being explained by dividend returns the p value of 0.00 and the 6.78% decrease in returns for every 1% increse in 12 mo. dividend returns deemed it both statisticaly and practically significant. The ffo regression was not deemed statistically significant due to its high p value of .309 but it could be considered practically significant because of the high slope, though this could be due to the ill fitted regression.]

**What we would do next:**
- Extend to multiple regression (include two or more predictors)
- Test for heteroskedasticity and other OLS assumption violations
- Examine whether relationships vary by time period or REIT sector
I agree with everything listed above but I also think spending more time analyzing the RIET specific types of data could help, easpecially if we looked into 1nmcap and other extra variables included in this data.
---

## Reproducibility Checklist
- [ yes] Script runs end-to-end without errors
- [ yes] Regression output saved to `Results/regression_div12m_me.txt`, `regression_prime_rate.txt`, `regression_ffo_at_reit.txt`
- [ yes] Scatter plots saved to `Results/scatter_div12m_me.png`, `scatter_prime_rate.png`, `scatter_ffo_at_reit.png`
- [ ] Report accurately reflects regression results
- [ ] All interpretations are in economic units (not just statistical jargon)
