# Hypothesis Testing Notes

## 1. Experiment Parameter Setup
* **Metric Being Tested:** Paid Conversion Rate (The North Star Metric)
* **Reason for Selection:** Paid Conversion Rate directly measures the conversion rate of user activation and onboarding. Improving this metric directly impacts subscription growth and business revenue.
* **Significance Level ($\alpha$):** 0.05 (Standard 5% error threshold)
* **Test Type:** Two-tailed Z-Test for Two Proportional Means
  * *Rationale:* A two-tailed test ensures we remain mathematically objective. It tests whether the Treatment group is significantly different (either better or worse) compared to the Control group, rather than blindly assuming a positive shift.

## 2. Hypothesis Framework
* **Null Hypothesis ($H_0$):** $P_{\text{treatment}} = P_{\text{control}}$
  * *Business Translation:* The new onboarding and activation campaign has no effect on the Paid Conversion Rate. The observed differences are due to random sampling variance.
* **Alternative Hypothesis ($H_1$):** $P_{\text{treatment}} \neq P_{\text{control}}$
  * *Business Translation:* The new onboarding and activation campaign has a statistically significant effect on the Paid Conversion Rate.

## 3. Decision Rules & Interpretation Logic
* **If $p\text{-value} < 0.05$:** Reject the Null Hypothesis ($H_0$). We conclude that the observed conversion lift in the treatment group is statistically significant and not a result of random chance.
* **If $p\text{-value} \ge 0.05$:** Fail to reject the Null Hypothesis ($H_0$). We conclude that the differences between the groups are not statistically reliable.

## 4. Test Execution & Results
* **Control Sample Size ($n_1$):** 687
* **Control Conversions ($x_1$):** 19 (Conversion Rate: 2.77%)
* **Treatment Sample Size ($n_2$):** 710
* **Treatment Conversions ($x_2$):** 50 (Conversion Rate: 7.04%)
* **Calculated Z-Score:** 3.6879
* **Calculated P-Value:** 0.000226

## 5. Statistical Decision & Business Interpretation
* **Statistical Decision:** Reject the Null Hypothesis ($H_0$) because the $p\text{-value} \ (0.000226) < \alpha \ (0.05)$.
* **Business Interpretation:** The exponential increase in the Paid Conversion Rate from 2.77% to 7.04% is statistically valid and highly reliable. It cannot be attributed to random variation or sampling noise. The new onboarding and activation campaign successfully drives a higher rate of user conversions.