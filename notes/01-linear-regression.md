# Linear Regression

> Google Machine Learning Crash Course  
> Status: ✅ Completed  
> Date: June 2026

# What is Linear Regression?
Linear Regression is a statistical and machine learning technique used to identify the relationship between one or more **features (inputs)** and a **label (output)**.

Its goal is to predict continuous numerical values by fitting the best possible straight line through the data.

Examples:
- Predicting house prices
- Predicting salary based on experience
- Predicting sales revenue


# Linear Regression Equation

## Algebra Form

y = mx + b

Where:

| Variable | Meaning |
|------------|------------------------------|
| y | Label (output) |
| m | Slope |
| x | Feature (input) |
| b | Y-intercept |


## Machine Learning Form

ŷ = b + w₁x₁

Where:

| Variable | Meaning |
|------------|------------------------------|
| ŷ | Predicted label |
| b | Bias |
| w₁ | Weight |
| x₁ | Feature |

Unlike algebra, the **bias and weights are learned automatically during training**.


# Bias and Weight

## Bias

Bias is a parameter that shifts the prediction up or down.

It is learned during model training.

## Weight

Weight determines how much influence a feature has on the prediction.

It is also learned during training.


# Models with Multiple Features

Real-world problems often contain multiple input variables.

The equation becomes:

ŷ = b + w₁x₁ + w₂x₂ + w₃x₃ + ...

Each feature has its own corresponding weight.

Example:

Predicting a house price might use:

- Number of bedrooms
- House size
- Location score
- Age of house

Each feature contributes differently to the final prediction.


# Loss

Loss is a numerical metric that measures how wrong a model's predictions are.

The objective of training is to **minimize loss**.

Loss measures the distance between:


Actual value (label)
vs
Predicted value


Loss only measures magnitude, not direction.


# Types of Loss

## L1 Loss


Σ |Actual - Predicted|

Measures absolute error.



## Mean Absolute Error (MAE)


(1/N) × L1 Loss

Average absolute error across all examples.


## L2 Loss

Σ (Actual - Predicted)²

Squares the error before summing.


## Mean Squared Error (MSE)

(1/N) × L2 Loss

Average squared error across the dataset.


## Root Mean Squared Error (RMSE)


RMSE = √MSE

Returns the error in the same units as the original data.


# Prediction Formula

```
Prediction = Bias + (Weight × Feature Value)
```

where

```
Actual Value = Label
```

---

# Choosing a Loss Function

Outliers are data points that differ significantly from the rest of the dataset.

Different loss functions treat outliers differently.

## Mean Squared Error (MSE)

- Squares large errors
- Penalizes outliers heavily
- Model moves closer to outliers
- Can reduce performance on normal data

## Mean Absolute Error (MAE)

- Uses absolute distance
- Less sensitive to outliers
- Model stays closer to the majority of data points

---

# Gradient Descent

Gradient Descent is an optimization algorithm that finds the best weights and bias by minimizing loss.

Training starts with random values near zero and repeats the following process:

1. Calculate loss
2. Determine the direction that reduces loss
3. Update weights and bias slightly
4. Repeat until loss can no longer be reduced

The goal is to find the lowest point on the loss surface.

---

# Model Convergence

Convergence occurs when Gradient Descent reaches the minimum possible loss.

The loss curve shows how loss changes during training.

A successful model produces a curve that decreases and eventually levels off.

---

# Convex Functions

The loss function for Linear Regression is convex.

This means:

- There is only one global minimum
- Gradient Descent will eventually reach the optimal weights and bias

A useful analogy:

> Imagine a ball rolling down a hill until it reaches the lowest point.

---

# Hyperparameters

Hyperparameters control how the model learns.

Unlike parameters, they are chosen by the developer rather than learned automatically.

Common hyperparameters include:

- Learning Rate
- Batch Size
- Epochs

---

# Learning Rate

Learning Rate controls how large each Gradient Descent update is.

### Too Low

- Very slow training
- Takes longer to converge

### Too High

- Overshoots the minimum
- May never converge
- Loss bounces around

Goal:

Choose a learning rate that is **not too high and not too low**.

---

# Batch Size

Batch Size is the number of training examples processed before updating weights and bias.

## Full Batch

Uses the entire dataset before updating parameters.

## Stochastic Gradient Descent (SGD)

Batch Size = 1

Advantages:
- Fast updates

Disadvantages:
- Very noisy
- Loss may temporarily increase

## Mini-Batch SGD

Uses a small subset of data for each update.

Provides a balance between stability and efficiency.

---

# Epochs

One epoch means the model has processed every training example once.

Training usually requires multiple epochs.

Example:

Dataset = 1000 examples

20 epochs = every example is processed 20 times.

---

# Parameter Updates

| Training Method | Weight/Bias Update |
|-----------------|-------------------|
| Full Batch | After all examples |
| SGD | After every example |
| Mini-Batch SGD | After every batch |

---

# Key Takeaways

- Linear Regression predicts continuous values.
- Features are inputs and labels are outputs.
- Weights and bias are learned during training.
- Loss measures prediction error.
- Gradient Descent minimizes loss.
- Linear Regression has a convex loss surface with one global minimum.
- Hyperparameters control the training process.
- Learning Rate, Batch Size, and Epochs significantly affect performance.

---

# My Reflection

This chapter introduced the fundamental concepts behind supervised machine learning.

One important realization is that machine learning is essentially the process of finding the best mathematical relationship between inputs and outputs. Rather than manually choosing weights and bias, Gradient Descent automatically adjusts these parameters to minimize prediction error.

Understanding Linear Regression provides a strong foundation for more advanced topics such as Logistic Regression, Neural Networks, and Large Language Models.

---

# Next Topic

➡ Logistic Regression






