# Technique :

Traverse whole array and have variable Maximum and Sum
if sum < 0 make sum = 0; means don't carry negative sum forward.

if maximum < sum ; update maximum 

### for <span style="color:rgb(255, 255, 0)">Subarray</span> have, 2 variables start and end whenever sum == 0 then start = current position .

![Kadane Example](../Image\Pasted-image-20260110192840.png)

## Code

```java

class Solution {

    public int maxSubArray(int[] nums) {
    
        int sum = 0;
        int max = Integer.MIN_VALUE;

        for(int i = 0; i < nums.length; i++){
            sum += nums[i];
            
            if(sum > max)
            max = sum;

            if(sum < 0)
            sum = 0;
        }
        return max;
    }

}
```

----
