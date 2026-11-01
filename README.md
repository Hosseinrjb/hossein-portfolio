# Hossein Rajabi

**Analytics Engineer Co-op at RBC · Data Science undergraduate at York University**

I work with data pipelines, predictive models, and analytics to turn complex data into useful decisions. My interests span analytics engineering, data engineering, machine learning, and applied AI.

[LinkedIn](https://www.linkedin.com/in/hossein-rajabi-abb541243/) · [GitHub](https://github.com/Hosseinrjb) · [Email](mailto:hlotusr@gmail.com)

[Featured projects](#featured-projects) · [Experience](#professional-experience) · [Skills](#technical-skills) · [Education](#education-and-recognition)

## About me

I am pursuing a BSc in Data Science (Business Stream) at York University, with expected graduation in April 2027. At RBC, my experience includes PySpark and SQL pipelines, NLP, model evaluation, and workflow observability. I enjoy connecting statistical reasoning with reliable data systems and clear communication.

This portfolio presents four **documented case studies**. Start with the summaries below, then explore each project's methodology, reported results, and limitations. Original academic notebooks and code screenshots exist in some folders; these are supporting artifacts, with no claim of a complete, reproducible public codebase. Employer systems and data are not included.

## Featured projects

| Case study | Focus | Reported outcome | Explore |
| --- | --- | --- | --- |
| **Movie Recommendation** | Item-based collaborative filtering | K=50; five-fold CV RMSE 0.9406, MAE 0.7264 | [Case study](01_Movie_Recommendation_EECS_2502/) · [Report (PDF)](01_Movie_Recommendation_EECS_2502/EECS_2502_Final_Report.pdf) |
| **Healthcare Analytics** | ICU length-of-stay modeling | Random Forest MAE ≈2.21 days; exploratory result with leakage concerns | [Case study](02_Healthcare_Analytics_MATH_2130/) · [Report (PDF)](02_Healthcare_Analytics_MATH_2130/MATH_2130_Final_Report.pdf) |
| **Image Classification** | Transfer learning versus a simple baseline | EfficientNetB0: 84.7% accuracy, 0.927 AUC | [Case study](03_Image_Classification_MATH_3333/) · [Report (PDF)](03_Image_Classification_MATH_3333/MATH_3333_Final_Report_and_Code.pdf) |
| **Captive Insurance Feasibility** | Research synthesis and financial scenarios | Preliminary cost estimates and a recommendation for detailed feasibility analysis | [Case study](04_Captive_Insurance_Feasibility_Study/) · [White paper (PDF)](04_Captive_Insurance_Feasibility_Study/White_Paper_CIBC.pdf) |

### Movie Recommendation

**Objective:** Predict movie ratings and generate personalized recommendations from MovieLens 1M.

**Approach:** Clean and explore ratings, construct a sparse movie–user matrix, and tune item-based KNN with cosine similarity through five-fold cross-validation. K=50 produced the lowest reported validation error among the tested settings. Ranking quality and cold-start behavior remain unvalidated.

**Tools:** Python, pandas, NumPy, SciPy, scikit-learn, Matplotlib, Seaborn.

**My contribution:** Data preparation, exploratory analysis, model selection, and the initial report draft, as recorded in the team report.

### Healthcare Analytics

**Objective:** Explore ICU length-of-stay prediction for a narrow cohort of cervical spinal cord injuries in MIMIC-IV v2.2.

**Approach:** Join clinical tables, summarize physiological measurements, transform skewed LOS, and compare Lasso, Random Forest, and XGBoost. Random Forest had the lowest reported test MAE (≈2.21 days) on a 20-stay test split from a 97-stay cohort. Existing artifacts retain outcome information and whole-stay event counts, so this result does **not** establish valid early prediction performance. See the case study for the evaluation limitations.

**Tools:** Python, pandas, Dask, scikit-learn, XGBoost, Matplotlib, Seaborn.

**Context:** Five-person academic team; individual responsibilities are not specified in the report.

### Image Classification

**Objective:** Classify outdoor-day images versus other scenes in an 800-image Columbia photographic/graphics subset.

**Approach:** Compare logistic regression on three RGB median features with ImageNet-pretrained EfficientNetB0. The report records accuracy of 84.7% and AUC of 0.927 for EfficientNetB0, versus 74.5% and 0.866 for the baseline. A small sample and shared validation/test terminology limit interpretation.

**Tools:** Python, TensorFlow/Keras, statsmodels.

**Context:** Individual academic report with code and output screenshots.

### Captive Insurance Feasibility Study

**Objective:** Assess the feasibility of a Cayman Islands captive-insurance subsidiary for CIBC.

**Approach:** Review industry practices, public cost benchmarks, and regulatory considerations; develop preliminary setup, operating, and capital scenarios. The team recommended a detailed feasibility study using internal loss and premium data. The reported costs are estimates, and savings were not measured.

**Tools:** Public-source research and financial scenario analysis; Excel modeling is described in my résumé, but the workbook is not included.

**Context:** Risk & Insurance Studies Centre / HAIIvVE 9 team project, January–May 2025.

## Professional experience

The experience highlights below are drawn from my résumé; this repository contains no employer implementation artifacts.

### RBC — Analytics Engineer Co-op

*May 2026–present*

- Engineered PySpark and SQL pipelines integrating **5 enterprise sources** into a **55-column analytical dataset** for recommendation use cases.
- Built a Python NLP pipeline to isolate client-attributed text and extract fund references and themes from **4,000+ meeting notes**.
- Developed a schema-based synthetic data generator for Databricks migration testing without exposing production data.
- Implemented S3-backed log persistence for **10+ production Airflow DAGs** to support historical debugging.
- Evaluated dimensionality reduction for a high-dimensional risk model, examining the tradeoff between model performance and explanation cost.

### RBC — Data Analyst Co-op

*May–December 2025*

- Standardized legacy IT portfolio data using Excel and Power Query for migration to SAP LeanIX.
- Reconciled master datasets with **70+ columns**, identifying missing keys, mismatches, and duplicates.
- Built a Power BI dashboard for verification recency and overdue items, and supported **100+ users** through post-migration workflows.

### Risk & Insurance Studies Centre — Risk Analyst Intern

*January–May 2025*

Contributed research and financial scenario analysis to the captive-insurance case study linked above.

## Technical skills

Skills listed from my résumé; individual case studies identify the tools supported by their materials.

| Area | Tools and methods |
| --- | --- |
| **Programming and Data** | Python · pandas · NumPy · SciPy · SQL · R · PySpark · Regex |
| **Machine Learning and AI** | scikit-learn · XGBoost · TensorFlow · PyTorch · SHAP · PCA · Feature engineering · NLP |
| **Data Engineering and Cloud** | Databricks · Airflow · Amazon S3 · Trino · Parquet · Git/GitHub |
| **Analytics and Visualization** | Power BI · Tableau · Excel/Power Query · Matplotlib · Seaborn · Statistics · A/B testing |

## Education and recognition

**York University — BSc, Data Science (Business Stream)**

September 2023–April 2027 (expected) · GPA: **8.57/9.00** · **Dean's Honour Roll**

- **Awards:** RBC Elevate Scholarship · TELUS Student Bursary · York University OSOTF Science Award
- **Leadership:** VP Operations, Business & Data Analytics Association · Global Leader, York Science

**Seneca College — Advanced Diploma, Business Administration – Financial Planning (Honours)**

May 2021–April 2023

## Contact

Interested in analytics engineering, data science, machine learning engineering, data engineering, and applied AI opportunities.

[LinkedIn](https://www.linkedin.com/in/hossein-rajabi-abb541243/) · [GitHub](https://github.com/Hosseinrjb) · [hlotusr@gmail.com](mailto:hlotusr@gmail.com)

## Materials and attribution

Original reports and supporting artifacts remain in their existing folders. Results are transcribed from those materials, not independently reproduced. Team attribution and evaluation caveats appear in each case study. No repository-wide license is granted; source datasets and third-party materials retain their own terms.
