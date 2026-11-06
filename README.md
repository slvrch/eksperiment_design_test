# Spotify A/B Testing

## 1. Experimental Overview & Methodology

### 1.1 Experiment Background & Objective

This project evaluates an A/B testing experiment designed to compare the outcomes of a Control group and a Target group in a Spotify-related business scenario.

The primary objective is to assess whether the Target group demonstrates better outcomes than the Control group across four observed metrics:

1. Engagement Score
2. Duration Played
3. Payment Status
4. Subscription Status

The analysis aims to evaluate differences in user engagement, listening behavior, payment status, and Premium subscription status between the two experimental groups.

**Key Research Question:**

Does the Target group demonstrate significantly different outcomes compared with the Control group across the selected user and business metrics?

The specific treatment or intervention applied to the Target group should be interpreted according to the original experiment assignment.

### 1.2 Experiment Design & Group Allocation

The experiment consists of two groups with an equal allocation based on the provided experiment information.

| Component | Description |
|---|---|
| Experiment Type | A/B Testing |
| Control Group | Baseline or existing experience |
| Target Group | Proposed treatment or alternative experience |
| Total Observations | 100,000 |
| Control Group | 50,000 observations (50%) |
| Target Group | 50,000 observations (50%) |
| Allocation Ratio | 50:50 |
| Randomization | Assumed to have been performed based on experiment information |
| Assumed Observation Unit | One user per row |
| Experiment Duration | 14 days, based on data documentation |

The Control group serves as the baseline comparison, while the Target group represents the experimental treatment.

The experiment is assumed to use data documentation. However, the dataset does not contain a unique User_ID, so user-level uniqueness and assignment consistency cannot be independently verified.

### 1.3 Metric Definition

Four metrics are evaluated and categorized into continuous and categorical outcomes.

| Metric | Data Type | Definition | Evaluation Metric |
|---|---|---|---|
| Engagement Score | Continuous | User-level engagement score | Mean |
| Duration Played | Continuous | User listening duration in minutes | Mean |
| Payment Status | Binary | Payment Yes/No status | Proportion of Yes |
| Subscription Status | Binary | Premium/Free subscription status | Proportion of Premium |

#### Continuous Metrics

Engagement Score and Duration Played are evaluated by comparing the mean values between the Control and Target groups.

Mean Difference:

Mean Difference = Mean(Target) - Mean(Control)

#### Categorical Metrics

Payment and Subscription are evaluated by comparing the proportion of positive outcomes between the two groups.

- Payment Rate = Number of Payment Yes / Total Group Observations
- Premium Rate = Number of Premium Users / Total Group Observations

Proportion Difference:

Proportion Difference = Proportion(Target) - Proportion(Control)

Categorical outcome differences are reported in percentage points (pp).

Payment and Subscription are treated as observed status variables. They are not assumed to represent new transactions or newly acquired subscribers because pre-experiment status information is unavailable.

### 1.4 Statistical Methodology

Statistical testing is conducted to determine whether the observed differences between the Control and Target groups are statistically significant.

#### Hypothesis Testing

Two-sided hypotheses are applied because a directional improvement hypothesis was not documented before the results were observed.

| Metric | Statistical Test | Null Hypothesis (H0) | Alternative Hypothesis (H1) |
|---|---|---|---|
| Engagement Score | Welch's t-test | Mean Control = Mean Target | Mean Control ≠ Mean Target |
| Duration Played | Welch's t-test | Mean Control = Mean Target | Mean Control ≠ Mean Target |
| Payment Status | Two-proportion z-test | Payment proportions are equal | Payment proportions differ |
| Subscription Status | Two-proportion z-test | Premium proportions are equal | Premium proportions differ |

#### Statistical Parameters

- Significance level (α): 0.05
- Confidence level: 95%
- Test direction: Two-sided
- Multiple testing correction: Holm correction
- Confidence intervals: 95% pointwise confidence intervals

#### Effect Size Measurement

Effect sizes are used to evaluate the magnitude of differences between the two groups.

| Metric Type | Effect Size |
|---|---|
| Continuous outcomes | Cohen's d |
| Binary outcomes | Cohen's h |

#### Statistical Assumptions

The analysis considers the following assumptions:

- Observations are independent between and within experimental groups.
- Welch's t-test does not require equal population variances between groups.
- The large sample sizes support approximate sampling distributions for the continuous and categorical comparisons.
- Two-proportion z-tests require sufficient outcome counts in each category.
- The assumed user-level randomization and observation unit are not independently verifiable due to the absence of User_ID.

### 1.5 Data Preparation & Assumptions

Before statistical testing, the dataset was checked for missing values, duplicate records, and invalid observations.

#### Data Validation

| Validation | Result |
|---|---:|
| Total rows | 100,000 |
| Control observations | 50,000 |
| Target observations | 50,000 |
| Missing values | 0 |
| Full-row duplicates | 0 |
| Negative Duration Played records | 2 |

#### Data Cleaning Treatment

| Data Issue | Treatment | Justification |
|---|---|---|
| Missing values | No imputation required | No missing values were identified |
| Full-row duplicates | No removal required | No full-row duplicates were identified |
| Negative Duration Played | Excluded from Duration Played analysis only | Negative elapsed play duration is considered invalid |
| Engagement Score above 1 | Retained | The variable is treated as a score rather than a bounded ratio |

The two negative Duration Played observations were found in the Control group. These observations were excluded only from the Duration Played analysis and retained for other outcome analyses.

#### Final Sample Size by Metric

| Metric | Control N | Target N |
|---|---:|---:|
| Engagement Score | 50,000 | 50,000 |
| Duration Played | 49,998 | 50,000 |
| Payment Status | 50,000 | 50,000 |
| Subscription Status | 50,000 | 50,000 |

#### Experiment Assumptions

The analysis uses the following assumptions:

1. Users were randomly assigned to the Control and Target groups, based on the provided experiment information.
2. The allocation ratio was 50:50.
3. Each row represents one user observation.
4. The experiment duration was 14 days, based on data documentation.
5. Duration Played is measured in minutes.
6. Engagement Score is treated as a score that may exceed 1.
7. Payment and Subscription represent observed post-experiment status variables.

These assumptions are documented for analytical transparency and should not be interpreted as independently verified dataset properties.

### 1.6 Experiment Design Limitations

Several limitations should be considered when interpreting the experiment results.

| Limitation | Potential Impact |
|---|---|
| No unique User_ID | User-level uniqueness and dataset consistency cannot be verified |
| Randomization cannot be independently audited | The integrity of group dataset cannot be fully assessed |
| Detailed treatment description unavailable | The specific intervention applied to the Target group cannot be fully documented |
| No pre-experiment Payment or Subscription status | New transactions and newly acquired Premium subscribers cannot be identified |
| Payment definition unavailable | Payment Yes cannot automatically be interpreted as a completed transaction during the experiment |
| Experiment duration cannot be verified from the main dataset timestamps | Temporal effects and the exact observation period cannot be independently assessed |
| No documented pre-registration | Primary outcomes and directional hypotheses cannot be confirmed as predetermined |

These limitations do not invalidate the descriptive comparisons or the statistical calculations. However, they affect the strength and scope of the business conclusions.

Therefore, the results should be interpreted as evidence of differences between the observed Control and Target groups, while causal attribution and incremental business outcomes require additional experiment documentation and baseline data.

--

## 2. Statistical Results

This section evaluates whether the observed outcomes differ between the Control and Target groups. It presents descriptive comparisons, inferential test results, effect sizes, and the overall statistical conclusion.

### 2.1 Descriptive Statistics
The descriptive analysis compares the observed values in the two experimental groups before interpreting the hypothesis-testing results.

| Metric | Measurement | Control | Target | Difference (Target − Control) |
|---|---|---:|---:|---:|
| Engagement Score | Mean ± SD | 0.599958 ± 0.100017 | 0.799726 ± 0.100046 | +0.199768 points |
| Duration Played | Mean ± SD (minutes) | 120.0758 ± 30.0389 | 159.9129 ± 30.0189 | +39.8371 minutes |
| Payment = Yes | Positive status rate | 34,844 (69.688%) | 39,907 (79.814%) | +10.126 percentage points |
| Subscription = Premium | Premium status rate | 29,871 (59.742%) | 40,125 (80.250%) | +20.508 percentage points |

Sample Sizes

| Metric | Control (N) | Target (N) |
|---|---:|---:|
| Engagement Score | 50,000 | 50,000 |
| Duration Played | 49,998 | 50,000 |
| Payment Status | 50,000 | 50,000 |
| Subscription Status | 50,000 | 50,000 |

Notes:
- SD represents standard deviation.
- Duration Played is measured in minutes, based on the stated dataset assumption.
- Payment and Subscription are reported as observed status proportions. They should not be interpreted as transaction conversion or newly acquired subscribers without baseline status and event-level definitions.
- The two negative Duration Played records in the Control group were excluded from the Duration Played analysis only.
- Percentage-point differences (pp) are absolute differences between group percentages. They are not the same as relative percentage uplift.

### 2.2 Statistical Test Results
Welch's t-test was used for the two continuous metrics. Two-proportion z-tests were used for the two binary metrics. All tests were two-sided, with a significance level of 0.05. Holm correction was applied across the four hypothesis tests.

| No. | Metric | Statistical Test | Test Statistic | Raw p-value | Holm-adjusted p-value | 95% CI of Difference | Effect Size | Decision |
|---:|---|---|---:|---:|---:|---|---:|---|
| 1 | Engagement Score | Welch's t-test | t = 315.762 | <0.001 | <0.001 | [0.198528; 0.201008] | Cohen's d = 1.997 | Reject H0 |
| 2 | Duration Played | Welch's t-test | t = 209.755 | <0.001 | <0.001 | [39.464853; 40.209341] minutes | Cohen's d = 1.327 | Reject H0 |
| 3 | Payment = Yes | Two-proportion z-test | absolute z = 36.853 | 2.58 × 10⁻²⁹⁷ | <0.001 | [9.5908; 10.6605] pp | Cohen's h = 0.234 | Reject H0 |
| 4 | Subscription = Premium | Two-proportion z-test | absolute z = 70.757 | <0.001 | <0.001 | [19.9535; 21.0608] pp | Cohen's h = 0.454 | Reject H0 |

#### Statistical reporting notes:
- The confidence intervals are 95% pointwise intervals for the difference (Target − Control). They have not been adjusted for multiple comparisons.
- Some computed p-values were displayed as 0.0 because of floating-point underflow. They are reported as p < 0.001, not as a true probability of zero.
- The absolute z-statistic is shown for the two-proportion tests; the sign depends on the order in which the groups are supplied to the test function.
- pp means percentage points.
- Effect-size conventions are guidelines rather than absolute decision thresholds. Cohen's d values of 1.997 and 1.327 represent large standardized differences. Cohen's h of 0.234 is relatively small, while 0.454 is approaching the conventional medium-effect benchmark.

### 2.3 Interpretation of Statistical Findings

#### A. Engagement Score

The Target group recorded a mean Engagement Score of 0.799726, compared with 0.599958 in the Control group. The estimated mean difference was +0.199768 points, with a 95% confidence interval of [0.198528, 0.201008].

Welch's t-test found a statistically significant difference (t = 315.762, p < 0.001). The standardized effect size was large (Cohen's d = 1.997).

**Interpretation:** The observed mean Engagement Score was higher in the Target group than in the Control group, with a large standardized difference.

#### B. Duration Played

The Target group recorded a mean Duration Played of 159.9129 minutes, compared with 120.0758 minutes in the Control group. The estimated mean difference was +39.8371 minutes, with a 95% confidence interval of [39.464853, 40.209341] minutes.

Welch's t-test found a statistically significant difference (t = 209.755, p < 0.001). The standardized effect size was large (Cohen's d = 1.327).

**Interpretation:** The observed average listening duration was approximately 39.84 minutes higher in the Target group. This result describes listening activity during the measured period; it does not by itself establish improved user retention.

The Control sample size was 49,998 because two negative Duration Played values were excluded from this metric's analysis only.

#### C. Payment Status

The reported proportion of Payment = Yes was 79.814% in the Target group and 69.688% in the Control group. The estimated difference was +10.126 percentage points, with a 95% confidence interval of [9.5908, 10.6605] percentage points.

The two-proportion z-test found a statistically significant difference (|z| = 36.853, raw p = 2.58 × 10⁻²⁹⁷; Holm-adjusted p < 0.001). Cohen's h was 0.234, indicating a relatively small effect size under conventional guidelines.

**Interpretation:** A higher proportion of observations in the Target group had Payment = Yes status than in the Control group. The dataset does not establish whether this status represents a completed transaction during the experiment, so the finding should not be described as a confirmed increase in payment conversion or revenue.

#### D. Subscription Status

The reported proportion of Premium status was 80.250% in the Target group and 59.742% in the Control group. The estimated difference was +20.508 percentage points, with a 95% confidence interval of [19.9535, 21.0608] percentage points.

The two-proportion z-test found a statistically significant difference (|z| = 70.757, p < 0.001 after Holm reporting). Cohen's h was 0.454, an effect size approaching the conventional medium-effect benchmark.

**Interpretation:** A higher proportion of observations in the Target group had Premium subscription status than in the Control group. Because pre-experiment subscription status is unavailable, this difference cannot be interpreted as a confirmed number of newly acquired Premium subscribers.

### 2.4 Overall Statistical Conclusion
All four evaluated metrics showed statistically significant differences between the observed Control and Target groups. Each result remained significant after Holm correction for the four hypothesis tests. The estimated differences were positive, meaning that the Target group had higher observed values or status proportions across all four metrics.

The largest standardized differences were observed for Engagement Score (Cohen's d = 1.997) and Duration Played (Cohen's d = 1.327). Among the categorical outcomes, Subscription Status had a larger effect size (Cohen's h = 0.454) than Payment Status (Cohen's h = 0.234).

These results provide statistical evidence of differences between the observed groups. Statistical significance alone does not demonstrate business value, incremental transactions, new subscriber acquisition, or incremental revenue. Causal interpretation also depends on the validity of random assignment and the independence of observations; these design properties cannot be fully audited from a dataset without a unique User_ID.

--

## 3. Business Impact Analysis

This section translates the statistical findings into potential business implications. It evaluates what the observed differences may mean for user engagement, listening activity, payment-related status, and subscription status. It does not estimate revenue or return on investment; those calculations are addressed separately in the Financial Feasibility section.

### 3.1 Business Context & Evaluation Objective

The business objective is to assess whether the higher observed outcomes in the Target group indicate potentially favorable changes in user engagement, listening behavior, and subscription-related indicators.

**Business evaluation question:**
Do the observed differences in the Target group indicate potentially meaningful improvements in user engagement, listening activity, payment-related status, and Premium subscription status compared with the Control group?

The analysis distinguishes between an observed difference in the dataset and a business outcome that has been independently verified. In particular, Payment and Subscription are treated as recorded statuses, not as confirmed transaction events or new customer acquisitions.

### 3.2 Metric-to-Business Impact Mapping

| Metric | Statistical Finding | Relative Uplift | Potential Business Implication | Business Dimension |
|---|---|---:|---|---|
| Engagement Score | +0.199768 points | +33.30% | May indicate stronger user engagement in the Target group | User Engagement |
| Duration Played | +39.8371 minutes | +33.18% | May indicate greater listening activity or service usage | User Activity |
| Payment = Yes | +10.126 pp | +14.53% | A higher proportion of observations has Payment = Yes status | Payment-related Indicator |
| Subscription = Premium | +20.508 pp | +34.33% | A higher proportion of observations has Premium status | Subscription-related Indicator |

Relative uplift is calculated as:

$$
\text{Relative Uplift} = \frac{\text{Target} - \text{Control}}{\text{Control}} \times 100\%
$$

For Payment and Subscription, the absolute difference in percentage points is the primary comparison. Relative uplift is included as supplementary context and should not replace percentage-point reporting.

### 3.3 Individual Business Impact Interpretation

#### A. Engagement Score — User Engagement

Observed change: The mean Engagement Score increased from 0.599958 in the Control group to 0.799726 in the Target group, a difference of 0.199768 points and a relative uplift of approximately 33.30%.

**Business interpretation:** The Target group recorded a higher engagement score. This may indicate that the Target experience is associated with stronger user engagement during the observed period.

Potential business value: Higher engagement may support a more active user experience and could be relevant to product engagement objectives.

**Limitation:** The dataset does not provide the score definition or establish how Engagement Score relates to retention, subscription renewal, or revenue. Those relationships should not be assumed from this comparison alone.

#### B. Duration Played — User Activity

**Observed change:** Mean Duration Played increased from 120.0758 minutes in the Control group to 159.9129 minutes in the Target group, a difference of approximately 39.84 minutes and a relative uplift of 33.18%.

**Business interpretation:** Users in the Target group recorded longer average listening duration than users in the Control group.

Potential business value: Greater listening activity may be a favorable product-usage indicator and may help assess whether the Target experience encourages more use of the service.

**Limitation:** Longer listening duration does not independently demonstrate better retention, higher satisfaction, or increased revenue. Further user-level and longitudinal analysis would be needed to evaluate those outcomes.

#### C. Payment Status — Payment-related Indicator

**Observed change:** The reported proportion of Payment = Yes was 79.814% in the Target group and 69.688% in the Control group, a difference of 10.126 percentage points and a relative uplift of approximately 14.53%.

**Business interpretation:** A higher proportion of observations in the Target group carried the Payment = Yes status.

Potential business value: If the status is confirmed to represent a valid payment event within a clearly defined period, this metric could support an assessment of payment-related performance.

**Limitation:** The meaning and timing of the Payment status are not documented in the available dataset. Without event-level transaction data and a pre-experiment baseline, the result cannot be interpreted as a confirmed increase in completed transactions, payment conversion, or revenue.

#### D. Subscription Status — Subscription-related Indicator

**Observed change:** The reported Premium proportion was 80.250% in the Target group and 59.742% in the Control group, a difference of 20.508 percentage points and a relative uplift of approximately 34.33%.

**Business interpretation:** A higher proportion of observations in the Target group had Premium subscription status.

**Potential business value:** A higher Premium share may be relevant to subscription mix and subscription-related business performance.

**Limitation:** Pre-experiment subscription status and subscription transition history are unavailable. Therefore, the observed difference cannot establish how many users newly subscribed, upgraded from Free to Premium, or generated incremental subscription revenue.

### 3.4 Overall Business Impact Assessment

| Business Dimension | Supporting Metric | Main Finding | Assessment |
|---|---|---|---|
| User Engagement | Engagement Score | +0.199768 points; approximately +33.30% relative uplift | Positive observed indicator |
| User Activity | Duration Played | +39.84 minutes; approximately +33.18% relative uplift | Positive observed indicator |
| Payment-related Status | Payment = Yes | +10.126 percentage points; approximately +14.53% relative uplift | Higher positive-status proportion |
| Subscription Status | Premium | +20.508 percentage points; approximately +34.33% relative uplift | Higher Premium-status proportion |

Across the four evaluated dimensions, the Target group showed higher observed values or status proportions than the Control group. Taken together, these findings provide a favorable directional signal for the Target group in the measured outcomes.

The four metrics should not be combined into a single business-impact score because they have different units and represent different business concepts. The analysis also does not test whether higher Engagement Score causes longer listening duration, Payment status, or Premium status. Each metric is interpreted as a separate observed outcome.

### 3.5 Business Implications & Further Validation

The findings identify several business questions that require additional data before the potential impact can be quantified or attributed to the Target treatment.

| Finding | Business Question | Additional Data Required |
|---|---|---|
| Higher Engagement Score | Is higher engagement associated with stronger user retention? | User-level activity history and retention/cohort data |
| Longer Duration Played | Does the increase in listening duration persist over time? | Longitudinal listening history and recurring usage data |
| Higher Payment = Yes proportion | Does the status represent an actual payment event during the experiment? | Defined payment events, transaction records, and transaction dates |
| Higher Premium proportion | How many users became Premium during the experiment? | Pre-experiment and post-experiment subscription status, plus subscription transition history |

#### Business Impact Conclusion

The Target group demonstrated positive observed differences across all four evaluated business indicators. Engagement Score was approximately 33.30% higher on a relative basis, while Duration Played was approximately 33.18% higher. The proportions of Payment = Yes and Premium status were higher by 10.126 and 20.508 percentage points, respectively.

These findings indicate potentially favorable differences in user engagement, listening activity, and subscription-related status in the Target group. However, higher engagement and listening duration do not independently establish improved retention. Similarly, Payment and Subscription status differences cannot yet be interpreted as incremental transactions or newly acquired Premium subscribers.

Further validation using user-level baseline information, clearly defined payment events, subscription history, and actual financial records is required before quantifying incremental business value. These findings will be used as context for the separate Financial Feasibility Analysis; they should not be treated as realized revenue or profit.

## 4. Financial Feasibility Analysis

### 4.1 Objective

This section evaluates the potential financial feasibility of the Target strategy using the observed difference in Premium subscription status between the Target and Control groups.

The analysis consists of two complementary components:
1. Financial Scenario Analysis — evaluates potential financial outcomes under Conservative, Base Case, and Optimistic assumptions.
2. Conversion Realization Sensitivity Analysis — evaluates how financial outcomes change when the share of estimated incremental Premium outcomes varies, while the other Base Case assumptions remain fixed.

The financial model is a hypothetical business simulation. It is not a report of Spotify's actual campaign expenditure, contribution margin, revenue, customer acquisition cost, or profit.

### 4.2 Financial Model Basis and Assumptions
The observed Premium status proportions from the A/B test are:

| Metric | Control | Target | Difference |
|---|---:|---:|---:|
| Premium proportion | 59.742% | 80.250% | +20.508 percentage points |

The estimated difference in Premium outcomes for a Target population of 50,000 is calculated as:

$$
\text{Estimated Premium Outcome Difference}
= 50{,}000 \times (0.80250 - 0.59742)
= 10{,}254
$$

The value of **10,254 is an estimated difference in the number of users with Premium status between the two groups**, scaled to 50,000 Target users. It is not a verified count of newly acquired subscribers because pre-experiment Subscription status and user-level transition data are unavailable.

The model uses the following assumptions:

| Assumption | Value | Description |
|---|---:|---|
| Target population | 50,000 users | Number of observations in the Target group |
| Observed Premium proportion difference | 20.508 pp | Target Premium proportion minus Control Premium proportion |
| Estimated outcome difference at 100% realization | 10,254 | 50,000 multiplied by the observed proportion difference |
| Monthly Premium price | Rp59,900 | Assumed monthly price used in the simulation |
| Contribution margin | 60% / 70% / 80% | Scenario assumptions, not verified Spotify margins |
| Campaign cost | Rp250 million / Rp150 million / Rp100 million | Scenario assumptions, not actual campaign expenditure |
| Conversion realization rate | 50% / 75% / 100% | Scenario assumptions representing the share of the estimated outcome difference assumed to be realized |
| Revenue period | One monthly billing cycle | Assumes each estimated realized outcome generates one full month of revenue at the assumed price |

**Important interpretation:** Conversion Realization Rate is a modeling parameter used to account for uncertainty in translating the observed Premium status difference into a financial estimate. It is not a measured conversion probability or a value observed in the experiment dataset.

### 4.3 Financial Formulas
The model applies the following formulas:

#### 1. Estimated incremental Premium outcomes

$$
\text{Estimated Outcomes}
= 10{,}254 \times \text{Conversion Realization Rate}
$$

#### 2. Incremental gross revenue

$$
\text{Incremental Revenue}
= \text{Estimated Outcomes} \times \text{Monthly Premium Price}
$$

#### 3. Contribution

$$
\text{Contribution}
= \text{Incremental Revenue} \times \text{Contribution Margin}
$$

#### 4. Net contribution

$$
\text{Net Contribution}
= \text{Contribution} - \text{Campaign Cost}
$$

#### 5. Return on Investment (ROI)

$$
\text{ROI}
= \frac{\text{Net Contribution}}{\text{Campaign Cost}} \times 100\%
$$

#### 6. Return on Ad Spend (ROAS)

$$
\text{ROAS}
= \frac{\text{Incremental Revenue}}{\text{Campaign Cost}}
$$

#### 7. Incremental Customer Acquisition Cost (CAC)

$$
\text{Incremental CAC}
= \frac{\text{Campaign Cost}}{\text{Estimated Outcomes}}
$$

#### 8. Monthly contribution per estimated outcome

$$
\text{Monthly Contribution per User}
= \text{Monthly Premium Price} \times \text{Contribution Margin}
$$

#### 9. CAC payback period

$$
\text{CAC Payback (months)}
= \frac{\text{Incremental CAC}}{\text{Monthly Contribution per User}}
$$

#### 10. Break-even conversion realization rate

$$
\text{Break-even Rate}
= \frac{\text{Campaign Cost}}
{10{,}254 \times \text{Monthly Premium Price} \times \text{Contribution Margin}}
\times 100\%
$$

ROI is calculated using contribution after the assumed contribution margin, less campaign cost. ROAS uses gross modeled revenue divided by campaign cost. Therefore, ROAS and ROI measure different things and should not be interpreted interchangeably.

### 4.4 Financial Scenario Analysis
Financial Scenario Analysis compares three combinations of assumptions to assess how financial feasibility changes under different operating conditions.

#### 4.4.1 Scenario Assumptions

| Scenario | Contribution Margin | Campaign Cost | Conversion Realization Rate |
|---|---:|---:|---:|
| Conservative | 60% | Rp250,000,000 | 50% |
| Base Case | 70% | Rp150,000,000 | 75% |
| Optimistic | 80% | Rp100,000,000 | 100% |

#### 4.4.2 Financial Projection Results

| Financial Indicator | Conservative | Base Case | Optimistic |
|---|---:|---:|---:|
| Estimated incremental outcomes | 5,127 | 7,690.5 | 10,254 |
| Incremental gross revenue (one month) | Rp307,107,300 | Rp460,660,950 | Rp614,214,600 |
| Contribution | Rp184,264,380 | Rp322,462,665 | Rp491,371,680 |
| Campaign cost | Rp250,000,000 | Rp150,000,000 | Rp100,000,000 |
| **Net contribution** | **-Rp65,735,620** | **Rp172,462,665** | **Rp391,371,680** |
| **ROI** | **-26.29%** | **114.98%** | **391.37%** |
| ROAS | 1.23x | 3.07x | 6.14x |
| Incremental CAC | Rp48,761.46 | Rp19,504.58 | Rp9,752.29 |
| Monthly contribution per user | Rp35,940 | Rp41,930 | Rp47,920 |
| CAC payback period | 1.36 months | 0.47 months | 0.20 months |
| Break-even realization rate | 67.84% | 34.89% | 20.35% |

Estimated outcomes can be fractional when expressed as expected values. For example, 7,690.5 in the Base Case is a model expectation, not an actual count of half a person or a verified subscriber count.

#### 4.4.3 Scenario Interpretation

**Conservative Scenario**

The Conservative Scenario assumes a 60% contribution margin, Rp250 million in campaign cost, and a 50% conversion realization rate. The model estimates 5,127 incremental outcomes and Rp307.11 million in one-month gross revenue. After applying the assumed contribution margin and deducting campaign cost, net contribution is -Rp65.74 million, resulting in an ROI of -26.29%.

Under these assumptions, the modeled contribution is insufficient to cover campaign cost. The assumed realization rate of 50% is also below the break-even realization rate of 67.84%. Therefore, this scenario is not financially feasible within the model assumptions.

**Base Case Scenario**

The Base Case assumes a 70% contribution margin, Rp150 million in campaign cost, and a 75% conversion realization rate. The model estimates 7,690.5 incremental outcomes and Rp460.66 million in one-month gross revenue. Net contribution is Rp172.46 million, resulting in an ROI of 114.98% and ROAS of 3.07x.

The assumed realization rate of 75% is above the break-even realization rate of 34.89%. This scenario indicates potential financial feasibility under the stated assumptions. It should be treated as a planning case rather than evidence of actual financial performance.

**Optimistic Scenario**

The Optimistic Scenario assumes an 80% contribution margin, Rp100 million in campaign cost, and a 100% conversion realization rate. The model estimates 10,254 incremental outcomes and Rp614.21 million in one-month gross revenue. Net contribution is Rp391.37 million, resulting in an ROI of 391.37% and ROAS of 6.14x.

This scenario produces the most favorable modeled outcome. However, it also relies on the highest realization rate and contribution margin, together with the lowest campaign cost. It should therefore be interpreted as an upside scenario, not the expected result.

#### 4.4.4 Scenario Analysis Conclusion

The scenario analysis indicates that the financial outcome is sensitive to the assumed contribution margin, campaign cost, and conversion realization rate. The Conservative Scenario produces a negative net contribution, while the Base Case and Optimistic Scenarios produce positive modeled net contributions.

The Base Case provides a useful reference for planning, but the model cannot establish actual campaign profitability until incremental new subscribers, actual revenue, contribution margin, and campaign expenditure are validated using operational and financial data.

### 4.5 Conversion Realization Sensitivity Analysis

4.5.1 Objective

The sensitivity analysis evaluates how changes in the Conversion Realization Rate affect the estimated financial outcome.

Unlike the Financial Scenario Analysis, this analysis changes only the Conversion Realization Rate while holding the other assumptions constant at the Base Case values. This isolates the effect of realization rate on the financial projections.

#### 4.5.2 Fixed Base Case Assumptions
| Assumption | Fixed Value |
|---|---:|
| Target population | 50,000 users |
| Estimated outcome difference at 100% realization | 10,254 |
| Monthly Premium price | Rp59,900 |
| Contribution margin | 70% |
| Campaign cost | Rp150,000,000 |

#### 4.5.3 Sensitivity Results

| Financial Indicator | 50% Realization | 75% Realization | 100% Realization |
|---|---:|---:|---:|
| Estimated incremental outcomes | 5,127 | 7,690.5 | 10,254 |
| Incremental gross revenue (one month) | Rp307,107,300 | Rp460,660,950 | Rp614,214,600 |
| Contribution | Rp214,975,110 | Rp322,462,665 | Rp429,950,220 |
| Campaign cost | Rp150,000,000 | Rp150,000,000 | Rp150,000,000 |
| **Net contribution** | **Rp64,975,110** | **Rp172,462,665** | **Rp279,950,220** |
| **ROI** | **43.32%** | **114.98%** | **186.63%** |
| ROAS | 2.05x | 3.07x | 4.09x |
| Incremental CAC | Rp29,256.88 | Rp19,504.58 | Rp14,628.44 |

#### 4.5.4 Sensitivity Interpretation

**50% Realization Rate**

At a 50% realization rate, the model estimates 5,127 incremental outcomes and Rp307.11 million in one-month gross revenue. Under the fixed Base Case contribution margin and campaign cost, net contribution is Rp64.98 million and ROI is 43.32%.

**75% Realization Rate**

At a 75% realization rate, the model estimates 7,690.5 incremental outcomes and Rp460.66 million in one-month gross revenue. Net contribution increases to Rp172.46 million and ROI reaches 114.98%.

**100% Realization Rate**

At a 100% realization rate, the model estimates 10,254 incremental outcomes and Rp614.21 million in one-month gross revenue. Net contribution increases to Rp279.95 million and ROI reaches 186.63%.

#### 4.5.5 Sensitivity Analysis Conclusion

With contribution margin, monthly price, and campaign cost held constant at Base Case values, higher Conversion Realization Rates result in higher modeled revenue, contribution, net contribution, and ROI. Incremental CAC decreases as the estimated number of realized outcomes increases.

The Base Case break-even realization rate is approximately 34.89%. Under the fixed Base Case assumptions, realization rates of 50%, 75%, and 100% are all above this break-even threshold.

This sensitivity analysis shows the financial model's dependence on realization assumptions. It does not prove that any of the tested realization rates will occur in practice.

### 4.6 Overall Financial Feasibility Assessment
The two analyses answer different questions:

| Analysis | Question Answered | Key Finding |
|---|---|---|
| Financial Scenario Analysis | What are the modeled financial outcomes under different combinations of assumptions? | ROI ranges from -26.29% in the Conservative Scenario to 391.37% in the Optimistic Scenario; Base Case ROI is 114.98%. |
| Conversion Realization Sensitivity Analysis | How does the financial outcome change when only realization rate changes? | Under fixed Base Case assumptions, ROI increases from 43.32% at 50% realization to 186.63% at 100% realization. |

**Overall assessment:** The model indicates potential financial feasibility under the Base Case assumptions. However, the financial result remains hypothetical because the experiment dataset does not establish the number of newly acquired Premium subscribers, and the model uses assumed price, contribution margin, campaign cost, and realization rate.

A full business decision should therefore remain conditional on validation of actual incremental subscribers, transaction-level revenue, campaign expenditure, contribution margin, and subscription retention.

### 4.7 Financial Model Limitations

The following limitations should accompany the financial projections:

1. **Premium status difference is not verified subscriber acquisition.** The estimated 10,254 outcomes are derived from the difference in post-experiment Premium proportions, not from observed user-level subscription transitions.
2. **No pre-experiment subscription baseline is available.** The dataset cannot identify which users moved from Free to Premium during the experiment.
3. **Conversion Realization Rate is an assumption.** The 50%, 75%, and 100% values are scenario inputs, not measured probabilities or experiment results.
4. **Monthly Premium price is assumed.** The model applies Rp59,900 per estimated outcome for one monthly billing cycle and does not establish the actual price paid by each user.
5. **Contribution margin is assumed.** The 60%, 70%, and 80% margins are scenario parameters, not verified company financial data.
6. **Campaign cost is assumed.** The modeled campaign costs are not actual Spotify campaign expenditures.
7. **Revenue is modeled for one month only.** The projections do not incorporate renewals, churn, discounts, refunds, taxes, payment fees, or longer-term customer value.
8. **Net contribution is not total company net profit.** Other operating expenses and financial items are not included in this model.
9. **CAC and payback depend on the incremental outcome estimate.** These metrics should not be treated as actual customer acquisition metrics until genuinely incremental new paying subscribers are validated.

### 4.8 Business Implications and Next Steps
The financial model suggests that the Target strategy may be financially attractive under the Base Case assumptions, but the evidence is not sufficient to support an unconditional full rollout.

Before making a final implementation decision, the following data should be validated:
- User-level subscription status before and after the experiment.
- Verified new Premium subscription events and transaction records.
- Actual monthly revenue collected and applicable pricing or discounts.
- Actual campaign and implementation expenditure.
- Verified contribution margin and relevant variable costs.
- Subscription retention and renewal behavior beyond the initial billing cycle.

The financial findings should be considered alongside the Statistical Results, Business Impact Analysis, and Risk Assessment. Post-implementation monitoring will be evaluated separately in the next stage and should not be treated as completed evidence in this analysis.
