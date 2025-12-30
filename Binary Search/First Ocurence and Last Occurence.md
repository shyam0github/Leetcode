# Find First and Last Position of Element in Sorted Array

👉 **You cannot truly get both first and last positions in _one pass_ of binary search** because binary search goes only one direction at a time.

#### 2 iteration of Binary Search for first and last position 

```java 

// Using 2 Binary Search for first and last occurence and when,

//nums[mid] == target then continue looking for first or last as per need.

class Solution {

    public int[] searchRange(int[] nums, int target) {

      // edge cases

      if(nums.length == 0) return new int[]{-1, -1};
      if(target < nums[0]) return new int[]{-1, -1};
      if(target > nums[nums.length - 1]) return new int[]{-1, -1};

      int left  = firstpos(nums, target); // calling first 
      int right = lastpos(nums, target);// calling last 

      return new int[]{left, right};

    }
    
    // first position

    public int firstpos(int[] nums, int target){

      int left = 0;
      int right = nums.length - 1;
      int ans = - 1;

      while(left <= right){

        int mid = left + (right - left) / 2;

        if(nums[mid] > target)
        right = mid - 1;

        if(nums[mid] < target)
        left = mid + 1;

        if(nums[mid] == target){
        ans = mid;
        right = mid - 1; // #key: update right and continue

        }
      }

      return ans;
    }
    
     // last position

    public int lastpos(int[] nums, int target){

      int left = 0;
      int right = nums.length - 1;
      int ans = - 1;
      
      while(left <= right){
        int mid = left + (right - left) / 2;

        if(nums[mid] > target)
        right = mid - 1;

        if(nums[mid] < target)
        left = mid + 1;

        if(nums[mid] == target){
        ans = mid;
        left = mid + 1; // #key: update left and continue

        }
      }
      return ans;
    }
}

```

## 🔍 Key Idea

Because the array is sorted, we use **Binary Search**.

But:

- Normal binary search stops at **any occurrence**
- We need **first** and **last**

So we run **binary search twice**:

1. Once biased toward the **left**
2. Once biased toward the **right**

---

## 🧩 <span style="color:rgb(255, 255, 0)">How the Two Searches Differ
</span>
### 🔹 First Occurrence

When `nums[mid] == target`:

- Store index
- Move **left** to find earlier occurrence

```
right = mid - 1  
```

---

### 🔹 Last Occurrence

When `nums[mid] == target`:

- Store index
- Move **right** to find later occurrence

```
left = mid + 1  
```

---

# **Finding them in Single Binary Search **

>**Use one reusable binary-search function** with a small flag  
 instead of writing two completely separate logics.


```java 

class Solution {
    public int[] searchRange(int[] nums, int target) {

        int first = binarySearch(nums, target, true);
        int last  = binarySearch(nums, target, false);

        return new int[]{first, last};
    }

    // isFirst = true  → find first occurrence
    // isFirst = false → find last occurrence
    private int binarySearch(int[] nums, int target, boolean isFirst) {

        int left = 0, right = nums.length - 1;
        int ans = -1;

        while (left <= right) {
            int mid = left + (right - left) / 2;

            if (nums[mid] == target) {
                ans = mid;

                if (isFirst) { // According to flag we update left and right 
                
                    // move left to find earlier occurrence
                    right = mid - 1;
                } else {
                    // move right to find later occurrence
                    left = mid + 1;
                }
            }
            else if (nums[mid] < target) {
                left = mid + 1;
            }
            else {
                right = mid - 1;
            }
        }
        return ans;
    }
}

```
---
