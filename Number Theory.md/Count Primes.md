# Problem -- **Given an integer `n`, return _the number of prime numbers that are strictly less than_ `n`.**

## Code --

```java

// Taking boolean Auxillary array and making all the multiple position of current True.

// And Iterating once more and Counting all false values and returning it.

class Solution {
    public int countPrimes(int n) {

        if(n == 0 || n == 1) return 0; //short base condition

        boolean[] flag = new boolean[n];

        for(int i = 2; i <= n/2; i++){

            if(flag[i] == false){

                int multiple = 2;

                while(i*multiple < n){
                    flag[i*multiple] = true;
                    multiple++;
                }
            }
        }
        // Counting all the false position
        
        int count = 0;
        for(int i = 2; i <= n-1; i++){
        if(flag[i] == false) count++;
    }
    return count;
    }
}

```

---
