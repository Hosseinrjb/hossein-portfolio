# Portfolio audit and publication notes

Review date: **November 1, 2026**. Scope: public GitHub profile, public repository list and metadata, all 12 tracked repository files at the original `main`, all five PDFs (82 pages total), and both existing notebooks (source and saved outputs). Notebooks were read, not executed. The supplied résumé is the source for personal experience, education, awards, and skills.

## Audit: before and after

| Area | Before | Change prepared on this branch |
| --- | --- | --- |
| Professional identity | Generic welcome; no current role, education, skills, or contact details | Role and degree headline, contact links, organized skills, concise experience and recognition |
| Recruiter navigation | Four unlinked project bullets | Linked project index, focused summaries, direct report links, and return links |
| Movie scope | Claims matrix factorization and user/item model comparisons | Corrected to item-based KNN; separates future work and team contributions |
| Healthcare clarity | Generic patient-outcome description | Exact cohort, methods, metric scales, 20-stay test split, and substantive leakage limitations |
| Image accuracy | Generic CNN description; résumé calls it a face dataset | Corrected to outdoor-day scene classification and documented baseline |
| Insurance credibility | Minimal feasibility description | Public-source scope, cost assumptions, team attribution, missing workbook, and citation issues |
| Artifact availability | Broad invitation to explore “code”; no boundaries | Case-study framing with precise inventories; original notebooks/screenshots acknowledged |
| Public profile | Name present; bio, company, website, and public email fields empty | Standalone profile README draft and suggested profile fields below |
| Repository metadata | Description, homepage, topics, and license absent | Suggested metadata below; no license added without confirmed rights |

The public profile page shows the portfolio under “Popular repositories”; no pinned section was visible in the fetched page. Some dynamic profile sections failed to load, so those sections were not treated as verified.

The public repository list contains only `hossein-portfolio`; no public `Hosseinrjb/Hosseinrjb` repository was found. GitHub's language metadata labels the portfolio Jupyter Notebook, which reflects the existing artifacts and does not demonstrate a packaged or reproducible application.

## Files changed

Modified:

- [Portfolio landing page](../README.md)
- [Movie case study](../01_Movie_Recommendation_EECS_2502/README.md)
- [Healthcare case study](../02_Healthcare_Analytics_MATH_2130/README.md)
- [Image case study](../03_Image_Classification_MATH_3333/README.md)
- [Insurance case study](../04_Captive_Insurance_Feasibility_Study/README.md)

Added:

- [Profile README draft](PROFILE_README.md), intended for a separate profile repository
- This audit and publication guide

No folders were renamed, no original report or notebook was edited or deleted, and no implementation, dataset, model, generic activity file, or license was created.

## Evidence and claims requiring review

| Item | Evidence and treatment | Owner follow-up |
| --- | --- | --- |
| Existing code artifacts | Two `.ipynb` files already contain code and outputs; image PDF contains code screenshots | Reconcile the requested “no public code” description with existing contents; no implementation was generated |
| Healthcare result | Report and saved outputs agree on RF MAE 2.211 days, but model includes outcome/discharge information and whole-stay counts | Review feature timing, leakage, patient grouping, and full-cohort feature selection before describing results as prospective performance |
| Healthcare public outputs | Notebook displays patient-level source/derived rows, including identifiers and dates | Review against [PhysioNet sharing guidance](https://physionet.org/content/mimiciv/2.2/) before promoting or further publishing artifacts; this branch preserves the file and does not reproduce those rows |
| Healthcare attribution | Five authors listed; no individual task breakdown | Confirm personal contribution if a more specific statement is desired |
| Image dataset | Report describes Columbia photographic/graphics scene data, not faces | Correct résumé wording; verify exact subset provenance and evaluation split |
| Image training details | Narrative supports augmentation/dropout and staged fine-tuning; résumé adds early stopping/standardization | Verify screenshot source/training records before featuring those additional details |
| Movie filtering | Genre/popularity EDA is present; validated filtering improvement is not established | Confirm filtering claim before adding it; matrix factorization is future work |
| Insurance sources | Multi-page bibliography includes placeholders and inconsistent citations | Authenticate sources, resolve duplicates/metadata, and verify support for each material claim before revising the original paper |
| Insurance recognition | “40+ sources” and “first of seven teams” are résumé statements, not independently established by PDFs | Provide an award/result reference or confirm the claim; excluded from promotional summaries pending review |
| Insurance workbook | Excel modeling described in résumé; no workbook supplied | Confirm personal role and availability/ownership before sharing any workbook |
| RBC accomplishments | User-supplied résumé, not publicly verified artifacts | Confirm metrics, current dates, and wording are approved for public disclosure; no internal segmentation rules, datasets, or implementation added |
| Education and recognition | User-supplied résumé only | Confirm GPA, expected graduation, award names, leadership titles, and dates are current |

Public résumé summaries retain selected quantitative accomplishments while omitting internal segmentation thresholds, business logic, and the precise risk-model performance tradeoff. No confidential employer source material was accessed.

## GitHub settings and profile actions

Changes remain on local branch **`docs/professional-portfolio`** for review. Nothing was pushed, merged, or published, and account settings were not modified.

### Repository About section

**Description:**

> Hossein Rajabi | York University Data Science student and RBC Analytics Engineer Co-op. Case studies in machine learning, healthcare analytics, and financial research.

**Website:** `https://www.linkedin.com/in/hossein-rajabi-abb541243/`

A separate website is unnecessary for this documentation upgrade. The GitHub repository remains the portfolio landing page.

**Suggested topics:** `portfolio`, `data-science`, `analytics-engineering`, `machine-learning`, `data-engineering`, `recommender-systems`, `healthcare-analytics`, `transfer-learning`, `financial-analysis`, `python`, `sql`.

Topics describe the portfolio and career focus; individual case studies identify actual project tooling.

### Profile fields

**Bio:**

> Data Science @ York University | Analytics Engineer Co-op @ RBC | Analytics engineering, machine learning, and data engineering

**Company:** `RBC` (if appropriate for your public profile)

**Website:** `https://github.com/Hosseinrjb/hossein-portfolio`

**Social link:** `https://www.linkedin.com/in/hossein-rajabi-abb541243/`

The README already links `hlotusr@gmail.com`; publishing it as the account's public email is optional.

### Profile README

Create a public repository named exactly **`Hosseinrjb/Hosseinrjb`**, then copy [PROFILE_README.md](PROFILE_README.md) into its root as **`README.md`**. [GitHub's profile README documentation](https://docs.github.com/en/account-and-profile/how-tos/profile-customization/managing-your-profile-readme) confirms these display requirements.

The draft uses `main` links for their eventual merged destinations. Review and merge the portfolio documentation before activating the profile draft so its project links show the upgraded pages.

### Pins

Pin **`hossein-portfolio`** first. It is the only public repository returned by the account inventory. Keep all four case studies in this repository; do not create empty project repositories for additional pins. The profile README repository serves the profile introduction and does not need a pin. Future pins should be substantive, owned work with inspectable artifacts.

### Rights and licensing

Do not add MIT, Apache, or another permissive blanket license until ownership and redistribution rights are confirmed for coauthored reports, screenshots, and third-party figures. Dataset access terms remain separate. If licensing is later appropriate, scope it to material whose rights you control.

## Verification

- Read every tracked README, all five PDFs, and both notebook sources/outputs. Precise project claims were cross-checked against report sections and saved outputs; no experiment was rerun.
- Rendered Markdown using a local parser with tables and heading anchors, then checked generated HTML structure. This is a structural check, not a visual browser inspection of GitHub's renderer.
- Checked every local Markdown link and same-page anchor, including report filenames with exact case; all resolved after edits.
- Compared original PDFs and notebooks byte-for-byte with `HEAD`; all unchanged.
- Reviewed heading hierarchy, table headers, link labels, and plain-text alternatives to visual results. No decorative images, widgets, or external badge dependencies were added.
- All PDFs expose searchable narrative text. Image-classification appendix code is raster screenshots, which remains less accessible; README text supplies methods and results without altering the source PDF. A full PDF accessibility/tagging audit was not performed.
- Public GitHub profile/repository API requests succeeded. PhysioNet and GitHub guidance pages loaded. LinkedIn returned HTTP 999 (automated access restricted), so its destination content could not be verified. The MovieLens source URL is cited by the report; automated retrieval timed out and should be checked manually.
- No original README contained clickable project-file links; this was primarily a missing-navigation issue. No missing source files were found among the original file lists.

## Recommended next improvements

1. Resolve the healthcare output-sharing issue and evaluation caveats before highlighting that case study more widely. If removal/redaction is needed, handle it separately with a deliberate source-preservation and Git-history plan.
2. Review and correct the insurance bibliography against primary sources. Update historical regulatory claims only after specialist/source verification.
3. Confirm personal contributions and competition recognition, then add concise attribution where evidence is available.
4. If you later choose to publish executable academic work, first confirm teammate rights and data permissions, then document dependencies and evaluation. This task intentionally adds no implementation.
5. Keep the current role, graduation date, GPA, and available-for-work wording current as your experience changes.
