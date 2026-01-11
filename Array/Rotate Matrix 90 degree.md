
![[Pasted image 20260111165057.png]]

#### <span style="color:rgb(71, 198, 240)">Remark:</span> Do it in In-Place.

## Out-Place Algo

```java
class Solution {

    public int[][] rotate(int[][] matrix) {
        int[][] res = new int[][];
        int n  = matrix.length;

        for(int i = 0; i < n; i++){
            for(int j = 0; j < matrix[i].length; j++){
                res[j][n-1-i] = matrix[i][j];
            }
        }
        return res;
    }

}
```

## In-Place :

There are two methods :

1. Using left, Right, Top and Bottom and then swapping relevant position until left < Right.  & Increment left and Decrement Right.

2. Doing Transpose of Matrix and then Reversing each Row. 

## Method 1 :

Use 4 pointer left, right, top and bottom.
while left < right 
iterate for range = right - left   // that many times every square swap values

use `i` iterator to swap all values of square.


```java

class Solution {

    public void rotate(int[][] matrix) {

        int left = 0;
        int right = matrix.length - 1;

        while (left < right) {

            for (int i = 0; i < right - left; i++) {

                int top = left;
                int bottom = right;

                int topLeft = matrix[top][left + i];

                // bottom-left -> top-left
                matrix[top][left + i] = matrix[bottom - i][left];

                // bottom-right -> bottom-left
                matrix[bottom - i][left] = matrix[bottom][right - i];

                // top-right -> bottom-right
                matrix[bottom][right - i] = matrix[top + i][right];

                // top-left -> top-right
                matrix[top + i][right] = topLeft;
            }

            left++;
            right--;
        }
    }
}

```


## Method 2 :

Doing Transpose of the matrix & 
then Reversing each Row.

```java

class Solution {
    public void rotate(int[][] matrix) {
        
        int n = matrix.length;

        // transpose
        for (int i = 0; i < n; i++) {
            for (int j = i; j < n; j++) {
                int tmp = matrix[i][j];
                matrix[i][j] = matrix[j][i];
                matrix[j][i] = tmp;
            }
        }

        // reverse each row
        for (int i = 0; i < n; i++) {
            int l = 0, r = n - 1;
            while (l < r) {
                int tmp = matrix[i][l];
                matrix[i][l] = matrix[i][r];
                matrix[i][r] = tmp;
                l++;
                r--;
            }
        }
    }
}

```

---
