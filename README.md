# 1. Experimental Overview & Methodology

## 1.1 Experiment Background & Objective

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

## 1.2 Experiment Design & Group Allocation

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
| Experiment Duration | 14 days, based on assignment information |

The Control group serves as the baseline comparison, while the Target group represents the experimental treatment.

The experiment is assumed to use randomized assignment. However, the dataset does not contain a unique User_ID, so user-level uniqueness and assignment consistency cannot be independently verified.

## 1.3 Metric Definition

Four metrics are evaluated and categorized into continuous and categorical outcomes.

| Metric | Data Type | Definition | Evaluation Metric |
|---|---|---|---|
| Engagement Score | Continuous | User-level engagement score | Mean |
| Duration Played | Continuous | User listening duration in minutes | Mean |
| Payment Status | Binary | Payment Yes/No status | Proportion of Yes |
| Subscription Status | Binary | Premium/Free subscription status | Proportion of Premium |

### Continuous Metrics

Engagement Score and Duration Played are evaluated by comparing the mean values between the Control and Target groups.

Mean Difference:

Mean Difference = Mean(Target) - Mean(Control)

### Categorical Metrics

Payment and Subscription are evaluated by comparing the proportion of positive outcomes between the two groups.

- Payment Rate = Number of Payment Yes / Total Group Observations
- Premium Rate = Number of Premium Users / Total Group Observations

Proportion Difference:

Proportion Difference = Proportion(Target) - Proportion(Control)

Categorical outcome differences are reported in percentage points (pp).

Payment and Subscription are treated as observed status variables. They are not assumed to represent new transactions or newly acquired subscribers because pre-experiment status information is unavailable.

## 1.4 Statistical Methodology

Statistical testing is conducted to determine whether the observed differences between the Control and Target groups are statistically significant.

### Hypothesis Testing

Two-sided hypotheses are applied because a directional improvement hypothesis was not documented before the results were observed.

| Metric | Statistical Test | Null Hypothesis (H0) | Alternative Hypothesis (H1) |
|---|---|---|---|
| Engagement Score | Welch's t-test | Mean Control = Mean Target | Mean Control ≠ Mean Target |
| Duration Played | Welch's t-test | Mean Control = Mean Target | Mean Control ≠ Mean Target |
| Payment Status | Two-proportion z-test | Payment proportions are equal | Payment proportions differ |
| Subscription Status | Two-proportion z-test | Premium proportions are equal | Premium proportions differ |

### Statistical Parameters

- Significance level (α): 0.05
- Confidence level: 95%
- Test direction: Two-sided
- Multiple testing correction: Holm correction
- Confidence intervals: 95% pointwise confidence intervals

### Effect Size Measurement

Effect sizes are used to evaluate the magnitude of differences between the two groups.

| Metric Type | Effect Size |
|---|---|
| Continuous outcomes | Cohen's d |
| Binary outcomes | Cohen's h |

### Statistical Assumptions

The analysis considers the following assumptions:

- Observations are independent between and within experimental groups.
- Welch's t-test does not require equal population variances between groups.
- The large sample sizes support approximate sampling distributions for the continuous and categorical comparisons.
- Two-proportion z-tests require sufficient outcome counts in each category.
- The assumed user-level randomization and observation unit are not independently verifiable due to the absence of User_ID.

## 1.5 Data Preparation & Assumptions

Before statistical testing, the dataset was checked for missing values, duplicate records, and invalid observations.

### Data Validation

| Validation | Result |
|---|---:|
| Total rows | 100,000 |
| Control observations | 50,000 |
| Target observations | 50,000 |
| Missing values | 0 |
| Full-row duplicates | 0 |
| Negative Duration Played records | 2 |

### Data Cleaning Treatment

| Data Issue | Treatment | Justification |
|---|---|---|
| Missing values | No imputation required | No missing values were identified |
| Full-row duplicates | No removal required | No full-row duplicates were identified |
| Negative Duration Played | Excluded from Duration Played analysis only | Negative elapsed play duration is considered invalid |
| Engagement Score above 1 | Retained | The variable is treated as a score rather than a bounded ratio |

The two negative Duration Played observations were found in the Control group. These observations were excluded only from the Duration Played analysis and retained for other outcome analyses.

### Final Sample Size by Metric

| Metric | Control N | Target N |
|---|---:|---:|
| Engagement Score | 50,000 | 50,000 |
| Duration Played | 49,998 | 50,000 |
| Payment Status | 50,000 | 50,000 |
| Subscription Status | 50,000 | 50,000 |

### Experiment Assumptions

The analysis uses the following assumptions:

1. Users were randomly assigned to the Control and Target groups, based on the provided experiment information.
2. The allocation ratio was 50:50.
3. Each row represents one user observation.
4. The experiment duration was 14 days, based on assignment information.
5. Duration Played is measured in minutes.
6. Engagement Score is treated as a score that may exceed 1.
7. Payment and Subscription represent observed post-experiment status variables.

These assumptions are documented for analytical transparency and should not be interpreted as independently verified dataset properties.

## 1.6 Experiment Design Limitations

Several limitations should be considered when interpreting the experiment results.

| Limitation | Potential Impact |
|---|---|
| No unique User_ID | User-level uniqueness and assignment consistency cannot be verified |
| Randomization cannot be independently audited | The integrity of group assignment cannot be fully assessed |
| Detailed treatment description unavailable | The specific intervention applied to the Target group cannot be fully documented |
| No pre-experiment Payment or Subscription status | New transactions and newly acquired Premium subscribers cannot be identified |
| Payment definition unavailable | Payment Yes cannot automatically be interpreted as a completed transaction during the experiment |
| Experiment duration cannot be verified from the main dataset timestamps | Temporal effects and the exact observation period cannot be independently assessed |
| No documented pre-registration | Primary outcomes and directional hypotheses cannot be confirmed as predetermined |

These limitations do not invalidate the descriptive comparisons or the statistical calculations. However, they affect the strength and scope of the business conclusions.

Therefore, the results should be interpreted as evidence of differences between the observed Control and Target groups, while causal attribution and incremental business outcomes require additional experiment documentation and baseline data.

---
