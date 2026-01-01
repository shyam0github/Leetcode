# GFG
## Pattern 8
### Problem
```
Input: 5

Output:

    *
   ***  
  *****
 *******
*********

```

### Code

```java 
class pattern{
public void printpattern(int n){

for(int i = 1; i <= n; i++){

for(int j = 1; j <= n - i; j++){
print(" ");
}

for(int j = 1; j <= 2i - 1; j++){
print("*");
}

}
}
}
```

---
## Pattern 10

### Problem

![[Pasted image 20260101170429.png]]

### Code
```java
class Solution {

    void printTriangle(int n) {

        // Upper half
        for (int i = 1; i <= n; i++) {
            for (int j = 1; j <= i; j++) {
                System.out.print("* ");
            }
            System.out.println();
        }

        // Lower half
        for (int i = n - 1; i >= 1; i--) {
            for (int j = 1; j <= i; j++) {
                System.out.print("* ");
            }
            System.out.println();
        }
    }
}

```

---
## Pattern 11

### Problem
```
Input: 5

Output:

1 
0 1 
1 0 1
0 1 0 1 
1 0 1 0 1

```

### Code

```java
class Solution {

    void printTriangle(int n) {
      
      for(int i = 1; i <= n; i++){
          
          if(i % 2 == 0){
              
              for(int j = i; j > 0; j = j - 2){
                  
                  System.out.print("0 ");
                  System.out.print("1 ");
              }
          }
          
          else{
              
              for(int j = i; j > 0; j--){
                  
                  if(j % 2 == 0) 
                  System.out.print("0 ");
                  
                  else System.out.print("1 ");
              }
          }
          System.out.println();
      }
        
    }
}

```

---

## Pattern 12

### Problem 
```
Input: 5

Output:

1                 1
1 2             2 1
1 2 3         3 2 1
1 2 3 4     4 3 2 1
1 2 3 4 5 5 4 3 2 1

```

This pattern consists of **three parts per row**:

1. Increasing numbers
2. Spaces in the middle
3. Decreasing numbers


```java 

class Solution {

    void printTriangle(int n) {

        for (int i = 1; i <= n; i++) {

            // Left part: increasing numbers
            for (int j = 1; j <= i; j++) {
                System.out.print(j + " ");
            }

            // Middle spaces
            for (int s = 1; s <= 2 * (n - i); s++) {
                System.out.print("  ");
            }

            // Right part: decreasing numbers
            for (int j = i ; j >= 1; j--) {
                System.out.print(j + " ");
            }

            System.out.println();
        }
    }
}

```


#### ✅ Correct Logic Breakdown

For row `i`:

##### 1️⃣ Left increasing numbers

$$  
1 \rightarrow i  
$$

##### 2️⃣ Middle spaces

Each missing number contributes **two spaces**:  
$$  
2 \times (n - i)  
$$

##### 3️⃣ Right decreasing numbers

$$  
(i - 1) \rightarrow 1  
$$

---

#### 🧠 Intuition (Very Important)

- Pattern width is **constant**
- As numbers increase on the left:
    - Spaces decrease in the middle
    - Right side mirrors the left

---

## Pattern 13

```

Input: 5

Output:

1 
2 3 
4 5 6 
7 8 9 10 
11 12 13 14 15

```

```java

class Solution {

    void printTriangle(int n) {
        
        int counter = 1;
        
        for(int i = 1; i <= n; i++){ // Number of Rows
            
            for(int j = 1; j <= i; j++){
            System.out.print(counter+ " ");
            counter++;
            }
            
        System.out.println();
        }
    }
}

```

---
## Pattern 21

### Pattern

```
Input: 4

Output:

****
*  *
*  *
****

```

### Code


---

## Pattern 22


---


