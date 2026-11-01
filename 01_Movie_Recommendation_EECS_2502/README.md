# Movie Recommendation

**Item-based collaborative filtering · EECS 2502 · Winter 2025**

[Portfolio](../README.md) · [Report (PDF, 22 pages)](EECS_2502_Final_Report.pdf)

## Overview and problem

How can historical ratings help users discover movies they have not seen? This academic team project explores an item-based nearest-neighbor recommender, from data preparation to rating prediction and example recommendation lists.

**Availability:** A documented case study with an original academic notebook as supporting material. No dataset, packaged environment, deployed service, or reproducibility guarantee is provided.

## Dataset and tools

The report uses **MovieLens 1M**: 1,000,209 ratings from 6,040 users, 3,883 movie records, and 3,706 movies with ratings. Ratings use a 1–5 scale. The dataset is not bundled.

Source: [GroupLens MovieLens 1M](https://grouplens.org/datasets/movielens/1m/), cited in the report. Dataset use remains subject to its source terms.

**Tools:** Python, pandas, NumPy, SciPy sparse matrices, scikit-learn, Matplotlib, and Seaborn.

## Methodology

1. Inspect ratings, users, and movies; check duplicates, identifiers, rating ranges, and timestamps.
2. Explore rating distributions, popularity, user activity, and demographic patterns.
3. Represent movies as sparse vectors of user ratings and find neighbors using cosine similarity.
4. Predict ratings from a user's ratings of neighboring movies, with user/global mean fallbacks.
5. Compare K ∈ {15, 20, 25, 30, 35, 40, 50} using five-fold cross-validation.
6. Examine an additional 80/20 split, then fit the selected configuration on all ratings for illustrative recommendations.

**Scope correction:** The completed study uses item-based KNN. User-based KNN, matrix factorization, and Spark are not completed comparisons; the report discusses alternatives and an earlier plan to use a larger dataset.

## Results and evaluation

Recorded notebook outputs provide the following values; the report rounds them to roughly 0.94 RMSE and 0.73 MAE.

| Evaluation | K | RMSE (rating points) | MAE (rating points) |
| --- | --- | --- | --- |
| Five-fold CV mean | 50 | 0.9406 | 0.7264 |
| Additional 80/20 split | 50 | 0.9425 | 0.7284 |

K=50 was best **among the tested values**. These are historical results, not independently rerun measurements. The extra split follows model selection on the same underlying dataset and is not a fully independent confirmation.

## Key insights

- Rating activity is uneven; popular titles dominate the observed interactions.
- Similar-movie examples include *Toy Story 2* for *Toy Story* and *Terminator 2* for *The Matrix*.
- Predictions concentrate near the middle-to-high rating range. The saved evaluation residual mean is about −0.19 (actual minus predicted), indicating some overprediction on that split.
- Low rating error alone does not establish recommendation ranking quality or user satisfaction.

## Limitations

- Sparse histories and cold-start users/items remain difficult.
- Brute-force neighbor search limits scalability.
- Popularity bias and demographic imbalance constrain broader conclusions.
- No temporal holdout, online study, or ranking metrics such as NDCG/recall@K are reported.
- Genre analysis appears in EDA; a validated genre/popularity filtering improvement is not established by the completed report.

## My contribution and attribution

The report's **Team Contributions** section credits Hossein Rajabi with cleaning and preprocessing, EDA, identifying the optimal model, and the initial report draft. Shami-uz Zaman implemented item-based KNN and evaluation. Both contributed to the presentation and report.

## Available materials

| Material | Contents |
| --- | --- |
| [Final report (PDF)](EECS_2502_Final_Report.pdf) | Methodology, evaluation, limitations, team contributions, and figures |
| [Original academic notebook](EECS_2502_Final_Code.ipynb) | Existing source and saved outputs; preserved without modification |

**Evidence guide:** Report §§4–6 cover methods and results, §7 limitations, and §9 contributions. Notebook Parts 6–8 contain the more precise saved metrics. Original materials retain their existing authorship and rights.
