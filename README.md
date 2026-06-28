# # Project Documentation: KPI Framework & Experiment Analysis

## 1. Business context

### ### Understanding the Business Problem

* **What decision needs to be made?** Leadership must decide whether the new onboarding and activation campaign (the treatment group) should be launched to all users globally, or if the company should stick with the existing onboarding experience (the control group).

* **Who the decision impacts?** This decision directly impacts new users navigating the registration funnel, the customer support team handling downstream interface friction, and the business leadership team tracking premium sign-up volumes.

* **What metric should improve?** The primary metric targeted for improvement is the **Paid Conversion Rate** (the percentage of total users who convert from a free or trial state to a premium paid subscription tier).

* **What risks must be monitored?** To avoid optimizing for top-line conversions blindly, we must actively monitor operational health metrics, specifically the **Refund Rate** (to identify buyer's remorse) and the **Support Ticket Rate** (to evaluate onboarding friction).

* **What evidence is required before making a recommendation?** A statistically significant increase in the Paid Conversion Rate backed by a multi-axis A/B test, alongside validation that defensive operational metrics have not triggered systemic risk alerts.

## 2. Dataset description

The experiment analysis was executed utilizing a randomized testing dataset (`campaign_experiment_data.xlsx`) containing 1,400 unique user interaction records. This transactional snapshot maps the user lifecycle across a standard digital product activation funnel, logging demographic tracking variables (`region`, `device_type`, `traffic_source`, `plan_type`), micro-funnel milestones, operational support logs, and 30-day post-activation premium revenues.

## 3. North Star metric selected
The designated North Star Metric for this experiment is the **Paid Conversion Rate**. 

* **Why this metric is the main success metric:** It serves as the ultimate validator of product value realization. While top-of-funnel benchmarks indicate product interest, paid conversion measures the exact moment a user transitions from evaluation to hard financial commitment.

* **Why other metrics are supporting metrics instead of the North Star:** Funnel milestones like "Landing page visit rate" or "Onboarding completion rate" function strictly as leading operational indicators. They diagnose where drop-offs happen, but they do not guarantee business survival or real monetization if users abandon the product before paying.

* **How this metric connects to business growth:** In a recurring subscription business model, elevating conversion efficiency expands Monthly Recurring Revenue (MRR) linearly without requiring additional marketing acquisition spend, optimizing unit economics.

* **What could go wrong if this metric is optimized blindly:** Forcing conversions via aggressive marketing prompts or confusing interface flows (dark patterns) creates artificial short-term spikes paired with severe downstream damage, including skyrocketing refund requests and high customer support backlogs.

## 4. KPI tree summary

To track product interactions systematically, a structured KPI Tree architecture anchors our primary conversion targets to underlying operational levers and defensive health safety valves:
* **North Star Metric:** Paid Conversion Rate
* **Primary Growth Drivers:** * *Top of Funnel Engagement:* Landing Page Visit Rate, Trial Start Rate
  * *Onboarding Success:* Onboarding Completion Rate, Average Days to Convert
  * *Product Value Realization:* Average Engagement Score, Trial DAU
* **Operational Guardrails:** Support Ticket Rate, Refund Rate, Average Revenue Per Converted User (ARPU)

## 5. Experiment analysis approach

Before executing hypothesis testing calculations, the raw transactional data underwent a rigorous data quality validation and preprocessing pipeline inside Excel to ensure accurate metrics:
* **Duplicate User IDs:** Identified duplicate user log instances, keeping only the initial interaction touchpoint and deleting redundant rows to prevent double-counting.
* **Missing Value Handling:** Structured demographic blanks in `device_type` and `traffic_source` under an "Unknown" placeholder string to protect segment-level distribution integrity. Blanks within conversion timelines (`days_to_convert`) were intentionally preserved as true null cells to prevent downstream metric skewing.
* **Invalid Binary Normalization:** Audited and verified that all funnel milestone indicators contained strict 1 and 0 boolean values.
* **Outlier Removal Boundaries:** Isolated extreme revenue value rows exceeding $3,000 to eliminate unrepresentative data entries and secure a clean baseline for average value metrics.
* **Sample Balance Audit:** Validated that group distribution metrics were statistically balanced near an even split (Control: ~49%, Treatment: ~51%) across core tracking segments.

## 6. Hypothesis test summary

* **Null Hypothesis ($H_0$):** $P_{\text{treatment}} = P_{\text{control}}$ (The new onboarding campaign has no statistically reliable effect on the Paid Conversion Rate).
* **Alternative Hypothesis ($H_1$):** $P_{\text{treatment}} \neq P_{\text{control}}$ (The new onboarding campaign exerts a statistically significant effect on the Paid Conversion Rate).
* **Significance Horizon:** $\alpha = 0.05$ at a standard 95% Confidence Interval.
* **Statistical Output Proof:** A two-proportions Z-test calculation evaluated on our clean experimental rows yielded a **Z-score of 3.6879**, translating to an extreme **p-value of 0.000226**. Because the calculated p-value is strictly less than our significance alpha ($0.000226 < 0.05$), we reject the Null Hypothesis ($H_0$) with high statistical reliability.

## 7. Guardrail metrics considered

While the primary funnel test proved a massive conversion expansion, optimizing for conversion blindly introduces severe business risks across three defensive guardrail dimensions:
* **Support Ticket Rate (Critical Risk):** The support queue baseline surged from 22.13% in the Control group to 37.32% in the Treatment group (+15.19% absolute increase). This reveals that nearly 40% of converting users encounter severe onboarding confusion or interface issues, risking support team burnout.
* **Refund Requests (Medium Risk):** The Control group maintained a perfect 0.00% refund pattern, whereas a 0.42% refund rate emerged within the Treatment group. Any immediate post-conversion refund patterns suggest post-purchase anxiety and aggressive onboarding messaging.
* **Average Revenue Per Converted User (High Risk):** The average revenue per converted customer dropped from $872.48 down to $770.36 (-$102.12 decline). This indicates that the new campaign drives user counts at the expense of revenue quality, likely relying too heavily on introductory tiers or heavy promotional discounts.

## 8. Final recommendation

* **Official Recommendation Stance:** **Continue Testing (Phased Optimization Rollout)**
* **Justification:** While the experimental treatment group triggered a major top-of-funnel conversion increase (+4.27% absolute lift, representing a 2.5x scaling shift), a total global rollout is heavily rejected. The massive spike in customer support backlogs combined with significant revenue decompression per user proves the flow introduces harmful interface friction. We must remain in a testing phase to resolve mobile UI flaws and discount loops before launching to 100% of the user base.

## 9. Assumptions and limitations

* **Capacity Assumptions:** The rollout strategy assumes internal customer success infrastructure can temporarily absorb targeted regional pilot loads while data engineers refactor onboarding screens.
* **Evaluation Window Constraints:** The data baseline covers a fixed, short-term 30-day post-activation window. This framework cannot evaluate long-term subscription renewal stability, account compounding cycles, or secondary customer retention dynamics.

## 10. Screenshots included

Below is the verified graphical evidence detailing the data engineering sheets, visual tree structures, and statistical calculations executed for this repository:

### ### 1. Main Experiment Summary Metrics
![Funnel Performance Summary](screenshots/summary_metrics.png)

### ### 2. Hypothesis Test Output & Mathematical Evidence
![Z-Test Execution Sheet](screenshots/hypothesis_test_output.png)

### ### 3. Visual KPI Tree Architecture
![KPI Tree Preview](screenshots/kpi_tree_preview.png)