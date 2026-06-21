# Exercise 2: E-commerce Platform Search Function Optimization
> **Cognizant DN 5.0 Deep Skilling Hands-on** > **Domain:** Data Structures, Algorithms & Performance Optimization

---

## 🧠 Part 1: Understanding Asymptotic Notation

### 1. Conceptual Breakdown of Big O Notation
In computer science, **Big O notation** is a theoretical and mathematical framework used to classify algorithms according to their running time or space requirements as the input size ($n$) grows toward infinity. It establishes an algebraic upper bound on the growth rate of an algorithm's execution steps.



When building large-scale software platforms, we cannot rely on physical time (seconds/milliseconds) to judge code efficiency because execution speed changes based on:
* **Hardware variances:** CPU architecture, clock speeds, and available RAM cache memory.
* **Runtime environments:** Garbage collection overhead, background processes, and compiler optimizations.
* **Data types:** Language-specific primitives versus object overhead.

Big O notation solves this by stripping away hardware variables and evaluating the **growth rate of algorithmic steps**. This allows engineers to mathematically predict how an implementation will behave when scaling from small testing environments to massive production datasets.

### 2. Search Operation Execution Scenarios
To architect highly available, resilient backend systems, we evaluate three analytical boundaries for search operations:

#### A. Best-Case Scenario ($O(1)$)
* **Definition:** The absolute minimum number of computational steps required to locate a target resource.
* **E-Commerce Context:** Occurs when the very first item inspected in our array/collection happens to match the target query identifier (`productId`). 
* **Design Value:** Minimal. While ideal, software cannot be architected around best-case assumptions because they represent statistical anomalies in large systems.

#### B. Average-Case Scenario
* **Definition:** The mathematical expectation or average number of steps executed over all possible valid input distributions.
* **E-Commerce Context:** For Linear Search, this equates to checking approximately $n/2$ items. For Binary Search, it approaches $\log_2 n - 1$.
* **Design Value:** Useful for general infrastructure capacity planning and calculating average server response latencies under nominal traffic.

#### C. Worst-Case Scenario
* **Definition:** The mathematical maximum limit of operations an algorithm can possibly perform for an input size of $n$.
* **E-Commerce Context:** Occurs when the requested `productId` is at the absolute end of the array storage layout, or when the item does not exist in the store directory at all.
* **Design Value:** **Critical.** Production systems are strictly designed and stress-tested against worst-case performance profiles. Ensuring a predictable performance floor prevents cascading microservice failures, socket timeouts, and CPU thrashing during peak traffic loads (e.g., flash sales).

---

## 📂 Project Architecture & Setup

The implementation leverages robust Object-Oriented Programming (OOP) paradigms in Java, strictly decoupling data entities from the algorithmic processing core.

```text
ecommerce-search-optimization/
│
├── src/
│   ├── Product.java           # Data model entity (productId, productName, category)
│   └── SearchEngine.java      # Sequential and logarithmic search implementations
│
└── README.md                  # Comprehensive engineering documentation
