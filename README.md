# Simple Linear Regression Explanation with Python (NumPy and Matplotlib)

## Introduction

This code demonstrates a **simple linear regression** model. In simple linear regression, the goal is to find a linear relationship between two variables \(x\) and \(y\), represented by the equation:

\[
y = \beta_0 + \beta_1 x\]

Where:
- \( \beta_0 \) is the **y-intercept**.
- \( \beta_1 \) is the **slope** of the line.

## Libraries Used

- **NumPy**: For numerical operations like mean calculation and vector manipulation.
- **Matplotlib**: For plotting the data and the regression line.

## Code Breakdown

### 1. Define Input Data

```python
x = np.array([6, 7, 7.5, 9, 10, 10.99, 12, 13.2, 14])
y = np.array([1, 3, 3, 5, 7, 7.5, 9, 11.4, 13.2])
```

The arrays `x` and `y` contain the data points for which we want to fit a regression line.

### 2. Calculate Means of \(x\) and \(y\)

```python
beta1_x = x.mean()
beta1_y = y.mean()
```

The means of `x` and `y` are calculated to use in the formula for the slope.

### 3. Calculate the Slope (\(\beta_1\))

The slope \(\beta_1\) is calculated using the formula:

\[
\beta_1 = \frac{\sum (x_i - \bar{x})(y_i - \bar{y})}{\sum (x_i - \bar{x})^2}
\]

In the code:

```python
level_x = x - beta1_x
level_y = y - beta1_y
numerator = (level_x * level_y).sum()
denominator = (level_x ** 2).sum()
beta1 = numerator / denominator
```

- **`level_x`**: Differences between each `x` value and the mean of `x`.
- **`level_y`**: Differences between each `y` value and the mean of `y`.
- **`numerator`**: Sum of the product of `level_x` and `level_y`.
- **`denominator`**: Sum of the squares of `level_x`.

### 4. Calculate the Intercept (\(\beta_0\))

The intercept \(\beta_0\) is calculated using:

\[
\beta_0 = \bar{y} - \beta_1 \bar{x}
\]

In the code:

```python
beta0 = beta1_y - (beta1 * beta1_x)
```

### 5. Predict Values (\(y_{pred}\))

Using the regression equation, predicted `y` values are calculated:

```python
y_pred = beta0 + beta1 * x
```

### 6. Display Results

Print the slope and intercept:

```python
print(f"Slope (Beta1): {beta1:.2f}")
print(f"y-intercept (Beta0): {beta0:.2f}")
```

### 7. Plot the Data and Regression Line

The `show` function plots the original data and the regression line:

```python
def show():
    plt.scatter(x, y, color='blue', label='Actual Data')
    plt.plot(x, y_pred, color='red', label='Linear Regression')
    plt.xlabel('x')
    plt.ylabel('y')
    plt.title('Simple Linear Regression')
    plt.legend()
    plt.show()

show()
```

### Output

- **Blue Points**: The actual data points.
- **Red Line**: The fitted regression line.

---

## Conclusion

This code helps find the linear relationship between two variables and visualize it. The slope and intercept are calculated using linear regression formulas, and the resulting line is plotted to show how well it fits the data.
