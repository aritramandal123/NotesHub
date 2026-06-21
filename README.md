# 1. Understand Recursive Algorithms

## What is Being Asked?

Explain the concept of recursion and describe how recursion simplifies the implementation of a Financial Predictor that estimates future values using previous years' growth rates.

## Answer

### Recursion

Recursion is a programming technique in which a function solves a problem by calling itself repeatedly until a stopping condition, known as the **base case**, is reached.

A recursive function consists of two main parts:

* **Base Case:** Stops further recursive calls.
* **Recursive Case:** Calls the same function with a smaller or modified input.

### Recursion in the Financial Predictor

In this project, recursion is used to predict future financial values based on historical growth rates. Instead of calculating each future year's value separately, the algorithm uses the previous year's value to generate the next prediction.

The prediction formula is:

[
Predicted\ Value = Previous\ Value \times (1 + Growth\ Rate)
]

For example:

| Year              | Revenue (₹) |
| ----------------- | ----------- |
| Current Year      | 100,000     |
| Year 1 Prediction | 110,000     |
| Year 2 Prediction | 121,000     |
| Year 3 Prediction | 133,100     |

Assuming a growth rate of **10%**, each year's prediction depends on the value predicted for the previous year. Recursion naturally models this relationship because the same calculation is repeatedly applied until the required number of future years has been predicted.

### Advantages of Using Recursion

* Simplifies repetitive calculations.
* Produces cleaner and more readable code.
* Naturally represents year-by-year financial forecasting.
* Reduces the need for complex looping logic.

---

# 3. Analysis

## What is Being Asked?

Analyze the recursive algorithm by discussing its time complexity and explain possible optimizations to improve performance and avoid unnecessary computations.

## Answer

### Time Complexity Analysis

Let:

* **n** = Number of future years to predict.

The recursive algorithm performs one recursive call for each year being forecasted.

Therefore:

[
T(n) = T(n-1) + O(1)
]

Solving the recurrence relation:

[
T(n) = O(n)
]

**Time Complexity:** `O(n)`

This means the execution time increases linearly with the number of years being predicted.

### Space Complexity Analysis

Since each recursive call is stored in memory until the base case is reached, the call stack grows with the number of recursive calls.

[
Space\ Complexity = O(n)
]

where **n** is the number of predicted years.

---

## Optimizing the Recursive Solution

Although recursion provides a simple and elegant solution, it can become inefficient for larger prediction periods due to increased memory consumption and function call overhead.

### 1. Memoization

Memoization stores previously calculated prediction values and reuses them when needed.

**Benefits:**

* Prevents redundant calculations.
* Improves performance when values are requested multiple times.
* Reduces computational overhead.

---

### 2. Dynamic Programming

Dynamic Programming calculates and stores intermediate prediction values in a table or array.

**Benefits:**

* Eliminates repeated recursive calls.
* Provides faster access to previously computed results.
* Suitable for large datasets.

---

### 3. Iterative Approach

The recursive algorithm can be replaced with a simple loop that calculates predictions year by year.

**Benefits:**

* Eliminates recursion overhead.
* Prevents stack overflow errors.
* Reduces space complexity from **O(n)** to **O(1)**.

---

## Conclusion

The recursive financial prediction algorithm effectively forecasts future values by repeatedly applying historical growth rates to previous predictions. The algorithm has a **time complexity of O(n)** and a **space complexity of O(n)**. For larger prediction horizons, optimization techniques such as **memoization**, **dynamic programming**, or an **iterative implementation** can improve efficiency and reduce memory usage while maintaining accurate financial forecasts.
