# Problem

You are given an array `nums` containing only:

$$  
{0, 1, 2}  
$$

You must sort it **in-place** in **one pass**.

---

# Optimal solution: **Dutch National flag Algo**

## ⭐ Optimal Idea (Dutch National Flag)

We partition the array into **three regions**:

- Left → all `0`s

- Middle → all `1`s
 
- Right → all `2`s

We do this using **three pointers**.

---

## 🧠 Three Pointers Meaning

Let:

- `low` → boundary for `0`

- `mid` → current element

- `high` → boundary for `2`    

Invariant maintained at all times:

$$  
[0 \dots low-1] = 0  
$$  
$$  
[low \dots mid-1] = 1  
$$  
$$  
[mid \dots high] = \text{Unsorted}  
$$  
$$  
[high+1 \dots n-1] = 2  
$$

---

## Code 

```java
class Solution {
    public void sortColors(int[] nums) {

        int low = 0;
        int mid = 0;
        int high = nums.length - 1;

        while (mid <= high) {

            if (nums[mid] == 0) {
                swap(nums, low, mid);
                low++;   // 0 to low-1 all 0's
                mid++;
            }
            else if (nums[mid] == 1) {
                mid++;   // low+1 to mid-1 all 1's
            }
            else { // nums[mid] == 2
                swap(nums, mid, high);
                high--;   // mid to high Unsorted
            }
        }
    }

    private void swap(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
}
```

---

## 🧩 Why Each Case Works

### 🔹 Case 1: `nums[mid] == 0`

- `0` belongs to the **left**

- Swap with `low`    

- Move both pointers


$$  
low++,\ mid++  
$$

---

### 🔹 Case 2: `nums[mid] == 1`

- `1` belongs in the **middle**

- Already in correct region    

$$  
mid++  
$$

---

### 🔹 Case 3: `nums[mid] == 2`

- `2` belongs to the **right**

- Swap with `high`  

- Do **not** increment `mid`    

Why?

Because the element swapped from `high` is **unchecked**.

$$  
high--  
$$

---

## 🧮 Example Dry Run

Input:

```
nums = [2, 0, 2, 1, 1, 0]
```

Steps:

```
mid=0 → swap with high → [0,0,2,1,1,2]
mid=0 → swap with low  → [0,0,2,1,1,2]
mid=1 → swap with low  → [0,0,2,1,1,2]
mid=2 → swap with high → [0,0,1,1,2,2]
mid=2 → 1 → mid++
mid=3 → 1 → mid++
```

Result:

```
[0,0,1,1,2,2]
```

---

## ⏱️ Complexity Analysis

- **Time Complexity**


$$  
O(n)  
$$

- **Space Complexity**


$$  
O(1)  
$$

(in-place, no extra array)

---

# (Naive way) Method with O(2n): 

## Code

Using 3 pointers and <span style="color:rgb(255, 255, 0)">Counting Frequency</span> then feeding frequencies to original array.

```java

class Solution {
    public void sortColors(int[] nums) {

        int[] freq = new int[3];

        // Count frequencies
        for (int num : nums) {
            freq[num]++;
        }
        
        int index = 0;
        
        // Fill 0s
        while (freq[0]-- > 0) {
            nums[index++] = 0;
        }

        // Fill 1s
        while (freq[1]-- > 0) {
            nums[index++] = 1;
        }

        // Fill 2s
        while (freq[2]-- > 0) {
            nums[index++] = 2;
        }
    }
}

```


