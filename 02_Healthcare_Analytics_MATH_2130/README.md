# Healthcare Analytics

**Exploratory ICU length-of-stay modelling · MATH 2130 · Winter 2025**

[Portfolio](../README.md) · [Report (PDF, 21 pages)](MATH_2130_Final_Report.pdf)

## Overview and problem

This team study explores intensive care unit (ICU) length of stay (LOS) for patients with acute traumatic cervical spinal cord injuries. It compares Lasso, Random Forest, and XGBoost and examines how preprocessing, feature timing, and a small cohort affect interpretation.

Available materials: A report and an existing notebook with source and saved outputs. The notebook is preserved, but its patient-level outputs need a sharing review. This is an exploratory study, not a validated clinical system.

## Dataset and tools

The report identifies MIMIC-IV v2.2 and a cohort of 97 ICU stays selected using ICD-9 prefix `8060`. Saved notebook outputs identify 89 patients and 90 admissions, so stays should not be treated as 97 independent patients.

Source: Johnson et al., [MIMIC-IV v2.2 on PhysioNet](https://physionet.org/content/mimiciv/2.2/), DOI: 10.13026/6mm1-ek67. Access is credentialed and subject to PhysioNet's data-use terms. The source dataset is not bundled with the repository.

Tools: Python, pandas, NumPy, Dask, SciPy, scikit-learn, XGBoost, Matplotlib, and Seaborn.

## Methodology

1. Join patient, admission, diagnosis, and ICU-stay tables; exclude invalid LOS.
2. Summarize selected chart/lab measurements between six hours before and 24 hours after ICU entry.
3. Count input, output, and procedure events by stay. In the notebook, these counts cover the whole stay, despite the report's early-window description.
4. Explore distributions, missingness, correlations, and statistical tests; remove selected sparse or redundant features.
5. Split stays into 77 training and 20 test observations (80/20), impute and encode through preprocessing pipelines, and train on `log1p(LOS)`.
6. Compare models with five-fold CV on the log scale and reverse the transform with `expm1` for test errors in days.

## Reported results and evaluation

These values match the report's rounded table and saved notebook outputs. They are historical exploratory results, not verified early-prediction performance.

| Model | Test MAE (days) | Test RMSE (days) | Mean CV R² (log scale) |
| --- | --- | --- | --- |
| Lasso | 2.888 | 4.592 | 0.174 |
| Random Forest | 2.211 | 3.839 | 0.845 |
| XGBoost | 2.573 | 4.646 | 0.802 |

Random Forest has the lowest reported errors. Test errors are reported in days; cross-validation R² is reported on the log scale. These metrics are not directly comparable. APACHE-IV was not applied to this cohort, so no superiority claim is supported.

## Key insights

- LOS is strongly right-skewed, motivating the log transformation.
- Total input-event count dominates recorded Random Forest importance; this association can reflect duration of stay because the count is not time-restricted.
- Feature availability must be checked at the intended prediction time; otherwise, evaluation can include information from later in the stay.

## Limitations and review findings

- Outcome leakage: The model feature list retains `hospital_expire_flag`, an outcome unavailable at an early prediction time.
- Feature timing: Event counts are grouped by stay without the early-window timestamp filter applied to chart/lab features. This can make longer stays predictable from information gathered later.
- Other late information: `discharge_location` is retained for modelling and needs an availability review.
- Evaluation design: Feature selection uses full-cohort exploration before splitting. The split is by stay rather than patient, and some patients have multiple stays. Both require review before claiming generalization.
- Sample and setting: Only 97 stays from a single hospital system; no external validation or clinical deployment is established.
- Data accessibility: The original notebook contains row-level saved outputs from MIMIC-IV. These outputs need review against PhysioNet's sharing terms before further publication. They are not reproduced in this README.

The models have not been rerun. Early prediction performance would need an evaluation that excludes later outcomes, restricts feature timestamps, and keeps each patient in a single training or evaluation group.

## Attribution and materials

The report lists Hossein Rajabi, Shami-uz Zaman, Eemeli Tepponen, Samantha Ly, and Kathleen Bajio. Individual responsibilities are not specified, so model work is attributed to the team.

- [Final report (PDF)](MATH_2130_Final_Report.pdf): cohort and features in section 2, evaluation in sections 4 and 5, limitations in section 6, and appendix figures.
- Original notebook: `MATH_2130_Final_Code.ipynb`. Steps 6, 16, and 18 to 20 support the feature-timing, retained-feature, and metric observations above. Its existing patient-level outputs need a sharing review before it is promoted as a public resource.

PhysioNet's source page states that derived datasets should be treated as sensitive and shared under the source agreement. The existing notebook's presence here does not establish permission to redistribute its outputs.
