<p align="center">
  <h2 align="center">My Customized Machine Learning Function 😵</h2>
  <h2 align="center">Linear Regression Optimization<br> Ternary Search vs Gradient Descent</h2>
</p>

<p align="center">
  <strong>Author:</strong> Nghiêm Quang Huy<br>
  <strong>Course:</strong> Just for fun HEHE<br>
  <strong>University:</strong> HCMC University of Technology and Education<br>
</p>

---

## Table of Contents

- [Dataset Description](#dataset-description)
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
The equation for cost with one variable is:
We define the hypothesis function as:

$$
f_{w,b}(x^{(i)}) = wx^{(i)} + b
$$

The cost function is:

$$
J(w,b) = \frac{1}{2m} \sum_{i = 0}^{m-1} (f_{w,b}(x^{(i)}) - y^{(i)})^2
$$

---
## Method 2: Gradient Descent on Mean Squared Error Loss
