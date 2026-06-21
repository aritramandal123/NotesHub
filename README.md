# Exercise 2: E-commerce Platform Search Function Optimization
> **Cognizant DN 5.0 Deep Skilling Hands-on**  
> **Domain:** Data Structures, Algorithms & Performance Optimization

---

## 🧠 Part 1: Understanding Asymptotic Notation

### 1. What is Big O Notation?
Big O notation is a mathematical framework used to describe the limiting behavior of a function when the argument tends towards a particular value or infinity. In software engineering, it measures the **time complexity** (execution steps) and **space complexity** (memory consumption) of an algorithm relative to the input size ($n$).

Instead of tracking execution time in milliseconds (which fluctuates based on processor speed, background tasks, and language runtimes), Big O isolates the fundamental scalability of the logic. It answers the question: *As the product catalog grows from 100 items to 10,000,000 items, how does the system resource consumption scale?*

### 2. Search Operation Execution Scenarios
To architect resilient software, we evaluate three primary performance boundaries:

*   **Best-Case Scenario ($O(1)$):** The minimum operations required. For both Linear and Binary Search, this happens when the very first item inspected is the target item.
*   **Average-Case Scenario:** The expected resource expenditure over standard, random distributions of inputs. 
*   **Worst-Case Scenario:** The maximum limit of operations an algorithm might perform. This happens when the item is at the final position or completely absent from the dataset. 

> ⚠️ **Engineering Rule:** Systems are always architected around the **Worst-Case Scenario**. Designing around worst-case performance bounds guarantees that our application will not crash or hang under heavy loads or edge-case scenarios.

---

## 📂 Project Architecture

The implementation uses standard Object-Oriented Programming (OOP) paradigms in Java, decoupling the data model entity from the processing search engine framework.

```text
ecommerce-search-optimization/
│
├── src/
│   ├── Product.java           # Data model blueprint & comparison rules
│   └── SearchEngine.java      # Linear & Binary search logic implementations
│
└── README.md                  # Comprehensive technical documentation
