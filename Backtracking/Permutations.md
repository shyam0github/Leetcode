## Naive Approach of Backtracking

```java

// Naive Approach with Backtracking

class Solution {

    public List<List<Integer>> permute(int[] nums) {

        List<List<Integer>> res = new ArrayList<>();

        List<Integer> ds = new ArrayList<>();

        boolean[] freq = new boolean[nums.length];

          allPermutation(nums, res, ds, freq);

          return res;

    }

    public void allPermutation(int[] nums, List<List<Integer>> res, List<Integer> ds, boolean[] freq) {

        if(ds.size() == nums.length){
        res.add(new ArrayList<>(ds));
        return;
        }
        
        for(int i = 0; i < nums.length; i++){
        
            if(!freq[i]){
                ds.add(nums[i]);
                freq[i] = true;

                allPermutation(nums, res, ds, freq);
                
                ds.remove(ds.size() - 1); // delete that element
                freq[i] = false;
            }
        }
}

}
```


## Optimal Approach with Swap: 
This is the **most expected interview solution**.


```java
class Solution {

    public List<List<Integer>> permute(int[] nums) {

        List<List<Integer>> result = new ArrayList<>();
        backtrack(nums, 0, result);
        return result;
    }

    private void backtrack(int[] nums, int index, List<List<Integer>> result) {

        // Base case: one permutation completed
        if (index == nums.length) {
        
            List<Integer> temp = new ArrayList<>();
            
            for (int num : nums) 
            temp.add(num); //### Add modified array which as at the end permute got 
            result.add(temp);
            return;
        }

        // Try all choices for current index
        for (int i = index; i < nums.length; i++) {
            swap(nums, index, i);
            backtrack(nums, index + 1, result);
            swap(nums, index, i); // backtrack to previous array
        }
    }

    private void swap(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
}

```

### Visualize 

![Visulaization](../Image\Pasted-image-20260109194511.png)

---
