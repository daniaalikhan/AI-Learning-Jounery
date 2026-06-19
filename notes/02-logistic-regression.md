# Logistic Regression

> Google Machine Learning Crash Course

> Status:Completed

> Date:June 2026



# What is Logistic Regression?

Logistic Regression is a machine learning algorithm used for **classification problems**.

Instead of predicting a continuous value (like Linear Regression), it predicts the **probability** that an example belongs to a particular class.

Examples:

- Predicting whether an email is spam or not spam
- Predicting whether a customer will buy a product
- Predicting whether a patient has a disease

Output:

```
Probability = 0 → 1
```

---

# Logistic Regression vs Linear Regression

| Linear Regression | Logistic Regression |
|------------------|--------------------|
| Predicts continuous values | Predicts probabilities |
| Output can be any number | Output is always between 0 and 1 |
| Uses L2 (Squared) Loss | Uses Log Loss |
| Best for regression problems | Best for classification problems |

---

# Sigmoid Function

Logistic Regression converts its output into a probability using the **Sigmoid Function**.

### Formula

```
f(x) = 1 / (1 + e^(-x))
```

where:

- **f(x)** = probability output
- **e** = Euler's number (≈ 2.71828)
- **x** = input value

---

# Properties of the Sigmoid Function

- Produces values only between **0 and 1**
- Has an **S-shaped curve**
- Never actually reaches 0 or 1
- Perfect for representing probabilities

As the input increases:

```
Output → 1
```

As the input decreases:

```
Output → 0
```

---

# Linear Component

Before applying the sigmoid function, Logistic Regression first calculates a linear equation.

### Formula

```
z = b + w₁x₁ + w₂x₂ + w₃x₃ + ... + wₙxₙ
```

where:

- **z** = log odds (linear output)
- **b** = bias
- **w** = learned weights
- **x** = feature values

---

# Final Logistic Regression Prediction

The linear output is passed through the sigmoid function.

### Formula

```
ŷ = 1 / (1 + e^(-z))
```

where:

- **ŷ** = predicted probability
- **z** = linear output
- **e** = Euler's number

The final prediction is always between **0 and 1**.

---

# Logistic Regression Training

Logistic Regression is trained similarly to Linear Regression but with two important differences:

- Uses **Log Loss** instead of Squared Loss
- Requires **Regularization** to reduce overfitting

---

# Log Loss

Log Loss measures how far predicted probabilities are from the actual labels.

Lower Log Loss indicates better predictions.

### Formula

```
Log Loss = -( y log(ŷ) + (1 - y) log(1 - ŷ) )
```

where:

- **y** = actual label (0 or 1)
- **ŷ** = predicted probability

---

# Why Not Use Squared Loss?

Squared Loss works well for Linear Regression because the relationship is linear.

Logistic Regression uses a sigmoid curve, meaning:

- Small changes near the center produce large probability changes.
- Large positive or negative values produce only small probability changes.

Therefore, **Log Loss is more suitable** than Squared Loss.

---

# Regularization

Regularization prevents the model from becoming overly complex and overfitting the training data.

Without regularization:

- The model keeps trying to reduce loss toward zero.
- It may memorize the training data instead of learning general patterns.

---

# Common Regularization Methods

### L2 Regularization

Adds a penalty for large weight values.

Benefits:

- Simpler model
- Better generalization
- Reduced overfitting

---

### Early Stopping

Stops training before the model begins overfitting.

Instead of training until loss reaches its minimum, training stops while the model still performs well on unseen data.

---

# Key Takeaways

- Logistic Regression predicts probabilities rather than continuous values.
- The Sigmoid Function transforms outputs into values between 0 and 1.
- The linear equation calculates log odds before the sigmoid function is applied.
- Logistic Regression uses Log Loss instead of Squared Loss.
- Regularization is essential to prevent overfitting.
- L2 Regularization and Early Stopping are common techniques for improving model performance.

---

# My Reflection

Linear Regression predicts numerical values, while Logistic Regression predicts probabilities for classification tasks.

Understanding the Sigmoid Function and Log Loss makes it clear why Logistic Regression is one of the most widely used classification algorithms in machine learning.

---

# Next Topic

➡️ Classification