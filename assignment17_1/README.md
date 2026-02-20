# Practical Application III: Comparing Classifiers — Summary

This project compares classifier performance for predicting whether a bank client will subscribe to a term deposit (binary classification), using the UCI Bank Marketing dataset.

---

## Data Processing

- **Target:** `y` (yes/no) mapped to 1/0.
- **Features:** All columns except `y`. Categorical and numerical features were prepared as follows:
  - **Numerical** (age, duration, campaign, pdays, previous, emp.var.rate, cons.price.idx, cons.conf.idx, euribor3m, nr.employed): standardized with `StandardScaler`.
  - **One-hot encoded:** job, marital, default, housing, loan, contact, poutcome.
  - **Ordinal encoded:** education (ordered from illiterate to university.degree).
  - **Cyclical encoding:** month and day_of_week (sin/cos) to preserve cyclical structure.
- **Train/test split:** 80/20 with `random_state=42`.
- Preprocessing was done inside a scikit-learn `ColumnTransformer` and used in a `Pipeline` with each classifier.

---

## Models Used

Four classifiers were compared (with default and/or tuned hyperparameters):

1. **K-Nearest Neighbors (KNN)** — tuned `n_neighbors`
2. **Logistic Regression** — tuned regularization (`C`)
3. **Decision Tree** — tuned `max_depth`
4. **Support Vector Machine (SVC)** — tuned `C`

Model selection and tuning were done with `GridSearchCV` (5-fold CV).

---

## Best Model and Scores

The **tuned Decision Tree** (best `max_depth=5`) had the strongest balance of metrics among the models tried:

| Metric    | Score   |
|----------|---------|
| Accuracy | ~91.5%  |
| Precision| ~65%    |
| Recall   | ~54%    |
| F1       | ~59%    |

So the best-performing model in this setup is the **Decision Tree** with limited depth (e.g. `max_depth=5`).

---

## Low Precision and Recall: What It Means for Use

- **Precision (~65%):** When the model predicts “will subscribe,” only about two-thirds of those predictions are correct. Many contacts will be wasted on people who do not subscribe.
- **Recall (~54%):** The model finds only about half of the clients who actually subscribe. Many potential subscribers are missed.

**Implications for deployment:**

- **Do not use the model as the sole filter for who to contact.** With moderate precision and recall, it is better used as a **support tool** (e.g. ranking or prioritizing leads) rather than a hard yes/no gate.
- **Prefer higher recall if the goal is “don’t miss subscribers”** (e.g. lower the decision threshold or accept more false positives). Prefer **higher precision** if contact cost or customer annoyance is the main concern.
- **Combine with business rules, segment-specific strategies, or A/B tests** rather than fully automating contact decisions on this model alone.
- **Monitor performance over time** and retrain as needed; class balance and campaign conditions can change.

In short: the model adds value for prioritization and insight, but given the current precision and recall it should be used cautiously and in combination with other decision factors rather than as the single basis for targeting.
