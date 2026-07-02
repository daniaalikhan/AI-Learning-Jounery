# Datasets, Generalization, and Overfitting

## Introduction

Data quality has a greater impact on machine learning performance than choosing a more advanced algorithm. In practice, machine learning engineers spend approximately **80% of a project's time** preparing, cleaning, and transforming data.

This module covers:

- Dataset characteristics
- Data quality and reliability
- Labels
- Dataset splitting
- Overfitting
- Generalization
- Regularization
- Interpreting loss curves

---

# Dataset Characteristics

A **dataset** is a collection of training examples used to build a machine learning model.

Datasets can come from:

- CSV files
- Databases
- Spreadsheets
- Log files
- Images
- Videos
- Audio
- Text
- Outputs from other ML models

Each row typically represents an **example**, while each column represents a **feature** or **label**.

---

# Types of Data

Machine learning datasets may contain:

- Numerical data
- Categorical data
- Text (Natural Language)
- Images
- Audio
- Video
- Embeddings
- Outputs from other ML systems

---

# Quantity of Data

Generally:

> **More high-quality data is better than more complex models.**

### Rule of Thumb

A model should train on at least:

```
10–100 × more examples than trainable parameters
```

Simple models trained on very large datasets often outperform highly complex models trained on smaller datasets.

---

# Data Quality

A high-quality dataset enables the model to achieve its objective accurately.

Reliable datasets have:

- Accurate labels
- Low noise
- Correct feature values
- Representative examples
- Proper filtering

---

# Causes of Unreliable Data

Common issues include:

- Missing values
- Duplicate records
- Incorrect feature values
- Incorrect labels
- Corrupted data
- Measurement errors
- Data collection errors
- Noisy features

Automation should be used to detect invalid or inconsistent data whenever possible.

---

# Missing Data

Real-world datasets often contain missing values.

Example:

| Age | Salary | House Price |
|------|---------|-------------|
| 28 | 50,000 | 320,000 |
| 35 | Missing | 410,000 |

Two common approaches:

## 1. Delete Examples

Best when:

- Very few rows contain missing values
- Enough complete data remains

---

## 2. Imputation

Estimate the missing value using a reasonable approximation.

Common methods:

- Mean
- Median
- Mode
- Predictive models

For Z-score normalized data:

```
Missing Value ≈ 0
```

since the mean Z-score is 0.

A good practice is adding another feature such as:

```
salary_is_imputed = True / False
```

so the model knows which values were estimated.

---

# Labels

Labels are the values the model attempts to predict.

---

## Direct Labels

Exactly match the prediction target.

Example:

```
Bike Owner

Yes
No
```

---

## Proxy Labels

Indirectly represent the target.

Example:

```
Recently Bought Bicycle
```

This does not guarantee bike ownership but is a useful approximation.

Whenever available:

> Direct labels are preferred over proxy labels.

---

# Human vs Machine Labels

## Human Labels (Gold Labels)

Advantages

- Higher quality
- Better judgement
- More reliable

Disadvantages

- Expensive
- Slow
- Human bias
- Inconsistent

---

## Machine Labels (Silver Labels)

Advantages

- Fast
- Cheap
- Scalable

Disadvantages

- Can inherit model errors
- Less reliable
- May require human verification

---

# Improving Human Labels

Improve label quality by:

- Providing clear instructions
- Multiple human reviewers
- Measuring inter-rater agreement
- Reviewing disagreements

---

# Class Imbalance

A dataset is **imbalanced** when one class occurs much more frequently than another.

Example:

```
Fraud Detection

99.9% Legitimate

0.1% Fraud
```

Problems:

- Poor minority-class learning
- Misleading accuracy
- Biased predictions

---

# Handling Class Imbalance

### Step 1 – Downsample Majority Class

Reduce examples from the majority class.

---

### Step 2 – Upweight Majority Class

Increase the loss contribution of majority-class examples to maintain the true class distribution during training.

This improves learning while preserving the original distribution.

---

# Dataset Splitting

Never evaluate a model using the same data it trained on.

Standard split:

| Dataset | Percentage |
|----------|-----------:|
| Training | 70% |
| Validation | 15% |
| Test | 15% |

---

## Training Set

Used to train the model.

---

## Validation Set

Used for:

- Hyperparameter tuning
- Model selection
- Early stopping

---

## Test Set

Used only once after training to evaluate the final model.

---

# Good Dataset Splits

A good split should:

- Represent the real world
- Contain no duplicate examples
- Be statistically similar
- Be large enough for reliable evaluation

---

# Data Transformation

Machine learning models require numerical inputs.

Transformations include:

- Encoding categorical data
- Normalization
- Feature engineering
- Feature scaling

---

# Personally Identifiable Information (PII)

Datasets should avoid storing sensitive information such as:

- Names
- Phone numbers
- Email addresses
- National IDs
- Addresses

Protecting privacy is an important part of responsible AI.

---

# Overfitting

## Definition

Overfitting occurs when a model memorizes the training data instead of learning general patterns.

Characteristics:

- Excellent training performance
- Poor performance on unseen data

---

# Underfitting vs Good Fit vs Overfitting

| Underfitting | Good Fit | Overfitting |
|--------------|----------|-------------|
| Poor training accuracy | Good training accuracy | Excellent training accuracy |
| Poor test accuracy | Good test accuracy | Poor test accuracy |

Goal:

> Build a model that **generalizes** well.

---

# Generalization

Generalization is the model's ability to perform well on new, unseen data.

Good generalization requires:

- Independent examples
- Similar data distributions
- Stationary datasets
- Representative training data

---

# Causes of Overfitting

- Model too complex
- Too many features
- Small dataset
- Noisy data
- Poor dataset representation

---

# Occam's Razor

When two models perform similarly:

> Prefer the simpler model.

Simpler models usually generalize better.

---

# Regularization

Regularization prevents overfitting by penalizing overly complex models.

Training minimizes:

```
Total Loss = Training Loss + λ × Regularization
```

where:

- **λ (Lambda)** = Regularization rate

---

# L2 Regularization

L2 Regularization penalizes large model weights.

### Formula

```
L2 = w₁² + w₂² + w₃² + ... + wₙ²
```

Large weights contribute much more to complexity than small weights.

L2 encourages weights to move closer to zero but rarely makes them exactly zero.

---

# Lambda (λ)

Lambda controls the strength of regularization.

### High λ

- Simpler model
- Lower overfitting
- Higher bias

---

### Low λ

- More complex model
- Greater overfitting risk
- Lower bias

Choosing λ is a hyperparameter tuning problem.

---

# Early Stopping

Another way to reduce overfitting.

Training stops when:

- Validation loss begins increasing

instead of waiting until full convergence.

Benefits:

- Faster training
- Less overfitting

---

# Learning Rate vs Regularization

Learning Rate:

- Controls update size

Regularization:

- Controls model complexity

A balance between both produces the best-performing model.

---

# Loss Curves

Loss curves show model performance during training.

Ideal curve:

- Rapid decrease
- Smooth convergence
- Stable minimum

---

# Common Loss Curve Patterns

### 1. Oscillating Loss

Possible causes:

- Learning rate too high
- Poor-quality data
- Insufficient training data

---

### 2. Exploding Loss

Possible causes:

- NaN values
- Outliers
- Numerical instability

---

### 3. Validation Loss Increases

Training loss decreases while validation loss rises.

Cause:

```
Overfitting
```

---

### 4. Chaotic Loss

Possible cause:

- Poorly shuffled training data

---

# Best Practices

- Prioritize data quality over model complexity.
- Remove duplicates and noisy examples.
- Handle missing values carefully.
- Use direct labels whenever possible.
- Split datasets into training, validation, and test sets.
- Monitor validation loss to detect overfitting.
- Apply regularization when needed.
- Choose the simplest model that performs well.
- Protect user privacy by removing PII.

---

# Key Takeaways

- Data quality has a greater impact on model performance than algorithm choice.
- Reliable, representative datasets produce better models.
- Missing values should be deleted or imputed appropriately.
- Direct labels are preferred over proxy labels.
- Human labels are generally more accurate than machine-generated labels.
- Class imbalance should be addressed using downsampling and upweighting.
- Separate datasets into training, validation, and test sets.
- Overfitting reduces performance on unseen data.
- Regularization and early stopping help improve generalization.
- Validation loss is one of the best indicators of overfitting.

---

# Personal Reflection

## What I Learned

- Preparing data is one of the most important stages of any machine learning project.
- More data is not always better unless it is high quality.
- Overfitting is a common problem that can be reduced using regularization and early stopping.
- Proper dataset splitting is essential for evaluating model performance fairly.
- Monitoring validation loss provides valuable insight into when a model begins to overfit.

## Real-World Applications

- Fraud Detection
- Medical Diagnosis
- Recommendation Systems
- Spam Detection
- Autonomous Vehicles
- Financial Forecasting
- Customer Analytics
- Image Classification