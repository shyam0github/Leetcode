# Find Occurrences of an Element in an Array

```java 

class Solution {

    public int[] occurrencesOfElement(int[] nums, int[] queries, int x) {

        int[] occur = new int[nums.length]; // Storing occurences first occurence at 0 then at 1 and so on

        int trav = 0; // holding the index where next occurence should be stored in Occur

        for(int i = 0; i < nums.length; i++){ // Traversing the nums and storing the occurences in Occur

            if(nums[i] == x)

            occur[trav++] = i;

        }

        int[] result = new int[queries.length]; // result array

        for (int i = 0; i < queries.length; i++) { // Travesing the queries array and..
        
        int k = queries[i];

            if (k > trav) { // if current query or number of occurence is greater than last occur stored in Occur means no occurences of x Present.

                result[i] = -1;

            } else {

                result[i] = occur[k - 1]; // else store the occurences asked by query in result

            }
        }

        return result;
    }

}
```

