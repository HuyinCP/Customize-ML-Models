# 🔎 Linear Regression Optimization: Ternary Search vs Gradient Descent

This project demonstrates and compares two optimization techniques — **Ternary Search** and **Gradient Descent** — for training a simple **univariate linear regression model** to minimize the **Mean Squared Error (MSE)** cost function.

---

## 📁 Dataset

- Source: `datasets/StudentScore.xls`
- Features:
  - Input: `reading score`
  - Target: `writing score`
- Preprocessing:
  - Imputation: Replace `-1.0` with **median** using `SimpleImputer`.
  - Split: 80% training / 20% test (`train_test_split`)

---

## 🧮 Problem Formulation

The hypothesis function:
\[
f_{w,b}(x) = wx + b
\]

The cost function (Mean Squared Error):
\[
J(w, b) = \frac{1}{2m} \sum_{i=0}^{m-1} (f_{w,b}(x^{(i)}) - y^{(i)})^2
\]

In this experiment:
- **Ternary Search:** fixes \( b = 0 \)
- **Gradient Descent:** learns both \( w \) and \( b \)

---

## 📐 Method 1: Ternary Search

### ✅ Idea
Ternary search is used to find the minimum of a **convex** function by iteratively narrowing down the range \([L, R]\).

### ⚙️ Complexity
\[
\mathcal{O}\left(\log_3 \left(\frac{R - L}{\varepsilon} \right) \cdot n\right)
\]

### ✅ Pros
- No learning rate required
- Guarantees convergence for unimodal (convex) loss functions

### ❌ Cons
- Only applies when function is unimodal
- Doesn’t optimize bias \( b \)

### 🔧 Implementation Highlights
```python
W = ternary_search(x_train, y_train)
