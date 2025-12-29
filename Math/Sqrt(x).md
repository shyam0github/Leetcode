# Binary Search 

```java 

class Solution {
    public int mySqrt(int x) {

        if (x == 0) return 0;

        int left = 1;
        int right = x;
        int ans = 0;

        while (left <= right) {
            int mid = left + (right - left) / 2;

            // mid^2 <= x  (avoid overflow)
            
            if (mid <= x / mid) {
                ans = mid;        // store valid result
                left = mid + 1;   // try bigger
            } else {
                right = mid - 1;  // mid too large
            }
        }
        return ans;
    }
}

```


---
# Newton Method 

```java 

class Solution {

    public int mySqrt(int x) {

// NEWTON Formula

        // Edge case
        if (x == 0) return 0;

        long r = x;   // use long to avoid overflow

        // Newton's iteration
        while (r * r > x) {

            r = (r + x / r) / 2;

        }
        return (int) r;
    }
}
```

