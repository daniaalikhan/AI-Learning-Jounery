# Working with Numerical Data

## Introduction

Machine Learning models rely heavily on the quality of the data they are trained on. In practice, ML engineers spend significantly more time collecting, cleaning, transforming, and validating data than building models.

This module focuses on numerical data, feature engineering, normalization techniques, data cleaning, and methods for improving numerical features before training.

---

# Numerical Data

Numerical data consists of values that can be measured and used mathematically.

### Examples

* Temperature
* Weight
* Age
* Income
* Population

> **Note:** Not every number is numerical. For example, postal codes are numbers but represent categories rather than mathematical values, making them categorical data.

---

# Feature Vectors

Models do **not** train directly on raw dataset columns.

Instead, selected features are transformed into a **feature vector**, which contains only the processed numerical values used during training.

### Example

Dataset

```text
Age | Salary | Name | Height
```

Feature Vector

```text
[Age, Salary, Height]
```

---

# Feature Engineering

Feature Engineering is the process of transforming raw data into a format that allows machine learning models to learn more effectively.

### Common Feature Engineering Techniques

* Normalization
* Binning (Bucketing)
* Clipping
* Polynomial Transforms
* Synthetic Features

---

# First Steps Before Training

Before training a model, always inspect your data.

## 1. Visualize the Data

Use:

* Scatter Plots
* Histograms

Purpose:

* Detect patterns
* Detect anomalies
* Identify outliers

---

## 2. Calculate Statistics

Useful statistics include:

* Mean
* Median
* Standard Deviation
* Minimum
* Maximum
* Quartiles (0%, 25%, 50%, 75%, 100%)

---

# Outliers

Outliers are values that are significantly different from the rest of the dataset.

### Example

```text
22
24
25
23
21
220
```

`220` is an outlier.

### Causes

* Data entry errors
* Faulty sensors
* Genuine rare observations

### What should you do?

**Keep the outlier if:**

* It is a valid observation.
* Similar values may appear during prediction.

**Remove or clip the outlier if:**

* It is incorrect.
* It negatively impacts training.

---

# Normalization

Normalization rescales numerical features to similar ranges.

## Why Normalize?

* Faster model convergence
* Better prediction accuracy
* Prevents the **NaN Trap**
* Prevents large-scale features from dominating smaller ones

> **Important:** Any feature normalized during training **must also be normalized during prediction.**

---

# Linear Scaling

Scales values into a fixed range, usually **0–1** or **-1 to 1**.

### Formula

```math
X' = (X - X_min) / (X_max - X_min)
```

### Best Used When

* Data has few outliers
* Data is approximately uniformly distributed
* Minimum and maximum values rarely change

### Example

Age

```text
0 – 100
```

---

# Z-Score Scaling

Measures how many standard deviations a value is from the mean.

### Formula

```math
Z = (X - μ) / σ
```

Where:

* μ = Mean
* σ = Standard Deviation

### Best Used When

* Data follows a normal (bell-shaped) distribution

### Example

* Human Height
* Exam Scores

---

# Log Scaling

Applies the natural logarithm to reduce skewed distributions.

### Formula

```math
X' = ln(X)
```

### Best Used When

* Data follows a power-law distribution
* Highly skewed datasets

### Examples

* Income
* Population
* Book Sales
* Movie Ratings

---

# Clipping

Clipping reduces the influence of extreme outliers by capping values above or below a chosen threshold.

### Example

Original

```text
1
2
3
4
25
```

After Clipping

```text
1
2
3
4
4
```

### Best Used When

The dataset contains extreme outliers that could dominate model training.

---

# Summary of Normalization Techniques

| Technique       | Best Used For               |
| --------------- | --------------------------- |
| Linear Scaling  | Uniform distributions       |
| Z-Score Scaling | Normally distributed data   |
| Log Scaling     | Highly skewed distributions |
| Clipping        | Extreme outliers            |

---

# Binning (Bucketing)

Binning groups numerical values into ranges (bins) instead of treating every value independently.

### Example

Original Values

```text
18
22
25
33
40
```

Buckets

```text
18–25
26–35
36–45
```

---

## Advantages

* Simplifies numerical data
* Handles clustered values
* Works well when relationships are non-linear

---

# Quantile Bucketing

Unlike equal-width bins, **Quantile Bucketing** creates bins containing approximately the **same number of examples**.

Useful for highly skewed datasets because every bucket contains enough data for training.

---

# Scrubbing

Scrubbing is the process of identifying and fixing poor-quality data before training.

### Common Problems

* Missing values
* Duplicate records
* Invalid values
* Incorrect labels

### Example

```text
Age = 250
```

Clearly invalid and should be corrected or removed.

---

# Qualities of Good Numerical Features

A good numerical feature should be:

## Clearly Named

Good

```text
house_age_years = 27
```

Poor

```text
house_age = 851472000
```

---

## Validated

Always check for impossible values.

Example

```text
Age = 224
```

Likely an error.

---

## Sensible

Avoid using **magic values**.

Instead of

```text
watch_time = -1
```

Use

```text
watch_time = 0
is_watch_time_defined = False
```

This clearly indicates that the value is missing.

---

# Polynomial Transforms

Polynomial transforms create new features by raising an existing feature to a power.

Examples:

```math
X²
```

```math
X³
```

These allow linear models to capture non-linear relationships.

### Linear Regression

```math
y = w₁x + b
```

### Polynomial Regression

```math
y = w₁x + w₂x² + b
```

---

# Synthetic Features

Synthetic features are created by combining existing features.

### Examples

BMI

```math
BMI = Weight / Height²
```

Area

```math
Area = Length × Width
```

Synthetic features often improve model performance by revealing hidden relationships.

---

# Best Practices

* Inspect your data before training.
* Visualize data using graphs.
* Detect and handle outliers.
* Normalize numerical features.
* Use binning when relationships are non-linear.
* Remove or fix poor-quality data.
* Create meaningful synthetic features.
* Document every preprocessing step.

---

# Key Takeaways

* Models train on **feature vectors**, not raw datasets.
* Feature engineering is often more important than changing the model itself.
* Normalization improves training speed and prediction quality.
* Different data distributions require different normalization techniques.
* Scrubbing removes poor-quality data before training.
* Polynomial transforms and synthetic features allow models to learn more complex relationships.
* High-quality data is often more valuable than a more complex algorithm.

---

# Personal Reflection

## What I Learned

* Machine Learning models depend heavily on clean, high-quality data.
* Different normalization techniques are suited to different data distributions.
* Feature engineering can significantly improve model performance.
* Proper data preprocessing often has a greater impact than choosing a more advanced model.

## Real-World Applications

* House Price Prediction
* Medical Diagnosis
* Recommendation Systems
* Financial Forecasting
* Fraud Detection
