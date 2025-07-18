<p align="center">
  <h2 align="center">𓀝 Yasuo, This's My Customized Machine Learning Function 𓀝</h2>
  <h2 align="center">Linear Regression Optimization <br> Using <br> Ternary Search <br> Gradient Descent </h2>
</p>

<p align="center">
  <strong>Author:</strong> Nghiêm Quang Huy (HuyCP)<br>
  HCMC University of Technology and Education<br>
</p>

---

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Dataset Description](#dataset-description)
  - [Column Descriptions](#column-descriptions)
  - [Correlation Analysis](#correlation-analysis)
- [Method 1: Ternary Search on Mean Squared Error Loss](#method-1-ternary-search-on-mean-squared-error-loss)
- [Method 2: Gradient Descent on Mean Squared Error Loss](#method-2-gradient-descent-on-mean-squared-error-loss)

## Dataset Description

The dataset is stored in the file:

```
datasets/StudentScore.xls
```

### Column Descriptions

| Column                      | Type    | Description                            |
| --------------------------- | ------- | -------------------------------------- |
| gender                      | string  | Student's gender                       |
| lunch                       | string  | Type of lunch received                 |
| math score                  | integer | Score in mathematics                   |
| parental level of education | string  | Highest level of education of a parent |
| race/ethnicity              | string  | Demographic group                      |
| reading score               | integer | Reading test score                     |
| test preparation course     | string  | Whether test preparation was completed |
| writing score               | integer | Writing test score                     |

> In this project, we focus only on:
>
> * Input: **reading score**
> * Output: **writing score**

### Correlation Analysis

Based on Pearson correlation coefficients:
![image](https://github.com/user-attachments/assets/6893aacb-a371-4f90-8093-a60cc40d390f)
Here is interactions between reading score and writing score:
![image](https://github.com/user-attachments/assets/24a92821-6fa4-49c7-844f-bfdf1e24db89)
* `reading score` and `writing score`: **0.947** —> very strong positive linear relationship
* `math score` is also positively correlated with both `reading` (0.802) and `writing` (0.778)
* Non-numeric fields like `gender`, `lunch`, and `test preparation course` have weaker correlations with scores (< 0.3)
* The feature `reading score` is a **very good predictor** for `writing score`.

---
## Method 1: Ternary Search on Mean Squared Error Loss
Initially, I observed that the cost function used in univariate linear regression Mean Squared Error (MSE) is a convex quadratic function with respect to the weight parameter w. Because of this convexity, we can apply Ternary Search, a derivative-free optimization method, to efficiently find the minimum point of this function.

The equation for cost with one variable is:
We define the hypothesis function as:

```math
f_{w,b}(x^{(i)}) = wx^{(i)} + b
```

```math
J(w, b) = \frac{1}{2m} \sum_{i = 0}^{m - 1} (w x^{(i)} + b - y^{(i)})^2
```

Ternary Search is particularly suitable when:
+ The function is unimodal (has a single global minimum)
+ We are working in a one-dimensional parameter space (optimizing only w, while keeping b = 0)

---
## Method 2: Gradient Descent on Mean Squared Error Loss

### Update rule
+ In each iteraction, gradient descent performs the follwing updates:

$$
\begin{aligned}
w = w - \alpha \frac{\partial J(w,b)}{\partial w} \\
b = b - \alpha \frac{\partial J(w,b)}{\partial b}
\end{aligned}
$$

+ The gradient is defined as:

$$
J(w, b) = \frac{1}{2m} \sum_{i = 0}^{m - 1}(f_{w, b}(X^{(i)}) - y^{(i)})^2
$$

$$
\Leftrightarrow J(w, b) = \frac{1}{2m} \sum_{i = 0}^{m - 1}(wx^{(i)} + b - y^{(i)})^2
$$

+ We want to compute:

$$
    \frac{\partial J(w, b)}{\partial w}
$$

$$
    \frac{\partial J(w, b)}{\partial w} = \frac{1}{2m} \sum_{i = 0}^{m - 1} 2(wx^{(i)} + b - y^{(i)})\cdot x^{(i)}
$$

+ We want to compute:
  
$$
    \frac{\partial J(w, b)}{\partial b}\
$$

$$
    \frac{\partial J(w, b)}{\partial b} = \frac{1}{2m} \sum_{i = 0}^{m - 1} 2(wx^{(i)} + b - y^{(i)})\cdot 1
$$

