# Hypothesis Testing Notes

## 1. Null Hypothesis ($H_0$)

The new onboarding and activation campaign experience has no statistically significant effect on the Paid Conversion Rate. Any observed variance is entirely due to random sampling noise.$$H_0: P_{\text{treatment}} = P_{\text{control}}$$

## 2. Alternate Hypothesis ($H_1$)

The new onboarding and activation campaign experience has a statistically significant effect on the Paid Conversion Rate, meaning the treatment group performance differs from the control group baseline.$$H_1: P_{\text{treatment}} \neq P_{\text{control}}$$

## 3. Test Tail Configuration

Type: Two-tailed Z-Test for Two Proportional MeansRationale: A two-tailed test ensures we remain mathematically objective. It tests whether the Treatment group is significantly different (either significantly better or significantly worse) compared to the Control group, rather than blindly assuming a positive directional shift.

## 4. Significance Level ($\alpha$)

Threshold Selection: $\alpha = 0.05$ (Standard $5\%$ error threshold)Context: This establishes a $95\%$ confidence level baseline, defining the boundary line required to confidently reject the null hypothesis.

## 5. Metric Being Tested

Primary Parameter: Paid Conversion Rate (The North Star Metric)Data Type: Binary Proportion Variable ($1 = \text{Converted to Paid}$, $0 = \text{Did not convert}$).

## 6. Reason for Choosing That Metric

Paid Conversion Rate directly measures the conversion rate of user activation and onboarding. Improving this metric directly impacts subscription growth, increases customer lifecycle initialization, and drives long-term business recurring revenue.

### ## 7. Interpretation Logic & Decision Rules

Following the calculations of the two-proportions z-test:
* **If $p\text{-value} < 0.05$:** Reject the Null Hypothesis ($H_0$). We conclude that the observed conversion variance in the treatment group is statistically significant and not a result of random chance.
* **If $p\text{-value} \ge 0.05$:** Fail to reject the Null Hypothesis ($H_0$). We conclude that the differences between the groups are not statistically reliable, and we do not have enough evidence to support deploying the new variant over the baseline.

## 8. Test Execution & Results
* **Control Sample Size ($n_1$):** 687
* **Control Conversions ($x_1$):** 19 (Conversion Rate: 2.77%)
* **Treatment Sample Size ($n_2$):** 710
* **Treatment Conversions ($x_2$):** 50 (Conversion Rate: 7.04%)
* **Calculated Z-Score:** 3.6879
* **Calculated P-Value:** 0.000226
* **Pooled Proportion ($\hat{p}$):** $0.04939$
* **Standard Error ($SE$):** $0.01160$

## 9. Statistical Decision & Business Interpretation
* **Statistical Decision:** Reject the Null Hypothesis ($H_0$) because the calculated $p\text{-value}$ ($0.000226$) is strictly less than our alpha threshold ($\alpha = 0.05$).
* **Business Interpretation:** The exponential increase in the Paid Conversion Rate from 2.77% to 7.04% is statistically valid and highly reliable. It cannot be attributed to random variation or sampling noise. The new onboarding and activation campaign successfully drives a higher rate of user conversions.