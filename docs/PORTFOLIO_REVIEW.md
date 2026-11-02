# Portfolio publication-readiness review

Review date: November 1, 2026. Branch: `docs/professional-portfolio`.

## Decision

**Not ready for publication in its current form.** Both notebooks contain source-data excerpts that are not cleared for unrestricted sharing. The insurance PDFs and healthcare report also need review. Safer README wording does not resolve problems in the original files.

The repository was already public when audited. The affected files and earlier copies may therefore already be accessible. This review did not change visibility, delete files, rewrite history, or publish anything. Choose a containment and remediation approach before any further publication. Making a repository private can limit further access but cannot recall existing downloads, forks, or cached copies.

## Scope and limits

Reviewed all 14 tracked files: seven Markdown files, five PDFs (82 pages), and two notebooks. Review covered PDF text, figures and screenshots, metadata, attachments, notebook source and saved outputs, and filenames and document/notebook blobs reachable in the local clone's Git history. Notebooks were not executed. Original PDFs and notebooks remain byte-for-byte identical to `main`.

No employer code, internal datasets, obvious credential literals, embedded PDF files, or confidential-use markings were found in the current files reviewed. This is a content review, not proof of ownership, consent, or permission to redistribute. No patient values or MovieLens source rows were copied into Markdown.

The local history contains nine distinct PDF/notebook blobs. These include the current originals under earlier paths, one legacy image-analysis notebook, and a malformed historical healthcare PDF. No readable content could be established for the malformed file. Remote caches, forks, downloads, and refs absent from this clone were not inspected.

## Issues and decisions

| Issue | Concern in plain language | Affected files | Action and status |
| --- | --- | --- | --- |
| Existing code availability | The original repository contains two notebooks and code screenshots, despite the initial description of documentation-only projects | READMEs and original files | Resolved in documentation: inventories acknowledge existing code without promising reproducibility. Neither notebook is cleared for publication as-is. |
| Healthcare leakage | Some model inputs contain information from later in the stay, which would be unavailable when making an early prediction | Healthcare notebook and report; portfolio summaries | Documentation corrected. Retained outcomes, whole-stay counts, and evaluation limitations are explicit. Original methodology and reported scores remain unchanged and unvalidated. |
| Healthcare patient-level outputs | Saved outputs reproduce restricted source or derived records, even though MIMIC uses de-identified IDs and shifted dates | Healthcare notebook and historical copies; sharing statements in Markdown | Publication blocker. Do not share the original notebook as-is. Direct links removed; no records copied. Decide how to preserve the original privately and remove restricted public content and historical copies. |
| Healthcare report figures | The report has no raw patient table found, but includes individual-observation plots and very small groups. Its early-window description also conflicts with the notebook | Healthcare report and its README | Hold for disclosure, methodology, and coauthor review. The report link was removed, but the file remains accessible in the repository. A text summary alone does not clear its figures. |
| Healthcare attribution | Five people are credited, but individual tasks are not documented | Healthcare README and report | Resolved by attributing model work to the team. Personal task details are optional and require confirmation before being added. |
| MovieLens source excerpts | The notebook prints rating and demographic rows, including ZIP codes. Absent dataset files do not mean no data is redistributed | Movie notebook and historical copies; movie README | New publication blocker. The official licence requires separate redistribution permission. Removed the notebook link and corrected the dataset-availability statement. Decide on permission or a reviewed public version without source-data excerpts. |
| Movie methods and filtering | Matrix factorization is future work, and genre analysis does not establish an evaluated filtering improvement | Portfolio/movie READMEs; résumé wording | Resolved in documentation: only item-based KNN and supported evaluation are claimed. Do not add filtering or completed matrix-factorization claims without evidence. |
| Image dataset identity | The project classifies outdoor-day scenes, not faces. The full Columbia resource has multiple component sets | Image report; READMEs; résumé | Public wording corrected and official dataset page linked. The exact component, file list, and label provenance remain unverified. No missing dataset details were invented. |
| Image evaluation | The evaluation images were used during training decisions, so their scores are not an independent test | Image report screenshots and narrative; public summaries | Resolved in documentation: metrics are reported validation results, not independently reproduced final test results. Original report retains its test terminology. |
| Image training details | The previous review had not established early stopping from the report narrative | Image README and review notes | Resolved by inspecting PDF screenshots: early stopping and learning-rate reduction are present. Additional feature standardization is not established and is not claimed. |
| Insurance bibliography | Some references are incomplete or inconsistent, so the paper's support cannot be assumed reliable | White paper and insurance README | Placeholder-reference text removed from public-facing summaries. References remain unresolved in the original PDF. Hold the paper pending source correction; do not invent replacements. |
| Insurance ranking/source count | Neither PDF confirms the résumé's first-place or 40+ sources statements | Insurance README and review notes | Excluded from promotional summaries. These remain unverified résumé claims, not evidence-backed project results. Confirm them before adding them to the published portfolio. |
| Insurance costs and regulation | Costs are estimates, savings were not measured, and regulatory statements have not been verified as current | Both insurance PDFs and public summaries | README qualifies every estimate and avoids capital-relief or realized-savings claims. Original PDFs still need factual review, particularly the infographic's stronger wording. |
| Insurance workbook | The résumé says Excel was used, but no workbook is available to check | Insurance/root READMEs | Resolved by attributing Excel use to the supplied résumé and stating the workbook is absent. Sharing a workbook is optional and requires permission first. |
| Headshots, branding, and coauthored materials | Being named in a project does not establish consent to redistribute a photograph or ownership of the report/design | Insurance infographic, white paper, movie and healthcare reports/code | Confirm project public-sharing permission and relevant coauthor, photograph, graphic, and branding rights. The infographic contains identifiable team and mentor headshots. No blanket licence added. |
| RBC/public résumé information | The résumé supports the experience summaries but does not independently prove employer permission to disclose them | Root and profile READMEs | Only supplied résumé information is used. No extra internal logic, rules, records, or source code was added. Confirm that the selected wording and figures are suitable for public disclosure. |
| Education and recognition | Education, GPA, awards, and leadership are supplied résumé information | Root and profile READMEs | Retained as supplied, without claiming external verification. Confirm they are current; no source documents need to be uploaded publicly. |

## Healthcare evidence

Notebook cell numbers below are 1-based positions in the saved JSON cell list, not execution counters.

- Cells 6 and 18 print patient/source tables and the merged cohort, including de-identified IDs, shifted dates, and clinical or admission information. Cell 44 also prints derived modelling rows. Do not publish these outputs.
- Cell 14 filters events by stay ID and counts them across the whole stay. It does not apply the early-window filter used for chart and lab measurements.
- Cell 44 retains `hospital_expire_flag` and `discharge_location` in the modelling data. These are later outcomes, not early prediction inputs.
- Feature selection follows exploration of the full cohort. Cell 47 uses a random stay-level split, with no patient-grouping mechanism. The saved cohort has 89 patients, 90 admissions, and 97 stays; overlap of patients between partitions was not independently recalculated.
- The saved test set has 20 stays, with 77 used for training. RF MAE 2.211 days and RMSE 3.839 days match saved outputs. Their presence is verified; their validity as early prediction performance is not.
- The report's description of first-day event counts conflicts with the notebook and some figure labels. Correcting the README does not correct the report.

[PhysioNet's MIMIC-IV v2.2 page](https://physionet.org/content/mimiciv/2.2/) describes the de-identification and source-sharing requirements. The [credentialed data licence](https://physionet.org/about/licenses/physionet-credentialed-health-data-license-150/) prohibits sharing access to restricted data. De-identification is not permission for unrestricted redistribution. A general user approval cannot replace source permission.

## Original-file publication inventory

| Original file | Decision | Reason |
| --- | --- | --- |
| `01_Movie_Recommendation_EECS_2502/EECS_2502_Final_Code.ipynb` | Do not publish as-is | Cells 5 and 6 include source-data rows; cell 5 includes demographics and ZIP codes. The [MovieLens 1M licence](https://files.grouplens.org/datasets/movielens/ml-1m-README.txt) requires separate redistribution permission. |
| `01_Movie_Recommendation_EECS_2502/EECS_2502_Final_Report.pdf` | No source-row blocker found; sharing permission still needed | Reviewed text and figures contain analysis, metrics, recommendation examples, and coauthor attribution. Confirm coauthor permission and any figure/source rights. |
| `02_Healthcare_Analytics_MATH_2130/MATH_2130_Final_Code.ipynb` | Do not publish as-is | Restricted patient-level outputs. Removing its README link does not remove the file or prior copies. |
| `02_Healthcare_Analytics_MATH_2130/MATH_2130_Final_Report.pdf` | Hold | Individual-observation figures, small groups, uncorrected methodology wording, and coauthor-sharing questions. No raw patient table or direct identifying field was found in its reviewed text/figures. |
| `03_Image_Classification_MATH_3333/MATH_3333_Final_Report_and_Code.pdf` | No sensitive source-row blocker found; retain evaluation caveat | Code/output screenshots support the metrics and training description. No source photographs were found in the reviewed pages. Exact sample provenance and original test terminology remain limitations. |
| `04_Captive_Insurance_Feasibility_Study/White_Paper_CIBC.pdf` | Hold | Unresolved bibliography, historical financial/regulatory claims, institutional branding, and team-sharing permission. |
| `04_Captive_Insurance_Feasibility_Study/HAIIVVE9_Infographic_Team7.pdf` | Hold | Headshots, logos, and other graphics need sharing permission; savings and regulatory wording needs review. No confidential company records were found. |

The seven Markdown files contain summaries, personal information supplied for public contact, technical field names, and review notes. They contain no copied patient records, MovieLens source rows, invented references, or additional confidential RBC material found in this review. They are suitable documentation drafts, but cannot make the repository safe while the held originals and history remain present.

## History and existing public exposure

The same notebook contents appear in earlier commits under different names. Healthcare paths include `MATH2130-Final-Code.ipynb` and `MATH_2130_Final_Code.ipynb`; movie paths include `EECS2502-Final-Code.ipynb`, `EECS_2502_Final_Code.ipynb`, and `Movie_Recco_1m_Analysis.ipynb`. Original reports also appear under earlier names. Deleting only the current files, adding `.gitignore`, or hiding links would leave these copies reachable through history.

Choose how to preserve the originals outside the public repository and whether to clean existing history or prepare a separately reviewed documentation-only publication. Any history rewrite, visibility change, deletion, or new publication requires a separate decision. Existing forks, cached views, or downloads may need additional handling; none were removed or contacted here.

## Safe documentation corrections completed

- Corrected MovieLens data availability and removed the original notebook's promotional link.
- Kept leakage, reported metrics, and data restrictions explicit in healthcare summaries; removed direct links to held healthcare files.
- Confirmed image early stopping from screenshots and explained validation-set reuse. Added the official dataset source without asserting a verified subset manifest.
- Removed quoted placeholder-reference examples and direct links to held insurance PDFs. Unverified ranking and source-count claims remain excluded from promotional summaries.
- Kept Excel, RBC, education, and recognition statements tied to the supplied résumé. No extra employer information or unsupported personal contributions were added.
- Preserved all original project files. Only the seven Markdown files were edited.

## Verification

Original reports and notebook outputs were inspected without executing implementation code. PDF checks included searchable text, rendered figures/screenshots, metadata, annotations, embedded attachments, and forms. No embedded PDF attachments or forms were found. Code-pattern screening found no obvious credential literals; it is not a guarantee that every possible secret format was excluded.

All seven Markdown files rendered, and all 20 remaining local links and heading anchors resolved after corrections. Relative navigation and exact file paths were also checked. Original PDF/notebook bytes were compared with `main`. Link removal is documented as a presentation change, never an access-control measure. No em or en dashes were introduced into Markdown.

External source checks loaded the PhysioNet licence and guidance, official Columbia dataset page, and MovieLens licence. LinkedIn and some GitHub browser requests were blocked or unavailable; the GroupLens landing page timed out, but the official dataset licence loaded. Those retrieval failures do not by themselves establish broken links.

## GitHub settings and profile actions


These are suggested settings for use only after the publication holds below are resolved. Changes remain on local branch `docs/professional-portfolio`. Nothing was pushed, merged, or published; visibility, account settings, and Git history were not changed.

### Repository About section

Description:

> Hossein Rajabi | York University Data Science student and RBC Analytics Engineer Co-op. Case studies in machine learning, healthcare analytics, and financial research.

Website: `https://www.linkedin.com/in/hossein-rajabi-abb541243/`

A separate website is unnecessary for this documentation upgrade. The GitHub repository remains the portfolio landing page.

Suggested topics: `portfolio`, `data-science`, `analytics-engineering`, `machine-learning`, `data-engineering`, `recommender-systems`, `healthcare-analytics`, `transfer-learning`, `financial-analysis`, `python`, `sql`.

Topics describe the portfolio and career focus; individual case studies identify actual project tooling.

### Profile fields

Bio:

> Data Science @ York University | Analytics Engineer Co-op @ RBC | Analytics engineering, machine learning, and data engineering

Company: `RBC` (if appropriate for your public profile)

Website: `https://github.com/Hosseinrjb/hossein-portfolio`

Social link: `https://www.linkedin.com/in/hossein-rajabi-abb541243/`

The README already links `hlotusr@gmail.com`; publishing it as the account's public email is optional.

### Profile README

Create a public repository named exactly `Hosseinrjb/Hosseinrjb`, then copy [PROFILE_README.md](PROFILE_README.md) into its root as `README.md`. [GitHub's profile README documentation](https://docs.github.com/en/account-and-profile/how-tos/profile-customization/managing-your-profile-readme) confirms these display requirements.

The draft uses `main` links for the eventual merged pages. Do not activate it while the repository remains on publication hold.

### Pins

Pin `hossein-portfolio` first. It is the only public repository returned by the account inventory. Keep all four case studies in this repository; do not create empty project repositories for additional pins. The profile README repository serves the profile introduction and does not need a pin. Future pins should be substantive, owned work with reports or code that reviewers can inspect.

### Rights and licensing

Do not add MIT, Apache, or another permissive blanket licence until ownership and redistribution rights are confirmed for co-authored reports, screenshots, and third-party figures. Dataset access terms remain separate. If licensing is later appropriate, scope it to material whose rights you control.
