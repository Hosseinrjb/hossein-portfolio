# Image Classification

**Outdoor-day scene classification · EfficientNetB0 transfer learning · MATH 3333 · March 2025**

[Portfolio](../README.md) · [Report and screenshots (PDF, 12 pages)](MATH_3333_Final_Report_and_Code.pdf)

## Overview and problem

In this individual project, I compared logistic regression with EfficientNetB0 to classify outdoor-day images versus other scenes. The baseline uses three colour features, while EfficientNetB0 learns image features through transfer learning.

Available materials: A report with embedded code and output screenshots. No standalone notebook, dataset, trained model, or executable environment is supplied. Reported measurements have not been independently reproduced.

## Dataset and tools

The report identifies an 800-image subset of the Columbia Photographic Images and Photorealistic Computer Graphics Dataset, with approximately 405 outdoor-day images and 395 other images. The task is binary scene classification, not face classification.

The report cites Ng, Chang, Hsu, and Pepeljugoski (2005), ADVENT Technical Report #205-2004-5. The exact list of images and how their labels were assigned are not documented well enough to reproduce the subset.

Tools supported by the report: Python, TensorFlow/Keras, NumPy, and statsmodels (`GLM`, binomial family). The report uses statsmodels for the logistic baseline.

## Methodology

1. Label outdoor-day images as 1 and all other categories as 0.
2. Use an approximately 50/50 random training/evaluation split with seed 42.
3. Fit logistic regression using the median red, green, and blue intensities per image.
4. Resize images to 224 × 224 for ImageNet-pretrained EfficientNetB0.
5. Add global average pooling, a 128-unit dense layer, dropout, and a sigmoid output.
6. Train the classification head with the base frozen, then fine-tune the top 20 base layers at a smaller learning rate. The report describes augmentation with shifts, rotations, and flips.
7. Compare accuracy, AUC, sensitivity, and specificity.

## Reported results

| Model | Training accuracy | Evaluation accuracy | AUC | Sensitivity | Specificity |
| --- | --- | --- | --- | --- | --- |
| Logistic regression, RGB medians | 71.8% | 74.5% | 0.866 | 0.386 | 0.955 |
| EfficientNetB0 transfer learning | 94.6% | 84.7% | 0.927 | 0.862 | 0.838 |

The report labels these as test results but also calls the evaluation set “validation (test).” A separate, untouched test set is not clearly documented. These values are reported results, not independently reproduced measurements.

## Key insights

- EfficientNetB0 improves reported accuracy by 10.2 percentage points over the three-feature baseline on the documented evaluation.
- The baseline has high specificity but low sensitivity; accuracy alone hides that imbalance in error types.
- EfficientNetB0's training/evaluation gap suggests overfitting despite augmentation and dropout.

## Limitations

- Only 800 images and a single random split; no external validation or confidence intervals are reported.
- Validation/test terminology leaves the independence of final evaluation unclear.
- Exact subset selection, preprocessing details, and screenshot code require review before reproduction.
- The résumé mentions standardization and early stopping; the report narrative does not establish enough detail to feature those claims here.
- The suggested 10 × 10 grid with SVM/Random Forest was not tested, so no measured advantage over that approach is claimed.
- Findings apply to this binary scene task, not general image forensics or face recognition.

## Attribution and available material

I am the sole author listed on the report.

[Final report and code/output screenshots (PDF)](MATH_3333_Final_Report_and_Code.pdf) contains dataset description (section 3), methodology (section 4), results (section 5), conclusions (section 6), references, and a screenshot appendix. PDF pages 3 to 8 contain searchable text and results. The appendix contains code screenshots rather than executable source, which also limits accessibility.

The original PDF is preserved. No licence has been added for the report or source images.
