# Assignment 04 Interpretation Memo

**Student Name:** Luna Wolfe
**Date:** 2/13/26
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
- The slope was -.0678  indicating a negative trajectory on the regression. I can see that the relationship between dividends and annual return is inverse, because as the dividends go up the annual return is much more likely to trend down with some outliars. So according to the model with each 2% increse in dividends, the annual return decreases by 6.7%.

**Prime Loan Rate (prime_rate):**
- A 1 percentage point increase in the year-end prime rate is associated with a [slope value] change in annual return.
- I am quite lost on this one, the slope is -0.0194 meaning there is an extremely small negative tradjectory. The strnage thing is the way the datapoints settle on the graph, in long verticle lines similar to a boxplot. The strongest and highest placed plot cluster lines seem to be around 5% on the prime rate axis. I am unsure what causes this behavior but it is interesting to see how the data clusters dont consistantly trend upwards or downwards in overall placement. 

**FFO to Assets (ffo_at_reit):**
- A 1 unit increase in FFO/Assets (fundamental performance) is associated with a [slope value] change in annual return.
- The slop is .5770  which isour only positive slope out of these models. It is much harder to understand the relationship here because most of the datapoints are concentrated in a mass in the center between ffo/assets of 0% and 2%, this indicates a sort of sweet spot in the relationship between ffo/assets and annual return. 

---

## 4. Statistical Significance

For each slope, at the 5% significance level:
- **div12m_me:** [Significant] — P (0.035 ) is less than .05, so we reject null and consider it significant. 
- **prime_rate:** [Significant] — p (0.00) is less than .05 so it is significant. 
- **ffo_at_reit:** [Not significant] — p (.309) is more than 0.05 so we accept null and consideer it not significant.

**Which predictor has the strongest statistical evidence of a relationship with annual returns?** I feel like the prime rate has the lowest p value and the highest r^2 number. 

---

## 5. Model Fit (R-squared)

Compare R² across the three models:
- The highest r^2 is attributed to the prime rate model at 0.016 where the closer it is to 1 the better the fit is. The other models have 0.002 (div) and 0.000 (ffo). I do not think this is a good sign for the goodness of fit of these regressions but it is hard to tell how we could improve this number. I am surprised that the one with thehighest r also was the hardest for me to interpret. 

---

## 6. Omitted Variables

By using only one predictor at a time, we might be omitting:
- [Variable 1]: [Why it might matter]
- [Variable 2]: [Why it might matter]
- [Variable 3]: [Why it might matter]

**Potential bias:** If omitted variables are correlated with both the X variable and ret, our slope estimates may be biased. [Brief discussion of direction if possible]

---

## 7. Summary and Next Steps

**Key Takeaway:**
[2-3 sentences summarizing which predictor(s) show the strongest relationship with REIT annual returns and whether the evidence is consistent with economic theory]

**What we would do next:**
- Extend to multiple regression (include two or more predictors)
- Test for heteroskedasticity and other OLS assumption violations
- Examine whether relationships vary by time period or REIT sector

---

## Reproducibility Checklist
- [ yes] Script runs end-to-end without errors
- [ yes] Regression output saved to `Results/regression_div12m_me.txt`, `regression_prime_rate.txt`, `regression_ffo_at_reit.txt`
- [ yes] Scatter plots saved to `Results/scatter_div12m_me.png`, `scatter_prime_rate.png`, `scatter_ffo_at_reit.png`
- [ ] Report accurately reflects regression results
- [ ] All interpretations are in economic units (not just statistical jargon)
