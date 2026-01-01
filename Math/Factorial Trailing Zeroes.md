# **172. Factorial Trailing Zeroes — Diagnosis & Correct Approach**

## 🔍 Problem Restatement

You are asked to find the **number of trailing zeros** in:

$$  
n!  
$$

---

## ❌ Why Your Approach Is Incorrect

### ❌ **Mistake 1: Computing the factorial**

Your code does:

```java
int fact = factorial(n);
```

This is invalid because:

- Factorials grow extremely fast
- Even:

$$  
20! = 2{,}432{,}902{,}008{,}176{,}640{,}000  
$$

❌ This does **not fit** in `int` or `long`

Also, the constraint allows very large `n`, so factorial computation is **impossible**.

---

### ❌ **Mistake 2: Recursive factorial causes stack overflow**

Your method:

```java
return n * factorial(n - 1);
```

Recursion depth is:

$$  
O(n)  
$$

For large `n`, this leads to **StackOverflowError**.


---

## ✅ Correct Mathematical Insight

Trailing zeros come from factors of **10**:

$$  
10 = 2 \times 5  
$$

In factorials:

- Factors of $2$ are **plentiful**
- Factors of $5$ are **scarce**

👉 Therefore, trailing zeros depend **only on the number of 5s** in:

$$  
n!  
$$

---

## 🧠 Counting Factors of 5

- Every multiple of $5$ contributes **one** factor of $5$
- Every multiple of $25 = 5^2$ contributes **one extra** factor of $5$
- Every multiple of $125 = 5^3$ contributes **one extra**, and so on

---

## 🧮 Final Formula (Core Equation)

The number of trailing zeros is:

$$  
\left\lfloor \frac{n}{5} \right\rfloor  
+  
\left\lfloor \frac{n}{25} \right\rfloor  
+  
\left\lfloor \frac{n}{125} \right\rfloor

- \cdots  
    $$

We stop when:

$$  
5^k > n  
$$

---

## ✅ Correct Java Solution

```java
class Solution {
    public int trailingZeroes(int n) {

        int count = 0;

        while (n > 0) {
            n /= 5;
            count += n;
        }

        return count;
    }
}
```

---

## ⏱️ Complexity Analysis

- **Time Complexity:**

$$  
O(\log_5 n)  
$$

- **Space Complexity:**

$$  
O(1)  
$$

---

## 🧠 One-Line Diagnosis Summary

> Trailing zeros in $n!$ depend on counting factors of $5$, not on computing $n!$.

---
