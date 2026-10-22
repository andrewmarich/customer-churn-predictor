# Customer Churn Predictor

WGU coursework. A Jupyter notebook that explores a bank-customer dataset, trains a random forest to predict churn, and lets you try predictions with interactive widgets.

## What it does

- Loads `Churn_Modelling.csv` (10,000 customers; a public dataset) and drops identifier columns.
- Visualizes churn by geography, churn rate by age, and the churn / non-churn split.
- Trains a `RandomForestClassifier` (100 trees, 80/20 train/test split, fixed seed).
- Provides sliders and dropdowns to enter a customer profile and see the predicted outcome.

## Results

On the 2,000-customer test set:

| | Precision | Recall | F1 | Support |
|---|---|---|---|---|
| Stayed | 0.88 | 0.96 | 0.92 | 1,607 |
| Churned | 0.74 | 0.47 | 0.58 | 393 |

Overall accuracy is 0.86, but that number flatters the model: about 20% of customers churned, and the model finds fewer than half of them (recall 0.47). Confusion matrix: 1,543 true negatives, 64 false positives, 208 false negatives, 185 true positives.

## Run it

```sh
pip install -r requirements.txt
pip install notebook   # requirements.txt does not include the Jupyter app itself
jupyter notebook notebook.ipynb
```

Run all cells, then use the widgets near the end of the notebook.

## Limitations and next steps

- Recall on churners is low. Class weighting, threshold tuning, or resampling would be the first things to try.
- Only one model and one split; no cross-validation or hyperparameter search.
- The dataset is a public teaching dataset, so the results say little about real customers.
