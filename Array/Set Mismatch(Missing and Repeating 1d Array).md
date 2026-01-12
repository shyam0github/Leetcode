# Missing and Repeating Number in 1-d Array

# **In-Place Index Marking (Best Practical)** ⭐⭐⭐

For each number `x`:

- visit index `abs(x)-1`
- negate it
- if already negative → repeating found

Remaining non-negative index → missing

---

# **(Set Mismatch) — Java Code**


```java

// Iterating and making position as -ve and if already -ve then that is repeating && Iterate once more for missing.

class Solution {

    public int[] findErrorNums(int[] nums) {
        int[] res = new int[2];

        for(int i = 0; i < nums.length; i++){
            int value = Math.abs(nums[i]);

            if(nums[value - 1] < 0) // -1 is here for to balance index
            res[0] = value; // repeating

            else
            nums[value - 1] *= -1;

        }
        for(int i = 0; i < nums.length; i++){

            if(nums[i] > 0)
            res[1] = i + 1;
        }
        return res;
    }
}

```

---

# **Dry Run**

Input:

```
[1,2,2,4]
```

Marked array:

```
[-1,-2,-2,4]
```

- Duplicate = `2`
- Missing = index of positive = `3`

Output:

```
[2,3]
```

---

# **Approach 1 — Mathematical XOR (Optimal)** ⭐

This is the best approach for interviews.

### Core idea:

Let:

- Sum of numbers `1..n` =  
    $$  
    S = \frac{n(n+1)}{2}  
    $$
    
- Sum of squares =  
    $$  
    S2 = \frac{n(n+1)(2n+1)}{6}  
    $$
    

Let:

- `rep` = repeating number
    
- `mis` = missing number
    

Given array sum:

$$  
S' = \sum nums[i]  
$$

Given square sum:

$$  
S2' = \sum nums[i]^2  
$$

We derive:

$$  
S' - S = rep - mis  
$$

and:

$$  
S2' - S2 = rep^2 - mis^2 = (rep - mis)(rep + mis)  
$$

Let:

$$  
A = rep - mis \  
B = rep + mis = \frac{S2' - S2}{A}  
$$

Solve:

$$  
rep = \frac{A + B}{2} \  
mis = rep - A  
$$

### **Complexity**

- Time: $$O(n)$$
    
- Space: $$O(1)$$

---

# **Approach 2 — Frequency / Counting Array**

Create count:

```java
int[] freq = new int[n+1];
for (int x : nums) freq[x]++;
```

Then:

- freq[i] == 2 → repeating
- freq[i] == 0 → missing

### Complexity

- Time: $$O(n)$$
- Space: $$O(n)$$

---

