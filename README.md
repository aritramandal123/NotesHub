# Exercise 7: Financial Forecasting Tool

## Project Overview
This project implements a financial forecasting tool designed to predict the future value of an asset or investment based on a historical or expected constant growth rate. The core engine utilizes a **recursive algorithm** to compute compounding returns over a specified time horizon.

---

## 1. Understanding Recursive Algorithms

### What is Recursion?
Recursion is a programming technique where a method solves a problem by calling itself with a smaller or simpler input. Every recursive function relies on two primary components:
1. **The Base Case:** The condition under which the function stops calling itself and returns a direct value. Without this, the program would loop indefinitely and crash due to a `StackOverflowError`.
2. **The Recursive Case:** The part of the function where the problem is broken down into a smaller sub-problem, and the function calls itself to solve it.

### How It Simplifies Financial Problems
Financial forecasting often deals with compounding structures (e.g., interest compounding annually). Instead of writing complex loops that manually track and update state variables across iterations, recursion allows us to model the problem exactly how it is defined mathematically:

> **The future value of an investment at Year $N$ is simply the future value at Year $N-1$ multiplied by the growth factor $(1 + \text{growthRate})$.**

By expressing the code in this top-down manner, the logic remains clean, readable, and highly reflective of financial theory.

---

## 2. Setup & Implementation

### The Core Formula
The recursive calculation mirrors the classic time-value-of-money formula:

$$FV = FV_{\text{previous}} \times (1 + \text{growthRate})$$

### Code Structure
The implementation uses a single, clean recursive function to unwind the forecasting period year by year until it reaches the baseline initial investment.

```java
public class FinancialForecaster {

    /**
     * Predicts future value based on a constant annual growth rate using recursion.
     * * @param presentValue The initial investment/value at year 0
     * @param growthRate   The annual growth rate (e.g., 0.07 for 7%)
     * @param years        The number of years to forecast into the future
     * @return The predicted future value
     */
    public static double predictFutureValue(double presentValue, double growthRate, int years) {
        // Base Case: Today's value requires 0 years of forecasting
        if (years <= 0) {
            return presentValue;
        }
        
        // Recursive Case: Reduce the problem size (years - 1) and compound the result
        return predictFutureValue(presentValue, growthRate, years - 1) * (1 + growthRate);
    }

    public static void main(String[] args) {
        double initialInvestment = 10000.0; // $10,000
        double annualGrowth = 0.07;         // 7% growth
        int forecastPeriod = 10;            // 10 years

        System.out.println("--- Financial Forecasting Tool ---");
        double forecastResult = predictFutureValue(initialInvestment, annualGrowth, forecastPeriod);
        System.out.printf("Forecasted Value after %d years: $%,.2f%n", forecastPeriod, forecastResult);
    }
}
