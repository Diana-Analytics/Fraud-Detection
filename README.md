# Credit Card Fraud Detection

## 🚀 Detecting Fraudulent Transactions: A Machine Learning Approach

### 1️⃣ Introduction
Fraud detection in financial transactions is a challenging problem due to the extreme class imbalance—fraud cases are significantly outnumbered by legitimate transactions. This project explores different machine learning approaches to improve fraud detection, starting with **Logistic Regression** and progressing to advanced techniques like **XGBoost with resampling methods**.

---

### 2️⃣ Problem Statement
The dataset consists of **20,000 transactions**, with only **200 fraudulent transactions** (1%). This makes fraud detection a highly imbalanced classification problem. Our goal is to build a model that effectively detects fraud while minimizing false positives.

---

### 3️⃣ Initial Approach: Logistic Regression
We initially applied **Logistic Regression**, but it failed to detect any fraudulent transactions due to the severe imbalance. The model was biased toward the majority class, achieving high accuracy but **zero recall** for fraud cases.

---

### 4️⃣ XGBoost Model Implementation
We introduced **XGBoost**, a powerful gradient boosting algorithm, and tuned its **scale_pos_weight** parameter to handle class imbalance.

#### 🔹 4.1 XGBoost with Scale Pos Weight
We experimented with different values for `scale_pos_weight`:

- **5** → Detected a few fraud cases, but recall remained low.
- **15, 20, 100, 200** → Increasing the weight improved recall slightly but also increased false positives, leading to a trade-off between **precision and recall**.
- **Final choice: 165** → Achieved the best balance.

---

### 5️⃣ Threshold Tuning
Instead of using the default **0.5 threshold**, we tested different values:

- **0.2, 0.3, 0.35** → Lowering the threshold improved recall but worsened precision.
- **Final choice: 0.2** → Achieved the best balance between fraud detection and false alarms.

---

### 6️⃣ Final Results

| Model & Technique | Precision (Fraud) | Recall (Fraud) | F1-Score (Fraud) | AUC-ROC |
|-------------------|-------------------|----------------|------------------|----------|
| Logistic Regression | 0.00 | 0.00 | 0.00 | N/A |
| XGBoost (scale_pos_weight = 5) | 0.01 | 0.14 | 0.02 | 0.50 |
| XGBoost (scale_pos_weight = 165) | 0.01 | 0.42 | 0.02 | 0.50 |

---

### 7️⃣ Confusion Matrix for Final Model
```
[[11582  8218]
 [  115    85]]
```
- ✅ **True Negatives (11582)** → Legitimate transactions correctly classified.
- ❌ **False Positives (8218)** → Legitimate transactions misclassified as fraud.
- ❌ **False Negatives (115)** → Fraud cases not detected.
- ✅ **True Positives (85)** → Correctly identified fraud cases.

---

### 8️⃣ Key Takeaways
- **Logistic Regression** was ineffective due to class imbalance.
- **XGBoost with Scale Pos Weight** improved recall but at the cost of precision.
- **Threshold tuning** helped balance precision-recall trade-offs.
- Fraud detection remains challenging, requiring more advanced techniques.

---

### 9️⃣ Next Steps
- Experiment with **resampling techniques** (undersampling,oversampling e.g SMOTE,ADASYN, NearMiss, etc.).
- Try **autoencoder-based anomaly detection**.
- Investigate **ensemble methods** combining multiple models.
- Use **real-world fraud detection datasets** for further validation.

---

### 🔟 Conclusion
While we did not achieve a **perfect** fraud detection system, this project highlights:
- The **challenges of extreme class imbalance**.
- The **importance of feature engineering & resampling techniques**.
- The **impact of threshold tuning on fraud detection performance**.

This project serves as a **solid foundation** for future improvements and a valuable addition to my portfolio. 🚀
