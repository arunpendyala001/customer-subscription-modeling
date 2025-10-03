# Bank Marketing ML Project

This project applies machine learning techniques to the **UCI Bank Marketing dataset**, which contains information from a Portuguese bank’s direct marketing campaigns. The main goal is to predict whether a client will subscribe to a long-term deposit based on demographic, campaign, and economic features.

---

## 📊 Dataset

- Source: UCI Bank Marketing Dataset
- 41,188 entries, 21 columns
- Target variable: `y` (binary: `"yes"` if client subscribed, `"no"` otherwise)
- Key challenge: **class imbalance** (~88% "no", ~12% "yes")

---

## 🛠️ Methods

The following steps were performed:

1. **Understanding the Data** – explored dataset structure and business objective.
2. **Feature Engineering** –
   - Dropped `duration` (leakage).
   - Transformed `pdays` so 999 → "never contacted".
   - Handled categorical variables with one-hot encoding.
3. **Train/Test Split** – 70/30 split with stratification to preserve class balance.
4. **Baseline Model** – Dummy Classifier (majority class) → ~88% accuracy, but 0% recall for "yes".
5. **Models Tested** –
   - Logistic Regression (with class balancing)
   - K-Nearest Neighbors (KNN)
   - Decision Tree
   - Support Vector Machine (SVM)
6. **Hyperparameter Tuning** – GridSearchCV for Decision Tree and KNN.
7. **Evaluation Metrics** – Compared **Accuracy, Precision, Recall, F1-score**.

---

## 📈 Key Findings

- **Baseline (majority class):** High accuracy (~88%) but failed to predict any positive cases.
- **Logistic Regression (balanced):** Accuracy ~58%, Recall for "yes" ~74%. Useful for catching actual subscribers despite lower accuracy.
- **KNN:** Accuracy ~87%, but low F1-score (~0.16). Struggled with imbalance.
- **Decision Tree:** Accuracy ~85%, but F1-score also low (~0.14). Overfitted on training data.
- **SVM:** Best accuracy (~88%), but training time was very high (~30s).

📌 **Business Insight:**  
Accuracy alone is misleading due to class imbalance. Models like Logistic Regression (with class weighting) improve recall and help identify potential subscribers. For the bank, recall and F1 are more meaningful because the business goal is to capture as many subscribers as possible.

---

[Link to notebook](prompt_III.ipynb)
