# Hossein Rajabi

**Analytics Engineer Co-op at RBC · Data Science undergraduate at York University**

I work with Python, SQL, and PySpark to build data pipelines and analyse data. My interests include analytics engineering, data engineering, machine learning, and applied AI.

[LinkedIn](https://www.linkedin.com/in/hossein-rajabi-abb541243/) · [GitHub](https://github.com/Hosseinrjb) · [Email](mailto:hlotusr@gmail.com)

[Featured projects](#featured-projects) · [Experience](#professional-experience) · [Skills](#technical-skills) · [Education](#education-and-recognition)

## About me

I am studying Data Science (Business Stream) at York University and expect to graduate in April 2027. At RBC, I have worked on data pipelines, NLP, model evaluation, and Airflow logging.

This portfolio contains four case studies with reports, methods, results, and limitations. Some folders also contain original academic notebooks or code screenshots. These materials do not form complete, reproducible codebases. Employer code and data are not included.

## Featured projects

Results below are reported in the original materials and have not been independently reproduced. RMSE is root mean squared error, MAE is mean absolute error, CV is cross-validation, and AUC is the area under the ROC curve.

| Case study | Focus | Reported outcome | Explore |
| --- | --- | --- | --- |
| Movie Recommendation | Item-based collaborative filtering | K=50; five-fold CV RMSE 0.9406, MAE 0.7264 | [Case study](01_Movie_Recommendation_EECS_2502/) · [Report (PDF)](01_Movie_Recommendation_EECS_2502/EECS_2502_Final_Report.pdf) |
| Healthcare Analytics | ICU length-of-stay modelling | Random Forest MAE ≈2.21 days; exploratory result with leakage concerns | [Case study](02_Healthcare_Analytics_MATH_2130/) |
| Image Classification | Transfer learning versus a simple baseline | EfficientNetB0: 84.7% validation accuracy, 0.927 AUC | [Case study](03_Image_Classification_MATH_3333/) · [Report (PDF)](03_Image_Classification_MATH_3333/MATH_3333_Final_Report_and_Code.pdf) |
| Captive Insurance Feasibility | Research synthesis and financial scenarios | Preliminary cost estimates and a recommendation for detailed feasibility analysis | [Case study](04_Captive_Insurance_Feasibility_Study/) |

### Movie Recommendation

Objective: Predict movie ratings and generate personalized recommendations from MovieLens 1M.

Approach: We cleaned and explored ratings, built a sparse movie-by-user matrix, and tuned item-based KNN with cosine similarity through five-fold cross-validation. K=50 produced the lowest reported validation error among the tested settings. Ranking quality and cold-start behaviour remain unvalidated.

Tools: Python, pandas, NumPy, SciPy, scikit-learn, Matplotlib, Seaborn.

My contribution: Data preparation, exploratory analysis, model selection, and the initial report draft, as recorded in the team report.

### Healthcare Analytics

Objective: Explore ICU length-of-stay prediction for a narrow cohort of cervical spinal cord injuries in MIMIC-IV v2.2.

Approach: Our team joined clinical tables, summarized physiological measurements, log-transformed length of stay (LOS), and compared Lasso, Random Forest, and XGBoost. Random Forest had the lowest reported test MAE (≈2.21 days) on a 20-stay test split from a 97-stay cohort. The existing notebook retains outcome information and whole-stay event counts, so this result does not establish valid early prediction performance. See the case study for the evaluation limitations.

Tools: Python, pandas, Dask, scikit-learn, XGBoost, Matplotlib, Seaborn.

Context: Five-person academic team; individual responsibilities are not specified in the report.

### Image Classification

Objective: Classify outdoor-day images versus other scenes in an 800-image Columbia photographic/graphics subset.

Approach: I compared logistic regression on three RGB median features with ImageNet-pretrained EfficientNetB0. The report records accuracy of 84.7% and AUC of 0.927 for EfficientNetB0, versus 74.5% and 0.866 for the baseline. The sample is small. Code screenshots show that the evaluation set guided early stopping and learning-rate changes during both training stages, so these are not independent final test results.

Tools: Python, TensorFlow/Keras, statsmodels.

Context: Individual academic report with code and output screenshots.

### Captive Insurance Feasibility Study

Objective: Assess the feasibility of a Cayman Islands captive-insurance subsidiary for CIBC.

Approach: Our team reviewed industry practices, public cost benchmarks, and regulatory considerations to develop preliminary setup, operating, and capital scenarios. The team recommended a detailed feasibility study using internal loss and premium data. The reported costs are estimates, and savings were not measured.

Tools: Public-source research and financial scenario analysis. I used Excel for modelling, as listed in my résumé; the workbook is not included.

Context: Risk & Insurance Studies Centre / HAIIvVE 9 team project, January to May 2025.

## Professional experience

These highlights are based on my résumé.

### RBC: Analytics Engineer Co-op

*May 2026 to present*

- Engineered PySpark and SQL pipelines integrating 5 enterprise sources into a 55-column analytical dataset for recommendation use cases.
- Built a Python NLP pipeline to isolate client-attributed text and extract fund references and themes from 4,000+ meeting notes.
- Developed a schema-based synthetic data generator for Databricks migration testing without exposing production data.
- Implemented S3-backed log persistence for 10+ production Airflow DAGs to retain logs for debugging.
- Evaluated PCA for a risk model to assess the trade-off between model performance and SHAP computation.

### RBC: Data Analyst Co-op

*May to December 2025*

- Standardized legacy IT portfolio data using Excel and Power Query for migration to SAP LeanIX.
- Reconciled master datasets with 70+ columns, identifying missing keys, mismatches, and duplicates.
- Built a Power BI dashboard for verification recency and overdue items, and supported 100+ users through post-migration workflows.

### Risk & Insurance Studies Centre: Risk Analyst Intern

*January to May 2025*

Contributed research and financial scenario analysis to the captive-insurance case study linked above.

## Technical skills

The skills below are from my résumé. Each case study lists the tools used in that project.

| Area | Tools and methods |
| --- | --- |
| Programming and Data | Python · pandas · NumPy · SciPy · SQL · R · PySpark · Regex |
| Machine Learning and AI | scikit-learn · XGBoost · TensorFlow · PyTorch · SHAP · PCA · Feature engineering · NLP |
| Data Engineering and Cloud | Databricks · Airflow · Amazon S3 · Trino · Parquet · Git/GitHub |
| Analytics and Visualization | Power BI · Tableau · Excel/Power Query · Matplotlib · Seaborn · Statistics · A/B testing |

## Education and recognition

York University: BSc, Data Science (Business Stream)

September 2023 to April 2027 (expected) · GPA: 8.57/9.00 · Dean's Honour Roll

- Awards: RBC Elevate Scholarship · TELUS Student Bursary · York University OSOTF Science Award
- Leadership: VP Operations, Business & Data Analytics Association · Global Leader, York Science

Seneca College: Advanced Diploma, Business Administration, Financial Planning (Honours)

May 2021 to April 2023

## Contact

Interested in analytics engineering, data science, machine learning engineering, data engineering, and applied AI opportunities.

[LinkedIn](https://www.linkedin.com/in/hossein-rajabi-abb541243/) · [GitHub](https://github.com/Hosseinrjb) · [hlotusr@gmail.com](mailto:hlotusr@gmail.com)

## Materials and attribution

The original reports and supporting files are preserved. Project results were checked against these materials but were not independently reproduced. Each case study explains team contributions and evaluation limitations.

The movie and healthcare notebooks contain source-data excerpts and are not cleared for public sharing. The healthcare report and insurance PDFs are also on hold for review. Removing direct links does not restrict access to files already in the repository. See the [publication review](docs/PORTFOLIO_REVIEW.md) for the remaining decisions. No repository-wide licence has been added; source datasets and third-party materials retain their own terms.
