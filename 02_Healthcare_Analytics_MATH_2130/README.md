# Healthcare Analytics

**Exploratory ICU length-of-stay modelling · MATH 2130 · Winter 2025**

[Portfolio](../README.md)

## Overview and problem

This team study explores intensive care unit (ICU) length of stay (LOS) for patients with acute traumatic cervical spinal cord injuries. It compares Lasso, Random Forest, and XGBoost and examines how preprocessing, feature timing, and a small cohort affect interpretation.

Publication status: The original notebook must not be shared publicly as-is. It contains restricted patient-level source and derived records in saved outputs. The report is also on hold for a figure-sharing and methodology review. Both files remain unchanged; this notice and removal of links do not restrict access to files already in GitHub.

This is an exploratory study, not a validated clinical system. The original report is 21 pages, and its methods and results are summarised below with corrections based on the notebook.

## Dataset and tools

The report identifies MIMIC-IV v2.2 and a cohort of 97 ICU stays selected using ICD-9 prefix `8060`. Saved notebook outputs identify 89 patients and 90 admissions, so stays should not be treated as 97 independent patients.

Source: Johnson et al., [MIMIC-IV v2.2 on PhysioNet](https://physionet.org/content/mimiciv/2.2/), DOI: 10.13026/6mm1-ek67. Access is credentialed and subject to PhysioNet's data-use terms. Full source tables are absent, but saved notebook outputs contain patient-level excerpts. De-identified source IDs and shifted dates are still restricted data; their presence does not make the records safe to redistribute.

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

The models have not been rerun. These findings establish that the saved evaluation includes information unavailable at the intended prediction time; they do not establish how much each issue affected the reported error. Early prediction performance would need an evaluation that excludes later outcomes, restricts feature timestamps, and keeps each patient in a single training or evaluation group.

## Attribution and materials

The report lists Hossein Rajabi, Shami-uz Zaman, Eemeli Tepponen, Samantha Ly, and Kathleen Bajio. Individual responsibilities are not specified, so model work is attributed to the team.

- `MATH_2130_Final_Report.pdf`: cohort and features in section 2, evaluation in sections 4 and 5, and limitations in section 6. Its early-window description conflicts with whole-stay counts in the notebook. Appendix plots include individual observations and small groups, which need a disclosure review before sharing.
- `MATH_2130_Final_Code.ipynb`: raw or derived patient rows appear in saved outputs in cells 6, 18, and 44 (1-based notebook cell positions). Cell 14 counts whole-stay events; cell 44 constructs the feature matrix; cell 47 splits by stay. Steps 18 to 20 contain the reported evaluation. No patient values are reproduced here.

[PhysioNet's MIMIC-IV guidance](https://physionet.org/content/mimiciv/2.2/) treats derived datasets as sensitive. Its [credentialed data licence](https://physionet.org/about/licenses/physionet-credentialed-health-data-license-150/) prohibits sharing restricted-data access with others. Preserve the original privately and decide how to remove restricted outputs from the public repository and its history. No files or history have been removed in this review.
