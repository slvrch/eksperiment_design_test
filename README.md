# Spotify Ramadan Audio Discovery
## A/B Testing, Financial Feasibility & Post-Implementation Evaluation

## Project Overview & Executive Summary

A simulated Spotify business case was developed to evaluate an enhanced personalized audio discovery experience. The proposed strategy was compared with a standard discovery experience using A/B testing across engagement, listening duration, payment status, and subscription status. The results were then evalated through financial scenario modeling and a subsequent population-level monitoring exercise during a simulated Ramadan rollout.

## Business Background

Music streaming platforms users with access to extensive libraries of music, podcasts, and other audio content. As content choices continue to expand, helping users discover relevant content becomes an important part of the overall listening experience.

Listening preferences may vary depending on users interests activities, and daily routines. Seasonal periods such as Ramadan can introduce additional changes in these routines.

Spotify has publicly highlighted changes in Indoensia listening behavior during Ramadan, including ngabuburit hours and interest in spirituality-related podcasts, wellness content, and music at different times of the day.

This project presents a simulated business case to evaluate whether an enhanced personalized audio discovery strategy can demonstrate better user engagement outcomes than a standard discovery experience. The evaluation is followed by financial feasibility modeling and population-level monitoring during a simulated Ramadan rollout.

## Business Problem 

As music and audio streaming platforms continue to expand their content libraries, helping users discover relevant audio experiences becomes increasingly important for maintaining user engagement and listening activity.

During seasonal periods such as Ramadan, users may have different listening preferences and routines across the day. This creates an opportunity to evaluate whether an enhanced personalized audio discovery experience can better accommodate users' changing content interests.

The existing standard discovery experience serves as the baseline, while an enhanced personalized discovery strategy is proposed as an alternative treatment. However, its ability to improve user outcomes and demonstrate potential subscription-related business value needs to be evaluated.

This project addresses the opportunity through four measurement dimensions:

**1. User Engagement & Listening Activity**
- Engagement Score
- Average Listening Duration

**2. Subscription-related Outcomes**
- Payment Yes Rate
- Premium Subscription Share

**3. Financial Feasibility**
- Modeled Monthly Revenue
- Net Contribution
- ROI and ROAS
- Break-even Realization Rate

**4. Post-Implementation User Activity**
- Daily Active Users (DAU)
- Day-over-Day (DoD) Growth
- Average DAU by Implementation Phase

The analysis compares the standard and enhanced discovery experiences through A/B testing, evaluates their potential financial value under different assumptions, and monitors population-level user activity during a simulated Ramadan rollout.

### Business Questions

1. Does personalized discovery demonstrate better engagement outcomes?
2. Are there differences in subscription-related outcomes?
3. Does the Target strategy demonstrate potential financial feasibility?
4. How sensitive are modeled financial outcomes to Conversion Realization Rate?
5. How does user activity change after implementation?

## Business Objectives

This project aims to:

1. Compare the observed outcomes of the standard audio discovery experience (Control) and enhanced personalized audio discovery experience (Target) across engagement, listening duration, payment status, and subscription status.

2. Evaluate the statistical evidence of the observed group differences using appropriate hypothesis tests, confidence intervals, effect sizes, and Holm multiple-testing correction.

3. Assess the potential financial feasibility of the Target strategy through financial scenario modeling and Conversion Realization Sensitivity Analysis.

4. Monitor population-level Daily Active Users during the simulated pilot and expanded rollout periods to understand changes in user activity and identify further measurement requirements.

## Data Understanding

### A. A/B Testing Dataset (Experiment Dataset)

100.000 Observations | 5 columns
| Column | Data Type | Description |
|--------|--------|--------|
| Group | Categorical | Control / Target |
| Engagement | Numerical | Engagement Score |
| Duration Played | Numerical | Duration listening by minutes |
| Payment | Categorical | Yes / No |
| Subscription | Categorical | Premium / Free |

Distribution grup:

| Group | Observations | Allocation |
|--------|--------|--------|
| Control | 50.000 | 50% |
| Target | 50.000 | 50% |
| Total | 100.000 | 100% |

### B. Post-Implementation Dataset (Population Monitoring Dataset)

15 Observations | 2 columns
| Column | Data Type | Description |
|--------|--------|--------|
| Date | DateTime | Date of observation |
| Total Users | Integer | Assumed to be Daily Active Users |

Periods in the project scenario:

| Phase | Date | Keterangan |
|--------|--------|--------|
| Phase 1 — Pilot | 1–7 Maret 2026 | Limited Target Pilot |
| Phase 2 — Full Rollout | 8–14 Maret 2026 | Expanded rollout |
| Follow-up | 15 Maret 2026 | Monitoring lanjutan |

### C. Data Quality Assessment

| Data Quality Check | A/B Testing | Post-Implementation |
|--------|--------|--------|
| Total Observations | 100.000 | 15 |
| Missing Values | 0 | 0 |
| Full-row Duplicates | 0 | 0 |
| Invalid Negative Duration | 2 | N/A |
| Unique User ID | Not available | Not available |
| Date Range | Not available in main dataset | 1–15 Maret 2026 |

## Analysis & Key Insights

<img width="853" height="292" alt="image" src="https://github.com/user-attachments/assets/470a6e97-f942-4bbb-a9fe-9038a81422b3" />

**Inisight:**
The Target group demonstrated higher observed engagement outcomes than the Control group. Engagement Score was 33.30% higher on a relative basis, while average listening duration was approximately 39.84 minutes higher.

These findings provide favorable statistical evidence for the enhanced personalized audio discovery strategy across the measured engagement and listening activity outcomes.

However, the findings should not be interpreted as confirmed improvements in user satisfaction, retention, or long-term business value. The interpretation also depends on the experiment's assumed randomization and observation independence, which cannot be independently verified from the available dataset.

<img width="849" height="354" alt="image" src="https://github.com/user-attachments/assets/a4c6d30b-812c-4e64-8e9e-d795b8c99c59" />

**Insight 2:**

The Target group demonstrated higher observed Payment = Yes and Premium subscription status proportions than the Control group. Both differences remained statistically significant after Holm multiple-testing correction.

These findings provide favorable statistical evidence of differences in subscription-related status outcomes between the two groups.

However, the results do not establish an increase in newly acquired Premium subscribers, completed payment transactions, or incremental subscription revenue because pre-experiment status information and transaction-level records were unavailable.

<img width="1050" height="449" alt="image" src="https://github.com/user-attachments/assets/88567953-657e-4fb5-af80-0a212cb43fd7" />

**Insight 3 - Financial**

The Target strategy demonstrates potential financial feasibility under the Base Case and Optimistic assumptions, generating modeled ROI values of 114.98% and 391.37%, respectively.

However, the Conservative Scenario results in a negative ROI of -26.29% and a negative Net Contribution of Rp65.74 million.

These findings indicate that the financial outcome is highly dependent on the assumed realization rate, contribution margin, and campaign cost. The Base Case provides a useful financial planning reference, but the results remain hypothetical.

**Insight 4 - Sensitivity**

### C. Post-Implementation Evaluations

**Final Result**
| Metric | Phase 1 — Pilot | Phase 2 — Full Rollout |
|--------|--------|--------|
| Period | 1–7 Maret | 8–14 Maret |
| Average DAU | 16.184,14 | 24.669,71 |

**Insight 1 - Pilot Monitoring:**
DAU between 1 and 7 March fluctuated, reaching a low of 11,660 on 7 March.

**Insight 2 - Expanded Rollout:**
The average DAU from 8 to 14 March stood at 24,669.71, 52.43 per cent higher than during the pilot period.

**Insight 3 - Peak Activity:**
DAU peaked at 29,803 on 11 March, before falling to 24,446 on 15 March

## Conclusion
The simulated A/B testing analysis shows that the Enhanced Personalized Audio Discovery group (Target) recorded higher observed outcomes across all four evaluated metrics compared with the Control group.

All four differences remained statistically significant after Holm multiple-testing correction. The largest standardized differences were observed in Engagement Score and Duration Played.

The financial feasibility model indicates potential positive financial contribution under the Base Case and Optimistic assumptions. However, the Conservative scenario generates negative net contribution, highlighting the model's sensitivity to realization rate, contribution margin, and campaign cost.

During the subsequent population-level monitoring period, average DAU was 52.43% higher during the expanded rollout phase than during the initial pilot phase. This comparison is descriptive and does not establish a causal effect of the Target strategy.

Overall, the Target strategy demonstrates promising experimental outcomes and modeled financial potential. However, further validation using verified incremental subscriptions, transaction records, actual costs, and more complete post-implementation data is required before making a full business investment decision.

## Recommendations
**Continue Testing/Controlled Rollout**

The Target Strategy can proceed to a controlled evaluation and implementation phase, but there is not yet sufficient evidence to conclude that a full roll-out will generate the projected financial returns.
### Recommended Next Actions
- Continue testing using User_ID and treatment exposure logs.
- Validate new Premium customers using baseline and transaction records.
- Replace financial assumptions with actual cost and revenue data.
- Continue monitoring DAU and retention.
- Evaluate music, podcasts and playlists separately to identify the most valuable discovery components.

## Tools & Technologies
Python, Power BI
