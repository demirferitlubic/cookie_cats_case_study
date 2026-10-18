# Cookie Cats: A/B Testing & Retention Analysis

**Independent Product Analytics Project | Mobile Gaming**

## Project Overview

Cookie Cats is a mobile puzzle game with progression gates that temporarily restrict players from advancing. This project analyzes a publicly available A/B test comparing two placements of the first progression gate:

- **Control:** Gate at Level 30
- **Treatment:** Gate at Level 40

**Business question:** Should the first progression gate remain at Level 30 or move to Level 40?

This is an independent analysis of an existing experiment—not an experiment I designed or ran.

## Dataset

The dataset contains **90,189 players**:

| Experiment Group | Players |
|---|---:|
| Gate 30 | 44,700 |
| Gate 40 | 45,489 |

Available fields include experiment assignment, total gameplay rounds over the first 14 days, and Day-1 (D1) and Day-7 (D7) retention indicators.

**Source:** [Mobile Games: A/B Testing — Kaggle](https://www.kaggle.com/datasets/yufengsui/mobile-games-ab-testing)

## Methodology

- Validated player counts and examined the dataset for missing values and duplicate user IDs.
- Compared D1 and D7 retention rates using **two-proportion z-tests** with a 5% significance threshold.
- Calculated a **95% confidence interval** for the D7 retention difference.
- Compared gameplay-round distributions using descriptive statistics and a boxplot.
- Checked for potential **sample ratio mismatch (SRM)** using a chi-square goodness-of-fit test under an assumed 50/50 allocation.

D7 retention was used as the main decision metric for this retrospective analysis.

## Key Findings

| Metric | Gate 30 | Gate 40 |
|---|---:|---:|
| D1 Retention | 44.82% | 44.23% |
| D7 Retention | 19.02% | 18.20% |
| Mean Gameplay Rounds | 52.46 | 51.30 |
| Median Gameplay Rounds | 17 | 16 |

**Statistical Results**

- **D1 Retention:** The observed difference was not statistically significant (p = 0.07441).
- **D7 Retention:** Gate 40 showed a 0.82-percentage-point lower retention rate (p = 0.00155). The 95% confidence interval for Gate 40 minus Gate 30 was approximately -1.33 to -0.31 percentage points.
- **Gameplay Engagement:** The two groups showed broadly similar distributions of gameplay rounds. Differences in gameplay rounds were analyzed descriptively, without statistical significance testing.
- **Experiment Validity:** The sample-ratio mismatch check produced p = 0.00861 under an assumed 50/50 allocation. Because the intended allocation ratio is unknown, this finding raises a potential concern rather than proving an experiment error.

## Product Recommendation

**Recommendation: Retain the Level 30 gate provisionally and avoid rolling out Level 40 based on the available evidence.**

Gate 30 performed better in terms of observed D7 retention, while Gate 40 showed no statistically significant improvement in D1 retention.

However, the potential sample-ratio mismatch should be investigated before treating the findings as definitive causal evidence.

Furthermore, the dataset lacks revenue, in-app purchase, session duration, and gate-interaction information. Therefore, the overall monetization impact of changing the progression gate cannot be established.

## Proposed Next Experiment

After validating the assignment process, a follow-up experiment could compare gate placements at Levels 30, 35, and 40.

Additional performance indicators should include:

- Day-1 and Day-7 retention
- Gate reach and completion rates
- Session behavior
- Payer conversion
- Average Revenue Per Daily Active User (ARPDAU)

The goal would be to identify a progression gate placement that optimizes retention without negatively affecting monetization.

## Tools & Technologies

- **Python:** pandas, SciPy, statsmodels, Matplotlib
- **Microsoft Excel:** Data analysis, KPI calculations, and visualizations
- **Statistical Methods:** Two-proportion z-tests, confidence intervals, chi-square goodness-of-fit test

## Repository Contents

- `Cookie_Cats_AB_Testing.ipynb` — Python analysis and statistical tests
- `Cookie_Cats_Analysis.xlsx` — Excel calculations and summaries
- `Cookie_Cats_Product_Analysis.pdf` — Detailed product analysis report and recommendations
