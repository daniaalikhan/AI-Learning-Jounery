# Classification

Classification is the task of predicting which category (class) an example belongs to. Unlike regression, which predicts numerical values, classification predicts labels such as Spam/Not Spam, Fraud/Not Fraud, or Cat/Dog.

---

# Thresholds and the Confusion Matrix

Logistic Regression outputs a probability between 0 and 1. To convert this probability into a class prediction, we use a **classification threshold**.

Example:

- Probability = 0.85
- Threshold = 0.50

Since 0.85 > 0.50, the example is classified as **Positive**.

If the probability is below the threshold, it is classified as **Negative**.

---

# Confusion Matrix

A Confusion Matrix is used to evaluate classification models.

|                      | Actual Positive | Actual Negative |
| -------------------- | --------------- | --------------- |
| Predicted Positive   | True Positive (TP) | False Positive (FP) |
| Predicted Negative   | False Negative (FN) | True Negative (TN) |

## True Positive (TP)

The model correctly predicts a positive example.

Example:
A spam email correctly classified as spam.

## False Positive (FP)

The model incorrectly predicts a positive example.

Example:
A legitimate email incorrectly classified as spam.

## False Negative (FN)

The model incorrectly predicts a negative example.

Example:
A spam email incorrectly classified as legitimate.

## True Negative (TN)

The model correctly predicts a negative example.

Example:
A legitimate email correctly classified as legitimate.

---

# Imbalanced Datasets

An imbalanced dataset occurs when one class appears much more frequently than another.

Example:

- 9,998 legitimate emails
- 2 spam emails

In such situations, accuracy alone can be misleading.

---

# Classification Metrics

## Accuracy

Accuracy measures the proportion of correct predictions.

### Formula

Accuracy = (TP + TN) / (TP + TN + FP + FN)

A perfect classifier has an accuracy of 1.0 (100%).

---

## Recall (True Positive Rate)

Recall measures how many actual positive examples are correctly identified.

### Formula

Recall = TP / (TP + FN)

Recall is important when missing positive cases is costly.

Examples:

- Disease detection
- Fraud detection
- Invasive species detection

---

## False Positive Rate (FPR)

FPR measures how many actual negative examples are incorrectly classified as positive.

### Formula

FPR = FP / (FP + TN)

A lower FPR means fewer false alarms.

---

## Precision

Precision measures how many positive predictions are actually correct.

### Formula

Precision = TP / (TP + FP)

Precision is important when false positives are expensive.

Examples:

- Spam filtering
- Legal document review
- Financial risk systems

---

# Choosing the Right Metric

## Use Accuracy

- Balanced datasets
- General performance monitoring

## Use Recall

When False Negatives are more expensive than False Positives.

Examples:

- Cancer detection
- Fraud detection
- Security threats

## Use Precision

When False Positives are more expensive than False Negatives.

Examples:

- Spam detection
- Legal systems
- Financial approvals

## Use False Positive Rate

When minimizing false alarms is critical.

---

# ROC Curve (Receiver Operating Characteristic)

The ROC Curve evaluates model performance across different threshold values.

It plots:

- X-axis → False Positive Rate (FPR)
- Y-axis → True Positive Rate (Recall)

The closer the curve is to the top-left corner (0,1), the better the model.

---

# Area Under the Curve (AUC)

AUC measures the area under the ROC Curve.

## AUC = 1.0

Perfect classifier.

## AUC = 0.5

Random guessing.

### Interpretation

AUC represents the probability that the model ranks a randomly chosen positive example higher than a randomly chosen negative example.

---

# Prediction Bias

Prediction Bias measures the difference between:

- Average model predictions
- Average ground-truth labels

A well-calibrated model should have similar values for both.

### Causes of Prediction Bias

- Biased data
- Poor sampling
- Excessive regularization
- Insufficient features
- Training pipeline errors

---

# Multi-Class Classification

Binary Classification predicts between two classes.

Examples:

- Spam / Not Spam
- Fraud / Not Fraud

Multi-Class Classification predicts between three or more classes.

Examples:

- Digits (0–9)
- Animal species
- Types of clothing

If an example can belong to multiple classes simultaneously, the problem becomes **Multi-Label Classification**.

---

# Key Takeaways

- Classification predicts categories rather than numerical values.
- Logistic Regression probabilities are converted into class labels using thresholds.
- Confusion matrices help evaluate classification performance.
- Accuracy can be misleading on imbalanced datasets.
- Precision and Recall are often more informative than Accuracy.
- ROC curves evaluate performance across different thresholds.
- AUC measures a model's ability to separate positive and negative classes.
- Multi-Class Classification extends binary classification to multiple categories.

---

# My Reflection

Classification helped me understand how machine learning models make decisions between categories rather than predicting numerical values.

One of the most valuable lessons was learning that accuracy alone is not always a reliable metric, especially when datasets are imbalanced. Metrics such as Precision, Recall, ROC, and AUC provide deeper insight into model performance and help determine whether a model is suitable for real-world applications.

Understanding the trade-off between Precision and Recall also showed me how evaluation metrics should be selected based on the specific problem being solved.

---

# Next Topic
Working with numerical data

